# Kart IT

## Setup Instructions

1.  You can use any server of your choice, WAMP is prefered as it is simple and easy to use. <br> 
Download and install WAMP server for your windows machine [WAMP Website](http://www.wampserver.com/en/)
1. After installing WAMP server open http://localhost in your browser. And click on **Add a Virtual Host**, it should look something like this : 

![WAMP Virtual Host][1]

1. After this is setingup the virtual and restarting WAMP, go to `<WAMP_LOCATION>\bin\apache\apache2.4.23\conf` and in that open `httpd.conf` and somewhere on Line 75 add all the ports you want to listen. This example will listen on port 8001 and 8002

```
Listen 0.0.0.0:8001
Listen [::]:8001
Listen 0.0.0.0:8002
Listen [::]:8002
```

1. Next go to the extras folder and open `httpd-vhosts.conf` file. There you shoud find your virtual host we setup earlier. Change it to this format. Replace `e:/Kart IT` with the location where you have placed your html files. Also make sure what ever port(here 8001) you have specified you are listening ot that port in `httpd.conf` file.

```
<VirtualHost *:8001>
	ServerName localhost
	DocumentRoot "e:/Kart IT"
	<Directory  "e:/Kart IT/">
		Options +Indexes +Includes +FollowSymLinks +MultiViews
		AllowOverride All
		Require all granted
	</Directory>
</VirtualHost>
```

1. After that open http://localhost:8001 in your browser and you should be able to see your index.html page being rendered.

![Homepage][2]

1. Make sure to test whether it works from other computers. Find the ipaddress of the server by typing `ipconfig` in CMD. It should be something like `192.168.12.123`. So open a browser from another computer and type http://192.168.12.123:8001 and you should be able to view the index.html page.

## NOTE

#### You will have to manually add and remove the code to display the images after every round
#### Make sure the image folder names cannot be guessed.


[1]: /images/screenshots/Creating%20Virtual%20Host.png?raw=true
[2]: /images/screenshots/Kart%20IT%20Homepage.png?raw=true
