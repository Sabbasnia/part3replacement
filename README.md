# part3replacement
first we have to install the nginx
```bash
sudo pacman -S nginx
```
we should enable nginx so it will start on system load.
```bash
sudo systemctl enable nginx
sudo systemctl start nginx
```

if you have to update your cpackages do it  with the following 
just in case
```bash
sudo pacman  -Syu
```
install the Vim
```bash
sudo pacman -S vim
```
  
now we have to create two directories
```bash 
sudo mkdir -p /etc/nginx/sites-available
sudo mkdir -p /etc/nginx/sites-enabled
```
sites-available folder is for storing our sites config files
sites-enabled folder contains all active configs (a link to the config files in sites-available)
```bash
sudo vim nginx-2420
```

now we should serve static file inside the created file above 
we should create 


```
server {
    listen 80 default_server;
    location / {
        root /srv/2420-files;
        autoindex on;
    }
}
```
the you should restart the nginx service.
```bash
sudo systemctl restart nginx
```

we should ct to this path: /srv/2420-files
and add some files to it

when it restarted the file there we should create some files to


we can test this by entering our ip in our browser
you should see a list of files 


now we are writing a script that will handle all the requests for us

note that in this process you might use something that is
```bash
sudo chmod +x <whatever file>
```
```
sudo pacman -Sy nginx
sudo pacman -Sy vim
sudo systemctl enable nginx
sudo systemctl start nginx
sudo mkdir /etc/nginx/sites-available
sudo mkdir /etc/nginx/sites-enabled
sudo mkdir -p /srv/2420-files
sudo chown -R http:http /srv
cd /etc/nginx/sites-available
touch nginx-2420
cat << EOF > nginx-2420
server {
    listen 80 default_server;
    location / {
        root /srv/2420-files;
        autoindex on;
    }
}
EOF
sudo ln -s nginx-2420 /etc/nginx/sites-enabled/nginx-2420
sudo systemctl restart nginx
```
ine khobe ????






