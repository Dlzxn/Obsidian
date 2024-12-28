source: [[Инфографика]]
tegs: #инфографика


```
pip install matplotlib
```


Пример простейшего графика:

Построим первый линейный график.

```python
import matplotlib.pyplot as plt

# Данные для графика
x = [1, 2, 3, 4, 5]
y = [2, 3, 5, 7, 11]

# Создание графика
plt.plot(x, y)

# Добавление подписей к осям
plt.xlabel('X ось')
plt.ylabel('Y ось')

# Заголовок
plt.title('Простой линейный график')

# Показать график
plt.show()
```