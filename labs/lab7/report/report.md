---
## Front matter
title: "Лабораторная работа 7"
subtitle: "Модель M|M|1|"
author: "Хватов М. Г."

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

Рассмотреть пример моделирования в *xcos* системы массового обслуживания типа $M|M|1|\infty$.

# Задание

1. Реализовать модель системы массового обслуживания типа $M|M|1|\infty$;
2. Построить график поступления и обработки заявок;
3. Построить график динамики размера очереди.

# Выполнение лабораторной работы

Зафиксируем начальные данные: lambda=.3;mu=.35;z0=6. В меню Моделирование, Установить контекст зададим значения коэффициентов (рис. [-@fig:001]).

![Задаем переменные в окружении](image/1.png){#fig:001 width=70%}

Суперблок, моделирующий поступление заявок, представлен на рис. [-@fig:002]. Тут у нас заявки поступают в систему по пуассоновскому закону. Поступает заявка в суперблок, идет в синхронизатор входных и выходных сигналов, происходит равномерное распределение на интервале $[0; 1]$ (также заявка идет в обработчик событий), далее идет преобразование в экспоненциальное распределение с параметром $\lambda$, далее заявка опять попадает в обработчик событий и выходит из суперблока.

![Суперблок, моделирющий поступление заявок](image/2.png){#fig:002 width=70%}

Суперблок, моделирующий процесс обработки заявок. Обработка происходит по экспоненциальному закону.[-@fig:003]

![Суперблок, моделирющий обработку заявок](image/3.png){#fig:003 width=70%}

Готовая модель [-@fig:004], представляет собой композицию из суперлоков, описанных раннее, и других блоков, которые описаны в задании.

![Готовая модель $M|M|1|\infty$](image/4.png){#fig:004 width=70%}

Результаты моделирования:

![Динамика размера очереди](image/5.png){#fig:005 width=70%}

![Поступление и обработка заявок](image/6.png){#fig:006 width=70%}

# Вывод

В процессе выполнения лабораторной работы я рассмотрел пример моделирования xcos системы массвого обслуживания типа $M|M|1|infinity$



