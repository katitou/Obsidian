
## **Декомпозиция** 

Цель: Построить модель прогнозирования временного ряда, способную учитывать:
    
	Недельную сезонность (пики в выходные).
	Ежегодную сезонность (рост продаж в декабре, особенно 30 и 31 числа).
	Влияние праздничных дней и предпраздничных эффектов.
	
Результат: Точный прогноз продаж с учетом описанных особенностей.

### **Сбор и предобработка данных**

**Действия**:
    1. Сбор данных о продажах в формате:
        - Дата (`datetime`).
        - Продажи (`number_sold`).
    2. Интеграция календаря праздников и предпраздничных дней (доп. фичи: `is_holiday`, `days_to_holiday`).
    3. Создание дополнительных признаков:
        - День недели (1–7).
        - Месяц (1–12).
        - Год.
        - Лаги и скользящие средние продаж (например, за 7, 30 дней).
    4. Проверка данных на пропуски и выбросы:
        - Заполнение пропусков.
        - Обработка выбросов (например, с помощью медианного сглаживания).


**Методы проверки**:
    - Визуализация временного ряда.
    - Корреляционный анализ признаков.
    - Проверка полноты данных (наличие всех дат).



Задача

1. Попробовать спрогнозировать дневные продажи по компании на 2 месяца вперёд (Вова сможет предоставить запрос на выгрузку данных по филиалам из gp).
2. Детальнее попробовать построить прогнозы по филиалам (если по компании получилось хорошо, по филиалам должно быть тоже хорошо в общем:) ).

Нам нужно уметь учитывать праздники, предпраздничные эффекты (30, 31 декабря).
Ряд продаж - это ряд с сильной недельной и ежегодной сезонностью.
Пики выпадают на субботу и  вск (вск чуть ниже).
Ежегодние пики продаж выпадают на 30, 31 декабря. А декабрь самый высокий месяц по продажам.

Потенциальные полезные методы прогнозирования:

0. Наивные методы (SeasonalityMotif, autots библиотека).
1. На основе фурье (Prophet, Fast Fourier Transform).
2. На основе декомпозиции ряда (MSTL, statsforecast библиотека)

Я бы попробовал поковырять сначала autots с различными motif методами (они достаточно быстрые для перебора параметров) и seasonal валидацией на истории (можно задавать в параметрах autots). И также запустил бы на всех филиалах с целью понять сколько хватит не хватит ресурсов системы (достаточно требователен по памяти). Нужно использовать все ядра.

И в идеале  использовать automl в проде (это позволит подбирать параметры специфические для месяца).

Источники

https://unit8co.github.io/darts/generated_api/darts.models.forecasting.fft.html
https://winedarksea.github.io/AutoTS/build/html/source/tutorial.html#id9
https://unit8co.github.io/darts/generated_api/darts.models.forecasting.prophet_model.html
https://nixtlaverse.nixtla.io/statsforecast/docs/models/multipleseasonaltrend.html

Задача

прогнозирование временных рядов продаж
нужно регулировать возможность учитывать праздники, предпраздничные эффекты (например скачки продаж 30, 31 декабря)
Ряд продаж - это ряд с сильной недельной и ежегодной сезонностью.
Пики выпадают на субботу и  воскресенье (воскресенье чуть ниже).
Ежегодные пики продаж выпадают на 30, 31 декабря. декабрь самый высокий месяц по продажам.
Потенциальные подходящий метод прогнозирования:
 autots библиотека с различными motif методами, они достаточно быстрые для перебора параметров,  и seasonal валидацией на истории . И в идеале  использовать automl в проде
 
1. На основе фурье (Prophet, Fast Fourier Transform).
2. На основе декомпозиции ряда (MSTL, statsforecast библиотека)

 И также запустил бы на всех филиалах с целью понять сколько хватит не хватит ресурсов системы (достаточно требователен по памяти). Нужно использовать все ядра.

И в идеале  использовать automl в проде (это позволит подбирать параметры специфические для месяца).



Дана линейная краевая задача для дифференциального уравнения второго порядка (n = 2):
```
u''-(x+1)**2*u'-(2u)/(x+1)**2 = 1 
u(0)-u'(0) =2
u(1) = 0.5
u(x) = 1/(x+1)
```

решение краевой задачи методом галеркина, искать приближенное решение в виде
```
phi_0(x) + C1*phi_1(x)+C2*phi_2(x)
где 
phi_0(x)  - phi_0'(x) = 2
phi_0(x) = 0.5 
```

функции phi_1, phi_2 линейно независимы, непрерывны до второй производной, однородные граничные условия 

Выберем базисные функции 
```
phi_0(x)= ax+b
phi_1(x) = ax**2 + bx+c
phi_2(x)  =ax**3 + bx**2 + cx + d
```

последовательно решаем 
1.
```
phi_0(0)  - phi_0'(0) = 2
phi_0(1) = 0.5 

тогда phi_0 = ...
```
2.
```
phi_1(0)  - phi_1'(0) = 2
phi_1(1) = 0.5 

тогда phi_1 = ...
```
3.
```
phi_2(0)  - phi_2'(0) = 2
phi_2(1) = 0.5 

тогда phi_2 = ...
```

тогда численное решение 
```
R(x, C1, C2) = u''-(x+1)**2*u'-(2u)/(x+1)**2 = 1 

u(x) = phi_0(x) + C1*phi_1(x)+C2*phi_2(x)
u'(x) = (phi_0(x) + C1*phi_1(x)+C2*phi_2(x))'
u(x)'' = (phi_0(x) + C1*phi_1(x)+C2*phi_2(x))''
```

условия ортогональности функции R(x, C1, C2) к функциям phi_1(x), phi_2(x) приводят к системе
```
int(от 0 до 1) phi_1*R(x, C1, C2)dx = 0
int(от 0 до 1) phi_2*R(x, C1, C2)dx = 0
```
подставляем значения, интегрируем, решаем слау, чтобы найти C1, C2

итоговый вид приближенного решения имеет вид:

