source:  [[WEB-программирование]]
tegs: #web #programming

```markdown
# Схема создания и деплоя API на Flask

## 1. Подготовка сервера
1. Обновите систему и установите зависимости:
   ```bash
   sudo apt update && sudo apt upgrade -y
   sudo apt install python3 python3-venv python3-pip nginx -y
```

2. Создайте директорию для проекта:
    
    ```bash
    sudo mkdir -p /var/www/api
    cd /var/www/api
    ```
    
3. Настройте виртуальное окружение:
    
    ```bash
    python3 -m venv venv
    source venv/bin/activate
    pip install flask gunicorn
    ```
    

---

## 2. Написание кода API

1. Создайте файл `/var/www/api/app.py` со следующим содержимым:
    
    ```python
    from flask import Flask
    
    app = Flask(__name__)
    
    @app.route('/')
    def index():
        return "Hello, World!"
    
    if __name__ == '__main__':
        app.run()
    ```
    
2. Настройте права доступа:
    
    ```bash
    sudo chown -R www-data:www-data /var/www/api
    sudo chmod -R 750 /var/www/api
    ```
    

---

## 3. Настройка Gunicorn

1. Проверьте запуск приложения с Gunicorn:
    
    ```bash
    /var/www/api/venv/bin/gunicorn --workers 3 --bind unix:/var/www/api/flask_api.sock app:app
    ```
    
2. Создайте Unit-файл для systemd: `/etc/systemd/system/flask_api.service`:
    
    ```ini
    [Unit]
    Description=Gunicorn instance to serve Flask API
    After=network.target
    
    [Service]
    User=www-data
    Group=www-data
    WorkingDirectory=/var/www/api
    ExecStart=/var/www/api/venv/bin/gunicorn --workers 3 --bind unix:/var/www/api/flask_api.sock app:app
    
    [Install]
    WantedBy=multi-user.target
    ```
    
3. Перезагрузите systemd и запустите сервис:
    
    ```bash
    sudo systemctl daemon-reload
    sudo systemctl start flask_api
    sudo systemctl enable flask_api
    ```
    

---

## 4. Настройка Nginx

1. Создайте конфигурацию: `/etc/nginx/sites-available/flask_api`:
    
    ```nginx
    server {
        listen 80;
        server_name your_domain_or_IP;
    
        location / {
            include proxy_params;
            proxy_pass http://unix:/var/www/api/flask_api.sock;
        }
    }
    ```
    
2. Активируйте конфигурацию:
    
    ```bash
    sudo ln -s /etc/nginx/sites-available/flask_api /etc/nginx/sites-enabled
    sudo nginx -t
    sudo systemctl restart nginx
    ```
    

---

## 5. Проверка работы

1. Проверьте статус сервисов:
    
    ```bash
    sudo systemctl status flask_api
    sudo systemctl status nginx
    ```
    
2. Убедитесь, что API доступно по вашему IP:
    
    ```bash
    curl http://your_domain_or_IP
    ```
    

---

## 6. Отладка ошибок

- **502 Bad Gateway:** Убедитесь, что `flask_api.sock` существует и имеет правильные права:
    
    ```bash
    sudo chown www-data:www-data /var/www/api/flask_api.sock
    sudo chmod 660 /var/www/api/flask_api.sock
    ```
    
- **Permission denied:** Проверьте права доступа:
    
    ```bash
    sudo chown -R www-data:www-data /var/www/api
    sudo chmod -R 750 /var/www/api
    ```
    
- **Gunicorn не запускается:** Проверьте, установлен ли Gunicorn:
    
    ```bash
    /var/www/api/venv/bin/pip install gunicorn
    ```
    
- **Nginx не работает:** Убедитесь, что конфигурация корректна:
    
    ```bash
    sudo nginx -t
    sudo systemctl restart nginx
    ```
    

---

## 7. Обновление API

1. Измените файл `app.py`.
2. Перезагрузите сервис:
    
    ```bash
    sudo systemctl restart flask_api
    ```