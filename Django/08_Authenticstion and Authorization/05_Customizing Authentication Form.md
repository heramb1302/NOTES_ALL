*Forms.py*(accounts app)
```python
from django.contrib.auth.forms import UserCreationForm, AuthenticationForm, UsernameField
from django.contrib.auth.models import User
from django import forms

class RegisterForm(UserCreationForm):

    email = forms.EmailField(required=True, widget=forms.EmailInput(attrs={'placeholder': 'Email', 'class': 'form-control'}))

    first_name = forms.CharField(max_length=50, required=True, widget=forms.TextInput(attrs={'placeholder': 'First Name', 'class': 'form-control'}))

    last_name = forms.CharField(max_length=50, required=True, widget=forms.TextInput(attrs={'placeholder': 'Last Name', 'class': 'form-control'}))

    password1 = forms.CharField(widget=forms.PasswordInput(attrs={'placeholder': 'Password', 'class': 'form-control'}))

    password2 = forms.CharField(widget=forms.PasswordInput(attrs={'placeholder': 'Confirm Password', 'class': 'form-control'}))

    class Meta:
        model = User
        fields = ['username', 'email', 'first_name', 'last_name', 'password1', 'password2']

        widgets = {
            'username': forms.TextInput(attrs={'placeholder': 'Username', 'class': 'form-control'}),
        }

class LoginForm(AuthenticationForm):
    username = UsernameField(max_length=254, widget=forms.TextInput(attrs={'placeholder': 'Username', 'class': 'form-control'}))

    password = UsernameField(widget=forms.PasswordInput(attrs={'placeholder': 'Password', 'class': 'form-control'}))
```

*views.py*
```python
from django.shortcuts import render
from django.http import HttpResponse
from django.urls import reverse
from accounts.forms import RegisterForm, LoginForm
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
```

*login.html*
```html
 {% extends 'accounts/base.html'%}

  

{% block css %}

{% endblock css %}

 {% block body %}

    <h1>Login</h1>

    <form method="POST">

        {% csrf_token %}

        {{ form}}    

        <button type="submit" class="btn btn-primary">Login</button>

    </form>

{% endblock body %}
```
