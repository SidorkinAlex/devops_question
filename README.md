# Вопросы для Девопс

- Что такое Load Average, SWAP, inode?

Средние значения нагрузки (Load Average) в Linux — это «средние значения нагрузки системы», показывающие потребность в исполняемых потоках (задачах) в виде усреднённого количества исполняемых и ожидающих потоков. Это мера нагрузки, которая может превышать обрабатываемую системой в данный момент.

SWAP (своп) — это механизм виртуальной памяти, при котором часть данных из оперативной памяти (ОЗУ) перемещается на хранение на HDD (жёсткий диск), SSD (твёрдотельный накопитель), флеш-накопитель или иное вторичное хранилище. Как правило, swapping (свопинг) происходит, когда оперативная память переполнена, и ей для работы требуется дополнительное пространство.

В информатике inode (произносится а́йнод или инод), индексный дескриптор — это структура данных в традиционных для ОС UNIX файловых системах (ФС), таких как UFS, ext4. В этой структуре хранится метаинформация о стандартных файлах, каталогах или других объектах файловой системы, кроме непосредственно данных и имени.

— Чем отличается TCP от UDP, как устанавливается соединение TCP?

TCP ориентирован на соединение, тогда как UDP является протоколом без соединения.
TCP очень надежен для передачи полезных данных, так как он принимает подтверждение отправленной информации. И отправляет потерянные пакеты, если таковые имеются. Принимая во внимание, что в случае UDP, если пакет потерян, он не будет запрашивать повторную передачу, и целевой компьютер получит поврежденные данные. Итак, UDP - ненадежный протокол.

<table class="text1" border="0" cellspacing="0" cellpadding="0">
<tbody>
<tr>
<td class="tabl" valign="top" width="36">
<p align="center">Шаг</p>
</td>
<td class="tabl" valign="top" width="226">
<p align="center">Действие</p>
</td>
<td class="tabl" valign="top" width="413">
<p align="center">Комментарии</p>
</td>
</tr>
<tr>
<td class="tabl" valign="top" width="36">
<p class="text1"><strong>1.</strong></p>
</td>
<td class="tabl" valign="top" width="226">
<p class="text1">Сторона, запрашивающая соединение,отправляет сегмент синхронизации на приёмное устройство (CTL=SYN), начиная тем самым процесс квитирования.</p>
</td>
<td class="tabl" valign="top" width="413">
<p class="text1">Сегмент синхронизации указывает номер порта приёмного устройства, с которым хочет установить связь отправитель. Сегмент синхронизации так же содержит значение ISN, которое будет использоваться процессом уведомления.</p>
</td>
</tr>
<tr>
<td class="tabl" valign="top" width="36">
<p class="text1">2.</p>
</td>
<td class="tabl" valign="top" width="226">
<p class="text1">Приёмное устройство отвечает сегментом с набором бит CTL=SYN, АСК для переговоров о соединении и подтверждения получения сегмента синхронизации от отправителя.</p>
</td>
<td class="tabl" valign="top" width="413">
<p class="text1">Приёмное устройство отвечает отправкой порядкового номера следующего байта данных ожидаемого приёмником от отправителя. Следующий порядковый номер – ISN отправителя увеличенный на единицу.</p>
</td>
</tr>
<tr>
<td class="tabl" valign="top" width="36">
<p class="text1">3.</p>
</td>
<td class="tabl" valign="top" width="226">
<p class="text1">Сторона, запрашивающая соединение подтверждает сегмент синхронизации, полученный от приёмника (CTL=ACK).</p>
</td>
<td class="tabl" valign="top" width="413">
<p class="text1">В заголовке TCP сбрасывается бит SYN, подтверждая, что трёхэтапное квитирование завершено.</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p>&nbsp;</p></td>
</tr>
</tbody>
</table>

— Когда нужно использовать SWAP, а когда нет?

— Чем отличается git pull от git fetch?

— Чем отличается транзакция от запроса, в контексте БД?

— Как починить chmod -x /bin/chmod?

— Что такое DevOps, Agile?

— С какими методологиями разработки ПО работал? Что знаешь о Scrum, Kanban и т.д?

— Чем виртуалки отличаются от контейнеров?

— Клиенты жалуются на то, что веб-сервис стал медленно работать, как бы ты последовательно докапывался до проблемы? Как обнаружить bottleneck?

— Чем отличаются реляционные БД от нереляционных и key-value? С какими из них работал, как бы ты организовывал разгрузку баз, репликации, миграции, бекапы?

— Что такое балансировщик? Какие типы балансировки при деплое знаешь? Что такое blue-green deployment, канареечные релизы?

— Как бы ты организовал поднятие инфраструктуры в облаке, в случае если отвалилась целая зона или регион?

— Как налету мигрировать работающую базу из одного региона в другую?

— Как бы ты строил ту или иную архитектуру проекта?

— Работал ли с облаками, AWS, GCP, Azure, OpenStack?

— Что представляет собой докер-контейнер? Из каких двух базовых вещей состоят контейнеры (имеется ввиду namespaces и cgroups)?

— Какие инструменты оркестрации контейнеров использовал? Для чего нужен Kubernetes, Nomad, Swarm, Compose?

— Есть ли опыт работы со стеком ELK, со стеком ПО от Hashicorp (Vault, Consul, Nomad, Terraform и т.д)?

— С какими системами мониторинга работал? Есть опыт работы с Prometheus?

— С какими CI-системами работал? В чем отличия Jenkins от TeamCity и других аналогичных систем?

— Что такое Continuous Integration/Delivery/Deployment и чем они друг от друга отличаются?

— Есть ли опыт внедрения CI/CD в инфраструктуру java-приложений (ant/maven/gradle)?

— С какими системами управления конфигурациями работал (Ansible/Puppet/Chef и т.д)? Почему именно с ними, в чем между ними разница?

— Как в access-логе Nginx посмотреть самые активные IP-адреса за последние сутки с помощью BASH?

— Как отсортировать массив в Python? Написать код в реальном времени.
