
**This Admin is app which is automatic get install while created a project.**
**In Installed apps in seettings.py file :**
```  

INSTALLED_APPS = [

    'django.contrib.admin',
```

---
## Access Admin Panel :

### Open Terminal and try :
```
(env) PS C:\Users\heram\Documents\My Study\Django\ORMandModels_Workspace\ORMandModels> python .\manage.py createsuperuser
Username (leave blank to use 'heram'): heramb.shinde02@gmail.com
Email address: heramb.shinde02@gmail.com
Password: 
Password (again):
Superuser created successfully.

```

**Go to http://127.0.0.1:8000/admin/ and login with created account**

**In admin.py file of created app we can register the models**

```python

from django.contrib import admin
from .models import Posts

# Register your models here.
admin.site.register(Posts)
```

**After registering model we can see the model and liitle operations we can do with using ui interfafce: 

![[Pasted image 20260424124151.png]]

![[Pasted image 20260424124251.png]]

![[Pasted image 20260424124221.png]]

**The title is not showing on ui where we  register the posts. For that we nee d to make a change in models.py file just add str return statement :**
```python
from django.db import models
# Create your models here.

class Posts(models.Model):
    post_title = models.CharField(max_length=200)
    post_content = models.TextField()
    published_date = models.DateField(auto_now=True)

    def __str__(self):
        return self.post_title
```

**Before change : **
![[Pasted image 20260424123929.png]]
**After Change:**
![[Pasted image 20260424124003.png]]



## If we need the more control on the ui while printing the our model data : 

**We can make change in the admin.py:**
```python
from django.contrib import admin

from .models import Posts
# Registering the Posts model with custom admin view

@admin.register(Posts)
class PostsAdmin(admin.ModelAdmin):
    # Columns to display in the admin list view

    list_display = ('id', 'post_title', 'post_content', 'published_date')
    # Clickable fields to open the edit page
    list_display_links = ('id', 'post_title')

  
    #Sort by dates
    list_filter = ('published_date',)

    #We can search using id, title and content
    search_fields = ('id', 'post_title', 'post_content')

# Alternative registration for @admin.register(Posts): admin.site.register(Posts, PostsAdmin)
```


## If we want to change login header:
**In the urls.py file of app:**
```python
from django.contrib import admin
from django.urls import path
from django.urls import include
from . import views

urlpatterns = [
     path('posts/',views.posts,name='posts'),
 ]

  
# add These lines to access the headers and more attributes to control
admin.site.site_header = "Posts Admin"
admin.site.site_title = "Posts Admin"
admin.site.index_title = "Posts Admin"
```
**after doing above:**
![[Pasted image 20260424131213.png]]
![[Pasted image 20260424131237.png]]
