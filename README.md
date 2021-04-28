# Вопросы для Девопс

## Что такое Load Average, SWAP, inode?

Средние значения нагрузки (Load Average) в Linux — это «средние значения нагрузки системы», показывающие потребность в исполняемых потоках (задачах) в виде усреднённого количества исполняемых и ожидающих потоков. Это мера нагрузки, которая может превышать обрабатываемую системой в данный момент.

SWAP (своп) — это механизм виртуальной памяти, при котором часть данных из оперативной памяти (ОЗУ) перемещается на хранение на HDD (жёсткий диск), SSD (твёрдотельный накопитель), флеш-накопитель или иное вторичное хранилище. Как правило, swapping (свопинг) происходит, когда оперативная память переполнена, и ей для работы требуется дополнительное пространство.

В информатике inode (произносится а́йнод или инод), индексный дескриптор — это структура данных в традиционных для ОС UNIX файловых системах (ФС), таких как UFS, ext4. В этой структуре хранится метаинформация о стандартных файлах, каталогах или других объектах файловой системы, кроме непосредственно данных и имени.

## Чем отличается TCP от UDP, как устанавливается соединение TCP?

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


## что такое DNS ?

## Когда нужно использовать SWAP, а когда нет?

## Что такое балансировщик?

## Можно ли организовать revers proxy для tcp на nginx ? по url ? 

## Чем отличаются реляционные БД от нереляционных и key-value? С какими из них работал, как бы ты организовывал разгрузку баз, репликации, миграции, бекапы?

## приходилось ли повышать производительность БД за счет конфигов ? на что бы смотрел в первую очередь ?

## Чем виртуалки отличаются от контейнеров?

## Что представляет собой докер-контейнер? Из каких двух базовых вещей состоят контейнеры (имеется ввиду namespaces и cgroups)?

## Какие инструменты оркестрации контейнеров использовал? Для чего нужен Kubernetes, Nomad, Swarm, Compose?

## как пробросить порт из хост машины в контейнер при создании контейнера ?

## как заставить контейнер перезагружаться при падении ?

## как пробросить дирректорию из хост машины в контейнер ?

## С какими системами мониторинга работал? Есть опыт работы с Zabix?

## С какими CI-системами работал? В чем отличия Jenkins от TeamCity и других аналогичных систем?

## Чем отличается транзакция от запроса, в контексте БД?


##### Linux Debugging

<details>
<summary>Where system logs are located?</summary><br><b>

/var/log
</b></details>

<details>
<summary>How to follow file's content as it being appended without opening the file every time?</summary><br><b>

tail -f <file_name>
</b></details>

<details>
<summary>What are you using for troubleshooting and debugging <b>network</b> issues?</summary><br><b>

<code>dstat -t</code> is great for identifying network and disk issues.
<code>netstat -tnlaup</code> can be used to see which processes are running on which ports.
<code>lsof -i -P</code> can be used for the same purpose as netstat.
<code>ngrep -d any metafilter</code> for matching regex against payloads of packets.
<code>tcpdump</code> for capturing packets
<code>wireshark</code> same concept as tcpdump but with GUI (optional).
</b></details>

<details>
<summary>What are you using for troubleshooting and debugging <b>disk & file system</b> issues?</summary><br><b>

<code>dstat -t</code> is great for identifying network and disk issues.
<code>opensnoop</code> can be used to see which files are being opened on the system (in real time).
</b></details>

<details>
<summary>What are you using for troubleshooting and debugging <b>process</b> issues?</summary><br><b>

<code>strace</code> is great for understanding what your program does. It prints every system call your program executed.
</b></details>

<details>
<summary>What are you using for debugging CPU related issues?</summary><br><b>

<code>top</code> will show you how much CPU percentage each process consumes
<code>perf</code> is a great choice for sampling profiler and in general, figuring out what your CPU cycles are "wasted" on
<code>flamegraphs</code> is great for CPU consumption visualization (http://www.brendangregg.com/flamegraphs.html)
</b></details>

<details>
<summary>You get a call from someone claiming "my system is SLOW". What do you do?</summary><br><b>

* Check with `top` for anything unusual
* Run `dstat -t` to check if it's related to disk or network.
* Check if it's network related with `sar`
* Check I/O stats with `iostat`
</b></details>

<details>
<summary>Explain iostat output</summary><br><b>
</b></details>

<details>
<summary>How to debug binaries?</summary><br><b>
</b></details>

<details>
<summary>What is the difference between CPU load and utilization?</summary><br><b>
</b></details>

<details>
<summary>How you measure time execution of a program?</summary><br><b>
</b></details>



##### Linux Permissions

<details>
<summary>How to change the permissions of a file?</summary><br><b>

Using the `chmod` command.
</b></details>

<details>
<summary>What does the following permissions mean?:

  * 777
  * 644
  * 750</summary><br><b>

<pre>
777 - You give the owner, group and other: Execute (1), Write (2) and Read (4); 4+2+1 = 7.
644 - Owner has Read (4), Write (2), 4+2 = 6; Group and Other have Read (4).
750 - Owner has x+r+w, Group has Read (4) and Execute (1); 4+1 = 5. Other have no permissions.
</pre>
</b></details>

<details>
<summary>What this command does? <code>chmod +x some_file</code></summary><br><b>
It adds execute permissions to all sets i.e user, group and others
</b></details>

<details>
<summary>Explain what is setgid and setuid</summary><br><b>

* setuid is a linux file permission that permits a user to run a file or program with the permissions of the owner of that file. This is possible by elevation of current user privileges.
* setgid is a process when executed will run as the group that owns the file.
</b></details>

<details>
<summary>What is the purpose of sticky bit?</summary><br><b>
Its a bit that only allows the owner or the root user to delete or modify the file.
</b></details>

<details>
<summary>What the following commands do?

  * chmod
  * chown
  * chgrp</summary><br><b>

  * chmod - changes access permissions to files system objects
  * chown - changes the owner of file system files and directories
  * chgrp - changes the group associated with a file system object
</b></details>

<details>
<summary>What is sudo? How do you set it up?</summary><br><b>
</b></details>

<details>
<summary>True or False? In order to install packages on the system one must be the root user or use the sudo command</summary><br><b>

True
</b></details>

<details>
<summary>Explain what are ACLs. For what use cases would you recommend to use them?</summary><br><b>
</b></details>

<details>
<summary>You try to create a file but it fails. Name at least three different reason as to why it could happen</summary><br><b>

* No more disk space
* No more inodes
* No permissions
</b></details>

##### Linux DNS

<details>
<summary>How to check what is the hostname of the system?</summary><br><b>

`cat /etc/hostname`

You can also run `hostnamectl` or `hostname` but that might print only a temporary hostname. The one in the file is the permanent one.
</b></details>

<details>
<summary>What the file <code>/etc/resolv.conf</code> is used for? What does it include?</summary><br><b>
</b></details>

<details>
<summary>What commands are you using for performing DNS queries (or troubleshoot DNS related issues)?</summary><br><b>

You can specify one or more of the following:

 * <code>dig</code>
 * <code>host</code>
 * <code>nslookup</code>
</b></details>

##### Dockerfile

<details>
<summary>What is Dockerfile</summary><br><b>

Docker can build images automatically by reading the instructions from a Dockerfile. A Dockerfile is a text document that contains all the commands a user could call on the command line to assemble an image.
</b></details>

<details>
<summary>What is the difference between ADD and COPY in Dockerfile?</summary><br><b>

COPY takes in a src and destination. It only lets you copy in a local file or directory from your host (the machine building the Docker image) into the Docker image itself.
ADD lets you do that too, but it also supports 2 other sources. First, you can use a URL instead of a local file / directory. Secondly, you can extract a tar file from the source directly into the destination.
Although ADD and COPY are functionally similar, generally speaking, COPY is preferred. That’s because it’s more transparent than ADD. COPY only supports the basic copying of local files into the container, while ADD has some features (like local-only tar extraction and remote URL support) that are not immediately obvious.
</b></details>

<details>
<summary>What is the difference between CMD and RUN in Dockerfile?</summary><br><b>

RUN lets you execute commands inside of your Docker image. These commands get executed once at build time and get written into your Docker image as a new layer.
CMD is the command the container executes by default when you launch the built image. A Dockerfile can only have one CMD.
You could say that CMD is a Docker run-time operation, meaning it’s not something that gets executed at build time. It happens when you run an image. A running image is called a container.
</b></details>

<details>
<summary>Do you perform any checks or testing related to your Dockerfile?</summary><br><b>

A common answer to this is to use [hadolint](https://github.com/hadolint/hadolint) project which is a linter based on Dockerfile best practices.
</b></details>

<details>
<summary>Explain what is Docker compose and what is it used for</summary><br><b>

Compose is a tool for defining and running multi-container Docker applications. With Compose, you use a YAML file to configure your application’s services. Then, with a single command, you create and start all the services from your configuration.

For example, you can use it to set up ELK stack where the services are: elasticsearch, logstash and kibana. Each running in its own container.
</b></details>

<details>
<summary>Describe the process of using Docker Compose</summary><br><br>

* Define the services you would like to run together in a docker-compose.yml file
* Run `docker-compose up` to run the services
</b></details>

<details>
<summary>Explain Docker interlock</summary><br><b>
</b></details>

<details>
<summary>Where can you store Docker images?</summary><br><b>
</b></details>

<details>
<summary>What is Docker Hub?</summary><br><b>
</b></details>

<details>
<summary>What is the difference between Docker Hub and Docker cloud?</summary><br><b>

Docker Hub is a native Docker registry service which allows you to run pull
and push commands to install and deploy Docker images from the Docker Hub.

Docker Cloud is built on top of the Docker Hub so Docker Cloud provides
you with more options/features compared to Docker Hub. One example is
Swarm management which means you can create new swarms in Docker Cloud.
</b></details>

<details>
<summary>What is Docker Repository?</summary><br><b>
</b></details>

<details>
<summary>Explain image layers</summary><br><b>

A Docker image is built up from a series of layers. Each layer represents an instruction in the image’s Dockerfile. Each layer except the very last one is read-only.
Each layer is only a set of differences from the layer before it. The layers are stacked on top of each other. When you create a new container, you add a new writable layer on top of the underlying layers. This layer is often called the “container layer”. All changes made to the running container, such as writing new files, modifying existing files, and deleting files, are written to this thin writable container layer.
The major difference between a container and an image is the top writable layer. All writes to the container that add new or modify existing data are stored in this writable layer. When the container is deleted, the writable layer is also deleted. The underlying image remains unchanged.
Because each container has its own writable container layer, and all changes are stored in this container layer, multiple containers can share access to the same underlying image and yet have their own data state.
</b></details>

<details>
<summary>What best practices are you familiar related to working with containers?</summary><br><b>
</b></details>

<details>
<summary>How do you manage persistent storage in Docker?</summary><br><b>
</b></details>

<details>
<summary>How can you connect from the inside of your container to the localhost of your host, where the container runs?</summary><br><b>
</b></details>

<details>
<summary>How do you copy files from Docker container to the host and vice versa?</summary><br><b>
</b></details>

#### Jenkins

* [Jenkins: writing scripts](exercises/jenkins_scripts.md)
* [Jenkins: writing pipelines](exercises/jenkins_pipelines.md)
