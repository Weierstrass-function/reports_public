# Лабораторная работа № 2. Администрирование MS Windows Server
Цель работы: сформировать навыки администрирования ОС MS Windows
Задачи работы:
- рассмотреть основные оснастки ОС MS Windows Server для администрирования системы;
- рассмотреть вопросы администрирования пользователей, групп пользователей, доступа к ресурсам.
Результат работы. В результате работы студент должен сдать отчет, в котором содержалось бы описание выбранной предметной области и политики администрирования, а также описание основных оснасток для администрирования системы.

## Aperture Science Enrichment Center
Центр развития компании Aperture Science. Здесь разрабатываются и испытываются продукты марки Aperture Laboratories. Aperture Science заанимается разработкой техники контр-маневра Хаймлиха, работой благотворительного фонда Take-A-Wish и исследования пространственных разрывов.
- Субьекты
  - Cave Кейв Джонсон главный админ CEO и вообще батька имеет полный доступ
  - GLaDOS имеет доступ к чтению своего промпта не может его изменить но при этом может изменить кучу всего другого
  - bookkeeper - бухгалтер центра
  - Chell - одна из тестируемых может посмотреть свой профайл но не может его даже редактировать
- Объекты
  - Личное дело Chell
  - Промпт для GLaDOS
  - Долги и иски по произведенным ваннам

## Где оснастки MMC?
По факту на текущий момент их заменил Windows Admin Center, мелкомягкие тоже рекомендуют использовать именно его, поэтому проведем его обзор.

## Overview

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/5b9bfd48-982c-4167-8855-fb7bee557147" />

на этом дэшборде сводная информация о ресурсах и их использовании

## Security

<img width="960" height="1032" alt="image" src="https://github.com/user-attachments/assets/48c89c4f-f4f1-4dbc-8e34-4040bcb3dbcd" />

Можно установить расписание сканирований. 

<img width="960" height="1032" alt="image" src="https://github.com/user-attachments/assets/e4ec382c-7aba-4711-8e7f-84f11e533199" />

А вот это самое интересное тут можно выбрать различные baseline политики. По сути различные настройки парольная политика (например минимальная длина пароля), что логировать и т.п. Причем недавно они разрешили прямо отдельные политики добавлять.

Также есть вкладка Silicon Assisted Security как не трудно догадаться это аппаратные средства безопасности.

Protection history видмо тут мы будем искать очередной файл котрый винда решила снести без суда, следствия, а кроме того вашего согласия и ведома.

## Certificates

<img width="960" height="1032" alt="image" src="https://github.com/user-attachments/assets/66fda0d6-9e3c-4007-9701-8a5ec474c1a3" />

Тут мы видим все возможные сертификаты и их состояние. Логи действий с ними. Можно удалить сертификаты или экспортировать.

## Devices

<img width="960" height="1032" alt="image" src="https://github.com/user-attachments/assets/daea9a33-2036-48bc-abf7-14ae4219d7b0" />

Местный диспетчер устройств. Можно например отключить устройство. Можно подумать, что получится обновить дрова, но опыт общения с диспетчером устройств на обычной винде подсказывает - НЕТ.

## Events

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/00d74875-921c-4734-8007-19e3ed5def78" />

Как не трудно догадаться логи. Экспорт, удаление.

## Files and file sharing

<img width="960" height="1032" alt="image" src="https://github.com/user-attachments/assets/481fbee8-94c6-4551-b244-129505413e56" />

Файлы, директории и доступы к ним.

Создадим сразу директорию EnrichmentCenterStorage.

После 10 секундного ожидания при создании перейдем в нормальный интерфейс.

## Local users and groups
<img width="960" height="1032" alt="image" src="https://github.com/user-attachments/assets/261a6387-9f4f-454e-b847-df865c6d6d0b" />

Тут очевидным образом можно выполнять различные действия с пользователями и группами пользователей.
## Services
<img width="960" height="1032" alt="image" src="https://github.com/user-attachments/assets/63bec144-ecf0-4525-9852-af9d8f8c1652" />

Управление службами.
## Registry
<img width="960" height="1032" alt="image" src="https://github.com/user-attachments/assets/5dd7da2c-bb70-4818-a97d-8e48d9fe0b19" />

Как известно все настройки, что нельзя покрутить нормальным способом можно покрутить тут. Будем надееться, сюда нам лезть не надо будет.
## Storage
<img width="960" height="1032" alt="image" src="https://github.com/user-attachments/assets/cffa485f-27b7-40e7-b54d-b042f12549e5" />


## Processes
<img width="960" height="1032" alt="image" src="https://github.com/user-attachments/assets/028434e5-82f2-4f30-a85d-8bbf520999f6" />


## Networks
<img width="960" height="1032" alt="image" src="https://github.com/user-attachments/assets/101d526c-063f-48d2-a467-06c4f2214898" />


## Firwall
<img width="960" height="1032" alt="image" src="https://github.com/user-attachments/assets/9e1f7ac0-99ad-43a3-9f1a-f762585f3655" />



<img width="960" height="1032" alt="image" src="https://github.com/user-attachments/assets/a1559861-4406-452c-b266-874e337f3bef" />

Поскольку мы собираемся разграничивать доступ жмем Apply
