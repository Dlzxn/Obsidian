source: [[SQL-запросы]]
tegs: #SQL
# PostgreSQL SQL Команды

## 1. Подключение к PostgreSQL
```sql
psql -U username -d database_name
```

## 2. Управление базами данных

### Просмотр списка баз данных
```sql
\l
```

### Создание новой базы данных
```sql
CREATE DATABASE database_name;
```

### Подключение к базе данных
```sql
\c database_name
```

### Удаление базы данных
```sql
DROP DATABASE database_name;
```

---

## 3. Работа с таблицами

### Просмотр списка таблиц
```sql
\dt
```

### Создание таблицы
```sql
CREATE TABLE table_name (
    id SERIAL PRIMARY KEY,
    name VARCHAR(50) NOT NULL,
    age INT,
    created_at TIMESTAMP DEFAULT NOW()
);
```

### Просмотр структуры таблицы
```sql
\d table_name
```

### Удаление таблицы
```sql
DROP TABLE table_name;
```

### Очистка таблицы
```sql
TRUNCATE TABLE table_name;
```

---

## 4. Работа с данными

### Вставка данных
```sql
INSERT INTO table_name (name, age) VALUES ('John', 30);
```

### Обновление данных
```sql
UPDATE table_name SET age = 35 WHERE name = 'John';
```

### Удаление данных
```sql
DELETE FROM table_name WHERE name = 'John';
```

### Выборка данных
```sql
SELECT * FROM table_name;
```

### Выборка с условием
```sql
SELECT * FROM table_name WHERE age > 25;
```

---

## 5. Работа с индексами

### Создание индекса
```sql
CREATE INDEX idx_name ON table_name (name);
```

### Удаление индекса
```sql
DROP INDEX idx_name;
```

---

## 6. Управление пользователями

### Создание пользователя
```sql
CREATE USER username WITH PASSWORD 'password';
```

### Изменение пароля пользователя
```sql
ALTER USER username WITH PASSWORD 'new_password';
```

### Удаление пользователя
```sql
DROP USER username;
```

### Предоставление прав
```sql
GRANT ALL PRIVILEGES ON DATABASE database_name TO username;
```

### Отзыв прав
```sql
REVOKE ALL PRIVILEGES ON DATABASE database_name FROM username;
```

---

## 7. Работа с транзакциями

### Начало транзакции
```sql
BEGIN;
```

### Подтверждение транзакции
```sql
COMMIT;
```

### Откат транзакции
```sql
ROLLBACK;
```

---

## 8. Работа с резервными копиями

### Создание резервной копии базы данных
```bash
pg_dump -U username -d database_name -F c -f backup.dump
```

### Восстановление базы данных из резервной копии
```bash
pg_restore -U username -d database_name backup.dump
```

---

## 9. Выход из PostgreSQL
```sql
\q
