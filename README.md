Download Link: https://assignmentchef.com/product/solved-csc402-homework-1-getting-started-values-operators-expressions-and-functions
<br>
For this assignment create a file called Program.fs that contains the declaration <strong>module HW1</strong> at the top.  All of your code for this assignment should be placed in the Program.fs file.

If you are using JetBrains Rider as your IDE then you can create the file (and runnable project) as follows:  From the Rider start-up screen select “New Solution”. (If you are already in Rider instead of the start-up screen, then go the menu and select File-&gt;New…).  Select “Console Application” under .NET Core.  Give the solution a name (e.g. “HW1” without the quotes). The dialog box will fill in the same name (e.g. “HW1”) as the name of the project.  Click “Create”.  Rider will create a file named Program.fs for you.  At the top of the file add a line that states <strong>module HW1</strong> and save the change (Ctrl+s or File-&gt;Save All). Now if you choose Run-&gt;Run ‘HW1’ (or hit Shift+F10) Rider will run the file and you will see the output “Hello World from F#!”.  You are now ready to begin the homework problems.

Problem 1 (3 points) Section 1.2 (page 3) of the textbook gives a <em>circleArea</em> function whose type is <em>float -&gt; float</em>.  Enter the code for circleArea into your file

(after the <strong>open System</strong> statement and before the <strong>[&lt;EntryPoint&gt;]</strong> declaration):

let circleArea r = System.Math.PI * r * r

Note that you do not need to put two semicolons (<strong><em>;;</em></strong>) at the end of this declaration.

In the textbook the authors assume that you will type the declaration into the F# Read-Eval-Print-Loop (REPL).  It is common practice (though not always necessary) to terminate with two semicolons an expression that is typed into the REPL:  This signals to the REPL that the desired expression is complete.  You should not need this terminator token in code that is contained in a source file.  In this document I will generally follow the usual custom by terminating expressions at the REPL with <em>;;</em>.  (I’m quite okay with you leaving out <em>;;</em> if you like.)

Next you should test that your function works correctly.  Do this in two ways:  (1) by calling it from the Read-Eval-Print-Loop (REPL) and (2) by calling it from <strong>main</strong>.

(1) Calling your function from the REPL:  Click on the line where circleArea is defined.  Then hit Ctrl+ (i.e. hold down the Ctrl key and press the ‘’ key).  This should open up the REPL (also known as F# Interactive), which consists of two small text areas, one above the other.  At the &gt; prompt in the bottom text area, evaluate your function on the value r = 3.0 by typing the following and hitting &lt;Enter&gt;:

&gt; circleArea 3.0;;

You should see the following appear in the text area that is immediately above the prompt (note that here we <em>do</em> use the double semicolons):

circleArea 3.0;; val it : float = 28.27433388

As you can see, the REPL displays the evaluated expression, followed on the next line by the type and value of the expression.  The variable called <strong>it</strong> is bound to the value most recently computed by the REPL.  You can use it in later expressions:

&gt; it + 1.0;;

&gt; it + 1.0;; val it : float = 29.27433388

(2) Calling your function from <strong>main</strong>:  Insert the following (single) line immediately before the last line in your main function:

printfn “The area of a circle with radius %1.1f is %1.8f” 3.0

(circleArea 3.0)




Now when you run your program (Shift+F10) you should get the following output:

Hello World from F#!

The area of a circle with radius 3.0 is 28.27433388




Problem 2 (3 points) Section 2.3 (page 25) shows how to write an <strong>isLowerCaseVowel</strong> function that takes a character and returns whether or not it is a lower case vowel.  Define this function in your file.   (Note:  if your definition is split over two lines, as it is in the textbook, if you want to read it into the REPL by using Ctrl+, then make sure that you select both lines by clicking and dragging over them.)

val isLowerCaseVowel : ch:char -&gt; bool

&gt; isLowerCaseVowel ‘e’;; val it : bool = true

&gt; isLowerCaseVowel ‘f’;; val it : bool = false

&gt; isLowerCaseVowel ‘E’;; val it : bool = false

Problem 3 (6 points) Define a function <strong>ithCharEquals</strong> of type <em>string -&gt; int -&gt; char -&gt; bool</em> where the value of <em>ithCharEquals str i ch</em> is true if and only if <em>ch</em> is the <em>i</em>-th character in <em>str</em>.  (If <em>i</em> is out of range or the <em>i</em>-th character is not <em>ch</em>, then return false.)  Note:  You can use the <em>String.length</em> function shown in Section 2.3 to get the length of <em>str</em>, but strings have a <em>Length</em> data field that you can use instead.  Regardless of which way you retrieve the length, see if you can define the function without using an if-then-else expression:  It should be possible to define it more succintly by using the conjunction (<em>&amp;&amp;</em>) of three expressions.  Also, note that  F# might not be able to infer the type of <em>str</em> based on the operations that you use.  You can explicitly tell it <em>str</em>’s type as follows:

let ithCharEquals (str:string) i ch = …

Once you’re loaded the function in the REPL you should be able to have the following interactions:

val ithCharEquals : str:string -&gt; i:int -&gt; ch:char -&gt; bool

&gt; ithCharEquals “Grace” 1 ‘r’;; val it : bool = true

&gt; ithCharEquals “Grace” 5 ‘e’;; val it : bool = false

Problem 4 (6 points) Write a higher-order function <strong>ithCharSatisfies</strong> of type <em>string -&gt; int -&gt; (char -&gt;bool) -&gt; bool</em> where the value of <em>ithCharSatisfies str i f</em> is true if and only if <em>f</em> returns true on the <em>i</em>-th character in <em>str</em>.  (If the <em>i</em>-th character does not satisfy <em>f</em>, or if <em>i</em> is out of range, then return false.)  Using your isLowerCaseVowel function from Problem 2, you should be able to generate the following interactions in the REPL:

val ithCharSatisfies : str:string -&gt; i:int -&gt; f:(char -&gt; bool) –

&gt; bool

&gt; ithCharSatisfies “Grace” 3 isLowerCaseVowel;; val it : bool = false

&gt; ithCharSatisfies “Grace” 4 isLowerCaseVowel;; val it : bool = true

&gt; ithCharSatisfies “Grace” 5 isLowerCaseVowel;; val it : bool = false

Note:  The <em>=</em> operator in F# is the binary infix operator for equality comparison: <sub> </sub>

&gt; 3 = 4;; val it : bool = false

&gt; 3 = 3;; val it : bool = true

You can use <em>=</em> as a prefix operator if you put it inside parentheses:

&gt; (=);; val it : (‘a -&gt; ‘a -&gt; bool) when ‘a : equality

&gt; (=) 3 4;; val it : bool = false

&gt; (=) 3 3;; val it : bool = true

Due to “currying”, you can give <em>(=)</em> one parameter and you will get back a function that receives one parameter:

&gt; (=) 3;; val it : (int -&gt; bool) = &lt;fun:<a href="/cdn-cgi/l/email-protection" class="__cf_email__" data-cfemail="88e1fcc8bba5b9ba">[email protected]</a>&gt;

&gt; ((=) 3) 4;; val it : bool = false

&gt; ((=) 3) 3;; val it : bool = true

Consequently, you should be able to use your <em>ithCharSatisfies</em> function as follows

&gt; ithCharSatisfies “Grace” 0 ((=) ‘G’);; val it : bool = true

&gt; ithCharSatisfies “Grace” 0 ((=) ‘H’);; val it : bool = false




Problem 5 (6 points) Section 2.4 shows how to write <em>if-then-else</em> expressions. Such expressions can, of course, be nested.  In your Program.fs file use nested if-thenelse expressions and the &lt; operator to write a function <strong>min3</strong> of type int -&gt; int -&gt; int -&gt; int that returns the smallest of three values.  Do not use any other operators.  (For example, do not use F#’s min operator.) Source code: let min3 (a:int) b c =

…

REPL inteaction:

val min3 : a:int -&gt; b:int -&gt; c:int -&gt; int

&gt; min3 1 2 3;; val it : int = 1

&gt; min3 4 2 3;; val it : int = 2

&gt; min3 4 5 3;; val it : int = 3

&gt; min3 2 2 2;; val it : int = 2

Once you get your min3 function working correctly, change the parameter

(a:int) to simply a.  You will get a more function with the more general type

‘a -&gt; ‘a -&gt; ‘a -&gt; ‘a when ‘a : comparison.  Now you will be

able to call min3 on integers, but also on floats or strings, or any other type that is compatible with the &lt; operator (more technically, that supports comparison).

val min3 : a:’a -&gt; b:’a -&gt; c:’a -&gt; ‘a when ‘a : comparison

&gt; min3 10 -2 8;; val it : int = -2

&gt; min3 10.0 -2.1 8.7;; val it : float = -2.1

&gt; min3 “Abe” “Betty” “Carl”;; val it : string = “Abe”




Problem 6 (6 points) Write a function called <strong>min3WithMin</strong> that performs the same task as <strong>min3</strong>.  This time do use F#’s <em>min</em> operator in defining your function.  Do not use if-then-else expressions or the &lt; operator.  The type of the function

should be ‘a -&gt; ‘a -&gt; ‘a -&gt; ‘a’ when a : comparison.  (F#’s <em>min</em> function is not covered in the textbook but you can easily guess what it does.)

val min3WithMin : a:’a -&gt; b:’a -&gt; c:’a -&gt; ‘a when ‘a : comparison

&gt; min3WithMin 5 2 3;; val it : int = 2

&gt; min3WithMin “Melanie” “Zeke” “Angie”;; val it : string = “Angie”

.