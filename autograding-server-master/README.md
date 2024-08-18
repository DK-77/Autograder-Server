# Autograding Server

A simple server-client architecture for imitating a multithreaded grading server with multiple clients and also doing performance analysis of the system.

Requirements:
	plotly
Commands:
	pip install plotly
	


Version 1:

This version is a single threaded version of the server with the clients code containing a loop to simulate number of requests sent by client.
The server can be run as ./server <port no>.
The client can be run as ./submit <server ip:port> <source file to be graded>
The server sends a reply to the client based on whether the submission was a PASS, Compiler Error, Runtime Error or a Difference Error which client prints on the screen.
Alternatively if both the client and server are run on one machine the experiment can simulated by just running loadtest.sh with appropriate arguments.

Version 2:

This version is a multithreaded version of the server with the server generating as many threads as the number of requests coming from the client, the client similarly contains a loop that simulates a number of requests sent by the client.
The server can be run ./server <port no.>
The client can be run as ./submit <server ip:port> <testfile> <num req to be graded> <sleeptime/thinktime> <Timeoutinseconds>
The server sends a reply to the client based on the output of grading which the client stores in the file "server_response.txt"
Alternatively if both the client and server are run on one machine the experiment can simulated by just running loadtest.sh with appropriate arguments.

Version 3:

The version is a multithreaded version with threadpool with server generating a threadpool based on user arguments to server the client requests.
The server can be run as ./server <port no.> <thread pool size>
The client can be run as ./submit <server ip:port> <testfile> <num req to be graded> <sleeptime/thinktime> <Timeoutinseconds>
The server sends a reply to the client based on the output of the grading which the cilent stores in the file "server_response.txt".
Alternatively if both the client and server are run on one machine the experiment can simulated by just running loadtest.sh with appropriate arguments.

Version 4:

This version is multithreaded with threadpool design but an asynchronous server version with the client just submitting the file and returning and making a new connection to check the status of submission.
The server can be run as ./server <port no.> <thread pool size>
The client can be run as ./submit  <new|status> <serverIP:port> <sourceCodeFileTobeGraded|requestID>  based on what type of request to be made.
The client when checks the status with the request_Id recieved the server gives one of the four replies based on whether the request is in queue, in processiing, or already processed, or non-existant.
The Client echoes this replies to the screen.

