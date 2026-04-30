**First Create the model**
**In views.py file of app Import the model and create the row**
```python 
views.py Teachers App
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
            name = form.cleaned_data['name']
            email = form.cleaned_data['email']
            phone = form.cleaned_data['phone']
            bio = form.cleaned_data['bio']
            Teachers.objects.create(name=name, email=email, phone=phone, bio=bio)
            # Output success message to the console
            print("FORM IS VALID")
            # Print the cleaned data from the form
            print(form.cleaned_data)
            # Redirect the user to the thank you page
            return HttpResponseRedirect('/teacher/thankyou')
    # If it is a GET request (first visit), create a blank form
    else:
        form = TeachersForm()
    # Render the home page with the form context
    # This now works for both first-time visits and invalid form submissions
    return render(request, 'teachers/teacher_home.html', {'form': form})
	def thankyou(request):

	    return HttpResponse("THANK YOU ...")
```

```html
<body>
    <h1>Teacher Home</h1>
    <div>
        {{form.non_field_errors}}
        <form action="" method="POST">
            {% csrf_token %}

            {% for field in form %}

            <div>
                {{field.label_tag}}
                {{field}}
                {% for error in field.errors %}
                <div>{{error}}</div>
                {% endfor %}
            </div>
            <br><br>
            {% endfor %}
            <input type="submit" value="Submit">

        </form>
    </div>
    <a href="{% url 'teacher_list' %}">View Teachers List</a>

</body>
```