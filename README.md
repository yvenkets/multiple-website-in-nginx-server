# multiple-website-in-nginx-server

#1.Install Updates

sudo apt-get update

#2.install Nginx package

sudo apt-get install nginx

#to restart nginx

sudo service nginx restart

#find which apps for configure firewall

sudo ufw app list

#configure nginx in firewall

sudo ufw allow 'Nginx HTTP'

#to know the nginx service status

sudo systemctl status nginx

#to enable or disable nginx service status at system startup

sudo systemctl enable nginx
sudo systemctl disable nginx


#3.create folder root for your website

sudo mkdir -p /var/www/html/venketraman.com/

#4.assign folder rights to the user

sudo chown -R $USER:$USER /var/www/html/venketraman.com/

#5.provide proper rights to the website path

sudo chmod -R 755 /var/www/html/

#6.edit your index.html file  OR put your static website files here

sudo vi /var/www/html/venketraman.com/index.html

#7.copy the defalut nginx conf file as your sitename.conf in the below location

sudo cp /etc/nginx/sites-available/default /etc/nginx/sites-available/venketraman.com.conf

#8.edit the configuration file

sudo vi /etc/nginx/sites-available/venketraman.com.conf
	#in server line change look like this
	
	server {
	listen 80;
	listen [::]:80;
	
	# in website folder location change like this
	
	root /var/www/html/venketraman.com/public_html;
	
	// if you have php website file enter like this
	
	# Add index.php to the list if you are using PHP
	
	index index.html index.htm index.nginx-debian.html index.php;
	
	# In Server name change like below
	
	server_name venketraman.com www.venketraman.com;
	# close server block
             }
	
	
#9.(optional)Delete the default conf file

sudo rm /etc/nginx/sites-enabled/default

#10.make the symbolic link your conf file to sites enabled folder

sudo ln -s /etc/nginx/sites-available/venketraman.com.conf /etc/nginx/sites-enabled/

#11.restart Nginx service

sudo service nginx restart

repeats Steps 3 to 11 for each website you want to create 
 Site 2 Follows
	sudo mkdir -p /var/www/html/venket.com

	sudo chown -R $USER:$USER /var/www/html/venket.com

	sudo vi /var/www/html/venket.com/index.html

	sudo cp /etc/nginx/sites-available/default /etc/nginx/sites-available/venket.com.conf

	sudo vi /etc/nginx/sites-available/venket.com.conf

	sudo ln -s /etc/nginx/sites-available/venket.com.conf /etc/nginx/sites-enabled/


Site 3 Follows
	

	sudo mkdir -p /var/www/html/we2.venket.com

	sudo chown -R $USER:$USER /var/www/html/we2.venket.com
  
	sudo vi /var/www/html/we2.venket.com/index.html

	sudo cp /etc/nginx/sites-available/default /etc/nginx/sites-available/we2.venket.com.conf

	sudo vi  /etc/nginx/sites-available/we2.venket.com.conf
	
	sudo ln -s /etc/nginx/sites-available/we2.venket.com.conf /etc/nginx/sites-enabled/
  
  after all the configuration check nginx configuration is correct
  
  sudo nginx -t
