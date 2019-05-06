# Proxy Wss Nginx

Проксирование wss nginx

Для проксирования требуется обратиться во внешний https! (не путать обращение по wss внешний)

Открываем настройки для домена (пример: nano /home/user/conf/web/domain1.com.nginx.ssl.conf):

<pre>
    location ~* ^/ws/$ {
                proxy_read_timeout 99999;
                proxy_pass https://stream.exemple.com/ws$request_uri;
                proxy_http_version 1.1;
                proxy_set_header Upgrade $http_upgrade;
                proxy_set_header Connection "upgrade";
    }
    resolver 8.8.8.8;
</pre>

Далее обратиться к своему хосту: wss://domain1.com/ws
