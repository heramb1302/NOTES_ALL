**1. In settings.py file create a variable**
```python
#MEDIA SETTINGS

MEDIA_ROOT = BASE_DIR / 'media'

MEDIA_URL = '/media/'
```

**2 . In main app urls.py:**
```python
from django.contrib import admin
from django.urls import path, include
from django.conf.urls.static import static
from django.conf import settings

urlpatterns = [
    path('admin/', admin.site.urls),
    path('f/', include('fileuploads.urls')),
] + static(settings.MEDIA_URL, document_root=settings.MEDIA_ROOT)
```
**3. Create the view**
```python
def server(request):

    userdata = UserData.objects.all()

    return render(request, 'fileuploads/server.html', {'userdata': userdata})
```
**4 . Create the html**
```html
</head>
<body>
    <div>
        {% for data in userdata %}
        <h1>{{ data.name }}</h1>
        <img src="{{ data.file.url }}" alt="" width="200px" height="200px">
        {% endfor %}
    </div>
</body>
</html>
```