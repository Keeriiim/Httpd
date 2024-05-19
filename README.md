







# Installation

```bash
yum install httpd -y
yum install vim -y

```

# Running Python Scripts
There are two ways of running .py scripts. 
![image](https://github.com/Keeriiim/Httpd/assets/117115289/b66b137c-8aab-4cc4-8be9-0195d5ccf848)  

## /var/www/html
This is the second way. In order for the script to work we need to edit the httpd.conf file.  
  
Go to <Directory "/var/www/html"> and add ExecCGI to Options, this is to enable .py scripts.  
Go to <IfModule dir_module> and add index.py(name of our script). If not our webserver will print the default test page.  
![image](https://github.com/Keeriiim/Httpd/assets/117115289/8a99e3e2-66bb-401a-8538-cda4a7bc8d00)  
  
Now we go down to <IfModule mime_module> and add AddType application/x-httpd-cgi .py
The AddType directive in Apache is used to associate certain filename extensions with specific MIME types.  
In the context of AddType application/x-httpd-cgi .py, it tells Apache that files with the .py extension should be treated as CGI (Common Gateway Interface) scripts and executed accordingly.  
This directive is essential for instructing Apache to handle Python scripts properly. Without it, Apache may not recognize .py files as executable scripts, and they would be served as plain text or download prompts instead of being executed by the Python interpreter.  

```bash
AddType application/x-httpd-cgi .py
```
![image](https://github.com/Keeriiim/Httpd/assets/117115289/9fc7e83a-5829-4116-9a84-712195583d5a)  


## /var/www/cgi-bin
This is the preferable way of running the scripts. In order for the script to work we need to edit the httpd.conf file.  
  
We do this the same way as before. The only differences are:  
* We don't need ExecCGI under Options in <Directory "/var/www/html">
* We need to curl localhost/cgi-bin/ or ipAddr/cgi-bin/
```bash
vim /etc/httpd/conf/httpd.conf
```





