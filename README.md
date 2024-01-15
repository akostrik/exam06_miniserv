# Subject 
Write a program that will listen for client to connect on a certain port on 127.0.0.1 and will let clients to speak with each other.  
  
This program will take as first argument the port to bind to.  
If no argument is given, it should write in stderr "Wrong number of arguments" followed by a \n and exit with status 1.  
If a System Calls returns an error before the program start accepting connection, it should write in stderr "Fatal error" followed by a \n and exit with status 1.  
If you cant allocate memory it should write in stderr "Fatal error" followed by a \n and exit with status 1.  
    
Your program must be non-blocking but client can be lazy and if they don't read your message you must NOT disconnect them...  
Your program must not contains #define preproc  
Your program must only listen to 127.0.0.1   
The fd that you will receive will already be set to make 'recv' or 'send' to block if select hasn't be called before calling them, but will not block otherwise.  

When a client connect to the server:  
the client will be given an id. The first client will receive the id 0, and each new client will received the last client id + 1, %d will be replace by this number.  
A message is sent to all the client that was connected to the server: "server: client %d just arrived\n".  
Clients must be able to send messages to your program.  
Message will only be printable characters, no need to check a single message can contains multiple \n.  
When the server receive a message, it must resend it to all the other client with "client %d: " before every line.  
When a client disconnect from the server: a message is sent to all the client that was connected to the server: "server: client %d just left\n".  
  
* Allowed functions: write, close, select, socket, accept, listen, send, recv, bind, strstr, malloc, realloc, free, calloc, bzero, atoi, sprintf, strlen, exit, strcpy, strcat, memset  
* Memory or fd leaks are forbidden  
* you will find the file main.c with the beginning of a server and maybe some useful functions (this file use forbidden functions or write things that must not be there in your final program)
* Warning our tester is expecting that you send the messages as fast as you can. Don't do un-necessary buffer.
* you should use nc to test your program
* to test you can use fcntl(fd, F_SETFL, O_NONBLOCK) but use select and NEVER check EAGAIN (man 2 send) 

https://github.com/Saxsori/42-ExamRank06  
https://github.com/pasqualerossi/42-School-Exam-Rank-06  
https://github.com/NahIIo/examrank-02-03-04-05-06/tree/master/examRank06  
