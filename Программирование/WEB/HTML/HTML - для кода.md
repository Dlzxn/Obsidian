
source:  [[WEB-программирование]]
tegs: #web #programming
-------**СТАТИКА**
{% load static %}

пример:
"{% static 'vendor/bootstrap/css/bootstrap.min.css' %}"


-------**ПЕРЕМЕННЫЕ**
{{ title }}



------**ПЕРЕХОД ПРИ НАЖАТИИ**

href="{% url 'products:index' %}"

-----**БЛОКИ**

{% block content %}  
  
{% endblock %}


------**НАСЛЕДОВАНИЕ**
{% extends 'users/base.html' %}


-------**ДЛЯ POST ЗАПРОСА ЗАЩИТА**
{% csrf_token %}


------**ВОЗВРАТ ДАННЫХ**

action="{% url 'users:login' %}