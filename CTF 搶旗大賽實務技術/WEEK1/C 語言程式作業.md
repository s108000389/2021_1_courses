#  250題練習
```
https://tutorialsbookmarks.com/c-programming-questions-and-answers-pdf/
https://docs.google.com/document/d/1jFAATUSQdrrqmppvStE9X2vw5wJc-HUEaUa-paw3Ulg/edit
```

# 範例 1
```
1. Simple C Questions

   Area and Circumference of a Circle
```
### C 解答
```
https://www.programmingwithbasics.com/2016/03/c-program-to-find-area-and.html
```
```
#include<stdio.h>
int main()
{
   /*Program By Ghanendra Yadav
   Visit http://www.programmingwithbasics.com/
  */
   int rad;
   float PI = 3.14, area, ci;

   printf("\nEnter radius of circle: ");
   scanf("%d", &rad);

   area = PI * rad * rad;
   printf("\nArea of circle : %f ", area);

   ci = 2 * PI * rad;
   printf("\nCircumference : %f ", ci);

   return (0);
}
```
### C++ 解答
```
https://www.programmingwithbasics.com/2016/12/c-program-to-find-area-and.html
```

```
#include <iostream>
using namespace std;
int main()
{
/*Program By Ghanendra Yadav
Visit http://www.programmingwithbasics.com/
*/
int rad;

float PI = 3.14, area, ci;
cout<<"Enter radius of circle: ";
cin>>rad;
area = PI * rad * rad;
cout<<"Area of circle "<< area<<endl;
ci = 2 * PI * rad;
cout<<"Circumference of circle "<< ci<<endl;
return (0);
}
```
### JAVA 解答
```
https://www.programmingwithbasics.com/2016/12/java-program-to-find-area-and.html
```

```
/* Program By Ghanendra Yadav
   Visit http://www.programmingwithbasics.com/
*/
import java.util.Scanner;
class circle
{
   static Scanner sc = new Scanner(System.in);
   public static void main(String args[])
   {
      System.out.print("Enter The Radius Of Circle: ");
      double radius = sc.nextDouble();
      
   double area = Math.PI * (radius * radius);
      System.out.println("Circle Area is : " + area);
      
   double circumference= Math.PI * 2*radius;
      System.out.println( "Circle Circumference is:"+circumference);
   }
}
```
