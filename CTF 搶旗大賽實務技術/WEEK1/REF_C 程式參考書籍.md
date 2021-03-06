# 參考書
```
C 語言教學手冊, 4/e
繁體中文/洪維恩/旗標出版日期：2007-04-19
```
```
C語言從入門到精通（微視頻精編版）
明日科技  清華大學  2019-10-01
```
```
Linux C 從入門到精通, 2/e Linux C从入门到精通（第2版）
明日科技  清華大學   2018-10-01
https://www.tenlong.com.tw/products/9787302498803
```
```
C語言項目開發全程實錄（第2版）（軟件項目開發全程實錄）
簡體中文/明日科技/清華大學出版社出版日期：2018-05-01
https://www.tenlong.com.tw/products/9787302498827

火車訂票系統、通訊錄管理系統、學生個人消費管理系統、企業員工管理系統、超級萬年曆、
貪吃蛇遊戲、學生信息管理系統、圖書管理系統、網絡通信系統、
窗體版圖書管理系統、商品管理系統和MP3音樂播放器
共12個實際項目開發程序為案例
```
# 進階
```
透視 C 語言指標－深度探索記憶體管理核心技術 
Understanding and Using C Pointers
Richard Reese 著、莊弘祥 譯
歐萊禮  2013-10-24

https://github.com/faquir-1990/itBooks/blob/master/understanding-and-using-c-pointers.pdf

介紹指標，包含不同指標型態的宣告
‧學習動態記憶體配置、釋放以及其他記憶體管理技巧
‧使用將資料傳入函數或自函數中傳回的技巧
‧透過陣列與指標的關係理解陣列的基礎概念
‧介紹字串的基礎，以及指標的各種字串操作
‧瞭解指標各能造成的安全問題，如緩衝區溢位
‧學習各種指標技巧，如不透明指標（opaque pointer）、有界指標（bounded pointer）以及使用 restrict 關鍵字

第一章 入門
第二章 C語言的動態記憶體管理
第三章 指標與函數
第四章 指標與陣列
第五章 指標與字串
第六章 指標與結構體
第七章 安全問題與不當使用指標
第八章 其他補充

1. Introduction
Pointers and Memory
Why You Should Become Proficient with Pointers
Declaring Pointers
How to Read a Declaration
Address of Operator
Displaying Pointer Values
Virtual memory and pointers
Dereferencing a Pointer Using the Indirection Operator
Pointers to Functions
The Concept of Null
To NULL or not to NULL
Pointer to void
Global and static pointers
Pointer Size and Types
Memory Models
Predefined Pointer-Related Types
Understanding size_t
Using the sizeof operator with pointers
Using intptr_t and uintptr_t
Pointer Operators
Pointer Arithmetic
Adding an integer to a pointer
Pointers to void and addition
Subtracting an integer from a pointer
Subtracting two pointers
Comparing Pointers
Common Uses of Pointers
Multiple Levels of Indirection
Constants and Pointers
Pointers to a constant
Constant pointers to nonconstants
Constant pointers to constants
Pointer to (constant pointer to constant)

2. 動態記憶體管理Dynamic Memory Management in C
Dynamic Memory Allocation
Memory Leaks
Losing the address
Hidden memory leaks
Dynamic Memory Allocation Functions
Using the malloc Function
To cast or not to cast
Failing to allocate memory
Not using the right size for the malloc function
Determining the amount of memory allocated
Using malloc with static and global pointers
Using the calloc Function
Using the realloc Function
The alloca Function and Variable Length Arrays
Deallocating Memory Using the free Function
Assigning NULL to a Freed Pointer
Double Free
The Heap and System Memory(系統記憶體)
Freeing Memory upon Program Termination
Dangling Pointers
Dangling Pointer Examples
Dealing with Dangling Pointers
Debug Version Support for Detecting Memory Leaks
Dynamic Memory Allocation Technologies
Garbage Collection in C
Resource Acquisition Is Initialization
Using Exception Handlers

3. Pointers and Functions 使用 指標 存取 陣列
Program Stack(堆疊) and Heap(堆積)
Program Stack
Organization of a Stack Frame
Passing and Returning by Pointer
Passing Data Using a Pointer
Passing Data by Value
Passing a Pointer to a Constant
Returning a Pointer
Pointers to Local Data
Passing Null Pointers
Passing a Pointer to a Pointer
Writing your own free function
Function Pointers
Declaring Function Pointers
Using a Function Pointer
Passing Function Pointers
Returning Function Pointers
Using an Array of Function Pointers
Comparing Function Pointers
Casting Function Pointers

4. Pointers and Arrays 使用 指標 存取 陣列
Quick Review of Arrays
One-Dimensional Arrays
Two-Dimensional Arrays
Multidimensional Arrays
Pointer Notation and Arrays
Differences Between Arrays and Pointers
Using malloc to Create a One-Dimensional Array
Using the realloc Function to Resize an Array
Passing a One-Dimensional Array
Using Array Notation
Using Pointer Notation
Using a One-Dimensional Array of Pointers
Pointers and Multidimensional Arrays
Passing a Multidimensional Array
Dynamically Allocating a Two-Dimensional Array
Allocating Potentially Noncontiguous Memory
Allocating Contiguous Memory
Jagged Arrays and Pointers

5. Pointers and Strings  使用 指標 存取 字串
String Fundamentals
String Declaration
The String Literal Pool
When a string literal is not a constant
String Initialization
Initializing an array of char
Initializing a pointer to a char
Initializing a string from standard input
Summary of string placement
Standard String Operations
Comparing Strings
Copying Strings
Concatenating Strings
Passing Strings
Passing a Simple String
Passing a Pointer to a Constant char
Passing a String to Be Initialized
Passing Arguments to an Application
Returning Strings
Returning the Address of a Literal
Returning the Address of Dynamically Allocated Memory
Returning the address of a local string
Function Pointers and Strings

6. Pointers and Structures 使用 指標 存取 結構體
Introduction
How Memory Is Allocated for a Structure
Structure Deallocation Issues
Avoiding malloc/free Overhead
Using Pointers to Support Data Structures
Single-Linked List
Using Pointers to Support a Queue
Using Pointers to Support a Stack
Using Pointers to Support a Tree

7. Security Issues and the Improper Use of Pointers
Pointer Declaration and Initialization
Improper Pointer Declaration
Failure to Initialize a Pointer Before It Is Used
Dealing with Uninitialized Pointers
Pointer Usage Issues
Test for NULL
Misuse of the Dereference Operator
Dangling Pointers
Accessing Memory Outside the Bounds of an Array
Calculating the Array Size Incorrectly
Misusing the sizeof Operator
Always Match Pointer Types
Bounded Pointers
String Security Issues
Pointer Arithmetic and Structures
Function Pointer Issues
Memory Deallocation Issues
Double Free
Clearing Sensitive Data
Using Static Analysis Tools

8. Odds and Ends
Casting Pointers
Accessing a Special Purpose Address
Accessing a Port
Accessing Memory using DMA
Determining the Endianness of a Machine
Aliasing, Strict Aliasing, and the restrict Keyword
Using a Union to Represent a Value in Multiple Ways
Strict Aliasing
Using the restrict Keyword
Threads and Pointers
Sharing Pointers Between Threads
Using Function Pointers to Support Callbacks
Object-Oriented Techniques
Creating and Using an Opaque Pointer
Polymorphism in C
```
