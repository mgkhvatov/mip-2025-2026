---
## Front matter
lang: ru-RU
title: Лабораторная работа №6
subtitle: Модель «хищник–жертва»
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

Реализовать модель "хищник-жертва" в *xcos*.

## Задание

1. Реализовать модель "хищник-жертва" в xcos;
2. Реализовать модель "хищник-жертва" с помощью блока Modelica в xcos;
3. Реализовать модель "хищник-жертва" в OpenModelica

## Выполнение лабораторной работы

$$
\begin{cases}
  \dot x = ax - bxy \\
  \dot y = cxy - dy,
\end{cases}
$$

где $x$ — количество жертв; $y$ — количество хищников; $a, b, c, d$ — коэффициенты, отражающие взаимодействия между видами.

## Реализация модели в xcos

Зафиксируем начальные данные: $\beta = 1, \, \nu = 0,3, s(0) = 0,999, \, i(0) = 0,001, \, r(0) = 0.$

## Реализация модели в xcos

![Задание переменных окружения в xcos для модели](image/1.png){#fig:001 width=70%}

## Реализация модели в xcos

![Модель «хищник–жертва» в xcos](image/2.png){#fig:002 width=70%}

## Реализация модели в xcos

![Задание начальных значений в блоках интегрирования](image/3.png){#fig:003 width=70%}

## Реализация модели в xcos

![Задание параметров моделирования](image/4.png){#fig:004 width=70%}

## Реализация модели в xcos

![Динамика изменения численности хищников и жертв модели Лотки-Вольтерры при $a = 2, b = 1, c = 0.3, d = 1, x(0) = 2, y(0) = 1$](image/5.png){#fig:005 width=50%}

## Реализация модели в xcos

![Фазовый портрет модели Лотки-Вольтерры при $a = 2, b = 1, c = 0.3, d = 1, x(0) = 2, y(0) = 1$](image/6.png){#fig:006 width=50%}

## Реализация модели с помощью блока Modelica в xcos

![Модель «хищник–жертва» в xcos с применением блока Modelica](image/7.png){#fig:007 width=55%}

## Реализация модели с помощью блока Modelica в xcos

![Параметры блока Modelica для модели "хищник–жертва"](image/8.png){#fig:008 width=50%}

## Реализация модели с помощью блока Modelica в xcos

![Параметры блока Modelica для модели "хищник–жертва"](image/9.png){#fig:009 width=50%}

## Реализация модели с помощью блока Modelica в xcos

![Динамика изменения численности хищников и жертв модели Лотки-Вольтерры при $a = 2, b = 1, c = 0.3, d = 1, x(0) = 2, y(0) = 1$](image/10.png){#fig:010 width=70%}

## Реализация модели с помощью блока Modelica в xcos

![Фазовый портрет модели Лотки-Вольтерры при $a = 2, b = 1, c = 0.3, d = 1, x(0) = 2, y(0) = 1$](image/11.png){#fig:011 width=70%}

## Упражнение

```
  parameter Real a = 2;
  parameter Real b = 1;
  parameter Real c = 0.3;
  parameter Real d = 1;
  parameter Real x0 = 2;
  parameter Real y0 = 1;
  Real x(start=x0);
  Real y(start=y0);
equation
    der(x) = a*x - b*x*y;
    der(y) = c*x*y - d*y;
```

## Вывод

В процессе выполнения данной лабораторной реализована модель "хищник-жертва" в *xcos*.