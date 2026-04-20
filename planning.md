Inbound	80 (HTTP)	0.0.0.0/0 (Internet)	Initial connection & redirect
Inbound	443 (HTTPS)	0.0.0.0/0 (Internet)	Secure encrypted traffic
Inbound	22 (SSH)	Admin IP / Bastion Host	Management access
Outbound	80/443	OS Repositories / APIs	Updates and external integrations
Outbound	53 (UDP/TCP)	DNS Servers	Domain resolution

hierarchy

nacl

security groups

system

create self singed
openssl req -x509 -newkey rsa:4096 -keyout key.pem -out cert.pem -sha256 -days 365 -nodes

storage / permissions 
store in /etc/ssl/private matters to be able to find them easily and backup scripts
private key 600, root, if the kye is readable, anyone can read it
for most,  domain validation is the use CA would do, its fast

https config
most servers require ssl module to be active

need port 80 and port 443

<VirtualHost *:80>
    ServerName (whatevertheservernameissetto)
    RewriteEngine On
    RewriteCond %{HTTPS} off
    RewriteRule ^(.*)$ https://%{HTTP_HOST}%{REQUEST_URI} [L,R=301]
</VirtualHost>
