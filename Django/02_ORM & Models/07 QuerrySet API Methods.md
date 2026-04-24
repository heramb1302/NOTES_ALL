In [43]: data = Posts.objects.all()

In [44]: data.order_by('id')
Out[44]: <QuerySet [<Posts: Posts object (1)>, <Posts: Posts object (2)>, <Posts: Posts object (3)>]>

In [45]: data.order_by('-id')
Out[45]: <QuerySet [<Posts: Posts object (3)>, <Posts: Posts object (2)>, <Posts: Posts object (1)>]>


In [48]: data.values()
Out[48]: <QuerySet [{'id': 1, 'post_title': 'First Post Title', 'post_content': 'First Post Content', 'published_date': datetime.date(2026, 4, 20)}, {'id': 2, 'post_title': 'Second Post Title', 'post_content': 'Second Post Content', 'published_date': datetime.date(2026, 4, 20)}, {'id': 3, 'post_title': 'Third Post Title', 'post_content': 'Third Post Content', 'published_date': datetime.date(2026, 4, 20)}]>



In [49]: data.count()
Out[49]: 3


In [51]: data.filter(id=2).count()
Out[51]: 1

In [54]: d1 = Posts.objects.get(id=1)
In [56]: data.contains(d1)
Out[56]: True

In [57]: data.first()
Out[57]: <Posts: Posts object (1)>

In [58]: data.last()
Out[58]: <Posts: Posts object (3)>

