## Define a css file in a static fodler
```css
posts.css
body {

    background-color: aqua;

}
```

## Apply css :

```html
{% extends 'posts/base.html' %}

{% load static %}

{% block css %}

<link rel="stylesheet" href="{% static 'posts/post.css' %}">

{% endblock css %}

{% block body %}

<h1>{{post.title}}</h1>

<p>{{post.content}}</p>

<a href="{% url 'library' %}">Back to Library</a>

{% endblock body %}
```