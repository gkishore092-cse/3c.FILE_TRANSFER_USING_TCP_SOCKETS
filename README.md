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
<img width="806" height="452" alt="image" src="https://github.com/user-attachments/assets/61d1fda1-0217-4874-80bc-ad50069b3f4b" />
<img width="809" height="482" alt="image" src="https://github.com/user-attachments/assets/4a17cea5-6aa8-48a6-9619-8f889640410e" />

## RESULT
Thus, the python program for creating File Transfer using TCP Sockets Links was 
successfully created and executed.
