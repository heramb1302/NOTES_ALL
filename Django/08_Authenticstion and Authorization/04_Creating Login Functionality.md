
![[Pasted image 20260507124617.png]]
![[Pasted image 20260507130320.png]]
![[Pasted image 20260507131014.png]]
![[Pasted image 20260507131537.png]]

*views.py*
```python
from django.shortcuts import render
from django.http import HttpResponse
from django.urls import reverse
from accounts.forms import RegisterForm
from django.contrib.auth.forms import AuthenticationForm
from django.contrib.auth import authenticate, login
# Create your views here.
def register(request):
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
    if request.method == 'POST':
        form = AuthenticationForm(request=request, data=request.POST)
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
        form = AuthenticationForm()
    return render(request, 'accounts/login.html', {'form': form})
```

*login.html*
```html
 {% extends 'accounts/base.html'%}
 {% block body %}
    <h1>Login</h1>
    <form method="POST">
        {% csrf_token %}
        {{ form }}
        <button type="submit">Login</button>
    </form>
{% endblock body %}
```