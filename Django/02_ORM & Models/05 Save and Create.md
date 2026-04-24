***python .\manage.py shell***
this allows to store data in table 
```in the terminal-->
***python .\manage.py shell***

 from models.models import Posts
 
 post1 = Posts(post_title="First Post Title",post_content="First Post Content")
 
  post1.save()
```


![[Pasted image 20260420124415.png]]
![[Pasted image 20260420124426.png]]

# Another Method:

in command:

: Posts.objects.create(post_title="Second Post Title",post_content="Second Post Content")

In [11]: from django.db import connection

In [12]: connection.queries

Posts.objects.all() -->

![[Pasted image 20260420154805.png]]

![[Pasted image 20260420154827.png]]
In [14]: data = Posts.objects.all()

In [15]: data [1]
Out[15]: <Posts: Posts object (2)>

In [16]: data
Out[16]: <QuerySet [<Posts: Posts object (1)>, <Posts: Posts object (2)>, <Posts: Posts object (3)>]>

In [17]: data[0]
Out[17]: <Posts: Posts object (1)>


In [21]: data[0].post_title
Out[21]: 'First Post Title'

