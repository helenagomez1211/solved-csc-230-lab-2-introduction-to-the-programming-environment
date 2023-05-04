Download Link: https://assignmentchef.com/product/solved-csc-230-lab-2-introduction-to-the-programming-environment
<br>
As a test of the C toolchain, copy and paste the following hello world program into a text editor and save it as helloworld.c (on drive H).

#include &lt;stdio.h&gt;

int main() {

printf(“Hello World
”);

return 0;

}

Open a command prompt and navigate to the location of your file (e.g., by running “H:” and then “cd csc230”). You should be able to compile your code with a command like the following.

gcc -Wall -std=gnu99 -o helloworld helloworld.c

Note that the flags -Wall and -std=gnu99 are optional. The -Wall flag enables all compiler warnings which can be helpful for debugging. The -std=gnu99 flag ensures that the compiler allows modern features of the language without complaining.

The -o flag allows us to name the resulting binary file. After compiling, you can run your program from the windows command prompt with the command helloworld. You can also run the program directly from the file browser by double-clicking the newly created binary file.

C has many standard libraries. In the example above, we used a function called printf() from the Standard Input and Output library (stdio.h). It produces formatted output, more information about it and other functions in the library can be found here: <u>http://www.cplusplus.com/reference/cstdio/</u>.

<h1>II.  User Input</h1>

We can read formatted input from the user using the standard library function scanf() as illustrated in the following program.

#include &lt;stdio.h&gt;

int main() {

int number = 0;

printf(“Please enter a number: “);      scanf(“%d”, &amp;number);

printf(“The number entered is: %d
”, number);

return 0;

}

Note that “%d” specifies the format of input and output, in this case, a positive or negative integer. Also note that “&amp;number” means “the address of the variable called number”, in other words, the memory location where the number is stored.

III.  Width (or size) of C Variables of Different Types

Consider the following C program; what happens to the output when the type of <em>i </em>is changed to <em>unsigned char </em>or <em>unsigned short int</em>? How can we find out what the width of any C type is?

#include &lt;stdio.h&gt;

int main() {

unsigned int i = 0x12345678;

printf(“The value of i in hex is %08x
”, i);

return 0;

}

<h1>IV.  Bitwise Operators</h1>

The following example program illustrates how to use the bitwise operator AND, you can use this code framework for testing other bitwise operations.

You should be able to perform all of the primary bitwise operations (and, or, exclusive or, complement, left and right logical and arithmetic shifts, rotations) yourself, without electronic assistance (although not necessarily in your head). However, when studying or working on assignments, it can be very helpful to write small C programs to verify bitwise arithmetic among other things.

<table width="681">

 <tbody>

  <tr>

   <td width="681"> #include &lt;stdio.h&gt;int main(){unsigned char x = 0x12;        unsigned char y = 0x34;unsigned char z = x &amp; y;      // Change the bitwise operation hereprintf(“The value of z in hex is %02x
”, z);return 0;}</td>

  </tr>

 </tbody>

</table>

Developing some degree of fluency in binary and hexadecimal is crucial for a course in low-level programming. Once we begin assembly language programming, you will need to use raw binary and hex representations for many programming tasks.

<h1>V.  Recursion</h1>

Sometimes a problem is easier to solve via recursion, for example, when traversing a tree data structure or enumerating number series like the Fibonacci sequence. For a much simpler example, which we could easily solve using a loop, consider a program that counts from 0 up to a given number using recursion. To do this, we need a recursive function, which is a function has two important design components: a stopping condition (base case) and a recursive step (calling itself). Following is the code for the program described above.

#include &lt;stdio.h&gt;

void count_down(unsigned int);  // forward declaration

int main() {

unsigned int number = 0;

printf(“Please enter a positive number between 0 and 65,535: “);     scanf(“%d”, &amp;number);

count_down(number);

return 0;

}

<table width="681">

 <tbody>

  <tr>

   <td width="681"> void count_down(unsigned int number) {if(number == 0) return;     // base casecount_down(number – 1);     // recursive stepprintf(“%d
”, number);     // processing} </td>

  </tr>

 </tbody>

</table>




A recursive function can do some work before the recursive step, after the recursive step, or, if there are multiple recursive cases, it can do some work in-between them. In the above example, the function prints its number after the recursive step, what would happen if the print happened before the recursive step instead of the way it is now?

<strong>  </strong>

<h1>VI.  Exercises</h1>

<ol>

 <li>Write a C program called check_even.c that checks if a given integer is even or odd. This program should prompt (ask) its user to provide a value between 0 and 255. Then, it would store this value as an 8-bit unsigned integer, check if it is even or odd, and print the corresponding message on the screen (e.g., “The number is odd”). If the user inputs a value that is wider than 8 bits (larger than 256), the program should consider only the least significant 8 bits and discard the rest. What happens when the user provides a negative value?</li>

 <li>Solve a puzzle.</li>

</ol>

Consider the following C program, with two variable values redacted. Note that the short int type is 16 bits (2 bytes) wide, and the output statements all use (unsigned) decimal, not hex.

#include &lt;stdio.h&gt;

int main() {

unsigned short int s = /* ??? */;     unsigned short int t = /* ??? */;

printf(“s &gt;&gt; 8 = %u
”, s &gt;&gt; 8 );      printf(“s &amp; 0xff = %u
”, s &amp; 0xff );     printf(“s ^ t = %u
”, s ^ t );

return 0;

}

Given (below) the output of this program, can you deduce the values of the variables s and t? You may have to convert the unsigned integer values to hexadecimal or binary.

s &gt;&gt; 8 = 128 s &amp; 0xff = 15 s ^ t = 36863