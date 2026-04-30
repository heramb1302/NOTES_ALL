```python
from unicodedata import name
from django import forms
from django.core import validators
from .models import Teachers


def start_s(value):
    if value[0] != 's' and value[0] != 'S':
        raise forms.ValidationError("Name should start with 's' check it")
class TeachersForm(forms.ModelForm):
    class Meta:
        model = Teachers
        fields = ['name','email','phone','bio']
        labels = {
            'name':'Your name',
            'email':'Your Email',
            'phone':'Contact',
            'bio':'Enter Details'
        }

        widgets = {
            'name': forms.TextInput(attrs={'class':"form-control"})
        }

        help_texts ={
            'email':"Pls Enter Email/Gmail value"
        }

        error_messages = {
            'name' : {
                'required':'Pls Enter Valid name'
            }
        }
```