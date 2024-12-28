
source: [[Инфографика]]
tegs: #инфографика

Теперь давайте посмотрим на то, как делать гистограмму.

```perl
import matplotlib.pyplot as plt

# Данные для столбчатой диаграммы
categories = ['A', 'B', 'C', 'D']
values = [5, 7, 3, 8]

# Построение графика
plt.bar(categories, values)
plt.title('Bar Chart')
plt.xlabel('Categories')
plt.ylabel('Values')
plt.show()
```

![](https://ucarecdn.com/3013e8d2-33e8-4f6b-bc0c-634529cf4877/)

И тут вроде все понятно, но давайте немного усложним задачу и поменяем цвет на графике.

```dart
import matplotlib.pyplot as plt

# Данные для столбчатой диаграммы
categories = ['A', 'B', 'C', 'D']
values = [5, 7, 3, 8]

# Построение графика с указанием цвета столбцов
plt.bar(categories, values, color='green')  # Можно указать цвет, например, 'green', 'red', 'blue', и т.д.
plt.title('Bar Chart')
plt.xlabel('Categories')
plt.ylabel('Values')
plt.show()
```

![](https://ucarecdn.com/107c36e0-6122-410e-b714-0735dc650b3c/)

А что если мы хотим использовать разные цвета для каждого столбца? 

```1c
import matplotlib.pyplot as plt

# Данные для столбчатой диаграммы
categories = ['A', 'B', 'C', 'D']
values = [5, 7, 3, 8]

# Построение графика с разными цветами для каждого столбца
colors = ['red', 'blue', 'green', 'orange']
plt.bar(categories, values, color=colors)
plt.title('Bar Chart')
plt.xlabel('Categories')
plt.ylabel('Values')
plt.show()
```

![](https://ucarecdn.com/69c4d7f0-f25a-48a1-9d64-65585f51d7ec/)

Выглядит неплохо. И здесь мы закинем кое-какую мысль. Почему бы нам не делать более яркий цвет, при более большом значении? На этот вопрос мы совсем скоро найдем ответ. Или можно сразу здесь, почему бы нет? Про numpy мы скоро узнаем.

```python
import matplotlib.pyplot as plt
import numpy as np

# Данные для столбчатой диаграммы
categories = ['A', 'B', 'C', 'D']
values = [5, 7, 3, 8]

# Нормализуем значения для использования в цветовой карте (значения от 0 до 1)
norm_values = np.array(values) / max(values)

# Используем colormap для задания цвета в зависимости от значения
colors = plt.cm.viridis(norm_values)  # Можно использовать другие colormap, например, 'plasma', 'inferno', 'coolwarm'

# Построение графика
plt.bar(categories, values, color=colors)
plt.title('Bar Chart with Gradient Colors')
plt.xlabel('Categories')
plt.ylabel('Values')
plt.show()
```

![](https://ucarecdn.com/1d313251-76a8-45e2-b254-decaa746e8fc/)

А что если мы хотим сохранить этот график? Не делать же нам каждый раз скриншот?

Для этого используйте код

```bash
plt.savefig('bar_chart.png')
```

Если вам нужно сохранить файл в определенном разрешении или с прозрачным фоном, можно добавить дополнительные параметры:

```python
plt.savefig('bar_chart.png', dpi=300, transparent=True)
```

Видим, что png реально png, без заднего фона и мыслей :)  
![](https://ucarecdn.com/42daf228-8f9a-47d1-9cda-20e60624a299/)

---

 4