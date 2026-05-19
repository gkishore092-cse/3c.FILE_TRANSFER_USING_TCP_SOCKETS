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
CLIENT
```
import socket
s = socket.socket()
host = socket.gethostname()
port = 60000
s.connect((host, port))
s.send("Hello server!".encode())
with open('received_file.txt', 'wb') as f:
    while True:
        print("Receiving data...")
        data = s.recv(1024)
        if not data:
            break
        f.write(data)
print("Successfully received the file")
s.close()
print("Connection closed")
```
SERVER
```
import socket
port = 60000
s = socket.socket()
host = socket.gethostname()
s.bind((host, port))
s.listen(5)
print("Server waiting...")
while True:
    conn, addr = s.accept()
    print("Connected from", addr)
    data = conn.recv(1024)
    print("Server received:", data.decode())
    filename = "mytext.txt"
    f = open(filename, 'rb')
    l = f.read(1024)
    while l:
        conn.send(l)
        print("Sent:", repr(l))
        l = f.read(1024)
    f.close()
    print("Done sending")
    conn.close()
```
## OUPUT
<img width="802" height="450" alt="3c 1" src="https://github.com/user-attachments/assets/b1d8e3b1-b1fa-49b7-8206-ec6788a060cf" />
<img width="809" height="482" alt="3c2" src="https://github.com/user-attachments/assets/65273ff2-3730-4bab-88cb-3340f05b201e" />

## RESULT
Thus, the python program for creating File Transfer using TCP Sockets Links was 
successfully created and executed.
