source: [[Инфографика]]
tegs: #инфографика 



Рассмотрим круговую диаграмму.

```python
import matplotlib.pyplot as plt

# Данные для круговой диаграммы
labels = ['Category A', 'Category B', 'Category C', 'Category D']
sizes = [20, 30, 25, 25]

# Построение графика
plt.pie(sizes, labels=labels, autopct='%1.1f%%')
plt.title('Pie Chart')
plt.show()
```

![](https://ucarecdn.com/3fb15efa-b232-413e-b2de-c1d71e5b1f4c/)

Выглядит красиво, но не очень. Давайте добавим сюда отступы. В код добавим строку 

```ini
explode = (0, 0.1, 0, 0) # Величина смещения для второго сектора
```

Чтобы весь код стал таким.

```python
import matplotlib.pyplot as plt

# Данные для круговой диаграммы
labels = ['Category A', 'Category B', 'Category C', 'Category D']
sizes = [20, 30, 25, 25]
explode = (0, 0.1, 0, 0)  # Величина смещения для второго сектора
plt.pie(sizes, labels=labels, autopct='%1.1f%%', explode=explode)
plt.title('Pie Chart with Explode')
plt.show()
```

![](https://ucarecdn.com/e93192ba-5b9f-4e15-b3ee-61d8c58f3d3b/)

Выглядит гораздо лучше. Можем добавить тень, путем добавления флага shadow=True.

```python
import matplotlib.pyplot as plt

# Данные для круговой диаграммы
labels = ['Category A', 'Category B', 'Category C', 'Category D']
sizes = [20, 30, 25, 25]
explode = (0, 0.1, 0, 0)  # Величина смещения для второго сектора
plt.pie(sizes, labels=labels, autopct='%1.1f%%', shadow=True, explode=explode)
plt.title('Pie Chart with Shadow')
plt.show()
```

 ![](https://ucarecdn.com/df5866cd-f340-4210-ac38-fafebcf23603/)

А можно сделать диаграмму в виде пончика.

```python
import matplotlib.pyplot as plt

# Данные для круговой диаграммы
labels = ['Category A', 'Category B', 'Category C', 'Category D']
sizes = [20, 30, 25, 25]
explode = (0, 0.1, 0, 0)  # Величина смещения для второго сектора
plt.pie(sizes, labels=labels, autopct='%1.1f%%', wedgeprops=dict(width=0.3))
plt.title('Donut Chart')
plt.show()
```