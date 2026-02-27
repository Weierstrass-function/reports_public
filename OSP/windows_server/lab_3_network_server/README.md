<img width="321" height="399" alt="image" src="https://github.com/user-attachments/assets/37e7ec6f-f87e-410d-ad84-ca4daf198ffe" /># Лабораторная работа № 3. Настройка сетевого сервера на базе MS Windows Server
Цель работы: сформировать навыки установки серверов на базе MS Windows Server и настройки сетевых служб

Задачи работы:
- рассмотреть набор серверных служб MS Windows, особенностей их использования и администрирования;
- сформировать навыки в установке и настройке DHCP;
- сформировать навыки в установке домена сети и службы DNS;

Результат работы. Отчет студента по результатам работы должен содержать:
- описание структуры домена;
- описание настройки DHCP и DNS.

## Да здравствует Domain Controller

<img width="679" height="158" alt="image" src="https://github.com/user-attachments/assets/641a6e96-8e5a-4cbd-b96d-a5d62b6a111d" />

<img width="466" height="108" alt="image" src="https://github.com/user-attachments/assets/56d5dc40-c985-4013-9aba-9fb195443058" />

Возникновение некоторого недопонимания между нами и SConfig. Проклинание всех существующих UI от Microsoft.

<img width="611" height="190" alt="image" src="https://github.com/user-attachments/assets/4d8d8b5c-262e-4557-ae43-13ee1715207f" />

Целуем ноги netsh... т.е. Настройка адаптера который смотрит во внутреннюю сеть ApertureNet. Раз мы типо бигтех компания с кучей сетевых устройств и филиалов будем использовать 10.0.0.0/8 Поскольку мы главное подразделение Aperture Scince наша сеть будет 10.1.1.0/24


Также был установлен DNS 127.0.0.1 на себя

<img width="861" height="137" alt="image" src="https://github.com/user-attachments/assets/79428bce-bfd7-4dc6-bbe1-8d9e6164fd2e" />

Поскольку WAC нас опять послал ставим через команду.

Даллее с попощью команды создаем...
```
Install-ADDSForest -DomainName "EnrCntr.local" -InstallDns -SafeModeAdministratorPassword (ConvertTo-SecureString "пароль" -AsPlainText -Force) -Force
```

<img width="851" height="268" alt="image" src="https://github.com/user-attachments/assets/c732cc7e-fd3f-4ec4-81c3-f769e2bbad79" />

Обнаруживаем косяк с DNS по дефолту туда вписался IPv6 адрес.

Поскольку настройка IPv6 в наши планы не входит фиксим. Чтоб все было красиво.
```
Set-DnsClientServerAddress -InterfaceAlias "Ethernet" -ServerAddresses ("127.0.0.1")
```

## Настройка DHCP
```
Install-WindowsFeature DHCP -IncludeManagementTools # Устанавливаем
Import-Module DhcpServer # Вопросов не задаваем
Add-DhcpServerInDC # Добавляем
Get-DhcpServerInDC # Если в списке значит все прокатило

# Создание scope типа с 10.1.1.2-10.1.1.49 зарезервировано под всякие сервера и принтеры
Add-DhcpServerv4Scope -Name "CentralChamber" -StartRange 10.1.1.50 -EndRange 10.1.1.200 -SubnetMask 255.255.255.0
SetDhcpServerv4OptionValue -ScopeId 10.1.1.0 -Router 10.1.1.1 3 # Устанавливаем шлюз чтобы из ApertureNet можно было попасть в интернет

# Поставим NAT поскольку архитектура нашей сети требует
Install-WindowsFeature -Name Routing -IncludeManagementTools
Set-NetIPInterface -Forwarding Enabled -InterfaceIndex 4, 7

```

## На клиенте
Ставим DNS 10.1.1.1 (ибо не получилось)

<img width="321" height="399" alt="image" src="https://github.com/user-attachments/assets/f3425692-6aad-43b4-a8ed-e74c5a9efdae" />

Задаем домен через sysdm.cpl

<img width="443" height="279" alt="image" src="https://github.com/user-attachments/assets/d1949b75-8063-4430-8779-d03e91e33161" />

Входим и отправляемся в Reboot

