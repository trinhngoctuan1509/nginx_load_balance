proxy_ip  = "192.168.0.3"
backend_ip_1  = "192.168.0.40"
backend_ip_2  = "192.168.0.41"
backend_ip_3  = "192.168.0.42"

proxy_script = 
"
sudo su -
mv /etc/nginx/conf.d/proxy.petshoptomandjerry.com.conf /etc/nginx/conf.d/proxy.petshoptomandjerry.com
apt update
apt install nginx -y
rm /etc/nginx/sites-enabled/default
rm /etc/nginx/sites-available/default
rm -r /var/www/html
mv /etc/nginx/conf.d/proxy.petshoptomandjerry.com /etc/nginx/conf.d/proxy.petshoptomandjerry.com.conf
systemctl reload nginx
"

backend_script_1 = 
"
sudo su -
mv /etc/nginx/conf.d/backend.petshoptomandjerry.com.conf /etc/nginx/conf.d/backend.petshoptomandjerry.com
apt update
apt install nginx -y
rm /etc/nginx/sites-enabled/default
rm /etc/nginx/sites-available/default
rm -r /var/www/html
mv /etc/nginx/conf.d/backend.petshoptomandjerry.com /etc/nginx/conf.d/backend.petshoptomandjerry.com.conf
mkdir /var/www/petshoptomandjerry.com
cd /var/www/petshoptomandjerry.com
echo 'Server BE tom&jerry number 1' > /var/www/petshoptomandjerry.com/index.html
systemctl reload nginx
"

backend_script_2 = 
"
sudo su -
mv /etc/nginx/conf.d/backend.petshoptomandjerry.com.conf /etc/nginx/conf.d/backend.petshoptomandjerry.com
apt update
apt install nginx -y
rm /etc/nginx/sites-enabled/default
rm /etc/nginx/sites-available/default
rm -r /var/www/html
mv /etc/nginx/conf.d/backend.petshoptomandjerry.com /etc/nginx/conf.d/backend.petshoptomandjerry.com.conf
mkdir /var/www/petshoptomandjerry.com
cd /var/www/petshoptomandjerry.com
echo 'Server BE tom&jerry number 2' > /var/www/petshoptomandjerry.com/index.html
systemctl reload nginx
"

backend_script_3 = 
"
sudo su -
mv /etc/nginx/conf.d/backend.petshoptomandjerry.com.conf /etc/nginx/conf.d/backend.petshoptomandjerry.com
apt update
apt install nginx -y
rm /etc/nginx/sites-enabled/default
rm /etc/nginx/sites-available/default
rm -r /var/www/html
mv /etc/nginx/conf.d/backend.petshoptomandjerry.com /etc/nginx/conf.d/backend.petshoptomandjerry.com.conf
mkdir /var/www/petshoptomandjerry.com
cd /var/www/petshoptomandjerry.com
echo 'Server BE tom&jerry number 3' > /var/www/petshoptomandjerry.com/index.html
systemctl reload nginx
"

Vagrant.configure("2") do |config|
  config.vm.box = "bento/ubuntu-18.04"

  config.vm.define "proxy" do |proxy|
    proxy.vm.network "private_network", ip: proxy_ip
    proxy.vm.provision "shell", inline: proxy_script
    proxy.vm.synced_folder "./proxy_conf.d", "/etc/nginx/conf.d"
  end
 
  config.vm.define "backend1" do |server|
    server.vm.network "private_network", ip: backend_ip_1
    server.vm.provision "shell", inline: backend_script_1
    server.vm.synced_folder "./backend_conf.d", "/etc/nginx/conf.d"
  end

  config.vm.define "backend2" do |server|
    server.vm.network "private_network", ip: backend_ip_2
    server.vm.provision "shell", inline: backend_script_2
    server.vm.synced_folder "./backend_conf.d", "/etc/nginx/conf.d"
  end

  config.vm.define "backend3" do |server|
    server.vm.network "private_network", ip: backend_ip_3
    server.vm.provision "shell", inline: backend_script_3
    server.vm.synced_folder "./backend_conf.d", "/etc/nginx/conf.d"
  end
end
