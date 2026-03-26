# 5a_Create_Socket_for_HTTP_for_webpage_upload_and_download
## AIM :
To write a PYTHON program for socket for HTTP for web page upload and download
## Algorithm

1.Start the program.
<BR>
2.Get the frame size from the user
<BR>
3.To create the frame based on the user request.
<BR>
4.To send frames to server from the client side.
<BR>
5.If your frames reach the server it will send ACK signal to client otherwise it will send NACK signal to client.
<BR>
6.Stop the program
<BR>
## Program 
```
import socket 
def send(host, port, req, data=b''): 
with socket.socket() as s: 
s.connect((host, port)) 
s.sendall(req.encode() + data) 
return s.recv(4096).decode() 
def upload(host, port, file): 
data = open(file, 'rb').read() 
req = f"POST /upload HTTP/1.1\r\nHost: {host}\r\nContent-Length:   
return send(host, port, req, data) 
def download(host, port, file): 
res = send(host, port, f"GET /{file} HTTP/1.1\r\nHost: {host}\r\n\r\n") 
open(file, 'wb').write(res.split('\r\n\r\n', 1)[1].encode()) 
if __name__ == "__main__": 
h, p, f = 'example.com', 80, 'example.txt' 
print("Upload:", upload(h, p, f)) 
download(h, p, f) 
print("Downloaded.")
```

## OUTPUT
<img width="812" height="492" alt="image" src="https://github.com/user-attachments/assets/20843030-90a4-4b6c-ae94-0493f9b54654" />

## Result
Thus the socket for HTTP for web page upload and download created and Executed
