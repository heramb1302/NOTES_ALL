
*forms.py*
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

*views.py*(accounts)
```python
from django.shortcuts import render

from django.http import HttpResponse

from django.urls import reverse

from accounts.forms import RegisterForm, LoginForm

from django.contrib.auth import authenticate, login

  

# Create your views here.

def register(request):

    if request.user.is_authenticated:

        return HttpResponse(f"You are already registered and logged in as {request.user.username}.")

    else:

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

    if request.user.is_authenticated:

        return HttpResponse(f"You are already logged in as {request.user.username}.")

    else:

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

## Also we can restrict the pages to show only authenticated users **For teachers/home:**

*views.py* of teachers app
```python
from django.http import HttpResponseRedirect, HttpResponse
from django.shortcuts import render
from .forms import TeachersForm
from .models import Teachers
# Create your views here.
# This view handles the teacher registration form submission and validation.
def home(request):
    if not request.user.is_authenticated:
        return HttpResponseRedirect('/accounts/login')
    else:
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
                return HttpResponseRedirect('/')
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
    # Fetch the specific teacher instance
    teacher = Teachers.objects.get(id=id)
    if request.method == 'POST':
        # Pass the 'teacher' INSTANCE, not the 'Teachers' class
        form = TeachersForm(request.POST, instance=teacher)
        if form.is_valid():
            # Save the form, which updates and saves the teacher instance
            form.save()
            return HttpResponseRedirect('/teacher/list')
    else:
        # Pass the 'teacher' INSTANCE so the form can populate initial values
        form = TeachersForm(instance=teacher)
    return render(request, 'teachers/teachers_update.html', {'teacher': teacher, 'form': form})
  
def delete_teacher(request, id):
    teacher = Teachers.objects.get(id=id)
    teacher.delete()
    return HttpResponseRedirect('/teacher/list')
```

