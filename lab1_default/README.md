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
