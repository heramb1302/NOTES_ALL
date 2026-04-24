![[Pasted image 20260420155427.png]]


![[Pasted image 20260420155439.png]]

In [22]: Posts.objects.get(id=1)
Out[22]: <Posts: Posts object (1)>
In [23]: d1 = Posts.objects.get(id=1)
In [28]: d1.post_title
Out[28]: 'First Post Title'



![[Pasted image 20260420160740.png]]
In [34]: d2 = Posts.objects.filter(id=2)
In [35]: d2[0].post_title
Out[35]: 'Second Post Title'



![[Pasted image 20260420161007.png]]

In [36]: d3 = Posts.objects.exclude(id=2)

In [37]: d3
Out[37]: <QuerySet [<Posts: Posts object (1)>, <Posts: Posts object (3)>]>

In [38]: d3[0].post_title
Out[38]: 'First Post Title'



