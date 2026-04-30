```python
from django import forms

  

from django.core import validators

  

def start_s(value):

    if value[0] != 's' and value[0] != 'S':

        raise forms.ValidationError("Name should start with 's' check it")

  

class TeachersForm(forms.Form):

    name = forms.CharField(validators=[start_s], max_length=100, label="Enter your name", widget=forms.TextInput(attrs={'class': 'form-control'}))

    email = forms.EmailField(validators=[start_s],label="Enter your email", widget=forms.EmailInput(attrs={'class': 'form-control'}))

    phone = forms.IntegerField(label="Enter your phone", widget=forms.NumberInput(attrs={'class': 'form-control'}))

    bio = forms.CharField(widget=forms.Textarea(attrs={'class': 'form-control', 'rows': 5, 'cols': 50}))

    # error_messages = {

    #     'required': 'This field is required',

    #     'invalid': 'Enter a valid email',

    #     'max_length': 'Enter a valid phone number',

    #     'min_length': 'Enter a valid phone number',

    # }

  

    def clean (self):

        cleaned_data = super().clean()

        email = cleaned_data.get('email')

        phone = cleaned_data.get('phone')

        bio = cleaned_data.get('bio')

        if email == "":

            raise forms.ValidationError("Email is required type it")

        if phone == "":

            raise forms.ValidationError("Phone is required")

        if bio == "":

            raise forms.ValidationError("Bio is required")

        return cleaned_data
```