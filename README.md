# vultr_letencrypt_nginx
how to create Https on Ubuntu


## 1. DNS   先加入兩個 A 級 www.domain.tw 、domain.tw

## 2. Ubuntu 執行以下指令
```sudo snap install core```

```sudo snap refresh core```

```sudo snap install --classic certbot```

```sudo ln -s /snap/bin/certbot /usr/bin/certbot```

## 3.打開 Nginx 設定檔
nano /etc/nginx/conf.d/default

server { 
  #加入
  
	location /.well-known/acme-challenge/ {}  
}

```service nginx reload```

```nginx -t```

## 4.你要使用HTTPS 的網址
```certbot --nginx --redirect -d domain.tw -d www.domain.tw -m yourmail@gmail.com --agree-tos```

certbot 將自動對 nginx 設定檔追加 ssl 區塊

## MEMO
server上檢查是否有憑證

```certbot certificates```
