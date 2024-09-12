# 3c.CREATION FOR FILE TRANSFER USING TCP SOCKETS
## AIM
To write a python program for creating File Transfer using TCP Sockets Links
## ALGORITHM:
1. Import the necessary python modules.
2. Create a socket connection using socket module.
3. Send the message to write into the file to the client file.
4. Open the file and then send it to the client in byte format.
5. In the client side receive the file from server and then write the content into it.
## PROGRAM
## CLIENT.PY:
~~~
import socket
s = socket.socket()
host = socket.gethostname()
port = 60000
s.connect((host, port))
s.send("Hello server!".encode())
with open('received_file', 'wb') as f:
    while True:
        print('receiving data...')
        data = s.recv(1024)
        print('data=%s', (data))
        if not data:
            break
        f.write(data)
        f.close()
print('Successfully got the file')
s.close()
print('Connection closed')
~~~
## SERVER.PY:
~~~
import socket
port = 60000
s = socket.socket()
host = socket.gethostname()
s.bind((host, port))
s.listen(5)
while True:
    conn, addr = s.accept()
    data = conn.recv(1024)
    print('Server received', repr(data))
    filename = 'F:\Comp_net\Ex no 7\sample.txt'
    with open(filename, 'rb') as f:
        while True:
            l = f.read(1024)
            if not l:
                break
            conn.send(l)
            print('Sent ', repr(l))
    print('Done sending')
    conn.send('Thank you for connecting'.encode())
    conn.close()
~~~
## OUPUT
## CLIENT.PY:
![image](https://github.com/user-attachments/assets/3a2e41a5-000a-4819-b8ba-58af3b7cd03a)

## SERVER.PY:
![image](https://github.com/user-attachments/assets/208b3de1-3d07-4551-89b9-956078195bb6)

## RESULT
Thus, the python program for creating File Transfer using TCP Sockets Links was 
successfully created and executed.
