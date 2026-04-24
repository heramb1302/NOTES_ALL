

In [38]: d1 = Posts.objects.get(id=1)

In [39]: d1.delete()
Out[39]: (1, {'models.Posts': 1})
