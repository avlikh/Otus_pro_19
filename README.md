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
### 2. Установите Docker Compose - как плагин, или как отдельное приложение.  
### 3. Создайте свой кастомный образ nginx на базе alpine. После запуска nginx должен отдавать кастомную страницу (достаточно изменить дефолтную страницу nginx):
Установим Docker,  Docker Compose и curl:
```
apt install -y docker docker-compose curl
```

<details>
<summary> результат выполнения команды: </summary>

```
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following additional packages will be installed:
  binutils binutils-common binutils-x86-64-linux-gnu cgroupfs-mount containerd criu docker.io git git-man iptables libbinutils libctf-nobfd0 libctf0 libcurl3-gnutls libcurl4 liberror-perl libgprofng0 libintl-perl
  libintl-xs-perl libip6tc2 libmodule-find-perl libnet1 libnetfilter-conntrack3 libnfnetlink0 libnl-3-200 libproc-processtable-perl libprotobuf32 libsort-naturally-perl libterm-readkey-perl libyaml-0-2 needrestart
  patch python3-attr python3-distro python3-distutils python3-docker python3-dockerpty python3-docopt python3-dotenv python3-json-pointer python3-jsonschema python3-lib2to3 python3-protobuf python3-pyrsistent
  python3-rfc3987 python3-texttable python3-uritemplate python3-webcolors python3-websocket python3-yaml runc sgml-base tini wmdocker
Suggested packages:
  binutils-doc containernetworking-plugins docker-doc aufs-tools btrfs-progs debootstrap rinse rootlesskit zfs-fuse | zfsutils-linux git-daemon-run | git-daemon-sysvinit git-doc git-email git-gui gitk gitweb git-cvs
  git-mediawiki git-svn firewalld needrestart-session | libnotify-bin ed diffutils-doc python-attr-doc python-jsonschema-doc sgml-base-doc
The following NEW packages will be installed:
  binutils binutils-common binutils-x86-64-linux-gnu cgroupfs-mount containerd criu curl docker docker-compose docker.io git git-man iptables libbinutils libctf-nobfd0 libctf0 libcurl4 liberror-perl libgprofng0
  libintl-perl libintl-xs-perl libip6tc2 libmodule-find-perl libnet1 libnetfilter-conntrack3 libnfnetlink0 libnl-3-200 libproc-processtable-perl libprotobuf32 libsort-naturally-perl libterm-readkey-perl libyaml-0-2
  needrestart patch python3-attr python3-distro python3-distutils python3-docker python3-dockerpty python3-docopt python3-dotenv python3-json-pointer python3-jsonschema python3-lib2to3 python3-protobuf
  python3-pyrsistent python3-rfc3987 python3-texttable python3-uritemplate python3-webcolors python3-websocket python3-yaml runc sgml-base tini wmdocker
The following packages will be upgraded:
  libcurl3-gnutls
1 upgraded, 56 newly installed, 0 to remove and 49 not upgraded.
Need to get 47.4 MB/86.4 MB of archives.
After this operation, 366 MB of additional disk space will be used.
Get:1 http://deb.debian.org/debian bookworm/main amd64 docker.io amd64 20.10.24+dfsg1-1+deb12u1 [36.2 MB]
Get:2 http://deb.debian.org/debian bookworm/main amd64 criu amd64 3.17.1-2+deb12u1 [665 kB]
Get:3 http://deb.debian.org/debian bookworm/main amd64 libcurl4 amd64 7.88.1-10+deb12u8 [390 kB]
Get:4 http://deb.debian.org/debian bookworm/main amd64 curl amd64 7.88.1-10+deb12u8 [315 kB]
Get:5 http://deb.debian.org/debian bookworm/main amd64 libcurl3-gnutls amd64 7.88.1-10+deb12u8 [385 kB]
Get:6 http://deb.debian.org/debian-security bookworm-security/main amd64 git-man all 1:2.39.5-0+deb12u2 [2,053 kB]
Get:7 http://deb.debian.org/debian-security bookworm-security/main amd64 git amd64 1:2.39.5-0+deb12u2 [7,260 kB]
Get:8 http://deb.debian.org/debian bookworm/main amd64 needrestart all 3.6-4+deb12u3 [60.5 kB]
Fetched 47.4 MB in 7s (6,972 kB/s)
apt-listchanges: Reading changelogs...
Extracting templates from packages: 100%
Selecting previously unselected package runc.
(Reading database ... 28697 files and directories currently installed.)
Preparing to unpack .../00-runc_1.1.5+ds1-1+deb12u1_amd64.deb ...
Unpacking runc (1.1.5+ds1-1+deb12u1) ...
Selecting previously unselected package containerd.
Preparing to unpack .../01-containerd_1.6.20~ds1-1+b1_amd64.deb ...
Unpacking containerd (1.6.20~ds1-1+b1) ...
Selecting previously unselected package libip6tc2:amd64.
Preparing to unpack .../02-libip6tc2_1.8.9-2_amd64.deb ...
Unpacking libip6tc2:amd64 (1.8.9-2) ...
Selecting previously unselected package libnfnetlink0:amd64.
Preparing to unpack .../03-libnfnetlink0_1.0.2-2_amd64.deb ...
Unpacking libnfnetlink0:amd64 (1.0.2-2) ...
Selecting previously unselected package libnetfilter-conntrack3:amd64.
Preparing to unpack .../04-libnetfilter-conntrack3_1.0.9-3_amd64.deb ...
Unpacking libnetfilter-conntrack3:amd64 (1.0.9-3) ...
Selecting previously unselected package iptables.
Preparing to unpack .../05-iptables_1.8.9-2_amd64.deb ...
Unpacking iptables (1.8.9-2) ...
Selecting previously unselected package tini.
Preparing to unpack .../06-tini_0.19.0-1_amd64.deb ...
Unpacking tini (0.19.0-1) ...
Selecting previously unselected package docker.io.
Preparing to unpack .../07-docker.io_20.10.24+dfsg1-1+deb12u1_amd64.deb ...
Unpacking docker.io (20.10.24+dfsg1-1+deb12u1) ...
Selecting previously unselected package sgml-base.
Preparing to unpack .../08-sgml-base_1.31_all.deb ...
Unpacking sgml-base (1.31) ...
Selecting previously unselected package binutils-common:amd64.
Preparing to unpack .../09-binutils-common_2.40-2_amd64.deb ...
Unpacking binutils-common:amd64 (2.40-2) ...
Selecting previously unselected package libbinutils:amd64.
Preparing to unpack .../10-libbinutils_2.40-2_amd64.deb ...
Unpacking libbinutils:amd64 (2.40-2) ...
Selecting previously unselected package libctf-nobfd0:amd64.
Preparing to unpack .../11-libctf-nobfd0_2.40-2_amd64.deb ...
Unpacking libctf-nobfd0:amd64 (2.40-2) ...
Selecting previously unselected package libctf0:amd64.
Preparing to unpack .../12-libctf0_2.40-2_amd64.deb ...
Unpacking libctf0:amd64 (2.40-2) ...
Selecting previously unselected package libgprofng0:amd64.
Preparing to unpack .../13-libgprofng0_2.40-2_amd64.deb ...
Unpacking libgprofng0:amd64 (2.40-2) ...
Selecting previously unselected package binutils-x86-64-linux-gnu.
Preparing to unpack .../14-binutils-x86-64-linux-gnu_2.40-2_amd64.deb ...
Unpacking binutils-x86-64-linux-gnu (2.40-2) ...
Selecting previously unselected package binutils.
Preparing to unpack .../15-binutils_2.40-2_amd64.deb ...
Unpacking binutils (2.40-2) ...
Selecting previously unselected package cgroupfs-mount.
Preparing to unpack .../16-cgroupfs-mount_1.4_all.deb ...
Unpacking cgroupfs-mount (1.4) ...
Selecting previously unselected package libprotobuf32:amd64.
Preparing to unpack .../17-libprotobuf32_3.21.12-3_amd64.deb ...
Unpacking libprotobuf32:amd64 (3.21.12-3) ...
Selecting previously unselected package python3-protobuf.
Preparing to unpack .../18-python3-protobuf_3.21.12-3_amd64.deb ...
Unpacking python3-protobuf (3.21.12-3) ...
Selecting previously unselected package libnet1:amd64.
Preparing to unpack .../19-libnet1_1.1.6+dfsg-3.2_amd64.deb ...
Unpacking libnet1:amd64 (1.1.6+dfsg-3.2) ...
Selecting previously unselected package libnl-3-200:amd64.
Preparing to unpack .../20-libnl-3-200_3.7.0-0.2+b1_amd64.deb ...
Unpacking libnl-3-200:amd64 (3.7.0-0.2+b1) ...
Selecting previously unselected package criu.
Preparing to unpack .../21-criu_3.17.1-2+deb12u1_amd64.deb ...
Unpacking criu (3.17.1-2+deb12u1) ...
Selecting previously unselected package libcurl4:amd64.
Preparing to unpack .../22-libcurl4_7.88.1-10+deb12u8_amd64.deb ...
Unpacking libcurl4:amd64 (7.88.1-10+deb12u8) ...
Selecting previously unselected package curl.
Preparing to unpack .../23-curl_7.88.1-10+deb12u8_amd64.deb ...
Unpacking curl (7.88.1-10+deb12u8) ...
Selecting previously unselected package wmdocker.
Preparing to unpack .../24-wmdocker_1.5-2_amd64.deb ...
Unpacking wmdocker (1.5-2) ...
Selecting previously unselected package docker.
Preparing to unpack .../25-docker_1.5-2_all.deb ...
Unpacking docker (1.5-2) ...
Selecting previously unselected package python3-distro.
Preparing to unpack .../26-python3-distro_1.8.0-1_all.deb ...
Unpacking python3-distro (1.8.0-1) ...
Selecting previously unselected package python3-lib2to3.
Preparing to unpack .../27-python3-lib2to3_3.11.2-3_all.deb ...
Unpacking python3-lib2to3 (3.11.2-3) ...
Selecting previously unselected package python3-distutils.
Preparing to unpack .../28-python3-distutils_3.11.2-3_all.deb ...
Unpacking python3-distutils (3.11.2-3) ...
Selecting previously unselected package python3-websocket.
Preparing to unpack .../29-python3-websocket_1.2.3-1_all.deb ...
Unpacking python3-websocket (1.2.3-1) ...
Selecting previously unselected package python3-docker.
Preparing to unpack .../30-python3-docker_5.0.3-1_all.deb ...
Unpacking python3-docker (5.0.3-1) ...
Selecting previously unselected package python3-dockerpty.
Preparing to unpack .../31-python3-dockerpty_0.4.1-4_all.deb ...
Unpacking python3-dockerpty (0.4.1-4) ...
Selecting previously unselected package python3-docopt.
Preparing to unpack .../32-python3-docopt_0.6.2-4.1_all.deb ...
Unpacking python3-docopt (0.6.2-4.1) ...
Selecting previously unselected package python3-dotenv.
Preparing to unpack .../33-python3-dotenv_0.21.0-1_all.deb ...
Unpacking python3-dotenv (0.21.0-1) ...
Selecting previously unselected package python3-attr.
Preparing to unpack .../34-python3-attr_22.2.0-1_all.deb ...
Unpacking python3-attr (22.2.0-1) ...
Selecting previously unselected package python3-pyrsistent:amd64.
Preparing to unpack .../35-python3-pyrsistent_0.18.1-1+b3_amd64.deb ...
Unpacking python3-pyrsistent:amd64 (0.18.1-1+b3) ...
Selecting previously unselected package python3-jsonschema.
Preparing to unpack .../36-python3-jsonschema_4.10.3-1_all.deb ...
Unpacking python3-jsonschema (4.10.3-1) ...
Selecting previously unselected package python3-texttable.
Preparing to unpack .../37-python3-texttable_1.6.7-1_all.deb ...
Unpacking python3-texttable (1.6.7-1) ...
Selecting previously unselected package libyaml-0-2:amd64.
Preparing to unpack .../38-libyaml-0-2_0.2.5-1_amd64.deb ...
Unpacking libyaml-0-2:amd64 (0.2.5-1) ...
Selecting previously unselected package python3-yaml.
Preparing to unpack .../39-python3-yaml_6.0-3+b2_amd64.deb ...
Unpacking python3-yaml (6.0-3+b2) ...
Selecting previously unselected package docker-compose.
Preparing to unpack .../40-docker-compose_1.29.2-3_all.deb ...
Unpacking docker-compose (1.29.2-3) ...
Preparing to unpack .../41-libcurl3-gnutls_7.88.1-10+deb12u8_amd64.deb ...
Unpacking libcurl3-gnutls:amd64 (7.88.1-10+deb12u8) over (7.88.1-10+deb12u7) ...
Selecting previously unselected package liberror-perl.
Preparing to unpack .../42-liberror-perl_0.17029-2_all.deb ...
Unpacking liberror-perl (0.17029-2) ...
Selecting previously unselected package git-man.
Preparing to unpack .../43-git-man_1%3a2.39.5-0+deb12u2_all.deb ...
Unpacking git-man (1:2.39.5-0+deb12u2) ...
Selecting previously unselected package git.
Preparing to unpack .../44-git_1%3a2.39.5-0+deb12u2_amd64.deb ...
Unpacking git (1:2.39.5-0+deb12u2) ...
Selecting previously unselected package libintl-perl.
Preparing to unpack .../45-libintl-perl_1.33-1_all.deb ...
Unpacking libintl-perl (1.33-1) ...
Selecting previously unselected package libintl-xs-perl.
Preparing to unpack .../46-libintl-xs-perl_1.33-1_amd64.deb ...
Unpacking libintl-xs-perl (1.33-1) ...
Selecting previously unselected package libmodule-find-perl.
Preparing to unpack .../47-libmodule-find-perl_0.16-2_all.deb ...
Unpacking libmodule-find-perl (0.16-2) ...
Selecting previously unselected package libproc-processtable-perl:amd64.
Preparing to unpack .../48-libproc-processtable-perl_0.634-1+b2_amd64.deb ...
Unpacking libproc-processtable-perl:amd64 (0.634-1+b2) ...
Selecting previously unselected package libsort-naturally-perl.
Preparing to unpack .../49-libsort-naturally-perl_1.03-4_all.deb ...
Unpacking libsort-naturally-perl (1.03-4) ...
Selecting previously unselected package libterm-readkey-perl.
Preparing to unpack .../50-libterm-readkey-perl_2.38-2+b1_amd64.deb ...
Unpacking libterm-readkey-perl (2.38-2+b1) ...
Selecting previously unselected package needrestart.
Preparing to unpack .../51-needrestart_3.6-4+deb12u3_all.deb ...
Unpacking needrestart (3.6-4+deb12u3) ...
Selecting previously unselected package patch.
Preparing to unpack .../52-patch_2.7.6-7_amd64.deb ...
Unpacking patch (2.7.6-7) ...
Selecting previously unselected package python3-json-pointer.
Preparing to unpack .../53-python3-json-pointer_2.3-2_all.deb ...
Unpacking python3-json-pointer (2.3-2) ...
Selecting previously unselected package python3-rfc3987.
Preparing to unpack .../54-python3-rfc3987_1.3.8-2_all.deb ...
Unpacking python3-rfc3987 (1.3.8-2) ...
Selecting previously unselected package python3-uritemplate.
Preparing to unpack .../55-python3-uritemplate_4.1.1-2_all.deb ...
Unpacking python3-uritemplate (4.1.1-2) ...
Selecting previously unselected package python3-webcolors.
Preparing to unpack .../56-python3-webcolors_1.11.1-1_all.deb ...
Unpacking python3-webcolors (1.11.1-1) ...
Setting up python3-dotenv (0.21.0-1) ...
Setting up python3-attr (22.2.0-1) ...
Setting up python3-texttable (1.6.7-1) ...
Setting up python3-docopt (0.6.2-4.1) ...
Setting up python3-distro (1.8.0-1) ...
Setting up libyaml-0-2:amd64 (0.2.5-1) ...
Setting up libip6tc2:amd64 (1.8.9-2) ...
Setting up wmdocker (1.5-2) ...
Setting up binutils-common:amd64 (2.40-2) ...
Setting up libctf-nobfd0:amd64 (2.40-2) ...
Setting up python3-yaml (6.0-3+b2) ...
Setting up libcurl3-gnutls:amd64 (7.88.1-10+deb12u8) ...
Setting up runc (1.1.5+ds1-1+deb12u1) ...
Setting up python3-uritemplate (4.1.1-2) ...
Setting up liberror-perl (0.17029-2) ...
Setting up python3-webcolors (1.11.1-1) ...
Setting up libmodule-find-perl (0.16-2) ...
Setting up python3-rfc3987 (1.3.8-2) ...
Setting up tini (0.19.0-1) ...
Setting up patch (2.7.6-7) ...
Setting up python3-pyrsistent:amd64 (0.18.1-1+b3) ...
Setting up libprotobuf32:amd64 (3.21.12-3) ...
Setting up libproc-processtable-perl:amd64 (0.634-1+b2) ...
Setting up python3-json-pointer (2.3-2) ...
Setting up libnfnetlink0:amd64 (1.0.2-2) ...
Setting up libnl-3-200:amd64 (3.7.0-0.2+b1) ...
Setting up libintl-perl (1.33-1) ...
Setting up libcurl4:amd64 (7.88.1-10+deb12u8) ...
Setting up git-man (1:2.39.5-0+deb12u2) ...
Setting up sgml-base (1.31) ...
Setting up curl (7.88.1-10+deb12u8) ...
Setting up cgroupfs-mount (1.4) ...
Setting up libterm-readkey-perl (2.38-2+b1) ...
Setting up libbinutils:amd64 (2.40-2) ...
Setting up python3-protobuf (3.21.12-3) ...
Setting up containerd (1.6.20~ds1-1+b1) ...
Created symlink /etc/systemd/system/multi-user.target.wants/containerd.service → /lib/systemd/system/containerd.service.
Setting up python3-lib2to3 (3.11.2-3) ...
Setting up libsort-naturally-perl (1.03-4) ...
Setting up python3-websocket (1.2.3-1) ...
Setting up python3-dockerpty (0.4.1-4) ...
Setting up libctf0:amd64 (2.40-2) ...
Setting up python3-distutils (3.11.2-3) ...
Setting up docker (1.5-2) ...
Setting up python3-docker (5.0.3-1) ...
Setting up libnet1:amd64 (1.1.6+dfsg-3.2) ...
Setting up libintl-xs-perl (1.33-1) ...
Setting up libgprofng0:amd64 (2.40-2) ...
Setting up python3-jsonschema (4.10.3-1) ...
Setting up git (1:2.39.5-0+deb12u2) ...
Setting up libnetfilter-conntrack3:amd64 (1.0.9-3) ...
Setting up criu (3.17.1-2+deb12u1) ...
Setting up binutils-x86-64-linux-gnu (2.40-2) ...
Setting up docker-compose (1.29.2-3) ...
Setting up iptables (1.8.9-2) ...
update-alternatives: using /usr/sbin/iptables-legacy to provide /usr/sbin/iptables (iptables) in auto mode
update-alternatives: using /usr/sbin/ip6tables-legacy to provide /usr/sbin/ip6tables (ip6tables) in auto mode
update-alternatives: using /usr/sbin/iptables-nft to provide /usr/sbin/iptables (iptables) in auto mode
update-alternatives: using /usr/sbin/ip6tables-nft to provide /usr/sbin/ip6tables (ip6tables) in auto mode
update-alternatives: using /usr/sbin/arptables-nft to provide /usr/sbin/arptables (arptables) in auto mode
update-alternatives: using /usr/sbin/ebtables-nft to provide /usr/sbin/ebtables (ebtables) in auto mode
Setting up docker.io (20.10.24+dfsg1-1+deb12u1) ...
Adding group `docker' (GID 109) ...
Done.
Created symlink /etc/systemd/system/multi-user.target.wants/docker.service → /lib/systemd/system/docker.service.
Created symlink /etc/systemd/system/sockets.target.wants/docker.socket → /lib/systemd/system/docker.socket.
Setting up binutils (2.40-2) ...
Setting up needrestart (3.6-4+deb12u3) ...
Processing triggers for man-db (2.11.2-2) ...
Processing triggers for libc-bin (2.36-9+deb12u8) ...
```
</details>

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

Посмотрим Docker-образы в системе:
```
docker images
```
<details>
<summary> результат выполнения команды: </summary>

```
REPOSITORY   TAG       IMAGE ID       CREATED         SIZE
nginxotus    latest    c31e013e6238   9 seconds ago   47MB
nginx        alpine    93f9c72967db   2 months ago    47MB
```
</details>

Запустим наш контейнер:
```
docker run -d --name webserver -p 8080:80 nginxotus
```
<details>
<summary> результат выполнения команды: </summary>

```
c894b1c821c7a6e1e6c9d498a9dd2b105e03369637697ff434570183b6a79623
```
</details>

Посмотрим запущенные контейнеры:
```
docker ps
```
<details>
<summary> результат выполнения команды: </summary>

```
CONTAINER ID   IMAGE       COMMAND                  CREATED         STATUS         PORTS                                   NAMES
c894b1c821c7   nginxotus   "/docker-entrypoint.…"   7 seconds ago   Up 6 seconds   0.0.0.0:8080->80/tcp, :::8080->80/tcp   webserver

```
</details>

Попробуем зайти на Nginx в нашем контейнере:

```
curl 127.0.0.1:8080
```
<details>
<summary> результат выполнения команды: </summary>

```
<h1><center>Test OTUS NGIX docker container</center></h1>
```
</details>

Зарегистрируемся на Docker Hub.   
Далее, выполним команду для подключения к Docker Hub:

```
docker login
```

<details>
<summary> результат выполнения команды: </summary>

```
Username: alexlikh
Password:
WARNING! Your password will be stored unencrypted in /root/.docker/config.json.
Configure a credential helper to remove this warning. See
https://docs.docker.com/engine/reference/commandline/login/#credentials-store

Login Succeeded
```
</details>

Выполним тегирование образа:
```
docker tag nginxotus alexlikh/nginxotus:latest
```

Выполним загрузку Docker-образа на Docker Hub:
```
docker push alexlikh/nginxotus:latest
```

<details>
<summary> результат выполнения команды: </summary>

```
The push refers to repository [docker.io/alexlikh/nginxotus]
1eb53152457a: Pushed
5a760029e979: Mounted from library/nginx
23625999797d: Mounted from library/nginx
9aa22afcf27f: Mounted from library/nginx
59a5cb944b91: Mounted from library/nginx
598e577f3a23: Mounted from library/nginx
fd5f65a144ef: Mounted from library/nginx
a8903c9578e9: Mounted from library/nginx
ce5a8cde9eee: Mounted from library/nginx
latest: digest: sha256:18c268bbb778f4f68021e16dcd35c86f286b571d81f3f004ef327b6f1d9eefc9 size: 2196
```
</details>

Посмотрим на запущенные докеры:
```
docker ps
```
<details>
<summary> результат выполнения команды: </summary>

```
CONTAINER ID   IMAGE       COMMAND                  CREATED          STATUS          PORTS                                   NAMES
c894b1c821c7   nginxotus   "/docker-entrypoint.…"   13 minutes ago   Up 13 minutes   0.0.0.0:8080->80/tcp, :::8080->80/tcp   webserver
```
</details>
Остановим запущенный докер:

```
docker stop c894
```

Посмотрим на docker контейнеры в системе:

```
docker images -a
```
<details>
<summary> результат выполнения команды: </summary>

```
REPOSITORY           TAG       IMAGE ID       CREATED          SIZE
alexlikh/nginxotus   latest    c31e013e6238   15 minutes ago   47MB
nginxotus            latest    c31e013e6238   15 minutes ago   47MB
nginx                alpine    93f9c72967db   2 months ago     47MB
```
</details>

Удалим все docker контейнеры:

```
docker rmi -f c31 93f
```
<details>
<summary> результат выполнения команды: </summary>

```
Untagged: alexlikh/nginxotus:latest
Untagged: alexlikh/nginxotus@sha256:18c268bbb778f4f68021e16dcd35c86f286b571d81f3f004ef327b6f1d9eefc9
Untagged: nginxotus:latest
Deleted: sha256:c31e013e6238f96e07ae721a0696801d64d5e46f5ce5da06a826741ccbec0faf
Untagged: nginx:alpine
Untagged: nginx@sha256:814a8e88df978ade80e584cc5b333144b9372a8e3c98872d07137dbf3b44d0e4
Deleted: sha256:93f9c72967dbcfaffe724ae5ba471e9568c9bbe67271f53266c84f3c83a409e3
```
</details>

Скачаем наш образ с Docker Hub:

```
docker pull alexlikh/nginxotus
```

<details>
<summary> результат выполнения команды: </summary>

```
Using default tag: latest
latest: Pulling from alexlikh/nginxotus
66a3d608f3fa: Already exists
58290db888fa: Already exists
5d777e0071f6: Already exists
dbcfe8732ee6: Already exists
37d775ecfbb9: Already exists
e0350d1fd4dd: Already exists
1f4aa363b71a: Already exists
e74fff0a393a: Already exists
559fb4d11d2d: Already exists
Digest: sha256:18c268bbb778f4f68021e16dcd35c86f286b571d81f3f004ef327b6f1d9eefc9
Status: Downloaded newer image for alexlikh/nginxotus:latest
docker.io/alexlikh/nginxotus:latest
```
</details>

Проверим докер контейнеры в системе:

```
docker images
```

<details>
<summary> результат выполнения команды: </summary>

```
REPOSITORY           TAG       IMAGE ID       CREATED        SIZE
alexlikh/nginxotus   latest    c31e013e6238   11 hours ago   47MB
```
</details>

Запустим докер, скаченный с Docker Hub:

```
docker run -d --name webserv -p 8080:80 alexlikh/nginxotus
```

Посмотрим запущенные контейнеры:
```
docker ps
```
<details>
<summary> результат выполнения команды: </summary>

```
CONTAINER ID   IMAGE                COMMAND                  CREATED          STATUS          PORTS                                   NAMES
28824af7e63d   alexlikh/nginxotus   "/docker-entrypoint.…"   29 seconds ago   Up 28 seconds   0.0.0.0:8080->80/tcp, :::8080->80/tcp   webserv

```
</details>

Попробуем зайти на Nginx в нашем контейнере:

```
curl 127.0.0.1:8080
```
<details>
<summary> результат выполнения команды: </summary>

```
<h1><center>Test OTUS NGIX docker container</center></h1>
```
</details>   
   

### 4. Определите разницу между контейнером и образом.   
### 5. Вывод опишите в домашнем задании.   

Docker-образ — это статический файл, который содержит все необходимые компоненты для запуска контейнера   
Docker-контейнер — это запущенная инстанция Docker-образа   
   
### 6. Ответьте на вопрос: Можно ли в контейнере собрать ядро?   

В Docker-контейнере можно собрать ядро. Для этого, контейнер необходимо запустить с расширенными правами (ключ: --privileged)
