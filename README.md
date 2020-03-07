# otus_27
# Web сервера

Домашнее задание:

Необходимо редактировать nginx.conf из репозитория https://gitlab.com/otus_linux/nginx-antiddos-example
(не следует использовать include и править Dockerfile).

Cделанную работу залить hub.docker.com, при этом content в otus.txt должен содержать в себе название Вашего репозитория hub.docker.com и только его

Базовое задание должно быть в образе с тегом latest, задание для продвинутых в образе с тегом advanced.

Самопроверка: docker run -p 80:80 your_account/your_repo:latest (или your_account/your_repo:advanced) - запустит nginx c выполненым заданием. сurl http://localhost/otus.txt - редирект(или ошибка) , открыв ту же страницу в браузере - увидим your_account/your_repo

_________________________________________________________________________________________________________________________

# Домашняя работа

Загрузить образ, запустить контейнер
```
docker pull edo2681/webhomework
docker run -d -p 80:80 edo2681/webhomework
```
# 1
```
curl http://localhost/otus.txt -i -L
```
Ответ
```
HTTP/1.1 302 Moved Temporarily
Server: nginx/1.17.6
Date: Sat, 07 Mar 2020 17:13:30 GMT
Content-Type: text/html
Content-Length: 145
Connection: keep-alive
Location: http://localhost/addcookie
Set-Cookie: first_uri=/otus.txt

HTTP/1.1 302 Moved Temporarily
Server: nginx/1.17.6
Date: Sat, 07 Mar 2020 17:13:30 GMT
Content-Type: text/html
Content-Length: 145
Connection: keep-alive
Location: 
Set-Cookie: access=secretkey

<html>
<head><title>302 Found</title></head>
<body>
<center><h1>302 Found</h1></center>
<hr><center>nginx/1.17.6</center>
</body>
</html>
```
# 2
```
curl http://localhost/otus.txt -i -L -b cookie -c cookie
```
Ответ
```
HTTP/1.1 302 Moved Temporarily
Server: nginx/1.17.6
Date: Sat, 07 Mar 2020 17:13:50 GMT
Content-Type: text/html
Content-Length: 145
Connection: keep-alive
Location: http://localhost/addcookie
Set-Cookie: first_uri=/otus.txt

HTTP/1.1 302 Moved Temporarily
Server: nginx/1.17.6
Date: Sat, 07 Mar 2020 17:13:50 GMT
Content-Type: text/html
Content-Length: 145
Location: http://localhost/otus.txt
Connection: keep-alive
Set-Cookie: access=secretkey

HTTP/1.1 200 OK
Server: nginx/1.17.6
Date: Sat, 07 Mar 2020 17:13:50 GMT
Content-Type: text/plain
Content-Length: 20
Last-Modified: Sat, 07 Mar 2020 14:36:31 GMT
Connection: keep-alive
ETag: "5e63b16f-14"
Accept-Ranges: bytes
```

выполнение
собрать образ

docker build -t ddos .
запустить контейнер

docker run --rm -d -p 80:80 ddos
проверить ss/netstat, что контейнер слушает на 80 порту

подключиться к докерхабу

docker login
задать тег latest

docker tag ddos:latest shaadowsky/ddos:latest
запушить образ

docker push shaadowsky/ddos:latest
