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
Terminal:

![Screenshot 2024-04-17 111317](https://github.com/ThakshaRishi/3c.FILE_TRANSFER_USING_TCP_SOCKETS/assets/144870423/0954a764-269f-4e23-bcc2-19e4929959a5)

Original File:

![Screenshot 2024-04-17 111552](https://github.com/ThakshaRishi/3c.FILE_TRANSFER_USING_TCP_SOCKETS/assets/144870423/a68389ea-4329-4948-a23c-32a5eae0714d)

Received File:

![Screenshot 2024-04-17 111527](https://github.com/ThakshaRishi/3c.FILE_TRANSFER_USING_TCP_SOCKETS/assets/144870423/0b08bfaa-718d-48d4-815a-148bd8132845)

## RESULT
Thus, the python program for creating File Transfer using TCP Sockets Links was 
successfully created and executed.
