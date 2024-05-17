

# 3c.CREATION FOR FILE TRANSFER USING TCP SOCKETS
## NAME : NARESH
## ROLL NO:212223240104
## AIM
To write a python program for creating File Transfer using TCP Sockets Links
## ALGORITHM:
1. Import the necessary python modules.
2. Create a socket connection using socket module.
3. Send the message to write into the file to the client file.
4. Open the file and then send it to the client in byte format.
5. In the client side receive the file from server and then write the content into it.
## PROGRAM
## Client:
```
import socket

s = socket.socket()
host = socket.gethostname()
port = 60000
s.connect((host, port))

s.send("Hello server!".encode())

with open('received_file', 'wb') as f:
    print('receiving data...')
    while True:
        data = s.recv(1024)
        print('data=%s', (data))
        if not data:
            break
        f.write(data)

print('Successfully received the file')
s.close()
print('Connection closed')
```

## Server:
```
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
 filename='mytext.txt'
 f = open(filename,'rb')
 l = f.read(1024)
 while (l):
    conn.send(l)
    print('Sent ',repr(l))
    l = f.read(1024)
 f.close()
 print('Done sending')
 conn.send('Thank you for connecting'.encode())
 conn.close()
```
## OUTPUT
## CLINT
![Screenshot 2024-05-17 190712](https://github.com/feryjfgkuyfgewjfgew/3c.FILE_TRANSFER_USING_TCP_SOCKETS/assets/150319377/9b986c61-c097-44bc-9cb7-3951bfac21fb)

## SERVER
![Screenshot 2024-05-17 190726](https://github.com/feryjfgkuyfgewjfgew/3c.FILE_TRANSFER_USING_TCP_SOCKETS/assets/150319377/d995064c-581b-44e5-9eb0-4a226fc2eb86)



## RESULT
Thus, the python program for creating File Transfer using TCP Sockets Links was 
successfully created and executed.
