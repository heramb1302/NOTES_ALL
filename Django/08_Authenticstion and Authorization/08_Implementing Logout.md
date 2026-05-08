
![[Pasted image 20260508124917.png]]

*views.py*
```python
from django.shortcuts import render
from django.http import HttpResponse
from django.urls import reverse
from accounts.forms import RegisterForm, LoginForm
from django.contrib.auth import authenticate, login, logout

  

# Create your views here.

def register(request):

    if request.user.is_authenticated:

        return HttpResponse(f"You are already registered and logged in as {request.user.username}.")

    else:

        if request.method == 'POST':

            form = RegisterForm(request.POST)

            if form.is_valid():

                homepage_url = reverse('teacher_home')

                form.save()

                return HttpResponse(f"Registration successful! <a href='{homepage_url}'>Go to homepage</a>")

        else:

            form = RegisterForm()

        return render(request, 'accounts/register.html', {'form': form})

  

def auth_login(request):

    if request.user.is_authenticated:

        return HttpResponse(f"You are already logged in as {request.user.username}.")

    else:

        if request.method == 'POST':

            form = LoginForm(request=request, data=request.POST)

            if form.is_valid():

                username = form.cleaned_data.get('username')

                password = form.cleaned_data.get('password')

                user = authenticate(request=request, username=username, password=password)

                print(user)

                if user is not None:

                    login(request, user)

                    return HttpResponse(f"Login successful! Welcome, {username}!")

                else:

                    return HttpResponse("Invalid username or password.")

        else:

            form = LoginForm()

        return render(request, 'accounts/login.html', {'form': form})

def login_register(request):

    return render(request, 'accounts/login_register.html')

  

def auth_logout(request):

    logout(request)

    return render(request, 'accounts/login_register.html')
```

```html
{% extends 'accounts/base.html' %}
{% block title %}Login or Register{% endblock title %}
  

{% block css %}

{% endblock css %}

  

{% block body %}

    <div class="container">

        {% if not user.is_authenticated %}

            <a href="{% url 'login' %}" class="btn btn-primary">Login</a>

            <a href="{% url 'register' %}" class="btn btn-secondary">Register</a>

        {% else %}

            <h2>Welcome, {{ user }}!</h2>

            <a href="{% url 'logout' %}" class="btn btn-danger">Logout</a>

         {% endif %}

  

    </div>

{% endblock body %}
```

