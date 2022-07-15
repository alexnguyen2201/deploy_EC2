# deploy_EC2

## Access EC2 by SSH

## Install
```console
sudo apt-get update
sudo apt install -y python3-pip nginx
```

## Configure Nginx
```console
sudo vim /etc/nginx/sites-enabled/fastapi_nginx
```
Câu lệnh trên tạo một file mới ở đường dẫn như trên

Trên cửa sổ vim hiện ra, ta thêm vào các nội dung sau:

```json
server {
    listen 80; 
    server_name 54.151.166.96;
    location / {
        proxy_pass http://127.0.0.1:8000;
    }
}
```

80 là default port của HTTP là nơi các traffic comming.
54.151.166.96 là địa chỉ public IPv4 của EC2 instance

location / là nơi Nginx route các traffic đến nơi đó
Theo góc nhìn của instance thì là địa chỉ loopback 


```console
sudo service nginx restart
```
restart lại để load config



