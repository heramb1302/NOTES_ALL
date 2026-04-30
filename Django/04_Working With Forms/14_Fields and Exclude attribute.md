**forms.py**
```python
from unicodedata import name
from django import forms
from django.core import validators
from .models import Teachers

  

def start_s(value):
    if value[0] != 's' and value[0] != 'S':
        raise forms.ValidationError("Name should start with 's' check it")

class TeachersForm(forms.ModelForm):

    name = forms.CharField(validators=[validators.MaxLengthValidator(10)])

  

    class Meta:
        model = Teachers
        #fields = ['name','email','phone','bio']
        fields = '__all__'
        exclude = ['email']
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
    # def clean (self):

    #     cleaned_data = super().clean()

    #     email = cleaned_data.get('email')

    #     phone = cleaned_data.get('phone')

    #     bio = cleaned_data.get('bio')

    #     if email == "":

    #         raise forms.ValidationError("Email is required type it")

    #     if phone == "":

    #         raise forms.ValidationError("Phone is required")

    #     if bio == "":

    #         raise forms.ValidationError("Bio is required")

    #     return cleaned_data

  

    # name = forms.CharField(max_length=100, label="Enter your name", widget=forms.TextInput(attrs={'class': 'form-control'}))

    # email = forms.EmailField(label="Enter your email", widget=forms.EmailInput(attrs={'class': 'form-control'}))

    # phone = forms.IntegerField(label="Enter your phone", widget=forms.NumberInput(attrs={'class': 'form-control'}))

    # bio = forms.CharField(widget=forms.Textarea(attrs={'class': 'form-control', 'rows': 5, 'cols': 50}))
```