
source: [[Инфографика]]
tegs: #инфографика


Двигаемся дальше. Здесь научимся работать с гистограммой частот.

```haskell
import matplotlib.pyplot as plt
import numpy as np

# Данные для гистограммы
data = np.random.randn(1000)

# Построение графика
plt.hist(data, bins=30, alpha=0.7)
plt.title('Histogram')
plt.xlabel('Value')
plt.ylabel('Frequency')
plt.show()
```

![](https://ucarecdn.com/9a184058-c9bf-43d8-8d88-13ab04bf707a/)

Опять же, интересного мало. Берем реальный пример.

```python
import matplotlib.pyplot as plt
import numpy as np

# Генерация данных: зарплаты сотрудников в тыс. долларов
salaries = np.random.normal(50, 15, 1000)  # Средняя зарплата = 50 тыс., стандартное отклонение = 15 тыс., 1000 сотрудников

# Построение гистограммы
plt.figure(figsize=(8,6))
plt.hist(salaries, bins=30, edgecolor='black', color='skyblue', alpha=0.7)

# Добавление подписей
plt.title('Distribution of Salaries in a Company', fontsize=14)
plt.xlabel('Salary (in thousands of dollars)', fontsize=12)
plt.ylabel('Number of Employees', fontsize=12)

# Добавление средней линии для акцента
mean_salary = np.mean(salaries)
plt.axvline(mean_salary, color='red', linestyle='dashed', linewidth=1.5, label=f'Mean Salary: ${mean_salary:.2f}K')

# Легенда
plt.legend()

# Показ графика
plt.show()
```

 ![](https://ucarecdn.com/66af7d98-debc-4bd5-84ca-a100d1197ee3/)

- **Данные о зарплатах**: Мы сгенерировали данные о зарплатах сотрудников с использованием нормального распределения. Средняя зарплата — 50K,стандартноеотклонение—50K,стандартноеотклонение—15K.
- **Гистограмма**: Гистограмма визуализирует распределение зарплат среди сотрудников. Мы использовали 30 "корзин" (bins) для отображения частот.
- **Цвет и прозрачность**: Цвет столбцов `skyblue` с прозрачностью `alpha=0.7`, что делает график визуально приятным.
- **Средняя линия**: Добавлена красная пунктирная линия, которая показывает среднюю зарплату на графике.
- **Легенда**: Легенда показывает значение средней зарплаты, что добавляет ясности.