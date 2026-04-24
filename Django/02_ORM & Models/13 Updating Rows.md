### Update Single Row : 

In [22]: data1 = Posts.objects.get(id=1)

In [23]: data1.post_title = "Fisrt"

In [24]: data1.save()
In [33]: Posts.objects.filter(id=1).update(post_title="First")
Out[33]: 1
### Updating Multiple Row
In [30]: data = Posts.objects.all()

In [31]: data.update(post_title = "Post Title")
Out[31]: 3