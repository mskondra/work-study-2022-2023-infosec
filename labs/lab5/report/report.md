---
## Front matter
title: "Лабораторная работа №5"
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

Изучение механизмов изменения идентификаторов, применения SetUID- и Sticky-битов. Получение практических навыков работы в консоли с дополнительными атрибутами. Рассмотрение работы механизма смены идентификатора процессов пользователей, а также влияние бита Sticky на запись и удаление файлов.

# Выполнение лабораторной работы

1. Вошли в систему от имени пользователя guest2.
2. Создали программу simpleid.c.
3. Скомплилируйте программу и убедитесь, что файл программы создан с помощью команды gcc simpleid.c -o simpleid.
4. Выполните программу simpleid.
5. Выполните системную программу id и сравнили полученный нами результат с данными предыдущего пункта. Данные иденичны.

![Выполнение программы simpleid](01.png){ #fig:001 width=70% }

![Программа simpleid](02.png){ #fig:002 width=70% }

6. Усложнили программу, добавив вывод действительных идентификаторов.Получившуюся программу назвали simpleid2.c.
7. Скомпилируйте и запустили simpleid2.c с помощью команды gcc simpleid2.c -o simpleid2.

![Программа simpleid2](03.png){ #fig:003 width=70% }

![Выполнение программы simpleid2](04.png){ #fig:004 width=70% }

8. От имени суперпользователя выполнили команды (для этого исползовали повышение своих прав с помощью sudo):
chown root:guest /home/guest/simpleid2
chmod u+s /home/guest/simpleid2
10. Выполнили проверку правильности установки новых атрибутов и смены владельца файла simpleid2.
11. Запустите simpleid2 и id.

![Выполнение программы simpleid2](4_1.png){ #fig:4_1 width=70% }

12. Создали программу readfile.c:
13. Откомпилировали её.

![Создание программы readfile.c](05.png){ #fig:005 width=70% }

![Программа readfile.c](06.png){ #fig:006 width=70% }

14. Сменили владельца у файла readfile.c и изменили права так, чтобы только суперпользователь (root) мог прочитать его, a guest2 не мог.

![Смена прав](07.png){ #fig:007 width=70% }

15. Проверили, что пользователь guest2 не может прочитать файл readfile.c.

![Проверка невозможности чтения](08.png){ #fig:008 width=70% }

16. Сменили у программы readfile владельца и установите SetU’D-бит.

![Смена владельца и установка SetU’D-бит](09.png){ #fig:009 width=70% }

17. Проверили, что программа readfile может прочитать файл readfile.c

![Проверка возможности чтения файла readfile.c](10.png){ #fig:010 width=70% }

18. Проверьте, что программа readfile может прочитать файл /etc/shadow

![Проверка возможности чтения файла /etc/shadow](11.png){ #fig:011 width=70% }


- Исследование Sticky-бита
1. Выяснили, установлен ли атрибут Sticky на директории /tmp, для чего выполнили команду ls -l / | grep tmp
2. От имени пользователя guest создали файл file01.txt в директории /tmp со словом test.
3. Просмотрели атрибуты у только что созданниого файла и разрешили чтение и запись для категории пользователей «все остальные».

![Атрибуты на директории /tmp и файла file01.txt](12.png){ #fig:012 width=70% }

4. От пользователя guest3 (не являющегося владельцем) попробовали прочитать файл /tmp/file01.txt. Нам это удалось.
5. От пользователя guest3 попробовали дозаписать в файл /tmp/file01.txt слово test2. Слово перезаписалось, а не дозаписалось.
6. От пользователя guest3 попробовали перезаписать в файл /tmp/file01.txt слово test3. Слово перезаписалось.
7. От пользователя guest3 попробовали удалить файл /tmp/file01.txt командой
8. Повысили свои права до суперпользователя и выполнили после этого команду, снимающую атрибут t (Sticky-бит) с
директории /tmp.

![Пункты 4-8](13.png){ #fig:013 width=70% }

9. От пользователя guest3 проверили, что атрибута t у директории /tmp нет.
10. Повторили предыдущие шаги, удалось удалить файл.
11. Повысили свои права до суперпользователя и вернули атрибут t на директорию /tmp:

![Пункты 9-11](14.png){ #fig:014 width=70% }

# Выводы

Изучили механизмы изменения идентификаторов, применения SetUID- и Sticky-битов. Получили практические навыки работы в консоли с дополнительными атрибутами. Рассмотрели работы механизма смены идентификатора процессов пользователей, а также влияние бита Sticky на запись и удаление файлов.
