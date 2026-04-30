```python

from django import forms
class TeachersForm(forms.Form):
    name = forms.CharField(max_length=100, label="Enter your name")
    email = forms.EmailField(label="Enter your email")
    phone = forms.IntegerField(label="Enter your phone")
    bio = forms.CharField(widget=forms.Textarea(attrs={'rows': 5, 'cols': 50}))
    error_messages = {

        'required': 'This field is required',

        'invalid': 'Enter a valid email',

        'max_length': 'Enter a valid phone number',

        'min_length': 'Enter a valid phone number',

    }
```