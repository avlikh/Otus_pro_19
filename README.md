# Otus_pro_19

## OTUS PRO Homework 19 Docker

### Домашнее задание:   
1. Установите Docker на хост машину.   
2. Установите Docker Compose - как плагин, или как отдельное приложение.   
3. Создайте свой кастомный образ nginx на базе alpine. После запуска nginx должен отдавать кастомную страницу (достаточно изменить дефолтную страницу nginx).   
4. Определите разницу между контейнером и образом.   
5. Вывод опишите в домашнем задании.   
6. Ответьте на вопрос: Можно ли в контейнере собрать ядро?   
---
## Выполнение задания:
* Примечание: Домашняя работа выполнялась на Debian 12
### 1. Установите Docker на хост машину.   
### 2. Установите Docker Compose - как плагин, или как отдельное приложение:   
Установим Docker,  Docker Compose и curl:
```
apt install -y docker docker-compose curl
```
Создадим папку для нашего образа и зайдем в нее:
```
mkdir -p /opt/nginx-otus ; cd /opt/nginx-otus
```
Создадим Dockerfile:
```
echo 'FROM nginx:alpine
COPY ./index.html /usr/share/nginx/html/index.html' > Dockerfile
```
Создадим index.html:
```
echo '<h1><center>Test OTUS NGIX docker container</center></h1>' > index.html
```
Создадим кастомизированный контейнер:
```
docker build -t nginxotus .
```
<details>
<summary> результат выполнения команды: </summary>

```
Sending build context to Docker daemon  3.072kB
Step 1/2 : FROM nginx:alpine
alpine: Pulling from library/nginx
66a3d608f3fa: Pull complete
58290db888fa: Pull complete
5d777e0071f6: Pull complete
dbcfe8732ee6: Pull complete
37d775ecfbb9: Pull complete
e0350d1fd4dd: Pull complete
1f4aa363b71a: Pull complete
e74fff0a393a: Pull complete
Digest: sha256:814a8e88df978ade80e584cc5b333144b9372a8e3c98872d07137dbf3b44d0e4
Status: Downloaded newer image for nginx:alpine
 ---> 93f9c72967db
Step 2/2 : COPY ./index.html /usr/share/nginx/html/index.html
 ---> c31e013e6238
Successfully built c31e013e6238
Successfully tagged nginxotus:latest
```
</details>
