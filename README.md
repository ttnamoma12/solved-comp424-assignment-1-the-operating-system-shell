Download Link: https://assignmentchef.com/product/solved-comp424-assignment-1-the-operating-system-shell
<br>
Labs 1 and 2 will provide some background for this assignment.

The question is presented from a Linux point of view using the computer science server

mimi.cs.mcgill.ca, which you can reach remotely using ssh or putty from your laptop (see lab 1). If you do this assignment from an MS Windows machine, then make sure to provide the DLL libraries your program uses (if any) so that the TA can run it from their MS Windows machine. It is not the TA’s responsibility to make your program run. The TAs will not debug your program.

I suggest you do this assignment directly from mimi.cs.mcgill.ca since these are the computers the TA will be using.

You must write this assignment in the C Programming language.

<h1><u>Assignment Question: Building an OS Shell</u></h1>

Your source files:

Your entire application must be built from three c files: shell.c, interpreter.c, and shellmemory.c. These three source files must be built using modular programming techniques (see lab 2). The file shell.c is the primary programming file. It contains the main() and parse() functions.  The file interpreter.c contains the interpreter() function. Each command the interpreter() function accepts has a corresponding function that implements the command’s functionality. Give the function the same name as the command.  The file shellmemory.c contains the private data structures and public functions that implement the shell memory (lab 2 will also be helpful here).

Compiling your shell:

Compile your application using gcc with the name mysh. To do modular programming, you must compile your application in the following manner:

gcc -c shell.c interpreter.c shellmemory.c gcc -o mysh shell.o interpreter.o shellmemory.o

Running your shell:

From the command line prompt type:    ./mysh

What mysh displays to the user:

Welcome to the &lt;your name goes here&gt; shell!

Version 1.0 Created January 2020

$

The above dollar sign is the prompt. The cursor flashes beside the prompt waiting for the user’s input.  From this prompt the user will type in their command and the shell will display the result from that command on the screen (or an error message), and then the dollar sign is displayed again prompting the next command.  The user stays in this interface until they ask to quit.

The command line syntax for your shell is: COMMAND  ARGUMENTS.

Each command line command is a single line of text (a string) separated by spaces and terminated by a carriage return. Some commands are a single word, while other commands contain multiple words.  Processes each command in a way that is similar to how it was presented in class.  You do not need to follow the class slides exactly.

The commands supported by mysh:

The commands are case sensitive.

<table width="566">

 <tbody>

  <tr>

   <td width="331">COMMAND</td>

   <td width="234">DESCRIPTION</td>

  </tr>

  <tr>

   <td width="331">help</td>

   <td width="234">Displays all the commands</td>

  </tr>

  <tr>

   <td width="331">quit</td>

   <td width="234">Exits / terminates the shell with “Bye!”</td>

  </tr>

  <tr>

   <td width="331">set VAR STRING</td>

   <td width="234">Assigns a value to shell memory</td>

  </tr>

  <tr>

   <td width="331">print VAR</td>

   <td width="234">Displays the STRING assigned to VAR</td>

  </tr>

  <tr>

   <td width="331">run SCRIPT.TXT</td>

   <td width="234">Executes the file SCRIPT.TXT</td>

  </tr>

 </tbody>

</table>

There are no other commands (for now).

If the user inputs an unsupported command the shell displays “Unknown command”.

The command set VAR STRING   first checks to see if VAR already exists. If it does exist, STRING overwrites the previous value assigned to VAR. If VAR does not exist, then a new entry is added to the shell memory where the variable name is VAR and the contents of the variable is STRING. For example: set x 10 creates a new variable x and assigns to it the string 10.

Another example: set name Bob creates a new variable called name with string value Bob. Another example: set x Mary, replaced the value 10 with Mary.  Implement the shell memory as an array of struct, not as a linked list. Struct MEM { char *var; char *value; };

The command print VAR   first checks to see if VAR exists. If it does not exist, then it displays the error “Variable does not exist”. If VAR does exist, then it displays the STRING. For example: print x from the above example will display Mary.

The command run SCRIPT.TXT assumes that a text file exists with the provided file name. It opens that text file and then sends each line one at a time to the interpreter (as seen in class).  The interpreter treats each line of text as a command.  Each line affects the shell and the UI. At the end of the script, the file is closed, and the command line prompt is displayed once more. While the script executes the command line prompt is not displayed.  For example: run test.txt will begin by opening the file test.txt. If that fails, then an error message is displayed: “Script not found”. If the file is opened, then each line of the file is interpreted. At the end, the file is closed, and the command line prompt is displayed.  If an error occurs while executing the script due a command syntax error, then the error is displayed and the script stops executing.







Testing your shell:

The TAs will use and modify the provided text file to test your shell.  You can also use this file to test your shell or you can test it the old fashion way by typing input from the keyboard.  To use the provided text file, you will need to run your program from the OS command line as follows:

$ ./mysh &lt; testfile.txt

Each line from testfile.txt will be used as input for each prompt your program displays to the user. Instead of typing the input from the keyboard the program will take the next line from the file testfile.txt as the keyboard input.

Make sure your program works in the above way.




<ul>

 <li style="list-style-type: none;"></li>

</ul>