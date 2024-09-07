---
## Front matter
lang: ru-RU
title: Презентация по лабораторной работе №1
subtitle: Подготовка лабораторного стенда 
author:
  - Лушин А.А.
institute:
  - Российский университет дружбы народов, Москва, Россия
  - Факультет Физико-математических и естественных наук
date: 18 февраля 2005

## i18n babel
babel-lang: russian
babel-otherlangs: english

## Formatting pdf
toc: false
toc-title: Содержание
slide_level: 2
aspectratio: 169
section-titles: true
theme: metropolis
header-includes:
 - \metroset{progressbar=frametitle,sectionpage=progressbar,numbering=fraction}
 - '\makeatletter'
 - '\beamer@ignorenonframefalse'
 - '\makeatother'
---

# Информация

## Докладчик

:::::::::::::: {.columns align=center}
::: {.column width="70%"}

  * Лушин Артём Андреевич
  * Бакалавр направления компьютерные и информационные науки
  * Кафедра теории вероятности и кибербезопасности
  * Российский университет дружбы народов
  * Редактор Первого Федерального канала
  * [lusin5745@gmail.com](mailto:lusin5745@gmail.com)

:::
::: {.column width="30%"}

![](/home/aalushin/work/study/study_2023-2024_infosec/labs/lab1/presentation/image/me.jpg)

:::
::::::::::::::

# Вводная часть

## Цели и задачи

Целью данной работы является приобретение практических навыков установки Rocky Linux на виртуальную машину с помощью инструманте Vagrant.

# Ход работы

## Создание рабочей зоны

Я выполняю лабораторную работу на ОС Windows, поэтому все папки и каталоги будут находиться на этой ОС. Сначала я создал папку packer и vagrant. Затем в каждом из папок создал подкаталоги. В packer я разместил файл vagrant-rocky.pkr.hcl. В подкаталоге vagrant разместил ещё один подкаталог http с файлом ks.cfg. Так же в каталоге vagrant мы разместили vagrantfile и Makefile. 

![](/home/aalushin/new/study_2024-2025_admin/labs/lab1/presentation/image/1.jpg)

## Создание основных скриптов

В каталоге vagrant мы создали ещё три подкаталога default, server, client. В каждом из этих подкаталогов я разместил скрипт-заглушки: 01-dummy.sh. В каталоге default я разместил скрипт 01-user.sh. Также в default мы разместили 01-hostname.sh. В каталоге server у нас находятся 02-forward.sh. И в client размещён 02-routing.sh.

![](/home/aalushin/new/study_2024-2025_admin/labs/lab1/presentation/image/7.jpg)

## Запуск виртуальной машины

Мы зарегистрировали образ виртуальной ОС с помощью команды. Запустили первую ОС - server и вторую - client. 

![](/home/aalushin/new/study_2024-2025_admin/labs/lab1/presentation/image/18.jpg)

## Проверка работоспособности

После запуска двух машин одновременно убедились, что они обе работают и никак не вылетают. Подключились к серверу и клиенту из консоли. 

![](/home/aalushin/new/study_2024-2025_admin/labs/lab1/presentation/image/20.jpg)


## Итоговая проверка

Зафиксировали внесённые изменения для внутренних настроек виртуальной машины. Сменили пользователей в vagrant на локальных, то есть на aalushin. Выключили машины и сохранили на переносные устройства. 

![](/home/aalushin/new/study_2024-2025_admin/labs/lab1/presentation/image/30.jpg)

# Результаты

## Вывод 

Я приобрёл практические навыки установки Rocky Linux на виртуальную машину с помощью инструмента vagrant. 

## Контрольные вопросы 

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


