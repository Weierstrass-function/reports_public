# Лабораторная работа № 3. Настройка сетевого сервера на базе MS Windows Server
Цель работы: сформировать навыки установки серверов на базе MS Windows Server и настройки сетевых служб

Задачи работы:
- рассмотреть набор серверных служб MS Windows, особенностей их использования и администрирования;
- сформировать навыки в установке и настройке DHCP;
- сформировать навыки в установке домена сети и службы DNS;

Результат работы. Отчет студента по результатам работы должен содержать:
- описание структуры домена;
- описание настройки DHCP и DNS.

## Да здравствует Domain Controller

<img width="792" height="628" alt="image" src="https://github.com/user-attachments/assets/98b5fe70-c160-47dd-a2c7-3e78e7310eec" />

Было динамично. Стало статично (
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

# Создание scope
Add-DhcpServerv4Scope -Name "CentralChamber" -StartRange 10.100.91.150 -EndRange 10.100.91.250 -SubnetMask 255.255.255.0

# Настраиваем
Set-DhcpServerv4OptionValue `
    -ScopeId 10.100.91.0 `
    -DnsDomain "EnrCntr.local" `
    -DnsServer 10.100.91.10 `
    -Router 10.100.91.196

```


