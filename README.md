#Install Docker

sudo apt-get update
sudo apt-get install ca-certificates curl
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc



echo \
"deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
$(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update



sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin


sudo apt install docker-compose

#versions
sudo docker --version
sudo docker-compose --version



# have:
- nginx
- php
- pgsql
- redis
- composer
- artisan
- Node.js, NPM, Yarn



### For first start
- `docker-compose up -d --build`
### install Laravel
- `cd src`
- `composer create-project laravel/laravel .`

### migration DB
- `cd src` //if in root directory
- `php artisan migrate`

### Other start
- `docker-compose up -d`

### Other down
- `docker-compose down`

### Other down with clean
- `docker-compose down -v`
