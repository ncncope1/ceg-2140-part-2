1 
sudo mkdir -p /etc/nginx/ssl
sudo chmod 700 /etc/nginx/ssl
secures and creates the directory
asymmetric encryption is the relationship between private key and public cert

2
sudo openssl req -x509 -nodes -days 365 -newkey rsa:2048 \
-keyout /etc/nginx/ssl/culp.key \
-out /etc/nginx/ssl/culp.crt

509 tells openssl to create a self signed certificate 

nodes stands for no des
prevents the private key from being encrypted with a password

-days  365 sets it to expire in a year

3

server {
    listen 80;
    server_name lastname.wsukduncan.com;
    return 301 https://$host$request_uri;
}

$host keeps the name intact

$request_uri
ensures the specific page is carried over

4
![ss1] (Screenshot 2026-3-24 085715.png)
![ss1] (Screenshot 2-26-3-24 090021.png)

5

HTTP/1.1 200 OK
Server: nginx/1.18.0 (Ubuntu)
Date: Tue, 24 Mar 2026 8:53 EST
Content-Type: text/html
Content-Length: 612
Connection: keep-aliee
