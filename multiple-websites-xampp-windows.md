# How to create multiple websites in XAMPP for Windows

Let's assume you have Xampp installed on your C: drive: `С:\Xampp`. All links will take this into account, but you can change them to the actual location of Xampp you have.

Open the `C:\Xampp\apache\conf\httpd.conf` file and make sure the httpd-vhosts.conf line is uncommented:
```bash
# Virtual hosts
Include conf/extra/httpd-vhosts.conf
```

Open the `C:\Xampp\apache\conf\extra\httpd-vhosts.conf` file and add the following:

```bash
# To make sure that the default localhost in Xampp\htdocs will work.
# Without this, the next project will be launched by default
<VirtualHost *:80>
  DocumentRoot "C:\Xampp\htdocs"
  ServerName localhost
</VirtualHost>

# Our second site, it can be anywhere, for example on drive D: in the Projects folder
<VirtualHost *:80>
    ServerName mynewproject.ua
    DocumentRoot "D:\Projects\MyNewProject"
    ErrorLog "logs/wordpress-errors.log"
    CustomLog "logs/wordpress-access.log" common
    <Directory "D:\Projects\wordpress-band">
        Options Indexes FollowSymLinks
        AllowOverride All
        Require all granted
    </Directory>
</VirtualHost>
```

Open the `%windir%\system32\drivers\etc\hosts` file and add your domain there at the end of the document:
```
127.0.0.1    mynewproject.ua
127.0.0.1    www.mynewproject.ua
```

And our last step, restart Xampp.
