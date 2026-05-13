![[Pasted image 20260509124718.png]]
![[Pasted image 20260509140517.png]]

# Defining relationship Implementation
**In models.py:**
```python
from django.db import models
# Create your models here.
class Husband(models.Model):
    name = models.CharField(max_length=100)

    def __str__(self):
        return self.name

class Wife(models.Model):
    name = models.CharField(max_length=100)
    husband = models.OneToOneField(Husband, on_delete=models.CASCADE)

    def __str__(self):
        return self.name
```


# Register The Model:

**admin.py**
```python
from django.contrib import admin

from .models import Husband, Wife

# Register your models here.

  
  

admin.site.register(Husband)

admin.site.register(Wife)
```