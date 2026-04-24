![[Pasted image 20260421161357.png]]


In [2]: from models.models import Posts

In [3]: data1 = Posts.objects.filter(id__gte=2)

In [4]: data1
Out[4]: <QuerySet [<Posts: Posts object (2)>, <Posts: Posts object (3)>]>

In [5]: data1[0].id
Out[5]: 2

In [6]: data1[1].id

---

In [7]: data2 = Posts.objects.filter(post_title__istartswith = "s")

In [8]: data2
Out[8]: <QuerySet [<Posts: Posts object (2)>]>

