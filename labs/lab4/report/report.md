---
## Front matter
title: "Лабораторная работа №4"
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

Получение практических навыков работы в консоли с расширенными атрибутами файлов.

# Выполнение лабораторной работы

1. От имени пользователя guest3 определяю расширенные атрибуты файла, затем устанавливаю на файл права, разрешающие чтение и запись для владельца файла. Пытаемся установить расширенный атрибут а, но нам это не удается, тогда мы делаем это от имени администратора.

![Расширенные атрибуты](image/01.png){ #fig:001 width=70% }

2. Выполняем дозапись в файл и убеждаемся, что оно запсалось. Затем перезаписываем файл и тоже проверяем результат. Ставим на файл права, запрещающие чтение и запись владельцу файла. Проделываем теже самые операции и получаем отказ. Убираем расширенные права а.

![Результаты расширенного атрибута а](image/02.png){ #fig:002 width=70% }

3. Заменяем атрибут а атрибутом i.

![Расширенный атрибут i](image/03.png){ #fig:003 width=70% }

4. Проделываем теже самые действия.В данном случае файл можно было только прочитать, а изменить или записать в него что-то нельзя.

![Результаты расширенного атрибута i](image/04.png){ #fig:004 width=70% }

# Выводы

Мы повысили свои навыки использования интерфейса командной строки, познакомились на примерах с тем, как используются основные и расширенные атрибуты при разграничении доступа.

