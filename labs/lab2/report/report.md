---
## Front matter
title: "Лабораторная работа №2"
subtitle: "Основы информационной безопасности"
author: "Анастасия Андреевна Кондрашова"

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
lot: true # List of tables
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
biblatex: true
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
lotTitle: "Список таблиц"
lolTitle: "Листинги"
## Misc options
indent: true
header-includes:
  - \usepackage{indentfirst}
  - \usepackage{float} # keep figures where there are in the text
  - \floatplacement{figure}{H} # keep figures where there are in the text
---

# Цель работы

1. Получение практических навыков работы в консоли с атрибутами файлов
2. Закрепление теоретических основ дискреционного доступа в современных системах на базе ОС Linux


# Выполнение лабораторной работы

1. В установленной ОС создаем учетную запись для нового пользователя, используя учетную запись администратора, а затем задаем пароль для этого пользователя.

![Создание учетной записи](image/01.png){ #fig:001 width=70% }

2. Входим в системы под именем нового пользователя

![Смена учетной записи](image/02.png){ #fig:002 width=70% }

3. Определяем директорию, в которой мы находимся.Она является домашней директорией (имя равно имени в домашней строке), поэтому менять директорию нам не требуется.

![Определение директории](image/03.png){ #fig:003 width=70% }

4. Уточняем имя пользователя, командой id уточняем более подробную информацию (имя пользователя, его группу, а также группы, куда он входит). Затем сравниваем вывод команды id и groups.

![Получение информации о пользователе](image/04.png){ #fig:004 width=70% }

5. Смотрим файл /etc/passwd, для того, чтобы видеть только информацию, требующуюся мне в данный момент воспользуемя командой cat /etc/passwd | grep guest. Это нужно нам, чтобы сравнить эту информацию с выведенной в предыдущем пункте.

![Просмотр информации](image/05.png){ #fig:005 width=70% }

6. Определяем существующие директории, нам удалось получить к ним доступ, а также посмотреть, какие права установлены на них.

![Директории в домашней папке](image/06.png){ #fig:006 width=70% }

7. Пытаемся посмотреть, какие расширения установленны на поддиректориях домашней папки, но нам это не удается.

![Поддиректории в домашней папке](image/07.png){ #fig:007 width=70% }

8. 
- Создаем поддиректорию
- Определяем, какие права доступа и расширенный атрибуты выставлены для нее
- Снимаем все атрибуты
- Пытаемся создать файл, но он не создается, т.к у нас недостаточно прав на это

![Создание файла](image/08.png){ #fig:008 width=70% }

9. Заполняем таблицу "Установленные права и разрешенные действия"

![Установленные права и разрешения](image/09.jpg){ #fig:009 width=70% }

10. Заполняем таблицу "Минимальные права для совершения операций"

![Минимальные права для совершения операций](image/10.jpg){ #fig:010 width=70% }

# Выводы

Получены навыки работы в консоли с атрибутами файлов и получены теоретические знания о них.



