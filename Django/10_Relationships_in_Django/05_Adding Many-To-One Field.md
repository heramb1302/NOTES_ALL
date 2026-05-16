
![[Pasted image 20260515160320.png]]

## Implementation :
**In posts (ORMandModels App)**

*models.py:*
```python
from django.db import models
# Create your models here.
class Posts(models.Model):

    post_title = models.CharField(max_length=200)
    post_content = models.TextField()
    published_date = models.DateField(auto_now=True)

    def __str__(self):
        return self.post_title

class Comments(models.Model):
  
    post = models.ForeignKey(Posts, on_delete=models.CASCADE)
    comment_content = models.TextField()
    published_date = models.DateField(auto_now=True)

    def __str__(self):
        return self.co
        mment_content
```