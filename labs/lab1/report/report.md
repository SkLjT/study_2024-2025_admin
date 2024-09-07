---
## Front matter
title: "Лабораторная работа 1" 
subtitle: "Подготовка лабораторного стенда"
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

Целью данной работы является приобретение практических навыков установки Rocky Linux на виртуальную машину с помощью инструманте Vagrant.

# Выполнение лабораторной работы

1)  создал каталог для проекта. Расположил согласно инструкции. Сделал два подкаталога packer u vagrant. Работаю на системе ОС Windows.

![Создание каталога для проекта](/home/aalushin/new/study_2024-2025_admin/labs/lab1/report/image/1.jpg){#fig:001 width=70%}

2) В подкаталоге packer разместил образ виртуальной операционной системы Rocky linux. 

![Размещение образа](/home/aalushin/new/study_2024-2025_admin/labs/lab1/report/image/2.jpg){#fig:002 width=70%}

3) Разместил необходимые подкаталоги и файлы в папках packer и vagrant. 

![Размещение файлов в packer](/home/aalushin/new/study_2024-2025_admin/labs/lab1/report/image/3.jpg){#fig:003 width=70%}

![Размещение файлов в vagrant](/home/aalushin/new/study_2024-2025_admin/labs/lab1/report/image/4.jpg){#fig:004 width=70%}

4) В каталоге vagrant создал ещё 3 подкаталога для работы: server, client, default.

![Размещение полкаталогов в vagrant](/home/aalushin/new/study_2024-2025_admin/labs/lab1/report/image/5.jpg){#fig:005 width=70%}

5) В папках server, client, default разместил подготовленный файл 01-dummy.sh

![01-dummy.sh](/home/aalushin/new/study_2024-2025_admin/labs/lab1/report/image/6.jpg){#fig:006 width=70%}

6) В каталоге default разместил скрипт 01-user.sh. Заменил user на aalushin.

![01-user.sh](/home/aalushin/new/study_2024-2025_admin/labs/lab1/report/image/7.jpg){#fig:007 width=70%}

7) В каталоге default разместил скрипт 01-hostname.sh. Заменил user на aalushin.

![01-hostname.sh](/home/aalushin/new/study_2024-2025_admin/labs/lab1/report/image/8.jpg){#fig:008 width=70%}

8) В каталоге server разместил скрипт 02-forward.sh.

![02-forward.sh](/home/aalushin/new/study_2024-2025_admin/labs/lab1/report/image/9.jpg){#fig:009 width=70%}

9) В каталоге client разместил скрипт 02-routing.sh.

![02-routing.sh](/home/aalushin/new/study_2024-2025_admin/labs/lab1/report/image/10.jpg){#fig:010 width=70%}

10) Сверил содержимое файла vagrant-rocky.pkr.hcl. Содержимое совпадает с задачей лабораторной работы.

![vagrant-rocky.pkr.hcl](/home/aalushin/new/study_2024-2025_admin/labs/lab1/report/image/11.jpg){#fig:011 width=70%}

11) Сверил содержимое файла ks.cfg. Содержимое совпадает с задачей лабораторной работы.

![ks.cfg](/home/aalushin/new/study_2024-2025_admin/labs/lab1/report/image/12.jpg){#fig:012 width=70%}

12) Сверил содержимое файла Vagrantfile. Содержимое совпадает с задачей лабораторной работы.

![Vagrantfile](/home/aalushin/new/study_2024-2025_admin/labs/lab1/report/image/13.jpg){#fig:013 width=70%}

13) Сверил содержимое файла Makefile в каталоге packer. Содержимое совпадает с задачей лабораторной работы.

![Makefile в packer](/home/aalushin/new/study_2024-2025_admin/labs/lab1/report/image/14.jpg){#fig:014 width=70%}

14) Сверил содержимое файла Makefile в каталоге vagrant. Содержимое совпадает с задачей лабораторной работы.

![Makefile в vagrant](/home/aalushin/new/study_2024-2025_admin/labs/lab1/report/image/15.jpg){#fig:015 width=70%}

15) Так как я работаю в ОС Windows, то и команды буду использовать для этой системы. Я скачал файл vagrant-virtualbox-rocky-9-x86_64.box по ссылке на туис, поэтому пропустил шаг с его созданием. Следующим шагом было регистрация образа виртуальной машины. 

![Регистрация образа виртуальной машины](/home/aalushin/new/study_2024-2025_admin/labs/lab1/report/image/17.jpg){#fig:017 width=70%}

16) С помощью консольной команды я запускаю виртуальную машину Server. 

![Запуск Server](/home/aalushin/new/study_2024-2025_admin/labs/lab1/report/image/18.jpg){#fig:018 width=70%}

17) С помощью консольной команды я запускаю виртуальную машины Client.

![Запуск client](/home/aalushin/new/study_2024-2025_admin/labs/lab1/report/image/19.jpg){#fig:019 width=70%}

18) Убедился что обе машины работают хорошо и параллельно. Ничего не вылетает, ошибок нет.\

![Сверка машин](/home/aalushin/new/study_2024-2025_admin/labs/lab1/report/image/20.jpg){#fig:020 width=70%}

19) Подключился к серверу из консоли. Ввёл пароль для пользователя вагрант. Перешёл на пользователя aalushin. 

![Подключение к серверу](/home/aalushin/new/study_2024-2025_admin/labs/lab1/report/image/24.jpg){#fig:022 width=70%}

20) Подключился к клиенту из консоли. Ввёл пароль для пользователя вагрант. Перешёл на пользователя aalushin. 

![Подключение к клиенту](/home/aalushin/new/study_2024-2025_admin/labs/lab1/report/image/23.jpg){#fig:023 width=70%}

21) После того как разлогинился от двух машин, обе виртуальные машины я закрыл. 

![Выключение машин](/home/aalushin/new/study_2024-2025_admin/labs/lab1/report/image/26.jpg){#fig:024 width=70%}

22) Убедился, что в конфигурации файла Vagrantfile есть необходимая запись. 

![Запись в Vagrantfile](/home/aalushin/new/study_2024-2025_admin/labs/lab1/report/image/27.jpg){#fig:025 width=70%}

23) Я зафиксировал машин Server и Сlient (фотографии с вводом команды для Client нет, но команда аналогичная, только вместо сервера пишем клиент) 

![Фиксация машин](/home/aalushin/new/study_2024-2025_admin/labs/lab1/report/image/28.jpg){#fig:026 width=70%}

24) Проверил, что обе машины работают от имени пользователя, разлогинился и выключил машины. Так же создал папку на рабочем столе, чтобы можно было переносить системы на другие компьютеры.

![Проверка работоспособности Сервер](/home/aalushin/new/study_2024-2025_admin/labs/lab1/report/image/29.jpg){#fig:027 width=70%}

![Проверка работоспособности Клиент](/home/aalushin/new/study_2024-2025_admin/labs/lab1/report/image/30.jpg){#fig:028 width=70%}

# Вывод 

Я приобрёл практические навыки установки Rocky Linux на виртуальную машину с помощью инструмента vagrant. 


# Контрольные вопросы

1) Для чего предназначен Vagrant?

Ответ: Инструмент для создания и управления средами виртуальных машин в одном рабочем процессе.

2) Что такое box-файл? В чём назначение Vagrantfile? 
Box-file - сохранённый образ виртуальной машины с развёрнутой в ней операционной системой. То есть этот файл используется как основа для клонирования виртуальным машин. Vagrantfile - конфигурационный файл, написанный на языке Ruby, в котором указаны настройки запуска виртуальных машин. 

3) Приведите описание и примеры вызова основных команда Vagrant.

- vagrant help — вызов справки по командам Vagrant; 

- vagrant box list — список подключённых к Vagrant box-файлов; 

- vagrant box add — подключение box-файла к Vagrant

- vagrant destroy— отключение box-файла отVagrant и удаление его из виртуального окружения; 

- vagrant init — создание «шаблонного» конфигурационного файла Vagrantfile для его последующего изменения

- vagrant up — запуск виртуальной машины с использованием инструкций по запуску из конфигурационного файла Vagrantfile; 

- vagrant reload — перезагрузка виртуальной машины;

- остановка и выключение виртуальной машины;

- vagrant provision — настройка внутреннего окружения имеющейся виртуальной машины (например, добавление новых инструкций (скриптов) в ранее созданную виртуальную машину);

- vagrant ssh — подключение к виртуальной машине через ssh. 

4) Дайте построчные пояснения содержания файлов vagrant-rocky.pkr.hcl, ks.cfg, Vagrantfile, Makefile.

Пример содержимого файла Vagrantfile:
# -*- mode: ruby -*- # vi: set ft=ruby : Vagrant.configure(2) do |config|

config.vm.box = "BOX_NAME" config.vm.hostname = "HOST_NAME" config.vm.network "private_network", ip: "192.168.1.1" config.vm.define "VM_NAME" config.vm.provider "virtualbox" do |vb| vb.gui = false vb.memory = "1024" end end

Первые две строки указывают на режим работы с Vagrantfile и использование языка Ruby. Затем идёт цикл do, заменяющий конструкцию Vagrant.configure далее по текстуна config. Строка config.vm.box = “BOX_NAME” задаёт название образа (box-файла) виртуальной машины (обычно выбирается из официального репозитория). Строка config.vm.hostname = “HOST_NAME” задаёт имя виртуальной машины. Конструкция config.vm.network задаёт тип сетевого соединения и может иметь следующие назначения:


- config.vm.network “private_network”, ip: “xxx.xxx.xxx.xxx” — адрес из внутренней сети;


- config.vm.network “public_network”, ip: “xxx.xxx.xxx.xxx” — публичный адрес, по которому виртуальная машина будет доступна;


- config.vm.network “private_network”, type: “dhcp” — адрес, назначаемый по протоколу DHCP.


Строка config.vm.define “VM_NAME” задаёт название виртуальной машины, по которому можно обращаться к ней из Vagrant и VirtualBox. В конце идёт конструкция, определяющая параметры провайдера, а именно запуск виртуальной машины без графического интерфейса и с выделением 1 ГБ памяти.



