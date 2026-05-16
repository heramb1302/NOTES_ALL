

![[Pasted image 20260515163138.png]]

models.py:
ORMModels APP

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

        return self.comment_content

  

class Tag(models.Model):

  

    tag_name = models.CharField(max_length=50)

    posts = models.ManyToManyField(Posts, related_name='tags')

  
  

    def __str__(self):

        return self.tag_name
```

# Querying :
```
>>> from models.models import Posts, Comments, Tag
>>> Posts=Posts.objects,all()
Traceback (most recent call last):
  File "<console>", line 1, in <module>
TypeError: all() takes exactly one argument (0 given)
>>> Posts=Posts.objects.all()
>>> Posts[0].post_title
'Post Title 2'
>>> Posts[0].tag       
Traceback (most recent call last):
  File "<console>", line 1, in <module>
AttributeError: 'Posts' object has no attribute 'tag'. Did you mean: 'tags'?
>>> Posts[0].tags
<django.db.models.fields.related_descriptors.create_forward_many_to_many_manager.<locals>.ManyRelatedManager object at 0x0000021809C678C0>
>>> Posts[0].tags.all()
<QuerySet [<Tag: t1>]>
>>>
```