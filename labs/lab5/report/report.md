---
## Front matter
title: "Лабораторная работа №5"
subtitle: "Модель эпидемии (SIR)"
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

Построить модель SIR в xcos и OpenModelica.

# Задание

1. Реализовать модель SIR в в *xcos*;
2. Реализовать модель SIR с помощью блока Modelica в в *xcos*;
3. Реализовать модель SIR в OpenModelica;
4. Реализовать модель SIR с учётом процесса рождения / гибели особей в xcos (в том числе и с использованием блока Modelica), а также в OpenModelica;
5. Построить графики эпидемического порога при различных значениях параметров модели (в частности изменяя параметр $\mu$);
6. Сделать анализ полученных графиков в зависимости от выбранных значений параметров модели.

# Выполнение лабораторной работы

Задача о распространении эпидемии описывается системой дифференциальных уравнений:

$$
\begin{cases}
  \dot s = - \beta s(t)i(t); \\
  \dot i = \beta s(t)i(t) - \nu i(t);\\
  \dot r = \nu i(t),
\end{cases}
$$

где $\beta$ -- скорость заражения, $\nu$ -- скорость выздоровления.

## Реализация модели в xcos

Зафиксируем начальные данные: $\beta = 1, \, \nu = 0,3, s(0) = 0,999, \, i(0) = 0,001, \, r(0) = 0.$

В меню Моделирование, Установить контекст зададим значения переменных $\beta$ и $\nu$ (рис. [-@fig:001]).

![Задание переменных окружения в xcos](image/1.png){#fig:001 width=70%}

Для реализации модели (рис. [-@fig:002]) потребуются следующие блоки xcos:

- `CLOCK_c` -- запуск часов модельного времени;
- `CSCOPE` -- регистрирующее устройство для построения графика;
- `TEXT_f` -- задаёт текст примечаний;
- `MUX` -- мультиплексер, позволяющий в данном случае вывести на графике сразу
несколько кривых;
- `INTEGRAL_m` -- блок интегрирования;
- `GAINBLK_f` -- в данном случае позволяет задать значения коэффициентов $\beta$ и $\nu$ ;
- `SUMMATION` -- блок суммирования;
- `PROD_f` -- поэлементное произведение двух векторов на входе блока.

![Модель SIR в xcos](image/2.png){#fig:002 width=70%}

В параметрах верхнего и среднего блока интегрирования необходимо задать начальные значения $s(0) = 0,999$ и $i(0) = 0,001$ (рис. [-@fig:003],[-@fig:004]).

![Задание начальных значений в блоках интегрирования](image/3.png){#fig:003 width=70%}

![Задание начальных значений в блоках интегрирования](image/4.png){#fig:004 width=70%}

В меню Моделирование, Установка зададим конечное время интегрирования, равным времени моделирования, в данном случае 30 (рис. [-@fig:005]).

![Задание конечного времени интегрирования в xcos](image/5.png){#fig:005 width=70%}

Результат моделирования представлен на рис. [-@fig:006], где черной линией обозначен график $s(t)$ (динамика численности уязвимых к болезни особей), красная
линия определяет $r(t)$ — динамику численности выздоровевших особей, наконец,
зеленая линия определяет $i(t)$ — динамику численности заражённых
особей. Пересечение трёх линий определяет порог эпидемии.

![Эпидемический порог модели SIR при $\beta = 1, \nu = 0.3$](image/6.png){#fig:006 width=70%}

## Реализация модели с помощью блока Modelica в xcos

Готовая модель SIR представлена на рис. [-@fig:007].

Для реализации модели SIR с помощью языка Modelica помимо блоков `CLOCK_c`,
`CSCOPE`, `TEXT_f` и `MUX` требуются блоки `CONST_m` — задаёт константу; `MBLOCK`
(Modelica generic) — блок реализации кода на языке Modelica. Задаём значения
переменных $\beta$ и $\nu$ (рис. [-@fig:001]).

![Модель SIR в xcos с применением блока Modelica](image/7.png){#fig:007 width=70%}

Параметры блока Modelica представлены на рис. [-@fig:008],[-@fig:009]. Переменные на входе (“beta”, “nu”) и выходе (“s”, “i”, “r”) блока заданы как внешние (“E”).

![Параметры блока Modelica для модели SIR](image/8.png){#fig:008 width=70%}

![Параметры блока Modelica для модели SIR](image/9.png){#fig:009 width=70%}

В результате получаем график (рис. [-@fig:010]), построенный с помощью блока Modelica идентичный графику (рис. [-@fig:006]), построенному без них.

![Эпидемический порог модели SIR при $\beta = 1, \nu = 0.3$](image/10.png){#fig:010 width=70%}

# Задание для самостоятельного выполнения

Предположим, что моедль SIR учитывает демографический процесс, в частности, что смертность уравновешивает рождаемость, а все ржденные индивидуумы появляются на свет абсолютно здоровыми. Получим следующую ситему уравнений:

$$
\begin{cases}
  \dot s = - \beta s(t)i(t) + \mu (N - s(t)); \\
  \dot i = \beta s(t)i(t) - \nu i(t) - \mu i(t);\\
  \dot r = \nu i(t) - \mu r(t),
\end{cases}
$$

![Модель SIR с учетом демографических процессов](image/13.png){#fig:013 width=70%}

В результате получаем следующий график (рис. [-@fig:014]).

![График модели SIR с учетом демографических процессов](image/14.png){#fig:014 width=70%}

Теперь реализуем модель SIR с учетом демографических процессов в *xcos* с помощью блоков Modelica (рис. [-@fig:015]).

![Модель SIR с учетом демографических процессов в xcos с применением блока Modelica](image/15.png){#fig:015 width=70%}

Параметры блока Modelica представлены на рис. [-@fig:016],[-@fig:017]. Переменные на входе (“beta”, “nu”, “mu” ) и выходе (“s”, “i”, “r”) блока заданы как внешние (“E”).

![Параметры блока Modelica для модели SIR с учетом демографических процессов](image/16.png){#fig:016 width=70%}

![Параметры блока Modelica для модели SIR с учетом демографических процессов](image/17.png){#fig:017 width=70%}

В результате получаем следующий график (рис. [-@fig:018]).

![График модели SIR с учетом демографических процессов](image/18.png){#fig:018 width=70%}

Реализуем модель SIR с учетом демографических процессов на OpenModelica.

```
  parameter Real I_0 = 0.001;
  parameter Real R_0 = 0;
  parameter Real S_0 = 0.999;
  parameter Real N = 1;
  parameter Real beta = 1;
  parameter Real nu = 0.3;
  parameter Real mu = 0.5;
  
  Real s(start=S_0);
  Real i(start=I_0);
  Real r(start=R_0);
  
equation
  der(s)=-beta*s*i + mu*i + mu*r;
  der(i)=beta*s*i-nu*i - mu*i;
  der(r)=nu*i - mu*r;
```

Выполнив симуляцию, у меня почему-то не получается график, а остается только пустая сетка, хотя уравнение должно быть верным, а также не происходит 30 секундная симуляция - всё завершается за секунду, хотя я ввёл время симуляции равный 30, оно сбрасывется до 1.



Иcходя из анализа графиков можно сказать, что чем выше значение любого из параметров, тем быстрее ситема достигает стационарного состояния. При высоком коэффициенте заражения система быстро проходит через пик развития эпидемии и достигает стационарного состояния

# Вывод



В процессе выполнения лабораторной работы была построена модель SIR в xcos