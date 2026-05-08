
**In main project.urls.py include the built in django url as:**
![[Pasted image 20260508143129.png]]
by using above url: we get all these available built in views 
![[Pasted image 20260508143638.png]]


**To call these view create a new app "registrations" and create templates also as login.html**

```html
{% extends 'accounts/base.html' %}

<h1>Login registration App</h1>

{% block title %}Login{% endblock title %}

  

{% block css %}

{% endblock css %}

  

{% block body %}

<form method="POST" action="">

    {% csrf_token %}

    {{form}}

    <button type="submit" class="btn btn-primary">Login</button>

</form>

  

<form action="{% url 'auth-logout' %}" method="POST">

    {% csrf_token %}

    <button type="submit" class="btn btn-danger">Logout</button>

</form>

{% endblock body %}
```


