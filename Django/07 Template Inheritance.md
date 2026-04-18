## Define a file eg [base.html]

```python
<!DOCTYPE html>

<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">

    <title>Document</title>
</head>
<body>
    <nav>
        <h1>Navebar</h1>
    </nav>
    
    {% block body %}
    {% endblock body %}
    
    <footer>Footer</footer>
</body>
</html>
```
## Inherit Like :
```python

{% extends 'posts/base.html' %}

{% block body %}

{% if posts %}

  

<h1>Welcome to Library {{username|capfirst|truncatechars:3}}</h1>

{% for post in posts %}

<h1>{{forloop.counter}}</h1>

<a href="{% url 'post' post.id %}">

    <h1>{{post.title|title}}:</h1>

</a>

<p>{{post.content|truncatewords:10}}</p>

  

{% endfor %}

{% elif posts|length == 0 %}

<h1>No posts found</h1>

{% else %}

<h1>No posts found</h1>

{% endif %}

{% endblock body %}

```