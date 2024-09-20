---
## Front matter
title: "Лабораторная работа 3" 
subtitle: "Настройка DHCP-сервера"
author: "Лушин Артём Андреевич"

## Generic otions
lang: ru-RU
toc-title: "Содержание"

## Bibliography
bibliography: bib/cite.bib
csl: pandoc/csl/gost-r-7-0-5-2008-numeric.csl

## Pdf output format
toc: true # Table of contents
toc-depth: 2
lof: true # List of figures
fontsize: 12pt
linestretch: 1.5
papersize: a4
documentclass: scrreprt
## I18n polyglossia
polyglossia-lang:
  name: russian
  options:
	- spelling=modern
	- babelshorthands=true
polyglossia-otherlangs:
  name: english
## I18n babel
babel-lang: russian
babel-otherlangs: english
## Fonts
mainfont: PT Serif
romanfont: PT Serif
sansfont: PT Sans
monofont: PT Mono
mainfontoptions: Ligatures=TeX
romanfontoptions: Ligatures=TeX
sansfontoptions: Ligatures=TeX,Scale=MatchLowercase
monofontoptions: Scale=MatchLowercase,Scale=0.9
## Biblatex
biblatex: false
biblio-style: "gost-numeric"
biblatexoptions:
  - parentracker=true
  - backend=biber
  - hyperref=auto
  - language=auto
  - autolang=other*
  - citestyle=gost-numeric
## Pandoc-crossref LaTeX customization
figureTitle: "Рис."
tableTitle: "Таблица"
listingTitle: "Листинг"
lofTitle: "Список иллюстраций"
lolTitle: "Листинги"
## Misc options
indent: true
header-includes:
  - \usepackage{indentfirst}
  - \usepackage{float} # keep figures where there are in the text
  - \floatplacement{figure}{H} # keep figures where there are in the text
---

# Цель работы

Приобретение практических навыков по установке и конфигурированию DHCP-сервера.

# Выполнение лабораторной работы

1) Я запустил виртуальную машину server, перешёл на суперпользователя и установил dhcp.

![Установка dhcp](/home/aalushin/фдд/new2/study_2024-2025_admin/labs/lab3/report/image/1.jpg){#fig:001 width=70%}

2) Скопировал файлы конфигурации dhcp в мои каталоги.

![Перенос файлов dhcp](/home/aalushin/фдд/new2/study_2024-2025_admin/labs/lab3/report/image/2.jpg){#fig:002 width=70%}

3) В файле dhcpd.conf изменил строку option domain-name под своего пользователя. Так же заменил option domain-name-servers на свои данные. Раскоментировал authoritative. Задал собственную конфигурация подсети.

![Изменения в dhcpd.conf](/home/aalushin/фдд/new2/study_2024-2025_admin/labs/lab3/report/image/3.jpg){#fig:003 width=70%}

4) Настроил привязку dhcpd к интерфейсу eth1. В файле dhcpd.service заменил ExecStart на свои данные.

![Перемещение файла dhcpd.service](/home/aalushin/фдд/new2/study_2024-2025_admin/labs/lab3/report/image/4.jpg){#fig:004 width=70%}

![Редактирование файла dhcpd.service](/home/aalushin/фдд/new2/study_2024-2025_admin/labs/lab3/report/image/5.jpg){#fig:005 width=70%}

5) Перезагрузил конфигурацию dhcpd и разрешил загрузку DHCP-сервера при запуске машины.

![Перезагрузка dhcpd](/home/aalushin/фдд/new2/study_2024-2025_admin/labs/lab3/report/image/6.jpg){#fig:006 width=70%}

6) Добавил файл DHCP в конец файла прямой днс-зоны. Также изменил файл обратной зоны и заменил серийные номера.

![Изменения прямой зоны](/home/aalushin/фдд/new2/study_2024-2025_admin/labs/lab3/report/image/7.jpg){#fig:007 width=70%}

![Изменения обратной зоны](/home/aalushin/фдд/new2/study_2024-2025_admin/labs/lab3/report/image/8.jpg){#fig:008 width=70%}

7) Перезапустил named.

![Перезапуск named](/home/aalushin/фдд/new2/study_2024-2025_admin/labs/lab3/report/image/9.jpg){#fig:009 width=70%}

8) Проверил, что можно обратиться к DHCP-серверу по имени. После выполнения большого количество операций всё сработало правильно, никаких ошибок нет, потеря пакетов составила 0%.

![Проверка DHCP](/home/aalushin/фдд/new2/study_2024-2025_admin/labs/lab3/report/image/10.jpg){#fig:010 width=70%}

9) Изменил настройки межсетевого экрана узла сервер, разрешил работу с DHCP.

![Редактирование межсетевого экрана](/home/aalushin/фдд/new2/study_2024-2025_admin/labs/lab3/report/image/12.jpg){#fig:011 width=70%}

10) Восстановил контекстные метки в SELinux.

![Восстановление SELinux](/home/aalushin/фдд/new2/study_2024-2025_admin/labs/lab3/report/image/13.jpg){#fig:012 width=70%}

11) В доп терминале запустил мониторинг происходящих в системе процессов. В основном терминале перезапустил DHCP-сервер и проверил, чтобы не было ошибок. 

![Мониторинг ошибок.](/home/aalushin/фдд/new2/study_2024-2025_admin/labs/lab3/report/image/14.jpg){#fig:013 width=70%}

12) В каталоге vagrant/provision/client создал файл л 01-routing.sh и заполнил его нужными командами. 

![Заполнение л 01-routing.sh](/home/aalushin/фдд/new2/study_2024-2025_admin/labs/lab3/report/image/15.jpg){#fig:014 width=70%}

13) В Vagrantfile подключил конфигурацию. 

![Подключение в Vagrantfile](/home/aalushin/фдд/new2/study_2024-2025_admin/labs/lab3/report/image/16.jpg){#fig:015 width=70%}

14) Зафиксировал изменения и запустил машину клиент. В окне с мониторингом происходящего увидел, что клиент подключился к серверу и ему выдался адрес.

![Подключение клиента](/home/aalushin/фдд/new2/study_2024-2025_admin/labs/lab3/report/image/17.jpg){#fig:016 width=70%}

15) В машине клиента ввёл команду и вывел информацию о подключении. Вывелась информация о трёх сетевых интерфейсах: eth0, eth1 и локальный(lo). О каждом интерфейсе вывелся одинаковый набор информации. Разберём интерфейс eth1.
ags=4163<UP,BROADCAST,RUNNING,MULTICAST> mtu 1500 inet 192.168.1.30 netmask 255.255.255.0 broadcast 192.168.1.255 \\ ip-адрес версии 4, маска сети и широковещательный адрес 
inet6 fe80::a00:27ff:fe23:cc66 prefixlen 64 scopeid 0x20<link> \\ ip-адрес версии 6, префикс сети и область dhcp, которой принадлежит адрес 
ether 08:00:27:23:cc:66 txqueuelen 1000 (Ethernet) \\MAC-адрес сетевого оборудования 
RX packets 18 bytes 3054 (2.9 KiB) \\ количество и размер отправленных пакетов 
RX errors 0 dropped 0 overruns 0 frame 0 \\ количество ошибок, сброшенных и превышающих время отправленных пакетов 
TX packets 317 bytes 33002 (32.2 KiB) \\ количество и размер полученных пакетов
TX errors 0 dropped 0 overruns 0 carrier 0 collisions 0 \\ количество ошибок, сброшенных, превысящих время пакетов. а также несущих и коллизий

![Инфорамция о клиенте](/home/aalushin/фдд/new2/study_2024-2025_admin/labs/lab3/report/image/18.jpg){#fig:017 width=70%}

16) На машине сервер отредактировал файл aalushin.net. Разрешил обновление зоны с локального адреса. 

![Файл aalushin.net](/home/aalushin/фдд/new2/study_2024-2025_admin/labs/lab3/report/image/19.jpg){#fig:018 width=70%}

17) Перезапустил днс-сервер.

![Перезапуск днс](/home/aalushin/фдд/new2/study_2024-2025_admin/labs/lab3/report/image/20.jpg){#fig:019 width=70%}

18) Изменил конфигурационный файл и добавил разрешения на динамическое обновление днс-записей с локального узла прямой и обратной зоны.

![Динамическое обновление](/home/aalushin/фдд/new2/study_2024-2025_admin/labs/lab3/report/image/21.jpg){#fig:020 width=70%}

19) Перезапустил DHCP-сервер. Перезапуск произошёл успешно и в каталоге /var/named/master/fz появился файл user.net.jnl в бинарной виде. 

![Появление user.net.jnl](/home/aalushin/фдд/new2/study_2024-2025_admin/labs/lab3/report/image/22.jpg){#fig:021 width=70%}

![Содержание user.net.jnl ](/home/aalushin/фдд/new2/study_2024-2025_admin/labs/lab3/report/image/23.jpg){#fig:022 width=70%}

20) С помощью утилиты dig убедился о наличии днс-записи в клиенте. Анализ информации: 

; <<>> DiG 9.16.23-RH <<>> @192.168.1.1 client.aalushin.net \\ версия DIG 
; (1 server found) \\ найден один сервер 
;; global options: +cmd \\глобальная опция, говорящая, что нужно отображать \\ аргументы при анализе 
;; Got answer: \\ ответ получен 
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 61619 \\ код операции -- \\запрос, ошибок нет, ID процесса 61619
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 1 \\ указаны флаги qr(указывающий, что мы производим запрос), \\rd(рекурсия желательна),aa (ответ авторитетный). \\ra(указывает, что сервер поддерживает рекурсивный запрос) 
;; OPT PSEUDOSECTION: \\псевдосекция 
; EDNS: version: 0, flags:; udp: 1232 \\версия EDNS флаги и \\ размер UDP пакета 
; COOKIE: a8ce51bda0ead2e101000000655112aac7f304ea8831b8d9 (good) \\ куки 
;; QUESTION SECTION: \\ полученные ответы 
;client.aaushin.net. IN A \\ А - ip-адреса версии 4 
;; ANSWER SECTION: \\ответ 
client.aalushin.net. 300 IN A 192.168.1.30 \\ ip-адрес версии 4 
;; Query time: 4 msec \\ время запроса 
;; SERVER: 192.168.1.1#53(192.168.1.1) \\адрес сервера 
;; WHEN: Sun Nov 12 18:00:10 UTC 2023 \\дата 
;; MSG SIZE rcvd: 94 \\ размер сообщения

![Проверка записи](/home/aalushin/фдд/new2/study_2024-2025_admin/labs/lab3/report/image/24.jpg){#fig:023 width=70%}

21) На машине сервер перешёл в каталог для внесения изменений в настройки внутреннего окружения. Создал новый каталог и поместил туда конфигурационные файлы DHCP.

![Перенос конфигурационных файлов](/home/aalushin/фдд/new2/study_2024-2025_admin/labs/lab3/report/image/25.jpg){#fig:024 width=70%}

22) Заменил конфигурационные файлы днс-сервера.

![Замена сервера](/home/aalushin/фдд/new2/study_2024-2025_admin/labs/lab3/report/image/26.jpg){#fig:025 width=70%}

23) В каталоге  /vagrant/provision/server создал исполняющий файл dhcp.sh и вписал соответствуйющий скрипт.

![Создание dhcp.sh](/home/aalushin/фдд/new2/study_2024-2025_admin/labs/lab3/report/image/27.jpg){#fig:026 width=70%}

![Скрип в dhcp.sh](/home/aalushin/фдд/new2/study_2024-2025_admin/labs/lab3/report/image/28.jpg){#fig:027 width=70%}

24) В Vagrantfile добавил скрипт в разделе конфигурации сервера.

![Изменения в Vagrantfile](/home/aalushin/фдд/new2/study_2024-2025_admin/labs/lab3/report/image/29.jpg){#fig:028 width=70%}

25) Выключил виртуальные машины клиент и сервер.

![Отключение машин](/home/aalushin/фдд/new2/study_2024-2025_admin/labs/lab3/report/image/30.jpg){#fig:029 width=70%}


# Вывод 

Я приобрёл практические навыки по установке и конфигурированию DHCP-сервера.

# Контрольные вопросы

1) В каких файлах хранятся настройки сетевых подключений?

- Конфигурация сетевого интерфейса хранится в /etc/sysconfig/network-scripts в соответствующем файле с префиксом ifcfg (там же конфигурационные файлы других интерфейсов).

2) За что отвечает протокол DHCP?

- Протокол DHCP (Dynamic Host Configuration Protocol) отвечает за автоматическую настройку IP-адресов и других сетевых параметров для устройств в сети.

3) Поясните принцип работы протокола DHCP. Какими сообщениями обмениваются клиент и сервер, используя протокол DHCP?

- Протокол DHCP работает по принципу клиент-серверной модели. Когда клиент подключается к сети, он отправляет DHCP-запрос на сервер, запрашивая IP-адрес и другие сетевые настройки. Сервер DHCP выделяет IP-адрес из своего пула доступных адресов и отправляет его клиенту вместе с другими настройками в сообщении DHCP-ответа.

4) В каких файлах обычно находятся настройки DHCP-сервера? За что отвечает каждый из файлов?

- Настройки хранятся в файле dhcpd.conf, а именно конфигурация dhcp-сети(адрес подсети, диапазон адресов для распределения клиентам, адрес маршрутизатора и broadcast-адрес), также доменное имя и его серверы. В файле dhcpd.service прописана привязка dhcpd к интерфейсу.

5) Что такое DDNS? Для чего применяется DDNS?

- DDNS (Dynamic Domain Name System) – это система, которая позволяет автоматически обновлять записи DNS при изменении IP-адресов устройств в сети. DDNS обеспечивает привязку доменных имен к динамически изменяющимся IP-адресам, что позволяет обращаться к сетевым ресурсам по именам, не зависящим от их текущего IP-адреса.

6) Какую информацию можно получить, используя утилиту ifconfig? Приведите примеры с использованием различных опций

- Утилита ifconfig позволяет получить информацию о сетевых интерфейсах на компьютере, включая IP-адреса, маски подсети, MAC-адреса и другие параметры. Например, команда “ifconfig” выводит информацию о всех активных сетевых интерфейсах, а команда “ifconfig eth0” показывает информацию о конкретном сетевом интерфейсе eth0.

7) Какую информацию можно получить, используя утилиту ping? Приведите примеры с использованием различных опций.

- Утилита ping используется для проверки доступности и измерения задержки (ping) до удаленного хоста с использованием ICMP (Internet Control Message Protocol).
