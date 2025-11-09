# Лабораторная работа №1 - обычная
## Настройка Nginx
> Nginx ― это программное обеспечение с открытым исходным кодом, которое позволяет создавать веб-сервер. 
> Nginx обслуживает соединения, обрабатывает запросы, которые поступают к серверу, а также используется:
> - для обработки запросов с сайтов, где много статического неизменного контента;
> - обслуживания серверов, на которые поступает много запросов одновременно;
> - в качестве почтового сервера или для распределения нагрузки на серверную часть;
> - SSL/TLS терминация: Nginx способен выполнять терминацию SSL/TLS, обеспечивая шифрование и дешифрование данных между клиентами и серверами. Это снижает нагрузку на бэкэнд-серверы и улучшает безопасность.
1. Установим Nginx
   - Обновим информацию о пакетах и установим Nginx:
     ![1](https://github.com/MkrtchyanKarina/DevOps_labs/blob/master/lab1_default/img/Screenshot%20from%202025-11-09%2018-49-53.png)
   - Добавим в автозагрузку и запустим:
     ![2](https://github.com/MkrtchyanKarina/DevOps_labs/blob/master/lab1_default/img/Screenshot%20from%202025-11-09%2018-57-26.png)
2. Создадим папку для лабораторной работы, которая будет содержать все файлы, необходимые нашим веб-сайтам/проектам:
   - В ней будут содержаться два наших проекта ( сайта ) и папка для сертификата:
     ![3](https://github.com/MkrtchyanKarina/DevOps_labs/blob/master/lab1_default/img/Screenshot%20from%202025-11-09%2019-06-09.png)
3. Создадим файлы index.html в проектах, а также папку breeds с файлами, соответствующими названию пород собачек и кошечек:
   - Для проекта с собачками:
     ![4](https://github.com/MkrtchyanKarina/DevOps_labs/blob/master/lab1_default/img/Screenshot%20from%202025-11-09%2019-17-21.png)
     ![5](https://github.com/MkrtchyanKarina/DevOps_labs/blob/master/lab1_default/img/Screenshot%20from%202025-11-09%2019-25-50.png)
     ![6](https://github.com/MkrtchyanKarina/DevOps_labs/blob/master/lab1_default/img/Screenshot%20from%202025-11-09%2019-24-59.png)
   - Аналогично для сайта с кошками:
     ![7](https://github.com/MkrtchyanKarina/DevOps_labs/blob/master/lab1_default/img/Screenshot%20from%202025-11-09%2019-36-59.png)
     ![8](https://github.com/MkrtchyanKarina/DevOps_labs/blob/master/lab1_default/img/Screenshot%20from%202025-11-09%2019-36-02.png)

4. Настроим права доступа
   - Все файлы в lab1/dogs и lab1/cats теперь принадлежат пользователю www-data (под которым работает nginx), chmod устанавливает права для владельца на любые действия, для остальных групп на чтение и выполнение файлов в папке lab1:
     ![9](https://github.com/MkrtchyanKarina/DevOps_labs/blob/master/lab1_default/img/Screenshot%20from%202025-11-09%2019-42-16.png)

5. Сгенерируем самоподписные ключи для обоих проектов соответственно с помощбю команд:
   ```
   sudo openssl req -x509 -nodes -days 365 -newkey rsa:2048 \
    -keyout dogs.key -out dogs.crt \
    -subj "/C=US/ST=State/L=City/O=Organization/CN=dogs.local"
   ```
   ```
   sudo openssl req -x509 -nodes -days 365 -newkey rsa:2048 \
    -keyout cats.key -out cats.crt \
    -subj "/C=US/ST=State/L=City/O=Organization/CN=cats.local"
   ```
   
6. Создадим файлы конфигурации для проектов:
   - Для собак:
     ![10](https://github.com/MkrtchyanKarina/DevOps_labs/blob/master/lab1_default/img/Screenshot%20from%202025-11-09%2020-07-23.png)
   - Для кошек
     ```
     # HTTP redirect to HTTPS
      server {
       listen 80;
       server_name cats.local www.cats.local;
       return 301 https://$server_name$request_uri;
      }

      # HTTPS server
      server {
       listen 443 ssl;
       server_name cats.local www.cats.local;

       # SSL configuration
       ssl_certificate /home/karina/lab1/ssl/cats.crt;
       ssl_certificate_key /home/karina/lab1/ssl/cats.key;

       # Security headers
       add_header Strict-Transport-Security "max-age=31536000" always;

       # Root location
       location / {
           root /home/karina/lab1/cats;
           index index.html index.htm;
           try_files $uri $uri/ =404;
       }

       # Alias example
       location /breeds/ {
           alias /home/karina/lab1/cats/breeds/;
       }
   }
   ```

7. Удалим дефолтный файл конфигураций и активируем виртуальные хосты:
   ```
   sudo rm -f /etc/nginx/sites-enabled/default
   ```
   
