### Notes from "Introduction Thinking Computationally"

* Before We Begin
	* Because of problems with Unit Testing frameworks and adding a dependency, I have come up with a way for us to not need them. But you guys have to understand something before we use it. 
	* Lets talk about Standard In/Out/Error
		* In almost every program we have what we call Standard In, Standard Out and Standard error.
		* These are called standard streams
			* Standard In (StdIn) - is what input is feed into your program, this can be a file pipped in or if that is absent it can be keyboard input or arguments that you use to start your program.
			* Standard Out (StdOut) - This is the output your program produces that are not considered to be errors. For example any output you usually see that is outputed to the console is standard out.
			* Standard Error (StdErr) - This is usually error codes and text that you want to stream back, this could be log input but is usually communicating to the OS that an error occured (it may or may not be fatal to the application)
		* Piplining 
			* In order to get an executable to get it to do useful things its necessary to pipe the output of one executable into another. 
		* Redirection
			* We can take the contents of a file redirect it to another file, or redirect the contents of the file into our application. For example we can build a simple console application and write commands like this in DOS/WinNT Shell

			```
				ping.exe 127.0.0.1 >> contents.txt
			``` 
			
			We can find reply in that file like so
			
			```
				find.exe /i Reply < contents.txt
			```
		* Great why do I care again?
			* In the future you guys will have the ability to try these excercises in any language you like.  	
* Get into teams, of 1 laptop per team
* The opening challange, I want you to build a console application that takes in one argument from standard-in.
* Do you remember the end of stages of Mario bros (Super Mario Bros on the NES?) Usually when mario got to the end of the level he had to jump from a pyramid on to a flag pole, now if you look at a picture of this you will notice a few properties. 
* ![Mario Bros](https://x.cs50.net/2013/psets/1/pyramid.png)

#### Build a Console Application
* Build a console application that uses hash marks to create a pyramid that is similar to the image. 
	* The inputs should be between 1 - 16 (positive)
	* If the number entered by the user is not positive, reprompt or if its not a number reprompt.
	*  Write error messages to standard error
	*  Write the output to standard output. 
	* Examples
	* Input
	 ```
	 Mario.exe 1
	 ```
	* Output 
```
		##
```
	* Input #2
	```
	Mario.exe 4
	```
	* Ouput #2

```
	   ##
	  ###
	 ####
	#####
```

	
* Error Conditions
	* Input Error 
	* `Mario.exe -4` 
	* Output Error
	* `Must be a positive number, cannot be a string` 


* Play Group Playlist 1 (20 minutes)
* Have 2 groups white board the solution out
* Show the real solution to this coding problem using C#

* Lets start with some math. No calculators!
* Solve the following equations.
	* (4×10^3) + (3×10^2) + (2×10^1) + (7×10^0)
	* (5x10^2) + (9x10^1) + (1x10^0)
	* (8x10^-1) + (9x10^-2) + (3x10^-3)


* Notice something?
* The positional number of the power of 10 relates to the location in a decimal number that you would see.
	* You don't even need to do the math you can literally solve this by following the location and writting it out
	* Answers: 
	* (4×10^3) + (3×10^2) + (2×10^1) + (7×10^0) = 4,327
	* (5x10^2) + (9x10^1) + (1x10^0) = 591
	* (8x10^-1) + (9x10^-2) + (3x10^-3) = 0.893
 * This is what we refer to as decimal numbers or base 10.
 * 0-9 inclusive [programmers always start from 0]
 * We use decmial numbers a lot in programming, in fact depending on what you are are working on you will use decimals for things like money, quantities, storage locators etc.

* Now i am going to let you in on a secret, your computer can not really understand integers and floating point numbers or strings for that matter. In fact almost everything to a computer is converted to bits. When we talk about the bitness of the storage type this is what we mean. Take this code. By the way i am talking about this at a low level (think machine level).

	```
		int MyAge = 31 /// = 00000000 00000000 00000000 00011111
```

* Notice something?
* There are 32 bits used to express this number. 
* But first lets talk about a bit
* A bit is a Binary digit 
* It has a single binary value (0 off, 1 on)
* For now lets just keep this in scope of 4 bit numbers. 
![Table](http://www2.nzmaths.co.nz/number/NumberImages/Exp3.gif)
* A bit is a power of 2 because the binary system only has two values for a single bit.
* Like the decimal system we can convert a number from binary to decimal by litterally adding the powers of 2
* Take for example the following number 
* 1000  = 8
* Why?
	* Because the left most bit is set to on if we were to expand this it would look like the following
	* (1x2^3) + (0x2^2) + (0x2^1) + (0x2^0) = 8
* Whats 1111?
	* The answer is 15 
	*  (1x2^3) + (1x2^2) + (1x2^1) + (1x2^0) = 15

* Now that we understand this, lets try converting a number from a decimal value to a binary representation.
* Converting any power of 2 is pretty straight forward and zero as well
	* for example 8,4,2,1 are powers of 2
	* same for 128,64,32,16
	* But what about numbers like 31 how would we convert it?
	* Simple. There is an algorithim you can use to convert.
	* For example, 31 we notice that the number is not greater than 32 but 16 is less than it, so we mark 16 and write out its power (1x4^2) and subtract 16 from 31 which will equal 15, 8 can be subtracted from 15 so we set that bit to on (1x3^2) 15-8=7, so we can mark 4 (1x2^2), now subtract 4 we are left with 3, the left we mark (1x2^1) and (1x2^0) we are left with 11111 this can be represented in 8 bits as so
	* 0001 1111 
	* Knowing what you know now.
	* Convert the following Decimal to Binary on paper
		* 100
		* 128
		* 251
		* 16
		* 48
		* 17
		* 5
		* 3

* Lets look at a big number that is 32 bits. 
` 01111010011100111100000100 `

This is a big number, and could be a lot of things, lets say for this example that is the amount of money our company brought in -- in 2015. Now if you were trying to view this in a program this would be difficult to translate to decimal. But maybe we can do something to more succintly represent this as a number that we can see and use.

#### Hexidecimal

*  01111010011100111100000100
*  Lets first turn this number into something a bit more parseable.
* 0000 0001 1110 1001 1100 1111 0000 0100
* lets turn these into decimal values in broken out sets
* 0 1 14 9 12 15 0 4
* Cool thats a little better, maybe what we can do is assign a value 0-9 using decimal but what about these values over 9?
 * Turns out we can assign letters
 *  So lets for the sake of this turn 10, 11, 12, 13, 14, 15 into letters
 	* 10 = A
 	* 11 = B
 	* 12 = C
 	* 13 = D
 	* 14 = E
 	* 15 = F
 * Lets simply subsitute 01E9CF04 
 * Look familiar? 0x01E9CF04 
 * We call this Hexidecimal its a number system for expressing 16 base numbers. We use this to represent binary more succintly and more human readable format. This is used primarily in memory addresses and in expressing large integers succintly. Another thing you might notice is that this is used in things like colors (RGB) are just octets. 
	* Convert the following to hex
		* 16 = 0001 0000 = 0x10
		* 24 = 0001 1000 = 0x18
		* 128 = 1000 0000 = 0x80	
		* 51 = 0011 0011 = 0x33
		* 80 = 0101 0000 = 0x50
		* 255 = 1111 1111 = 0xFF
		* 162 = ???? ???? = a2
 * To convert the numbers all you had to do was convert them to binary and split them into 4 bits each. Then simply do the math for each set and assign the value using hex.


* Video CS50 [Video](https://www.youtube.com/watch?v=nrFHGtGdOzA)
*  Video 1 [Video 1](https://www.youtube.com/watch?v=tSUhEOtYKIg)
* Convert To Decimal from Hex [Video](https://www.youtube.com/watch?v=lTjFFEtmZyA)

#### Boolean Logic

* This is simple logic that we can do with BITWISE values.
* When a computer evaluates a conditional it will turn statements into true or false statements for example
* (1 > 2) = FALSE OR 0
* (2 =< 2) = TRUE OR 1
* ( 1=1) = TRUE OR 1
* (1 != 1) = FALSE OR 0

With this we can can actually run some logic through some gates. These are called Boolean Logic Operators and are usually the following.

* AND (&) = And operator is the easiest if a gate or value of boolean is set to true then the value of the operand must be set to true for teh value to be true.
	* For example:
		* TRUE AND TRUE = True
		* True AND FALSE = False
		* 5 & 2 = ???
		* First must conver to binary
		* 5 = 0101 AND 0010 = 0000
		* 10 & 2 = ???
		* First must convert to binary
		* 1010 AND 0010 = 0010 = 2 
* OR (Inclusive) = any value equal to true -- this is then true. Both operands must be false for the value to be false 
	* for example 
		* TRUE OR True = TRUE
		* TRUE OR FALSE = TRUE
		* FALSE OR FALSE = FALSE

* XOR (Exclusive) - Only when an operand contains a true and false is teh value true
	* For example
		* True Or False = TRUE
		* TRUE OR TURN = FALSE
		* False Or False = False  

* In C# there is something to NOTE a & will evaluate both operands no matter what a && will short circuit the operand evaluation. It will only evaluate till it gets to the first FALSE statement, same FOR || vs |

* ~ NOT - Will invert the bits against the operand, for example if we LOGICAL NOT -10 then we get 0000 0000 0000 1001
the reason being that -10 is  1111 1111 1111 0110

* These operations are really useful in conditionals and creating BITMASKS that can be used to store a complex value of a state. For example like a Flags enumeration.

### Excercise #2: Access Granted!

Your team just inherited some new code that has introduced a major security issue. The code that was created by a programmer who found a better job last week allows any person to access sensitive files, you have been tasked with figuring out how to fix the issue. 

Get into your team and fix this bug and help get this code into production.  

* The structures have been setup via a console program
* Make all the Screen Go Green
* All the setup i 

### Measuring Memory

* 1 bit is 1 0/1 flag
* 4 is equal to a max value of 15
* 8 Bits is equal to 1 byte
* There are 1000 bytes in a KB (Kilo Byte) or 8000 bits
* There are 1000 KB in a MB
* There are 1000 MB in a GB
* There are 1000 GB in a TB

* For the present your programs and Web Apps should never reach over the GB threshold for memory. Even then it should be re-evaluated if you can scale your software out over multiple boxes (exceptions are large data processing) or use more efficent data types

### Storing Data

* For the most part I am betting that a lot of care is not chosen right now for correct data types. Usually because for the most part you have a unlimited pool of memory and solving the problem is more important at this stage then thinking about the correct data type to use, so allocating extra memory is OK. 
* However, as cloud computing becomes more cheap through serverless resources it will be necessary to push your code to the limit and to optimize when necessary instead of scalling up. Because servers have a cost, and while its a great short term solution to just spin up more servers its a better long term solution to fix the time complexity of the code or to at least use the correct data type. 
* Also depending on your target deployment server it could be that memory could be extremely important, for example maybe your application runs on a RasPi where memory constraints are from 512MB to 1GB and your application would have to coexist with the OS as well so the max memory you could allocate would be about 256MB to 512MB.
* In C# like other languages the lowest amount of memory you can use for a type is measured in bytes with the minimum being 1. This means that even a structure that should be a bit (like TRUE/FALSE) is stored in with 8 bits.
``` Console.WriteLine(sizeof(bool)); ```

* Data types for a C# application could be any of the following
	* Boolean
	* Int32
	* Int64
	* float
	* decimal
	* short
	* long
	* byte
	* char
	* string

* Find out the size of each type using the sizeof operator in C#

* Knowing the information you got back from size of which type based on the following would be it OK store with?
	* Age (no dead persons will be stored)
	* Salary
	* Age of teh earth
	* a name
	* The first letter of a persons name
	* The amount of distance an astroid barreling towards earth is located on a cartesian plane. 
	* A binary representation of a name that we want store in a file.  
  
#### Signed Vs Unsigned

* Sometimes we have a need for negative numbers these are known as signed numbers and will cut our values like Int and double in half of the size of numbers we can represent, because each number has to be able to be expressed with a (-) a sign.
* For example if you use a unsigned int you can have any value from 0 to 4,294,967,295 if you use a signed integer you are limited from -2,147,483,648 to 2,147,483,647. If you dont need negative numbers then consider using unsigned as you wont have to scale up as quickly to the next data type. 
 
#### How a computer works

A computer will load your program into RAM (Random Access Memory) and will execute instructions on the CPU. From .net the way this looks is that your code is converted From IL to native instructions that can be understood by the CPU. This will usually be x86 instruction sets or could be specific platforms like ARM or x64 instructions, this will then run a series of low level commands that will be in assembly and return the result to your program. It will run through the program till the user terminates the program or an unhandled exception kills the program with an illegal instruction and windows or the HOST OS unloads the program from memory if it can, this is usually in teh USER SPACE of the operating system, your kernel and other things with exception of the UI run in Kernel space, this ensures that programs don't try to crash the HOST OS. 

Your program will store primitive variables on a part of memory called the stack, any numeric value primatives will be stored here. When you need to create an object it will store a refrence in teh stack but its value will be stored in teh HEAP. 

* Stack vs Heap
 * Stack is usually continous accessed memory for your application that is allocated by the OS to the application at run time. 
 * These are usually for short lifetime objects think of the call stack
 * Once the value is no longer used it is pop'd from the stack so that the next value can be used.
 * The stack and the heap are randomly assigned memory locations, do not depend on memory locations in any context they are random and for the most part will never repeat allocation location.
 * The Heap on the other hand is for dynamically allocated objects, think of when you use the new Keyword in C# that will create a ref to it in the stack but will store its ref in the heap. When the GC see's that a ref to it is no longer used, it will delete the entry in the stack and delete the object in the heap to reclaim the memory the system used. Its important though that with non .net objects (think non managed COM+, DCOM, OLE) that objects can not be tracked with thte GC you must explicitly get rid of those resources or you will introduce memory leaks. And in order to cycle these memory leaks will require a restart of the machine or in the case of asp.net a recycle of the application pools.

 ![Stack](https://upload.wikimedia.org/wikipedia/commons/thumb/2/29/Data_stack.svg/2000px-Data_stack.svg.png)
 
 ![](http://thumbs.dreamstime.com/z/heap-colorful-sweet-candy-sprinkles-isolated-white-backgrou-33055237.jpg)
 
 ![](http://i.stack.imgur.com/4Dfaa.gif)
 
 
 
 ### Lets talk about By Val and By Ref
 
 In most cases you do not need to know about byval and by ref because the .net runtime takes care of this for you for the most part. However, to become a better programmer you should understand the tradeoffs when it comes to this. Because as with everything in life TANSAAFL (There ain't no such thing as a free lunch)
 For the most part if you use primitives you can not alter thier value in the scope of a function and another function, for example if you make a function called changeIt which takes in a integer as a paramter and modify the integer in the scope of the function, if you were to run this code, nothing would be modified. Because a copy of the value is passed and not the refrence. If we wanted to change it so that hte value could be accessed and modified and would update the reference we would need to pass the variable by reference. 
 
  For objects they are by default passed by reference so if you modify an object it will reflect in the next time you use a variable referenced to that object. To pass the object by value you would need to create a clone of the object (ICloneable in C#). 
 
 ## Finally Timing Complexity
 
 How well our algorithim runs which we will get into next month, is how fast our code can scale. Rather then butcher this I am going to depend on the CS50 explaination of this concept.
 
 [CS50](http://cs50.wiki/Big+O+notation)
 
  

