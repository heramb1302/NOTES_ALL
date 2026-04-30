
### Create a forms.py file in app
```python
from django import forms
class TeachersForm(forms.Form):
    name = forms.CharField(max_length=100)
```

### Import this file in views.py
```python
from django.shortcuts import render
from .forms import TeachersForm
# Create your views here.

def home(request):
    form = TeachersForm()
    return render(request, 'teachers/teacher_home.html', {'form': form})
```

```html

<body>
    <h1>Teacher Home</h1>
    <form action="">
        {{form}}
        <input type="submit" value="Submit">
    </form>

</body>
```

# GET AND POST METHODS:

![[Pasted image 20260425114339.png]]


## GET Method:

```html
<body>
    <h1>Teacher Home</h1>
    <form action="" method="POST">
        {{form}}
        <input type="submit" value="Submit">
    </form>
</body>
```

# CSRF Attack:

![[Pasted image 20260425114915.png]]
![[Pasted image 20260425114955.png]]
```html
<body>
    <h1>Teacher Home</h1>
    <form action="" method="POST">
        {% csrf_token %}
        {{form}}
        <input type="submit" value="Submit">
    </form>
</body>
```

# Handle form:

**We have to handle the request in view : **

```python
Teacher view.py
from django.http import HttpResponseRedirect, HttpResponse
from django.shortcuts import render
from .forms import TeachersForm

# Create your views here.
# This view handles the teacher registration form submission and validation.

def home(request):
    # Check if the request method is POST to handle form submission
    if request.method == 'POST':
        # Initialize the form with data from the POST request
        form = TeachersForm(request.POST)
        # Check if the form passes validation
        if form.is_valid():
            # Output success message to the console
            print("FORM IS VALID")
            # Print the cleaned data from the form
            print(form.cleaned_data)
            # Redirect the user to the thank you page
            return HttpResponseRedirect('/teacher/thankyou')
        # Handle cases where the form is not valid or reset the form
        else:
            form = TeachersForm()
        # Render the home page with the form context
        return render(request, 'teachers/teacher_home.html', {'form': form})

def thankyou(request):
    return HttpResponse("THANK YOU ...")
```
