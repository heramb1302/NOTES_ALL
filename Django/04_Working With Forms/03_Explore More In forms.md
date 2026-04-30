**in forms.py file in app : **

```python
from django import forms

  

class TeachersForm(forms.Form):

    name = forms.CharField(max_length=100)

    email = forms.EmailField()

    phone = forms.IntegerField()
    
```

```python

from django import forms

  

class TeachersForm(forms.Form):

    name = forms.CharField(max_length=100, label="Enter your name")

    email = forms.EmailField(label="Enter your email")

    phone = forms.IntegerField(label="Enter your phone")
```

# Accessing Form as Table:
```html

body>
    <h1>Teacher Home</h1>
    <form action="" method="POST">
        {% csrf_token %}
        <table>
            {{form.as_table}}
        </table>
        <input type="submit" value="Submit">
    </form>
</body>
```