# otus_27
# Web сервера

Домашнее задание:

Необходимо редактировать nginx.conf из репозитория https://gitlab.com/otus_linux/nginx-antiddos-example
(не следует использовать include и править Dockerfile).

Cделанную работу залить hub.docker.com, при этом content в otus.txt должен содержать в себе название Вашего репозитория hub.docker.com и только его

Базовое задание должно быть в образе с тегом latest, задание для продвинутых в образе с тегом advanced.

Самопроверка: docker run -p 80:80 your_account/your_repo:latest (или your_account/your_repo:advanced) - запустит nginx c выполненым заданием. сurl http://localhost/otus.txt - редирект(или ошибка) , открыв ту же страницу в браузере - увидим your_account/your_repo

_________________________________________________________________________________________________________________________
