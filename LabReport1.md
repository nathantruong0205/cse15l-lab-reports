# cd
![image](https://github.com/nathantruong0205/cse15l-lab-reports/assets/108157832/e1f4a58c-2399-4406-874e-28ac92569091)

For cd, if you are to input it with no arguments, then the directory changes back to the root directory /home.
Using cd to go into directories such as lecture1 and messages worked fine, but when trying to go into a file it would not allow it and result in error
Also even when multiple directories deep such as /home/lecture1/messages, doing cd will reset it to root direc3tory /home


# ls
![image](https://github.com/nathantruong0205/cse15l-lab-reports/assets/108157832/84b441f5-2adc-4b20-bc56-33458525a5f2)

For ls, if you input it with no argument then it will display the directories of the root directory /home which is just lecture1
if you do ls lecture1, then it will display all files and directories under lecture1, however if you do ls messages it will result in error. To successfully do ls messages, you must input ls lecture1/messages which makes the absolute path /home/lecture1/messages
ls with a file argument will not work such as ls Hello.java will result in an error 


# cat
![image](https://github.com/nathantruong0205/cse15l-lab-reports/assets/108157832/51e0b8ae-4a3e-45da-aeed-3fc9475d5d90)

For cat, with no argument the terminal sort of breaks and anything you type in won't do anything till you ctrl + c to fix the command line.
When typing in a directory as an argument, it will always display "cat: **argument**: Is a directory" most likely because cat is supposed to display what is in files
When typing in a file as an argument, you must first make an absolute path using the relative path which in this example is /home, so you musdt type cat lecture1/messages/en-us.txt in order to display what is in the text file with cat. If you were to simply go straight to cat messages or cat Hello.java, it would result in an error. 
