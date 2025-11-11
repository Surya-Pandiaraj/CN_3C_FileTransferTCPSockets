### NAME: SURYA P <br>
### REG NO: 212224230280

## EX. No. 3c : FILE TRANSFER USING TCP SOCKETS

## AIM :

To write a python program for creating File Transfer using TCP Sockets Links

## ALGORITHM :

1. Import the necessary python modules.
2. Create a socket connection using socket module.
3. Send the message to write into the file to the client file.
4. Open the file and then send it to the client in byte format.
5. In the client side receive the file from server and then write the content into it.

## PROGRAM : 

### client.py :

```
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
print('Successfully get the file')
s.close()
print('connection closed')
```

### server.py :

```
import socket

port = 60000
s = socket.socket()
host = socket.gethostname()
s.bind((host, port))
s.listen(5)

print("Server is listening...")

while True:
    conn, addr = s.accept()
    print("Got connection from", addr)
    
    data = conn.recv(1024)
    print("Server received", repr(data))
    
    filename = 'surya.txt'
    f = open(filename, 'rb')
    l = f.read(1024)
    
    while l:
        conn.send(l)
        print("Sent", repr(l))
        l = f.read(1024)
    
    f.close()
    print("Done sending")
    
    conn.send('Thank you for connecting'.encode())
    conn.close()

```

## OUPUT :

### client.py :

<img width="515" height="251" alt="image" src="https://github.com/user-attachments/assets/fb37cbe9-e129-46cd-b8d5-d596b8a2da37" />

### server.py :

<img width="599" height="206" alt="image" src="https://github.com/user-attachments/assets/8d7961d1-748e-4429-85f4-f36d83e12d0b" />

## RESULT :

Thus, the python program for creating File Transfer using TCP Sockets Links was successfully created and executed.
