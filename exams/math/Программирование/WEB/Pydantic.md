source: [[Программирование/Python/Python|Python]]
tegs: #python #программирование
**Pydantic** — это библиотека в Python, которая используется для проверки, обработки и сериализации данных. Она идеально подходит для работы с данными в таких фреймворках, как FastAPI, где требуется строгая проверка входящих данных. Вот основные моменты, которые объясняют, зачем нужен Pydantic:

---

### 1. **Валидация данных**

Pydantic автоматически проверяет данные на соответствие типам, которые ты указал в модели. Если данные не соответствуют, Pydantic выдает ошибку.

Пример:

```python
from pydantic import BaseModel

class User(BaseModel):
    name: str
    age: int

# Проверяем данные
data = {"name": "Alice", "age": "25"}  # Возраст передан как строка
user = User(**data)  # Pydantic автоматически преобразует строку "25" в число
print(user)
```

Вывод:

```python
name='Alice' age=25
```

Если передать некорректные данные (например, `age="abc"`), Pydantic выбросит ошибку.

---

### 2. **Автоконвертация типов**

Pydantic умеет автоматически преобразовывать данные в указанные типы, если это возможно. Например:

```python
data = {"name": "Bob", "age": "30"}
user = User(**data)
print(user.age)  # Pydantic преобразует "30" в 30
```

---

### 3. **Простое создание моделей данных**

Pydantic позволяет создавать структуры данных (модели), которые похожи на объекты Python, но с добавленной валидацией и обработкой типов. Это очень удобно для работы с JSON-данными.

---

### 4. **Работа с FastAPI**

В FastAPI Pydantic используется для описания входящих данных в запросах. Например:

```python
from fastapi import FastAPI
from pydantic import BaseModel

app = FastAPI()

class Item(BaseModel):
    name: str
    price: float
    is_offer: bool = None  # Значение по умолчанию

@app.post("/items/")
async def create_item(item: Item):
    return {"item_name": item.name, "item_price": item.price}
```

Если клиент отправит запрос с некорректными данными, FastAPI автоматически ответит с ошибкой, объясняющей, что именно не так.

---

### 5. **Преобразование в JSON и из JSON**

Pydantic поддерживает сериализацию (преобразование модели в JSON) и десериализацию (из JSON обратно в модель). Например:

```python
user = User(name="Alice", age=25)
json_data = user.json()  # Преобразование в JSON
print(json_data)  # '{"name": "Alice", "age": 25}'
```

---

### 6. **Расширяемость**

Ты можешь добавлять свои проверки с помощью валидаторов. Например:

```python
from pydantic import BaseModel, validator

class Product(BaseModel):
    name: str
    price: float

    @validator("price")
    def price_must_be_positive(cls, value):
        if value <= 0:
            raise ValueError("Цена должна быть больше нуля!")
        return value
```

---

### Вывод

Pydantic:

- Проверяет данные.
- Автоматически преобразует типы.
- Работает с FastAPI для обработки входящих запросов.
- Помогает работать с JSON.
- Упрощает жизнь, делая код чистым и надежным.

Если хочешь разбирать Pydantic на примерах или понять конкретный кейс, пиши! 😊