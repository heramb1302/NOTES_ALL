in urlpatterns:
give name to url
```
    path('library/',views.library, name='library'),
    path('<int:id>/', views.post, name='post'),
```

in html:
```python

post.html
<body>

    <h1>{{post.title}}</h1>

    <p>{{post.content}}</p>

    <a href="{% url 'library' %}">Back to Library</a>

</body>
```

```python
library.html

<body>

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

</body>

```