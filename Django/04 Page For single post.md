
```python

view:
def post(request, id):

    for post in posts:

        if post['id'] == id:

            post_dict = post

            break

    return render(request, 'posts/post.html', {'post' : post_dict})
    -------------------------------------------------------------------
    post.html:
    
      

<body>

    <h1>{{post.title}}</h1>

    <p>{{post.content}}</p>

</body>

---------------------------------------------------------------------
also in all library.html 
    <h1>{{forloop.counter}}</h1>

    <a href="/posts/{{post.id}}/">

        <h1>{{post.title|title}}:</h1>

    </a>

    <p>{{post.content|truncatewords:10}}</p>

```