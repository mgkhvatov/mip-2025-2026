---
## Front matter
title: "Упражнение 1"
subtitle: "Построить с помощью xcos фигуры Лиссажу с различными значениями параметров."
author: "Хватов Максим Григорьевич"

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
lot: false # List of tables
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

Построить с помощью xcos фигуры Лиссажу с различными значениями параметров.

# Задание

Построить с помощью xcos фигуры Лиссажу с различными значениями параметров.

# Выполнение лабораторной работы

Сначала построю модель с двумя синусоидальными сигналами и параметрами по умолчанию соответственно.

![Основная схема](image/1.png){#fig:001 width=70%}

Далее задам параметром фазу равную pi/2и получу при запуске изображение элиипса

![Эллипс с фазой pi/2](image/2.png){#fig:002 width=70%}

Изменю фазу на pi/4 и получу элипс, но повернутый под углом

![Повернутый эллипс с фазой pi/4](image/3.png){#fig:003 width=70%}

теперь для синусоидального сигнала задам задам параметр частоты равный 3 и получу изображение следующего вида

![Фигура, полученная изменением параметров синусоидального сигнала](image/4.png){#fig:004 width=70%}

# Вывод

В процессе выполнения упражнения я построил фигуру Лиссажу с помощью xcos



