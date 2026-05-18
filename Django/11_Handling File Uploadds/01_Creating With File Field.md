
# 1 Create the model:
model.py
```python
from django.db import models
# Create your models here.

class UserData(models.Model):
    name = models.CharField(max_length=100)
    file = models.FileField(upload_to='uploads/')

    def __str__(self):
        return self.name
```

# 2 Create model form for same:

forms.py:
```python
from django import forms
from .models import UserData

	class UserDataForm(forms .ModelForm):

    class Meta:
        model = UserData
        fields = '__all__'
```

# 3 Create the view for  respond that form :

views.py:
```python
from django.shortcuts import render
from django.http import HttpResponse, HttpResponseRedirect
from .forms import UserDataForm
# Create your views here.
def home(request):  

    if request.method == 'POST':
        form = UserDataForm(request.POST, request.FILES)

        if form.is_valid():
            form.save()
            return HttpResponseRedirect('/f/home/')

    else:
        form = UserDataForm()
        return render(request, 'fileuploads/home.html', {'form': form})
```

# 4 Create the HTML page to display form:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>File Upload Home Page</title>

</head>
<body>
    <form action="" method="POST" enctype="multipart/form-data">
        {% csrf_token %}
        {{ form}}
        <button type="submit">Upload</button>
    </form>
</body>
</html>
```

# 5 In settings.py file  create the variable to store media (path) :

```python

#MEDIA SETTINGS
MEDIA_ROOT = BASE_DIR / 'media'
```

# 6 All files will store in media/uploads folder

# 7 To store only image in models.py :
*use file = models.ImageField(upload_to='uploads/')*