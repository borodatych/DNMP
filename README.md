###### DNMP - Docker + Nginx + PHP-FPM + MySQL

Для старта из корня нужно выполнить команду:
```
$ docker-compose up -d
```
По завершению мы увидим заветные строчки:
```
Use 'docker scan' to run Snyk tests against images 
to find vulnerabilities and learn how to fix them
[+] Running 4/4
 - Network dnmp_default  Created
 - Container dnmpMySQL   Started
 - Container dnmpPHP     Started
 - Container dnmpNginx   Started
```

Так же нужно дождаться как dnmpMySQL поднимется:
```
2021-10-31 14:57:04+00:00 [Note] [Entrypoint]: MySQL init process done. Ready for start up.
```
> Это через Docker Desktop подглядел

Для проверки откроем браузер и перейдем по адресу:  
http://hello.loc

Но сперва добавим одну строку в hosts файл:
```
127.0.0.1 hello.loc
```

---

Можно легко добавлять новые проекты:
1. Просто создаем новую папку для проекта в www
2. Добавляем новый конфиг для nginx
3. Перезапускаем контейнеры и вперед!

---

###### COMMANDS LIST
```
docker-compose config
docker ps

// stop all
docker-compose down -v

// WARNING!! clear all mysql data files
rm -rf ./mysql/lib/*

// start all
docker-compose up -d

// bash
docker exec -it dnmpMySQL bash

// run mysql under dev
docker exec -it dnmpMySQL sh -c 'mysql -udev -pjnrhjqcz'
docker-compose exec mysql sh -c 'mysql -udev -pjnrhjqcz'

// restart nginx after add virtual host
docker restart dnmpNginx
```
