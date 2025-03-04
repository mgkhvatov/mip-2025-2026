---
## Front matter
lang: ru-RU
title: Лабораторная работа №5
subtitle: Модель эпидемии (SIR)
author:
  - Хватов М. Г.
institute:
  - Российский университет дружбы народов, Москва, Россия

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
::: {.column width="60%"}

  * Хватов Максим Григорьевич
  * студент
  * Российский университет дружбы народов
  * [1032204364@pfur.ru](mailto:1032204364@pfur.ru)

:::
::: {.column width="25%"}

![](./image/mgkhvatov.jpg)

:::
::::::::::::::

## Цель работы

Построить модель SIR в *xcos* и OpenModelica.

## Задание

1. Реализовать модель SIR в в *xcos*;
2. Реализовать модель SIR с помощью блока Modelica в в *xcos*;
3. Реализовать модель SIR в OpenModelica;
4. Реализовать модель SIR с учётом процесса рождения / гибели особей в xcos (в том числе и с использованием блока Modelica), а также в OpenModelica;
5. Построить графики эпидемического порога при различных значениях параметров модели (в частности изменяя параметр $\mu$);
6. Сделать анализ полученных графиков в зависимости от выбранных значений параметров модели.

## Выполнение лабораторной работы

$$
\begin{cases}
  \dot s = - \beta s(t)i(t);
  \dot i = \beta s(t)i(t) - \nu i(t);
  \dot r = \nu i(t),
\end{cases}
$$

где $\beta$ -- скорость заражения, $\nu$ -- скорость выздоровления.

## Реализация модели в xcos

Зафиксируем начальные данные: $\beta = 1, \, \nu = 0,3, s(0) = 0,999, \, i(0) = 0,001, \, r(0) = 0.$

## Реализация модели в xcos

![Задание переменных окружения в xcos](image/1.png){#fig:001 width=70%}

## Реализация модели в xcos

![Модель SIR в xcos](image/2.png){#fig:002 width=70%}

## Реализация модели в xcos

![Задание начальных значений в блоках интегрирования](image/3.png){#fig:003 width=70%}

## Реализация модели в xcos

![Задание начальных значений в блоках интегрирования](image/4.png){#fig:004 width=70%}

## Реализация модели в xcos

![Задание конечного времени интегрирования в xcos](image/5.png){#fig:005 width=70%}

## Реализация модели в xcos

![Эпидемический порог модели SIR при $\beta = 1, \nu = 0.3$](image/6.png){#fig:006 width=70%}

## Реализация модели с помощью блока Modelica в xcos

![Модель SIR в xcos с применением блока Modelica](image/7.png){#fig:007 width=70%}

## Реализация модели с помощью блока Modelica в xcos

![Параметры блока Modelica для модели SIR](image/8.png){#fig:008 width=50%}

## Реализация модели с помощью блока Modelica в xcos

![Параметры блока Modelica для модели SIR](image/9.png){#fig:009 width=50%}

## Реализация модели с помощью блока Modelica в xcos

![Эпидемический порог модели SIR при $\beta = 1, \nu = 0.3$](image/10.png){#fig:010 width=70%}

## Упражнение

```
  parameter Real I_0 = 0.001;
  parameter Real R_0 = 0;
  parameter Real S_0 = 0.999;
  parameter Real beta = 1;
  parameter Real nu = 0.3;
  parameter Real mu = 0.5;
  Real s(start=S_0);
  Real i(start=I_0);
  Real r(start=R_0);
  
equation
  der(s)=-beta*s*i;
  der(i)=beta*s*i-nu*i;
  der(r)=nu*i;
```

## Упражнение

![Эпидемический порог модели SIR при $\beta = 1, \nu = 0.3$](image/11.png){#fig:012 width=70%}

## Задание для самостоятельного выполнения

$$
\begin{cases}
  \dot s = - \beta s(t)i(t) + \mu (N - s(t)); 
  \dot i = \beta s(t)i(t) - \nu i(t) - \mu i(t);
  \dot r = \nu i(t) - \mu r(t),
\end{cases}
$$

где $\mu$ — константа, которая равна коэффициенту смертности и рождаемости.

## Задание для самостоятельного выполнения

![Модель SIR с учетом демографических процессов в xcos](image/13.png){#fig:013 width=60%}

## Задание для самостоятельного выполнения

![График модели SIR с учетом демографических процессов](image/14.png){#fig:014 width=70%}

## Задание для самостоятельного выполнения

![Модель SIR с учетом демографических процессов в xcos с применением блока Modelica](image/15.png){#fig:015 width=70%}

## Задание для самостоятельного выполнения

![Параметры блока Modelica для модели SIR с учетом демографических процессов](image/16.png){#fig:016 width=50%}

## Задание для самостоятельного выполнения

![Параметры блока Modelica для модели SIR с учетом демографических процессов](image/17.png){#fig:017 width=50%}

## Задание для самостоятельного выполнения

![График модели SIR с учетом демографических процессов](image/18.png){#fig:018 width=60%}

## Задание для самостоятельного выполнения

```
  parameter Real I_0 = 0.001;
  parameter Real R_0 = 0;
  parameter Real S_0 = 0.999;
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

## Выводы

В процессе выполнения данной лабораторной работы была построена модель SIR в *xcos*
