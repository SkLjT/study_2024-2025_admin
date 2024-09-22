---
## Front matter
title: "Лабораторная работа 4" 
subtitle: "Базовая настройка HTTP-сервера Apache"
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

Приобретение практических навыков по установке и базовому конфигурированию HTTP-сервера Apache.

# Выполнение лабораторной работы

1) На машине сервер переходим на суперпользователя. Устанавливаем из репозитория стандартный веб-сервер.

![Установка утилиты httpd](/home/aalushin/фдд/new2/study_2024-2025_admin/labs/lab4/report/image/1.jpg){#fig:001 width=70%}

![Установка базовых серверов](/home/aalushin/фдд/new2/study_2024-2025_admin/labs/lab4/report/image/2.jpg){#fig:002 width=70%}

2) В каталоге сonf лежат два файла: httpd.conf и magic. httpd.conf - это основной файл конфигурации HTTP-сервера Apache. Он содержит директивы конфигурации, которые дают серверу инструкции. magic содержит данные для модуля mod_mime_magic, этот модуль определяет тип MIME файлов. В каталоге conf.d лежат много файлов. Autoindex.conf - настраивает листинг директорий по http, средствами веб-сервера. fcgid.conf - настраивает клиент-серверный протокол взаимодействия веб-сервера и приложения. manual.conf - позволяет получить доступ к руководству. ssl.conf - протокол для безопасной передачи кодированных данных между веб-браузером и веб-сервером. Userdir.conf позволяет пользователям размещать материалы на сайте, без предоставления доступа к директории веб-сервера. 

![Анализ файлов](/home/aalushin/фдд/new2/study_2024-2025_admin/labs/lab4/report/image/3.jpg){#fig:003 width=70%}

3) Внесли изменения в настройки межсетевого узла сервер, разрешив работа с HTTP.

![Изменения межсетевого сервера](/home/aalushin/фдд/new2/study_2024-2025_admin/labs/lab4/report/image/4.jpg){#fig:004 width=70%}

4) Запустил во втором терминале расширенный лог системных сообщений, чтобы проверить корректность работы системы. Активировал и запустил HTTP-сервер. В лог системе проверил, что всё запустилось корректно.

![Активация HTTP-сервера](/home/aalushin/фдд/new2/study_2024-2025_admin/labs/lab4/report/image/5.jpg){#fig:005 width=70%}

![Проверка в логе](/home/aalushin/фдд/new2/study_2024-2025_admin/labs/lab4/report/image/6.jpg){#fig:006 width=70%}

5) Запустил виртуальную машину клиент. На сервере запустил лог ошибок работы веб-сервера, всё работает.

![Лог ошибок сервера](/home/aalushin/фдд/new2/study_2024-2025_admin/labs/lab4/report/image/7.jpg){#fig:007 width=70%}

6) На сервере запустил мониторинг доступа к веб-серверу. 

![Мониторинг доступа](/home/aalushin/фдд/new2/study_2024-2025_admin/labs/lab4/report/image/8.jpg){#fig:008 width=70%}

7) На машине клиент зашёл на нужный адрес и посмотрел, работает ли сайт.

![Сайт с клиента](/home/aalushin/фдд/new2/study_2024-2025_admin/labs/lab4/report/image/9.jpg){#fig:009 width=70%}

8) Остановил работу днс-сервера, чтобы внести изменения в файлы описания днс-зон.

![Остановка днс-сервера](/home/aalushin/фдд/new2/study_2024-2025_admin/labs/lab4/report/image/10.png){#fig:010 width=70%}

9) Изменил файлы обратной и прямой днс-зоны, вписал в концы файлов нужные скрипты.

![Изменения прямой зоны](/home/aalushin/фдд/new2/study_2024-2025_admin/labs/lab4/report/image/11.jpg){#fig:011 width=70%}

![Изменения обратной зоны](/home/aalushin/фдд/new2/study_2024-2025_admin/labs/lab4/report/image/12.jpg){#fig:012 width=70%}

10) Удалил файлы aalushin.net.jnl и 192.168.1.jnl.

![Удаление aalushin.net.jnl](/home/aalushin/фдд/new2/study_2024-2025_admin/labs/lab4/report/image/13.jpg){#fig:013 width=70%}

![Удаление 192.168.1.jnl](/home/aalushin/фдд/new2/study_2024-2025_admin/labs/lab4/report/image/14.jpg){#fig:014 width=70%}

11) Перезапустил днс-сервер.

![Перезапуск днс-сервера](/home/aalushin/фдд/new2/study_2024-2025_admin/labs/lab4/report/image/15.jpg){#fig:015 width=70%}

12) В каталоге  /etc/httpd/conf.d  создал файлы server.aalushin.net.conf и www.aalushin.net.conf.

![Создание файлов в conf.d ](/home/aalushin/фдд/new2/study_2024-2025_admin/labs/lab4/report/image/16.jpg){#fig:016 width=70%}

13) Внёс скрипт в файл server.aalushin.net.conf.

![Скрипт в server.aalushin.net.conf.](/home/aalushin/фдд/new2/study_2024-2025_admin/labs/lab4/report/image/17.jpg){#fig:017 width=70%}

14) Внёс скрипт в файл www.aalushin.net.conf.

![Скрипт в www.aalushin.net.conf](/home/aalushin/фдд/new2/study_2024-2025_admin/labs/lab4/report/image/18.jpg){#fig:018 width=70%}

15) В каталоге /var/www/html создал каталоги с тестовыми страницами для виртуальных веб-серверов. Создал каталог server.aalushin.net, а в нём файл  index.html. Внёс строки, которые будут приветствовать пользователя при входе на страницу.

![index.html в каталоге server.aalushin.net](/home/aalushin/фдд/new2/study_2024-2025_admin/labs/lab4/report/image/19.jpg){#fig:019 width=70%}

![Текст в index.html](/home/aalushin/фдд/new2/study_2024-2025_admin/labs/lab4/report/image/20.jpg){#fig:001 width=70%}

16) В каталоге /var/www/html создал каталоги с тестовыми страницами для виртуальных веб-серверов. Создал каталог www.aalushin.net, а в нём файл  index.html. Внёс строки, которые будут приветствовать пользователя при входе на страницу.

![index.html в каталоге www.aalushin.net](/home/aalushin/фдд/new2/study_2024-2025_admin/labs/lab4/report/image/21.jpg){#fig:021 width=70%}

![Текст во втором index.html](/home/aalushin/фдд/new2/study_2024-2025_admin/labs/lab4/report/image/22.jpg){#fig:022 width=70%}

17) Скорректировал права доступа в каталог с веб-контентом.

![Корректировака прав доступа](/home/aalushin/фдд/new2/study_2024-2025_admin/labs/lab4/report/image/23.jpg){#fig:023 width=70%}

18) Восстановил контекстные метки безопасности в SELinux.

![Восстановление меток SELinux](/home/aalushin/фдд/new2/study_2024-2025_admin/labs/lab4/report/image/24.jpg){#fig:024 width=70%}

19) Перезапустил HTTP-сервер.

![Перезапуск HTTP](/home/aalushin/фдд/new2/study_2024-2025_admin/labs/lab4/report/image/25.jpg){#fig:025 width=70%}

20) На машине клиент зашёл на веб-страницы server.aalushin.net и www.aalushin.net. 

![веб-страница server.aalushin.net](/home/aalushin/фдд/new2/study_2024-2025_admin/labs/lab4/report/image/26.jpg){#fig:026 width=70%}

![веб-страница www.aalushin.net](/home/aalushin/фдд/new2/study_2024-2025_admin/labs/lab4/report/image/27.jpg){#fig:027 width=70%}

21) Создал каталог http в который поместил конфигурационные файлы HTTP-сервера.

![Создание каталога HTTP](/home/aalushin/фдд/new2/study_2024-2025_admin/labs/lab4/report/image/28.jpg){#fig:028 width=70%}

22) Заменил конфигурационные файлы днс-сервера.

![Замена файлов](/home/aalushin/фдд/new2/study_2024-2025_admin/labs/lab4/report/image/29.jpg){#fig:029 width=70%}

23) Создал исполняемый файл http.sh, внёс соответсвующий скрипт, который повторяет произведённые действия по настройке сервера.

![Создание http.sh](/home/aalushin/фдд/new2/study_2024-2025_admin/labs/lab4/report/image/30.jpg){#fig:030 width=70%}

![Скрипт в http.sh](/home/aalushin/фдд/new2/study_2024-2025_admin/labs/lab4/report/image/31.jpg){#fig:031 width=70%}

24) Изменил Vagrantfile, чтобы скрипт отрабатывал во время загрузки виртуальной машины.

![Изменения в Vagrantfile](/home/aalushin/фдд/new2/study_2024-2025_admin/labs/lab4/report/image/32.jpg){#fig:032 width=70%}

# Вывод 

Я приобрёл практические навыки по установке и базовому конфигурированию HTTP-сервера Apache.

# Контрольные вопросы

1) Через какой порт по умолчанию работает Apache?

- По умолчанию Apache работает через порт 80.

2) Под каким пользователем запускается Apache и к какой группе относится этот пользователь?

- Apache обычно запускается под пользователем “www-data” и относится к группе “www-data”.

3) Где располагаются лог-файлы веб-сервера? Что можно по ним отслеживать?

- Лог-файлы веб-сервера обычно располагаются в каталоге /var/log/apache2. Можно отслеживать доступ, ошибки, запросы и другую информацию.

4) Где по умолчанию содержится контент веб-серверов?

- Контент веб-серверов по умолчанию содержится в каталоге /var/www/html.

5) Каким образом реализуется виртуальный хостинг? Что он даёт?

- Виртуальный хостинг реализуется через конфигурацию веб-сервера, позволяя одному серверу обслуживать несколько доменов. Он дает возможность размещать несколько веб-сайтов на одном сервере.
