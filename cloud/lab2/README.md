# Отчёт о проделанной работе

## (Воспоминания) В рамках первой лабораторной работы были выявлены и классифицированы следующие ключевые группы сервисов:

* **Data Warehouse и аналитика** (Amazon Redshift) - аналог в РФ: Yandex DataProc / VK Cloud Big Data.
* **Объектные и архивные хранилища** (Amazon S3, Amazon Glacier) - аналоги: Yandex Object Storage, SberCloud Object
  Storage.
* **Сервисы машинного обучения и ИИ** (Amazon Translate, Transcribe, Polly, Amazon ML) - аналоги: Yandex SpeechKit, VK
  Cloud ML.
* **DevOps и CI/CD** (AWS CodePipeline, CodeBuild) - аналоги: GitLab CI/CD в облачной инфраструктуре РФ-провайдеров.
* **Сервисы интеграции и уведомлений** (Amazon SNS) - аналоги: очереди и pub/sub в Yandex Cloud и VK Cloud.
* **Сервисы безопасности и каталогов** (AWS Directory Service) - аналоги: AD-сервисы в SberCloud.



## Результаты применения иерархии к Azure:

### IT Tower: Database

* Service Family: Analytics (как для Amazon Redshift) - использован для Azure Analysis Services (OLAP-аналитика).

* Service Family: Databases (новая подкатегория) - использован для управляемых БД Azure Database for PostgreSQL/MySQL.

* Service Family: Caching (новая подкатегория) - использован для Azure Cache for Redis (управляемый кэш в памяти).

### IT Tower: Cloud Services

* Service Family: Application Services (как для Amazon SNS) - использован для Azure Data Factory (интеграция данных) и Azure Scheduler (планировщик задач).

* Service Family: Security and Identity (как для AWS Directory Service) - использован для Azure Key Vault (хранилище секретов) и Azure Sentinel (SIEM).

* Service Family: Compute Services (новая подкатегория) - введён для Azure Virtual Machines, так как в ЛР1 чистые вычисления (EC2) отсутствовали в данных, а в Azure они составили значительную статью расходов.

### IT Tower: Storage

* Service Family: Storage&Content Delivery (как для Amazon S3/Glacier/CloudFront) - использован для Azure CDN (доставка контента).

* Service Family: Data Transfer (новая подкатегория) - введён для Azure Data Box (физическое устройство миграции), специфичного для Azure сервиса.



#### Вывод: Модель классификации, созданная для AWS, подтвердила свою эффективность при работе с Azure. Внесённые минимальные изменения (четыре новые подкатегории) лишь подчеркнули гибкость подхода и позволили точно отразить архитектурные особенности Azure. В результате создана универсальная кросс-провайдерная модель для анализа архитектуры и затрат в облаке.

