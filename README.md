# tools


##telnet without it:

bash
#bash:
$ cat < /dev/tcp/127.0.0.1/22
SSH-2.0-OpenSSH_5.3
^C

$ cat < /dev/tcp/127.0.0.1/23
bash: connect: Connection refused
bash: /dev/tcp/127.0.0.1/23: Connection refused

Curl
#Curl:
$ curl -v telnet://127.0.0.1:22
* About to connect() to 127.0.0.1 port 22 (#0)
*   Trying 127.0.0.1... connected
* Connected to 127.0.0.1 (127.0.0.1) port 22 (#0)
SSH-2.0-OpenSSH_5.3
^C

$ curl -v telnet://127.0.0.1:23
* About to connect() to 127.0.0.1 port 23 (#0)
*   Trying 127.0.0.1... Connection refused
* couldn't connect to host
* Closing connection #0
curl: (7) couldn't connect to host

Python
# python:
Python 2.6.6 (r266:84292, Oct 12 2012, 14:23:48)
[GCC 4.4.6 20120305 (Red Hat 4.4.6-4)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import socket
>>> clientsocket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
>>> clientsocket.connect(('127.0.0.1', 22))
>>> clientsocket.send('\n')
1
>>> clientsocket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
>>> clientsocket.connect(('127.0.0.1', 23))
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "<string>", line 1, in connect
socket.error: [Errno 111] Connection refused
