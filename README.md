Download Link: https://assignmentchef.com/product/solved-cs204-advanced-programming-homework-3-two-languages
<br>
<h1>Introduction</h1>

<strong> </strong>This homework’s aim is to make you familiar with the logic behind <strong>queues</strong> and <strong>stacks</strong> (and a bit of <strong>simply linked lists</strong> again) by practically using them in a real-case scenario (you will probably encounter similar cases as a future programmer).




<h1>A Tale of Two Languages</h1>




We have created a new programming language called CS++ which has a very simple syntax and another language called Machine Language. Details about the languages will be explained later in the document. The program you will implement will take an input of CS++ language and transform it to Machine Language code. After the transformation, it will evaluate the Machine Language code and run it step-bystep.




<h1>CS++ Syntax</h1>

<strong> </strong>

With the programming language one can define up to 20 variables. And users can define only integer variables. Syntax is similar to C++, but there is no other function than the <strong>main</strong> function. Below, a sample CS++ program is given.

main:

int a1   int a2   int b1 = 5

a1 = 4

a2 = ( ( b1 + 4 ) * a1 )             print a2 return







The CS++ code above will be translated to machine code below – comments (in red) are added just for your sake, they are not required in your solution:




<strong>mov CSG2 5 </strong><strong>//store the value 5 in <em>register</em> CSG2 – we will explain the registers later</strong><strong> mov CSG0 4 </strong><strong>// store the value 4 in <em>register</em> CSG0 </strong><strong>add CSG2 4 </strong><strong>//perform addition with b1 and 4 </strong><strong>push CSA </strong><strong>//CSA is a special register that stores the results of all arithmetic operations</strong><strong> pop </strong><strong>//pop the last element from the stack – it will be stored in a special register CSP</strong><strong> mul CSP CSG0 </strong><strong>//multiply the values of CSP and CSG0</strong><strong>   push CSA </strong><strong>//push the result to the stack </strong><strong>pop </strong><strong>//pop it back to CSP</strong><strong> mov CSG1 CSP </strong><strong>//set the value of CSG1 to that of CSP</strong><strong> push CSG1  </strong><strong>//push the value of CSG1 to stack </strong><strong>print </strong><strong>//pop and print the top value in the stack</strong><strong> ret </strong><strong>//return</strong>




The details of the machine code are given below.




<strong>Registers:</strong>

In the machine code there are small storage units to store the variables, which are called registers. In real life, a processor register (CPU register) is one of a small set of data holding places that are part of the computer processor. You will be using these registers to store the variables defined in the CS++ program given as input. You have 25 registers. 5 of them have special purposes and the rest is for you to store the defined variables. The names and purposes of the registers are given below:

<ul>

 <li>25 Registers o CSA (Add/mul/sub operation result will be stored in) o CSB (After Div operation, result will be here) o CSC (After Div operation, remainder will be here)

  <ul>

   <li>CSG0 (General use) o CSG1 (General use) o    CSG2 (General use) o    CSG3 (General use) o    CSG4 (General use) o CSG5 (General use)</li>

  </ul></li>

</ul>

…

…

<ul>

 <li>CSG19 (General use)</li>

 <li>CSP (After pop operation, popped value from stack is stored in here) o CST (Can be used to store values for a temporary time)</li>

</ul>

<strong> </strong>

<strong>Instructions</strong>




The code written in CS++ is translated into simple instructions to be processed by the CPU. And we have 9 simple instructions, which are defined clearly below:

<ul>

 <li>Instructions: o push o pop o mov o add o sub

  <ul>

   <li>mul o div o     print</li>

   <li>ret</li>

  </ul></li>

</ul>




Instruction Definitions:

<ul>

 <li>push:

  <ul>

   <li>Pushes the parameter to the stack (memory) which you will generate to simulate computer behavior. If the given parameter is register or a user-defined variable, only the value of it will be pushed to stack.</li>

  </ul></li>

 <li>mov: o Takes two parameters and assigns the value of the first parameter to second. o For example <strong>mov CSG0 6 </strong>means, CSG0 = 6.

  <ul>

   <li>And <strong>mov CSG0 CSG1 </strong>means, CSG0 = CSG1.</li>

  </ul></li>

 <li>pop: o Pops the item at the top of the stack and stores it in CSP.

  <ul>

   <li><strong>pop </strong>means pop the item at the top of stack then store it in <strong>CSP </strong>register (CSP = 4).</li>

  </ul></li>

 <li>add:

  <ul>

   <li>Add takes two parameters; it sums up the values of parameters and stores the result in the <strong>CSA </strong></li>

   <li><strong>add CSG0 CSG1, </strong>in the example, sums up the values stored in CSG0 (let’s say it is 6) and CSG1 (let’s say it is 4) and stores the result in CSA (which becomes 10).</li>

  </ul></li>

 <li>sub:

  <ul>

   <li>Sub takes two parameters. It subtracts the second parameter from the first one and stores the result in the <strong>CSA </strong> For example:

    <ul>

     <li><strong>mov CSG0 6 </strong></li>

     <li><strong>mov CSG1 4 </strong></li>

     <li><strong>sub CSG0 CSG1 </strong>o The example operation given subtracts the value stored in CSG1 from CSG0 and stores the result in <strong>CSA </strong>(CSA becomes 2).</li>

    </ul></li>

   <li>mul:

    <ul>

     <li>This instruction takes two parameters (values or registers). It multiplies the values and stores the result of it in the <strong>CSA </strong>

      <ul>

       <li>For example<strong>, mul 5 12 </strong>operation will multiply 5 with 12 and stores the result (60) in</li>

      </ul></li>

     <li>div:

      <ul>

       <li>It takes two parameters, lets just call them param1 and param2. Then divides param1 to param2. It is an integer division and the result of it will be stored in <strong>CSB</strong>. Also remainder will be calculated and stored in the <strong>CSC</strong>.</li>

       <li>For example: <strong>div 21 5</strong> o After the instruction is processed:

        <ul>

         <li>CSB = 4</li>

         <li>CSC = 1</li>

        </ul></li>

       <li>print:

        <ul>

         <li>The print function pops the item at the top of the stack and prints it. Sample usage:

          <ul>

           <li><strong>push 4 </strong></li>

           <li><strong>print </strong>o The example above will print 4.</li>

          </ul></li>

        </ul></li>

      </ul></li>

    </ul></li>

  </ul></li>

</ul>




<ul>

 <li>ret:

  <ul>

   <li>There is no special thing about <strong>ret</strong>. When you see <strong>ret</strong>, it means program is ended. Program must exit at that point</li>

  </ul></li>

</ul>




<h1>The main menu</h1>




Part of the program is given to you in the zip file. In the main menu there will be 8 option presented to the user. The main menu is as follows:










Even though part of program is given to you, you can edit any part of it as long as the output is the same. Below we describe each of the main menu options (with option 0 being obvious and already implemented).




1) Give Input File




It will ask the user for an input CS++ file to transform into Machine Language code. The steps of the generated machine code will be stored in a <strong>queue.</strong> If the input file couldn’t be opened it will print an error and return to main menu. <strong>There won’t be any syntax errors in the given CS++ file. You don’t need to check that – you can assume that everything is as they are supposed to be, e.g., the variables are defined only once, if they are used they are already defined etc.</strong> Just focus on the conversion and running the steps. The erroneous and successful outputs are shown below.













Sample input file used for demonstration is given below:

<em>input.txt </em>main:

int a1    int a2 = 4

int a3

int a4 = ( ( 5 + 13 ) / ( 4 – 2 ) )  print a4

int a5

int a6 = a2           print a6  a1 = 5

a2 = 3    print a2  a3 = 8    a5 = 12                 print a5  a6 = 9

int a7

a7 = ( ( ( a3 * ( a1 + a2 ) ) – a4 ) / ( a5 % a6 ) )        print a7 return




As seen in the input file, code starts with main, then int variables are defined. Variables can be initialized when they are defined also values can be assigned to variables after definition. On the right side of assignment operator (=), there can be integer value (e.g. a2 = 4), there can be another variable ( e.g. a6 = a2) and there can be a computation consists of simple arithmetic operations: addition, subtraction, multiplication, division and mod.  Calculations will be in infix form as seen in the line:




<ul>

 <li>a7 = ( ( ( a3 * ( a1 + a2 ) ) – a4 ) / ( a5 % a6 ) )</li>

</ul>

<strong> </strong>

<strong>There is an empty space (“ ”) between every token in the calculation. So, you can get every variable name, operator, parenthesis with stringstream.  In an equation, all arithmetic operations are always parenthesized. So you know when to perform an operation. </strong>




The Machine Code version of the <strong><em>input.txt </em></strong>is given below:




<strong>mov CSG1 4 add 5 13 push CSA sub 4 2 push CSA pop mov CST CSP pop div CSP CST push CSB pop mov CSG3 CSP </strong>

<strong>push CSG3 print </strong>

<strong>mov CSG5 CSG1 </strong>

<strong>push CSG5 print mov CSG0 5 mov CSG1 3 push CSG1 print mov CSG2 8 mov CSG4 12 </strong>

<strong>push CSG4 print mov CSG5 9 add CSG0 CSG1 push CSA pop mul CSG2 CSP push CSA pop sub CSP CSG3 push CSA div CSG4 CSG5 push CSC </strong>

<strong>pop mov CST CSP pop div CSP CST push CSB pop mov CSG6 CSP </strong>

<strong>push CSG6 print ret </strong>

<strong> </strong>




After the user uses 2<sup>nd</sup> and 3<sup>rd</sup> options, the Machine Code instructions will be executed, so that there might be values on memory stack, the instruction queue may not be empty, registers may be storing some values; so that when the user selects option 1, these structures must be cleared.




<ul>

 <li>Run Until the End</li>

</ul>




With this option, your program will run the Machine Code you generated from CS++ code in the first option. The output for this option with the input file (<em>input.txt</em>) is given below.










After the instructions of Machine Code are executed, the program should return to the main menu. Since there is no instruction left in the queue, the instruction queue should be empty. After option 2 is called, if user tries to select option 2 again, it should state that there are no more instructions left in the queue.







<ul>

 <li>Run One Instruction</li>

</ul>




This option will be used to run only one instruction. You will dequeue one instruction from instruction queue and execute it.










When there is no instruction left on the queue, it should print a proper message and go back to main menu.













<ul>

 <li>Print Current Stack</li>

</ul>




At this option, the memory stack will be printed. The stack is used when running the Machine Code instructions. When <strong>push </strong>instruction is executed, the parameter given to push is pushed to memory stack. (e.g. push 5, push CSA, push CSG1, push CSP).




When the stack is empty, it should print a proper message.










Otherwise it should print the elements in the stack. Below is an example after 3<sup>rd</sup> instruction is executed in the instruction queue generated by <strong><em>input.txt</em></strong><em>.</em>













<ul>

 <li>Print Register Values</li>

</ul>




With this option, program will print the Special Use Registers and General Use Registers and the values stored in them. The Machine Code generated by <strong><em>input.txt</em> </strong>is executed till the end, and the registers are printed as follows.







<ul>

 <li>Print Next Instruction</li>

</ul>




The next instruction to be executed will be printed. If there is no instruction left, proper message should be printed and go back to main menu.













<ul>

 <li>Print Remaining Instructions</li>

</ul>




It will print the remaining instructions in the instruction queue. If there is no instruction left in the queue it should print a proper message and go back to main menu.
















<ul>

 <li>Print Defined Variables</li>

</ul>




This option will print the variables defined in the input CS++ file and values of the variables.













<strong>Some Important Rules </strong>

In order to get a full credit, your programs must be efficient and well presented, presence of any redundant computation or bad indentation, or missing, irrelevant comments are going to decrease your grades. You also have to use understandable identifier names, informative introduction and prompts. Modularity is also important; you have to use functions wherever needed and appropriate.




When we grade your homeworks we pay attention to these issues. Moreover, in order to observe the real performance of your codes, we are going to run your programs in <em>Release</em> mode and <strong>we may test your programs with very large test cases</strong>.




<strong> </strong>

<strong>What and where to submit (PLEASE READ, IMPORTANT) </strong>

You should prepare (or at least test) your program using MS Visual Studio 2012 C++. We will use the standard C++ compiler and libraries of the abovementioned platform while testing your homework. It’d be a good idea to write your name and last name in the program (as a comment line of course).




Submissions guidelines are below. Some parts of the grading process are automatic. Students are expected to strictly follow these guidelines in order to have a smooth grading process. If you do not follow these guidelines, depending on the severity of the problem created during the grading process, 5 or more penalty points are to be deducted from the grade. Name your cpp file that contains your program as follows: <strong><em>“SUCourseUserName_YourLastname_YourName_HWnumber.cpp” </em></strong>




Your SUCourse user name is actually your SUNet username that is used for checking sabanciuniv e-mails. Do NOT use any spaces, non-ASCII and Turkish characters in the file name. For example, if your SUCourse user name is valent, name is Valentina, and last name is Tereşkova, then the file name must be:




<h1><em>Valent_Tereskova_Valentina_hw1.cpp </em></h1>




Do not add any other character or phrase to the file name. Make sure that this file is the latest version of your homework program. Compress this cpp file using WINZIP or WINRAR programs. Please use “zip” compression. “rar” or another compression mechanism is NOT allowed. Our homework processing system works only with zip files. Therefore, make sure that the resulting compressed file has a zip extension. Check that your compressed file opens up correctly and it contains your cpp file.




You will receive no credits if your compressed zip file does not expand or it does not contain the correct file. The naming convention of the zip file is the same as the cpp file (except the extension of the file of course). The name of the zip file should be as follows:




<strong><em>SUCourseUserName_YourLastname_YourName_HWnumber.zip </em></strong>




For example zubzipler_Zipleroglu_Zubeyir_hw1.zip is a valid name, but




<h1><em>hw1_hoz_HasanOz.zip, HasanOzHoz.zip  </em></h1>




are <strong>NOT</strong> valid names.