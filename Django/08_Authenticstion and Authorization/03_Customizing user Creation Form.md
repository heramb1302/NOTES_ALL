
**Create a forms.py file in app(eg --> accounts)**

*forms.py*
```python
from django.contrib.auth.forms import UserCreationForm
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
```

*register.html*
```html
{% extends 'accounts/base.html' %}

{% block body %}
    <h1>Register</h1>
    <form action="" method="post">
         {% csrf_token %}
         {% for field in form %}
            <div class="mb-3">
                {{ field.label_tag }}
                {{ field }}
                {% if field.errors %}
                    <div class="text-danger">
                        {% for error in field.errors %}
                            {{ error }}
                        {% endfor %}
                    </div>
                {% endif %}
            </div>
         {% endfor %}
        <button type="submit">Register</button>
    </form>
{% endblock body %}
```

*views.py*
```python
from django.shortcuts import render
from django.http import HttpResponse
from django.urls import reverse
from accounts.forms import RegisterForm
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
```
