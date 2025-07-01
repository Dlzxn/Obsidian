![[ChatGPT Image 20 апр. 2025 г., 17_18_01.png]]


**Основная структура - DataFrame**

```python
impot pandas as pd

pd.DataFrame()
```

Аргументы:
---

*1)* data - значение самого DaraFrame
Может быть представлен по-разному

```python
{
"car": ["Ford", "Mitsubishi", "BMW"]
}

или:

{
"car":
	{
	"BMW": 5
	}
}

P.s. Так же может быть NumPy массив
```

*2)* index

Определяет метки (названия) строк.

Примеры:

```python
pd.DataFrame({"a": [1, 2]}, index=["первая", "вторая"])`

Если не указать — будет [0, 1, 2, ...] по умолчанию.
```


*3)* Columns 

Определяет имена столбцов, в том порядке, в каком ты хочешь.
```python
pd.DataFrame([[1, 2], [3, 4]], columns=["X", "Y"])`

Если не указать — будут 0, 1, 2... по умолчанию (если data без имён).
```

*4)* dtype

Ты можешь задать **один тип данных** для всего DataFrame (все ячейки будут приведены к нему, если возможно):

```python

pd.DataFrame({"a": [1, 2], "b": [3, 4]}, dtype=float)`

Обычно pandas сам определяет типы данных в столбцах (`int64`, `float64`, `object`, `bool`, и т.д.).
```

*5)* copy

По умолчанию False

Если `True` — создаётся копия входных данных, даже если они уже DataFrame. Обычно `False`, чтобы не расходовать память зря.

```python
df2 = pd.DataFrame(df1, copy=True)
```


Манипуляции над DataFrame
--
### ⚠️ Важно:
Некоторые методы по умолчанию **возвращают новый DataFrame**, а не меняют исходный. Чтобы изменить "на месте", часто нужно передать inplace=True.


```python
df2 = df.copy() # копирование DataFrame

P.s. создается именное копия ДатаФрейма, т е мы можем именять исходный и не получим изменения нового

df2 = df - НЕПРАВИЛЬНО(т к передается просто ссылка на обьект)
```


```python
df["name"] = ["Egor", "Sasha"]
#происходят изменения именно в названии столбца "name"
```

```python
df["surname"] = ["Dlzxn", "Dev"] #добавление нового столбца
```

```python
df.loc[0, "name"] = "Kolya" #вносим изменения по адресу нулевого индекса в стообце "name"
```

```python
df.drop("money", axis=1, inplace=True) #удаление столбца
df.drop([0, 1], axis=1, inplace=True) #удаление по индексам
```

```python
df.loc[len(df)] = (["Ivan", 34, 23000]) #добавление строк
```

```python
df = df.T #транспонирование (т е строки -> столбцы)
```

```python
df = df.sort_values("money") #сортировка по столбцу "money" по возрастанию
```


### **Объединение и слияние**

- **Конкатенация**:  
    `pd.concat([df1, df2], axis=0)`
    
- **Слияние** (merge):  
    `df1.merge(df2, on='id')`
    
- **Присоединение** (join):  
    `df1.join(df2, lsuffix='_left')`

Вывод данных
--

```python
anime.head(3) #вывод первых трех значений

rating.tail(1) #вывод последнего значения
```

```python
a.info() #выводит всю информацию о ДатаФрейме

--------ПРИМЕР----------------

<class 'pandas.core.frame.DataFrame'>
Index: 2 entries, 0 to 1
Data columns (total 3 columns):
 #   Column  Non-Null Count  Dtype 
---  ------  --------------  ----- 
 0   name    2 non-null      object
 1   age     2 non-null      object
 2   money   2 non-null      object
dtypes: object(3)
memory usage: 64.0+ bytes
None

```

