In [59]: data2 = Posts.objects.filter(id=1) & Posts.objects.filter(post_content = "First Post Content")

In [60]: data2
Out[60]: <QuerySet [<Posts: Posts object (1)>]>

In [62]: data3 = Posts.objects.filter(id=1) | Posts.objects.filter(post_content = "Second Post Content")
In [63]: data3
Out[63]: <QuerySet [<Posts: Posts object (1)>, <Posts: Posts object (2)>]>