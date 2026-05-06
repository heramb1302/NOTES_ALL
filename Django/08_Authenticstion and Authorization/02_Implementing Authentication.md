**In django database we have auth_user table defaultlay, we going to use that table**

**In Django we have ready input form for register, just we have to use it by creating object like: 

***Create a view in app :***

```python
from django.shortcuts import render
from django.http import HttpResponse
from django.urls import reverse
from django.contrib.auth.forms import UserCreationForm

# Create your views here.

def register(request):
    if request.method == 'POST':
        form = UserCreationForm(request.POST)

        if form.is_valid():
            homepage_url = reverse('teacher_home')
            form.save()
            return HttpResponse(f"Registration successful! <a href='{homepage_url}'>Go to homepage</a>")

    else:
        form = UserCreationForm()

    return render(request, 'accounts/register.html', {'form': form})
```

**register.html:**

```html
{% extends 'accounts/base.html' %}

{% block body %}
    <h1>Register</h1>

    <form action="" method="post">
         {% csrf_token %}
         {{ form }}
        <button type="submit">Register</button>
    </form>

{% endblock body %}
```