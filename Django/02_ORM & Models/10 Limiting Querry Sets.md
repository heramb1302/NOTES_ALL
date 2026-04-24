### The Limiting querry sets is most similar to list slicing in python 


In [6]: data = Posts.objects.all()

In [7]: data
Out[7]: <QuerySet [<Posts: Posts object (1)>, <Posts: Posts object (2)>, <Posts: Posts object (3)>]>

In [8]: data[::-1]
Out[8]: 
[<Posts: Posts object (3)>,
 <Posts: Posts object (2)>,
 <Posts: Posts object (1)>]

In [9]: data[1::]
Out[9]: <QuerySet [<Posts: Posts object (2)>, <Posts: Posts object (3)>]>


