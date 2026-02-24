# Отчет не требуется

Качаем iso-шник https://www.microsoft.com/en-us/evalcenter/download-windows-server-2025
Из соображений снобизма и мазохизма English версию

При установке на виртуалку снимаем галочку:

<img width="315" height="80" alt="Screenshot 2026-02-23 164541" src="https://github.com/user-attachments/assets/dea49669-cede-4213-85d9-a35a5734289b" />

Выпивем 800 мл чая даже не смотря на SSD в процессе установки.

Пароль admin не подошел((( зато подошел 
```
Hello world!
```

<img width="362" height="157" alt="image" src="https://github.com/user-attachments/assets/548ac477-1ebb-4a3c-9a06-c1ddd85733d8" />

безопасно

а вот это не безопасно

<img width="719" height="545" alt="image" src="https://github.com/user-attachments/assets/58d30f78-bef1-4067-9366-8478e0e8f28a" />

>For the record: Ctrl+Alt+Del перехватывается хостом раньше чем доходит до виртуалки просто используйте RIGHT_Ctrl+Del

На виртуалке стоит чисто Server Core без графической оболочки.


# Почему Server Core
С некоторых пор мелкомягкие решили расчленить версию с GUI и без него на этапе установки из чего мы делаем вывод, что если перед нами в реальной рабочей задаче возникнет версия без GUI без полной переустановки мы окажемся в несколько неловком положени. Кроме они сами рекомендуют без острой необходимости GUI не ставить здесь: https://learn.microsoft.com/en-us/windows-server/get-started/install-options-server-core-desktop-experience 

Есть ли у нас данная необходимость? А в чем? Оснастки? Да термин больше из GUI но по сути полные их эквиваленты можно использовать в PowerShell что и будет продемонстрированно в данной лабораторной работе.

Ладно, на самом деле истинные причны в том, что я мазохист который устанавливал на АСВТ MS-DOS с консольным интерфейсом через виртуальные дискеты на VirtualBox.

Плюс, как сообщает нейронка, серьезные дяди одетые в вязаные кофты в больших прохладных датацентрах не используют GUI. Верим?

Для большего реализма будем работать через https://www.microsoft.com/de-de/evalcenter/download-windows-admin-center

При установке Windows Admin Center придется использовать самоподписные, извините удостоверяющего центра у меня нет(((

<img width="372" height="235" alt="image" src="https://github.com/user-attachments/assets/eeff2e70-0643-4992-a102-cfbb8e51d299" />

Хватит отправлять мои данные!

<img width="492" height="334" alt="image" src="https://github.com/user-attachments/assets/b0c36282-b7c0-49b8-9935-0fbc0e94f8ce" />

Делаем раз

<img width="377" height="39" alt="image" src="https://github.com/user-attachments/assets/dac7ce9e-ca92-4116-897c-e80436b5164e" />

<img width="623" height="470" alt="image" src="https://github.com/user-attachments/assets/40139d3e-d668-4e40-85a8-d5707ac77bed" />


Делаем два

<img width="831" height="317" alt="image" src="https://github.com/user-attachments/assets/1c1c821f-d1e1-43cf-8c14-ab9066a4f30a" />

>For the record: для того чтобы указать локального админа на сервере следует писать так:

<img width="462" height="80" alt="image" src="https://github.com/user-attachments/assets/9d1cdee0-1417-4b3d-8c14-4756e6dc97c9" />


