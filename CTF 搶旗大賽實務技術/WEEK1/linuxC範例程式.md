```
//1.1 do_while
#include <stdio.h>

int main(void)
{
	int n;
	int mul = 1;
	int i;

	scanf("%d", &n);
	
	i = 1;
	do{
		mul *= i;
		i++;
	}while(i <= n);

	printf("the result is %d\n", mul);

	return 0;
}
```
```
//1.2 err_goto
#include <stdio.h>

int convert(void)
{
	FILE *fp;
	struct stat statbuf;
	char *p, *q;
	int n;
	int res = -1;

	if(stat("test.txt", &statbuf) == -1){
		perror("fail to get stat");
		return res;
	}

	fp = fopen("test.txt", "rb");
	if(fp == NULL){
		perror("fail to open");
		return res;
	}
	
	p = (char *)malloc(sizeof(char) * (statbuf.st_size + 1));
	if(p == NULL){
		perror("fail to malloc");
		goto err1;
	}
	
	n = fread(p, sizeof(char), statbuf.st_size, fp);
	if(n == -1){
		perror("fail to read");
		goto err2;
	}
	*(p + n) = '\0';
	
	q = p;
	while(*q != '\0'){
		if('a' =< *q && *q <= 'z')
			*q += 32;
		printf("%c\n");
		q++;
	}
	
	res = 0;

err2:
	free(p);
err1:
	fclose(fp);

	return res;
}

int main(void)
{
	if(convert() == -1)
		printf("fail to convert\n");

	return 0;
}

```
```
//1.3 for
#include <stdio.h>

int main(void)
{
	int n;
	int add = 0;
	int i;

	scanf("%d", &n);

	for(i = 1; i <= 10; i++)
		add += i;

	printf("the result is %d\n", add);

	return 0;
}

```
```
//1.4 goto
#include <stdio.h>

int main(void)
{
	printf("the begin\n");

	goto end;

	printf("hello world\n");

end:
	printf("the end\n");

	return 0;
}

```
```
//1.5 ifelse
#include <stdio.h>

int main(void)
{
	int a, b;

	scanf("%d%d", &a, &b);

	if(a > b)
		printf("a is higher than b\n");
	else
		printf("a is lower than b\n");

	return 0;
}

```
```
//1.6 ifelse_goto
#include <stdio.h>

int main(void)
{
	int a, b;
	int t;

	scanf("%d%d", &a, &b);

	t = a > b;
	if(t == 1)
		goto true;
	printf("a is lower than b\n");

	goto done;
true:
	printf("a is higher than b\n");

done:
	return 0;
}

```
```
//1.7 sum
#include <stdio.h>

int main(void)
{
	int sum;
	int n;

	scanf("%d", &n);

	sum = ((1 + n) * n) / 2;

	printf("the result is : %d\n", sum);

	return 0;
}

```
```
//1.8 sum_fast
#include <stdio.h>

int main(void)
{
	char score;
	
	scanf("%c", &score);

	switch(score){
	case 'A': 
		printf("excellent\n");
		break;
	case 'B': 
		printf("good\n");
		break;
	case 'C': 
		printf("pass\n");
		break;
	default: 
		printf("fail\n");
	}

	return 0;
}

```
```
//1.9 switch
#include <stdio.h>

int main(void)
{
	int n;
	int mul = 1;
	int i;

	scanf("%d", &n);
	
	i = 1;
	while(i <= n){
		mul *= i;
		i++;
	}

	printf("the result is %d\n", mul);

	return 0;
}

```
```
//1.10 while
#include <stdio.h>

int main(void)
{
	int n;
	int mul = 1;
	int i;

	scanf("%d", &n);
	
	i = 1;
	while(i <= n){
		mul *= i;
		i++;
	}

	printf("the result is %d\n", mul);

	return 0;
}


```
```
//1.10 while_goto
#include <stdio.h>

int main(void)
{
	int n;
	int mul = 1;
	int i;
	int t;

	scanf("%d", &n);

	i = 1;
	t = i <= n;
	if(t == 0)
		goto done;
loop:
	mul *= i;
	i++;
	t = i <= n;
	if(t == 1)
		goto loop;

done:
	printf("the result is %d\n", mul);

	return 0;
}

```
```
//2.1 main
#include <stdio.h>

extern int array[ ];
extern int sum();
extern int get_max();
extern void print();

int main(void)
{
	int all, max;

	all = sum();
	max = get_max();
	print();
	printf("the sum : %d, the max : %d\n", all, max);

	return 0;
}

```
```
//2.2 operate
#include <stdio.h>

#define MAX 5
int array[MAX] = {2,7,6,4,8, };

int sum()
{
	int i;
	int n;

	n = 0;
	for(i = 0; i < MAX; i++)
		n += array[i];

	return n;
}

int get_max()
{
	int max;
	int i;
	
	i = 0;
	max = array[i];
	for(i = 0; i < MAX; i ++) 
		if(array[i] > max)
			max = array[i];

	return max;
}


void print()
{
	int i; 

	for(i = 0; i < MAX; i++)
		printf("array[%d] : %d\n", i + 1, array[i]);
}

```
```
//2.3 cmp
#include "common.h"

int cmp_int(void *p, void *q)
{
	int *a, *b;
	a = (int *)p;
	b = (int *)q;
	
	if(*a > *b)
		return 1;
	else if(*a < *b)
		return -1;
	else
		return 0;
}

int cmp_struct(void *p, void *q)
{
	Book a, b;
	
	a = (Book)p;
	b = (Book)q;

	if(a->id > b->id)
		return 1;
	else if(a->id < b->id)
		return -1;
	else
		return 0;
}

```
```
//2.4 common
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

typedef int (*cmp)(void *, void *);

typedef struct book * Book;

struct book{
	int id;
	char name[10];
};

extern void *max(void *array[], int len, cmp func);

extern int cmp_int(void *p, void *q);
extern int cmp_struct(void *p, void *q);

extern int insert_struct(Book *pos, int id, char * name);
extern int insert_int(int **pos, int val);

```
```
//2.5 main max
#include "common.h"

#define MAX 3

int main(void)
{
	Book array1[MAX];
	int *array2[MAX];
	int i;
	int id;
	int val;
	char name[10];
	Book res1;
	int *res2;

	for(i = 0; i < MAX; i++){
		printf("input info of book\n");
		scanf("%d", &id);
		scanf("%s", name);
		if(insert_struct(&(array1[i]), id, name) == -1)
			exit(1);

		printf("input int\n");
		scanf("%d", &val);
		if(insert_int(&(array2[i]), val) == -1)
			exit(1);
	}

	res1 = (Book)max(array1, MAX, cmp_struct);
	res2 = (int *)max(array2, MAX, cmp_int);

	printf("the max of books : %d, %s\n", res1->id, res1->name);
	printf("the max of int : %d\n", *res2);

	return 0;
}

```
```
//2.6 obj
#include "common.h"

void *max(void *array[], int len, cmp func)
{
	int i;
	void *tmp;

	tmp = array[0]; 
	for(i = 1; i < len; i++) { 
		if((*func)(tmp, array [i]) == -1)
			tmp = array [i];
	}
	
	return tmp;
}

```
```
//2.7 local
#include "common.h"

int insert_struct(Book *pos, int id, char * name)
{
	Book p;

	p = (Book)malloc(sizeof(struct book));
	if(p == NULL){
		perror("fail to malloc");
		return -1;
	}

	p->id = id;
	strcpy(p->name, name); 

	*pos = p; 
	
	return 0;
}

int insert_int(int **pos, int val)
{
	int *p;
	
	p = (int *)malloc(sizeof(int)); 

	*p = val; 
	*pos = p; 
	
	return 0;
}

```
```
//2.8 my_printf
#include <stdio.h>

int add(int a, int b)
{
	return a + b; 
}

int main(void)
{
	int array[5]; 
	int i;

	while(i < 5){
		int res; 

		res = add(i, 1); 
		array[i] = res; 
	}
	
	for(i = 0; i < 10; i++)
		printf("array[%d] : %d\n", i + 1, array[i]); 

	return 0;
}

```
```
//2.9 optim
#include <stdio.h>
#include <stdarg.h>
#include <string.h>

#define MAX 64

char * itoa(int n, char *p)
{
	char *q;

	if(p == NULL)
		return NULL;

	p[0] = (n / 10000) + '0';
	n = n % 10000;
	p[1] = (n / 1000) + '0';
	n = n % 1000;
	p[2] = (n / 100) + '0';
	n = n % 100;
	p[3] = (n / 10) + '0';
	n = n % 10;
	p[4] = n + '0';
	p[5] = '\0';
	
	q = p;
	while(*q != '\0' && *q != '0')
		q++;
	
	if(*q == '\0')
		return p;
	strcpy(p, q);

	return p;
}

int my_printf(const char *format, ...)
{
	va_list ap;
	char c, ch;
	int i;
	char *p;
	int n = 0;
	char buf[MAX];

	va_start(ap, format); 

	c = *format;
	while(c != '\0'){
		if(c == '%'){
			format++; 
			c = *format;
			
			switch(c){
			case 'c': 
				ch = va_arg(ap, int); 
				putchar(ch); 
				n++;
				break;

			case 'd':
				i = va_arg(ap, int); 
				itoa(i, buf); 
				n += strlen(buf); 
				fputs(buf, stdout); 
				break;

			case 's': 
				p = va_arg(ap, char *);
				n += strlen(p);
				fputs(p, stdout); 
			}
		}else{
			putchar(c); 
			n++;
		}
		
		format++; 
		c = *format;
	}
	
	va_end(ap); 

	return n; 
}

int main(void)
{
	my_printf("the char is : %c\n, the number is : %d\n, the string is : %s\n", 'a', 100, "hello world\n"); 
	
	return 0;
}

```
```
//2.10 print_args
#include <stdio.h>

int count = 0; 

int func(int a)
{
	count++; 
	return a + 1; 
}

int main(void)
{
	int res;

	res = 4 * func(1); 
	
	printf("the count : %d\n", count); 
	printf("the result : %d\n", res);

	return 0;

}

```
```
//2.11
#include <stdio.h>
#include <stdarg.h>

int print_args(int begin, ...)
{
	va_list ap;
	char *p;
	int n;

	va_start(ap, begin);
	p = va_arg(ap, char *);
	n = 0;

	while(p != NULL){
		n++;
		
		printf("arg %d : %s\n", n, p);
	
		p = va_arg(ap, char*);
	}
	
	va_end(ap);

	return n;
}

int main(void)
{
	int n;
	
	n = print_args(-1, "hello", "world", NULL);
	printf("first, without NULL : %d\n", n);
	
	n = print_args(-1, "China", "beijing", "Olympic", NULL);
	printf("second, without NULL : %d\n", n);

	return 0;
}

```
```
//2.12 static_local
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

#define MAX 1024

int output(char *file_name)
{
	FILE *fp;
	char buf[MAX];	
	static int count = 0;
	int n;

	fp = fopen(file_name, "r");
	if(fp == NULL){
		perror("fail to open");
		return -1;		
	}
	
	while(fgets(buf, MAX, fp) != NULL){
		n = strlen(buf);
		buf[n - 1] = '\0';

		printf("%s\n", buf); 

		if(count++ % 5 == 0)
			printf("\n");
	}

	fclose(fp);
	
	return 0;
}

int main(void)
{
	char file_name[][10] = {"test.txt", 
					"test1.txt",
					"test2.txt"
					};
	int i;
	
	i = 0;
	while(i < 3){
		if(output(file_name[i]) == -1)
			exit(1);
		i++;
	}

	return 0;
}

```
```
//3.1 cmp
#include "common.h"

int cmp_int(void *p, void *q)
{
	int *a, *b;
	a = (int *)p;
	b = (int *)q;
	
	if(*a > *b)
		return 1;
	else if(*a < *b)
		return -1;
	else
		return 0;
}

int cmp_struct(void *p, void *q)
{
	Book a, b;
	
	a = (Book)p;
	b = (Book)q;

	if(a->id > b->id)
		return 1;
	else if(a->id < b->id)
		return -1;
	else
		return 0;
}

```
```
//3.2 common
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

typedef int (*cmp)(void *, void *);

typedef struct book * Book;

struct book{
	int id;
	char name[10];
};

extern void *max(void *array[], int len, cmp func);

extern int cmp_int(void *p, void *q);
extern int cmp_struct(void *p, void *q);

extern int insert_struct(Book *pos, int id, char * name);
extern int insert_int(int **pos, int val);

```
```
//3.3 main
#include "common.h"

#define MAX 3

int main(void)
{
	Book array1[MAX];
	int *array2[MAX];
	int i;
	int id;
	int val;
	char name[10];
	Book res1;
	int *res2;

	for(i = 0; i < MAX; i++){
		printf("input info of book\n");
		scanf("%d", &id);
		scanf("%s", name);
		if(insert_struct(&(array1[i]), id, name) == -1)
			exit(1);

		printf("input int\n");
		scanf("%d", &val);
		if(insert_int(&(array2[i]), val) == -1)
			exit(1);
	}

	res1 = (Book)max(array1, MAX, cmp_struct);
	res2 = (int *)max(array2, MAX, cmp_int);

	printf("the max of books : %d, %s\n", res1->id, res1->name);
	printf("the max of int : %d\n", *res2);

	return 0;
}

```
```
//3.4 max
#include "common.h" 

void *max(void *array[], int len, cmp func)
{
	int i;
	void *tmp;

	tmp = array[0]; 
	for(i = 1; i < len; i++) { 
		if((*func)(tmp, array [i]) == -1)
			tmp = array [i];
	}
	
	return tmp;
}

```
```
//3.5 obj
#include "common.h"

int insert_struct(Book *pos, int id, char * name)
{
	Book p;

	p = (Book)malloc(sizeof(struct book));
	if(p == NULL){
		perror("fail to malloc");
		return -1;
	}

	p->id = id;
	strcpy(p->name, name); 

	*pos = p; 
	
	return 0;
}

int insert_int(int **pos, int val)
{
	int *p;
	
	p = (int *)malloc(sizeof(int)); 

	*p = val; 
	*pos = p; 
	
	return 0;
}

```
```
//3.6 cmp
#include "common.h"

int cmp_int(void *p, void *q)
{
	int *a, *b;
	a = (int *)p;
	b = (int *)q;
	
	if(*a > *b)
		return 1;
	else if(*a < *b)
		return -1;
	else
		return 0;
}

int cmp_struct(void *p, void *q)
{
	Book a, b;
	
	a = (Book)p;
	b = (Book)q;

	if(a->id > b->id)
		return 1;
	else if(a->id < b->id)
		return -1;
	else
		return 0;
}

```
```
//3.7 common
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

typedef int (*cmp)(void *, void *);

typedef struct book * Book;

struct book{
	int id;
	char name[10];
};

extern void *max(void *array[], int len, cmp func);

extern int cmp_int(void *p, void *q);
extern int cmp_struct(void *p, void *q);

extern int insert_struct(Book *pos, int id, char * name);
extern int insert_int(int **pos, int val);

```
```
//3.8 main
#include "common.h"

#define MAX 3

int main(void)
{
	Book array1[MAX];
	int *array2[MAX];
	int i;
	int id;
	int val;
	char name[10];
	Book res1;
	int *res2;

	for(i = 0; i < MAX; i++){
		printf("input info of book\n");
		scanf("%d", &id);
		scanf("%s", name);
		if(insert_struct(&(array1[i]), id, name) == -1)
			exit(1);

		printf("input int\n");
		scanf("%d", &val);
		if(insert_int(&(array2[i]), val) == -1)
			exit(1);
	}

	res1 = (Book)max(array1, MAX, cmp_struct);
	res2 = (int *)max(array2, MAX, cmp_int);

	printf("the max of books : %d, %s\n", res1->id, res1->name);
	printf("the max of int : %d\n", *res2);

	return 0;
}

```
```
//3.9 max
#include "common.h"

void *max(void *array[], int len, cmp func)
{
	int i;
	void *tmp;

	tmp = array[0]; 
	for(i = 1; i < len; i++) { 
		if((*func)(tmp, array [i]) == -1)
			tmp = array [i];
	}
	
	return tmp;
}

```
```
//3.10 obj
#include "common.h"

int insert_struct(Book *pos, int id, char * name)
{
	Book p;

	p = (Book)malloc(sizeof(struct book));
	if(p == NULL){
		perror("fail to malloc");
		return -1;
	}

	p->id = id;
	strcpy(p->name, name); 

	*pos = p; 
	
	return 0;
}

int insert_int(int **pos, int val)
{
	int *p;
	
	p = (int *)malloc(sizeof(int)); 

	*p = val; 
	*pos = p; 
	
	return 0;
}

```
```
//3.11 malloc
#include <stdio.h>
#include <stdlib.h>

void alter(int ** p)
{
	int *q;
	
	q = (int *)malloc(sizeof(int)); 

	*q = 100; 
	*p = q; 
}

int main(void)
{
	int a;
	int *p;

	a = 10; 
	p = &a; 

	printf("p : 0x%x, *p %d\n", p, *p);
	alter(&p); 
	printf("p : 0x%x, *p %d\n", p, *p);

	return 0;
}

```
```
//3.12 pointer 
#include <stdio.h>

struct test{
	int array[2];
	char ch;
};

typedef struct test Test;

int main(void)
{
	Test var = {0x12345678, 0x12345678, 0x30};
	char *p;

	p = (char *)&var;
	printf("1 byte : 0x%d\n", *p);

	p = (short *)p;
	printf("2 bytes : 0x%d\n", *p);

	p = (int *)p;
	printf("4 bytes : 0x%d\n", *p);

	p = (long long *)p;
	printf("8 bytes : 0x%d\n", *p);

	p = (Test *)p;
	printf("whole bytes : 0x%d, 0x%d, %c", p->array[0], p->array[1], p->ch);

	return 0;
}

```
```
//3.13 pointer_pointer
#include <stdio.h>

int main(void)
{
	int a;
	int *p;
	int **q;

	a = 100;
	p = & a;
	q = &p;

	printf("var a : %d\n", a);
	printf("pointer p : 0x%x\n", *p);
	printf("pointer pointer q : 0x%x\n", *q);

	return 0;
}

```
```
//3.14 replace

#include <stdio.h>

const char * replace(const char *str)
{
	const char *p; 

	if(str == NULL)
		return NULL;

	p = str;
	while(*p != '\0'){
		if(*p == ' ')
			*p = '_';
		p++;
	}

	return p;
}

int main(void)
{
	const char *p = "hello world and China\n"; 

	if(replace(p) != NULL) 
		printf("the string : %s");

	return 0;
}

```
```
//3.15 type
#include <stdio.h>

int main(void)
{
	printf("int : %d\n", sizeof(int));

	printf("short : %d\n", sizeof(short));

	printf("char : %d\n", sizeof(char));

	printf("unsigned int : %d\n", sizeof(unsigned));

	printf("long : %d\n", sizeof(long));

	printf("long long: %d\n", sizeof(long long));

	printf("float : %d\n", sizeof(float));

	printf("deouble : %d\n", sizeof(deouble));

	printf("long deouble : %d\n", sizeof(long deouble));

	return 0;
}

```
```
//4.1 normal
#include <stdio.h>

int main(void)
{
	int a = 31;
	int x = 0xFFFFFFFF;  

	printf("the first is : %d\n",  0xFFFFFFFF >> 31) ;  
	printf("the second is : %d\n",  x >> 31) ;  
	printf("the third is : %d\n",  0xFFFFFFFF >> a) ;

	return 0;
}

```
```
//4.2 sort
#include <stdio.h>

extern void bubble_sort(int *array, int len);

#define DEBUG 1  
#ifdef DEBUG
#define PRINT(str) printf(str);  
#define PRINT1(str, arg); printf(str, arg);  
#else
#define PRINT(str) ;  
#define PRINT1(str, arg); ;
#endif

int main(void)
{
	int array[5] = {1,2,4,3, 0};
	int i;

	PRINT("before sort\n");

	bubble_sort(array, 5);  

	PRINT("after sort\n");

	for(i = 0; i < 5; i++)
		PRINT("%d\n", array[i]);  

	return 0;
}

```
```
//4.3 struct
#include <stdio.h>

struct test{  
	int array[5];
	int a;
	int *p;
};  

int main(void)
{	
	struct test var;  
	int i;

	 
	for(i = 0; i < 5; i++)
		printf("array [%d] : 0x%x\n", i + 1, &(var.array[i]));  
	printf("a : 0x%x\n", &(var.a));  
	printf("p : 0x%x\n", &(var.p));  

	return 0;
}

```
```
//5.1 longjmp
#include <stdio.h>
#include <setjmp.h>

jmp_buf env;

void f(void)
{
	longjmp(env, 10); 
}

int main(void)
{
	int val;
	
	val = setjmp(env); 
	if(val != 0) 
		printf("after long jump, the value is %d\n", val);
	else
		printf("ready to jump\n");

	f(); 

	return 0;
}

```
```
//5.2 malloc
#include <stdio.h>
#include <stdlib.h>

void f1(int **p)
{
	*p = (int *)malloc(sizeof(int));
}

void f2(int *p)
{
	printf("the heap is %d\n", *p);
}

int main(void)
{
	int *p;
			
	f1(&p);
	*p = 4;
	f2(p);

	free(p); 
	f2(p); 
	
	return 0;
}

```
```
//5.3 putenv
#include <stdio.h>
#include <stdlib.h>

int main(void)
{
	char * p;
	
	p = getenv("HOME");
	if(p == NULL){
		perror("fail to putenv");
		exit(1);
	}
	printf("$HOME is %s\n", p);
	
	if(putenv("HOME=/home/admin") == -1){
		perror("fail to putenv");
		exit(1);
	}
	
	p = getenv("HOME");
	if(p == NULL){
		perror("fail to putenv");
		exit(1);
	}
	printf("$HOME is %s \n", p); 

	if(putenv("ADMIN=hello") == -1){ 
		perror("fail to putenv");
		exit(1);
	}

	p = getenv("ADMIN");
	if(p == NULL){
		perror("fail to putenv");
		exit(1);
	}
	printf("$ADMIN is %s \n", p); 

	return 0;
}

```
```
//5.4 rindex
#include <stdio.h>

char* basename(char*  full_name)
{
		char *p;
		
		p = rindex(full_name,'/');
		
		if (p == '\0')  	
			p = full_name; 
		else 
			p++; 
		
		return p; 
}

int main(int argc, char * argv[])
{
	char *p;
	
	p = basename(argv[0]);
	printf("file name is : %s\n", p); 
	
	return 0;
}

```
```
//5.5 setenv
#include <stdio.h>
#include <stdlib.h>

int main(void)
{
	char * p;
	
	p = getenv("HOME"); 
	if(p == NULL){
		perror("fail to putenv");
		exit(1);
	}
	printf("$HOME is %s\n", p); 
	
	if(setenv("HOME", "/home/admin", 0) == -1){ 
		perror("fail to putenv");
		exit(1);
	}
	
	p = getenv("HOME"); 
	if(p == NULL){
		perror("fail to putenv");
		exit(1);
	}
	printf("$HOME is %s \n", p); 

	if(setenv("HOME", "/home/admin", 1) == -1){ 
		perror("fail to putenv");
		exit(1);
	}

	p = getenv("HOME"); 
	if(p == NULL){
		perror("fail to putenv");
		exit(1);
	}
	printf("$ HOME is %s \n", p);

	return 0;
}

```
```
//5.6 unsetenv
#include <stdio.h>
#include <stdlib.h>

int main(void)
{
	char * p;
	
	p = getenv("HOME"); 
	if(p == NULL){
		perror("fail to putenv");
		exit(1);
	}
	printf("$HOME is %s\n", p); 
	
	if(unsetenv("HOME") == -1){ 
		perror("fail to putenv");
		exit(1);
	}
	
	p = getenv("HOME"); 
	if(p == NULL){
		perror("fail to putenv");
		exit(1);
	}
	printf("$HOME is %s \n", p); 

	if(setenv("HOME", "/home/admin", 1) == -1){ 
		perror("fail to putenv");
		exit(1);
	}

	p = getenv("HOME"); 
	if(p == NULL){
		perror("fail to putenv");
		exit(1);
	}
	printf("$ HOME is %s \n", p); 

	return 0;
}

```
