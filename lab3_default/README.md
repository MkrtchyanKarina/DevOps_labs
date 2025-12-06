Установка Auditor'а:
1. Склонируем https://gitlab.inview.team/whitespots-public-fork/auditor.git
2. Установить докер
3. Перейти в папку
4. Выполнить docker compose up -d
   <img width="1097" height="624" alt="image" src="https://github.com/user-attachments/assets/84e01c10-e111-441c-8a2a-059e33f16fc7" />
5. Перейдите по адресу 127.0.0.1:8080 и сгенерируйте новый Access Token, сохраните его.
 <img width="547" height="365" alt="image" src="https://github.com/user-attachments/assets/0274a654-546f-40a0-a705-b8b1e141e401" />
8.Добавьте этот токен в переменную ACCESS_TOKEN в .env файл в директории auditor.
9.  Перезапустим контенеры
    <img width="457" height="270" alt="image" src="https://github.com/user-attachments/assets/09020c79-9ab4-4c5a-9d68-ddafde4809f3" />
    <img width="1176" height="317" alt="image" src="https://github.com/user-attachments/assets/a156747e-15b5-4fc8-a105-4ad66a47bb1b" />
<img width="1130" height="325" alt="image" src="https://github.com/user-attachments/assets/9d5e9e43-a3a9-4ccb-b783-e1226e9f8a65" />
Установка AppSec Portal
12. Склонировать https://gitlab.inview.team/whitespots-public-fork/appsec-portal.git
13. Выполните
```./set_vars.sh ```
<img width="532" height="250" alt="image" src="https://github.com/user-attachments/assets/4856539d-d49b-42d8-9b91-7d6dcfda1e2d" />
14. Добавьте версию echo IMAGE_VERSION=release_v25.11.3 >> .env
15. Запустите портал sh run.sh
16. Создадим суперпользователя
    <img width="1123" height="210" alt="image" src="https://github.com/user-attachments/assets/1631ee3b-dcfc-4b58-b2d7-14f823f36936" />
<img width="368" height="59" alt="image" src="https://github.com/user-attachments/assets/d73fc3aa-5d9b-480b-b287-aed2a3b7181d" />
17. Перейдите по адресу 127.0.0.1:80 и введите лицензионный ключ, который вы можете получить здесь: (@inview_bot)
    <img width="1911" height="597" alt="image" src="https://github.com/user-attachments/assets/c25b953c-f571-4621-9c03-0fa00dd4a0b4" />

18. Перейдите в раздел Auditor - Config. Укажите адрес аудитора http://host.docker.internal:8080/ и ваш Access Token, полученный ранее.
<img width="956" height="405" alt="image" src="https://github.com/user-attachments/assets/4501d74e-b8f1-4a27-8d5d-8f7fe8ba3f17" />

19.  Измените Internal Portal URL на http://host.docker.internal/, кликнув на той же странице на Workflow Settings.
    <img width="485" height="245" alt="image" src="https://github.com/user-attachments/assets/f39f9c2b-50a6-4c9b-8dc8-4da8b2eba5b5" />
20. Сгенерируем ssh ключ с помощью keygen и добавим его в настройки аккаунта на github
    <img width="962" height="280" alt="image" src="https://github.com/user-attachments/assets/8a214e86-a09d-4ac1-8d13-689ef7681207" />

Добавление репозиториев и сканирование
22. Добавим репозиторий
    <img width="751" height="832" alt="image" src="https://github.com/user-attachments/assets/4f887a8d-fbe7-43c8-a841-becde1bb50f8" />
23. Запустим аудит для него
    <img width="491" height="310" alt="image" src="https://github.com/user-attachments/assets/5ea8b6e6-ebe1-430b-be9c-9c3325aba179" />


24. Добавили репозиторий с лабами :)
    <img width="410" height="346" alt="image" src="https://github.com/user-attachments/assets/5d38bdb9-312f-410e-bd77-f6a0e9754c9d" />

    <img width="760" height="866" alt="image" src="https://github.com/user-attachments/assets/5e1a5281-cc06-4bce-9c75-e8b78e922119" />

