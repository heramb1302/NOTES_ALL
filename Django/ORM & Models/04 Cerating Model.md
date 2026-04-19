

# In models.py file in App created

```python

from django.db import models
# Create your models here.
class Posts(models.Model):

    post_title = models.CharField(max_length=200)
    post_content = models.TextField()
    published_date = models.DateTimeField(auto_now=True)
```


# Migrations : 

![[Pasted image 20260419154327.png]]
## Work Flow :

![[Pasted image 20260419154412.png]]

***python .\manage.py makemigrations***
***python .\manage.py sqlmigrate models 0001***
***python .\manage.py migrate *** 


![[Pasted image 20260419155254.png]]


![[Pasted image 20260419155324.png]]
![[Pasted image 20260419155606.png]]
