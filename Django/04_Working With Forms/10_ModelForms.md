```python
in forms.py

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
    # name = forms.CharField(max_length=100, label="Enter your name", widget=forms.TextInput(attrs={'class': 'form-control'}))

    # email = forms.EmailField(label="Enter your email", widget=forms.EmailInput(attrs={'class': 'form-control'}))

    # phone = forms.IntegerField(label="Enter your phone", widget=forms.NumberInput(attrs={'class': 'form-control'}))

    # bio = forms.CharField(widget=forms.Textarea(attrs={'class': 'form-control', 'rows': 5, 'cols': 50}))

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


**views.py:**

```python
from django.http import HttpResponseRedirect, HttpResponse
from django.shortcuts import render
from .forms import TeachersForm
from .models import Teachers

# Create your views here.

# This view handles the teacher registration form submission and validation.

def home(request):
    # Check if the request method is POST to handle form submission
    if request.method == 'POST':
        # Initialize the form with data from the POST request
        form = TeachersForm(request.POST)
        # Check if the form passes validation
        if form.is_valid():
            form.save()
            # Output success message to the console
            print("FORM IS VALID")
            # Print the cleaned data from the form
            print(form.cleaned_data)
            # Redirect the user to the thank you page
            return HttpResponseRedirect('/teacher/home')
    # If it is a GET request (first visit), create a blank form
    else:
        form = TeachersForm()
    # Render the home page with the form context
    # This now works for both first-time visits and invalid form submissions
    return render(request, 'teachers/teacher_home.html', {'form': form})

def thankyou(request):
    return HttpResponse("THANK YOU ...")
def teacher_list(request):
    teachers = Teachers.objects.all()
    return render(request, 'teachers/teachers_list.html', {'teachers': teachers})

def update_teacher(request, id):
    teacher = Teachers.objects.get(id=id)
    if request.method == 'POST':
        form = TeachersForm(request.POST)
        if form.is_valid():
            teacher.name = form.cleaned_data['name']
            teacher.email = form.cleaned_data['email']
            teacher.phone = form.cleaned_data['phone']
            teacher.bio = form.cleaned_data['bio']
            teacher.save()
            return HttpResponseRedirect('/teacher/list')

    form = TeachersForm(initial={'name': teacher.name, 'email': teacher.email, 'phone': teacher.phone, 'bio': teacher.bio})

    return render(request, 'teachers/teachers_update.html', {'teacher': teacher, 'form': form})

  

def delete_teacher(request, id):

    teacher = Teachers.objects.get(id=id)
    teacher.delete()
    return HttpResponseRedirect('/teacher/list')
```