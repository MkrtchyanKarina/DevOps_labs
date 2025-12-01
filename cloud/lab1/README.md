## Отчёт о проделанной работе

В рамках задания был проанализирован реальный биллинг-файл облачного провайдера Amazon Web Services без указания
стоимостей. На основе полей `Product Code`, `Usage Type`, `LineItemDescription` и `Operation` выполнена структуризация
потребляемых сервисов и распределение их по иерархии
`IT Tower → Service Family → Service Type → Service Sub Type → Service Usage Type`. В результате данные были "причесаны"
и приведены к аналитическому виду, позволяющему однозначно определить, к какому классу относятся расходы: вычисления,
хранилища, машинное обучение, DevOps, обмен сообщениями, безопасность или накладные расходы (налоги).

В биллинге были выявлены и классифицированы следующие ключевые группы сервисов:

* **Data Warehouse и аналитика** (Amazon Redshift) - аналог в РФ: Yandex DataProc / VK Cloud Big Data.
* **Объектные и архивные хранилища** (Amazon S3, Amazon Glacier) - аналоги: Yandex Object Storage, SberCloud Object
  Storage.
* **Сервисы машинного обучения и ИИ** (Amazon Translate, Transcribe, Polly, Amazon ML) - аналоги: Yandex SpeechKit, VK
  Cloud ML.
* **DevOps и CI/CD** (AWS CodePipeline, CodeBuild) - аналоги: GitLab CI/CD в облачной инфраструктуре РФ-провайдеров.
* **Сервисы интеграции и уведомлений** (Amazon SNS) - аналоги: очереди и pub/sub в Yandex Cloud и VK Cloud.
* **Сервисы безопасности и каталогов** (AWS Directory Service) - аналоги: AD-сервисы в SberCloud.

В результате таблица стала пригодной для управленческого анализа затрат с возможностью агрегации от уровня IT-блоков до
конкретных типов потребления сервисов.
