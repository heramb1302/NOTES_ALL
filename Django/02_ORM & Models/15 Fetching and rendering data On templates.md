

```python
from .models import Posts
def posts(request):

    all_posts = Posts.objects.all()

    print(f"""All Posts: {all_posts}""")

    return render(request, 'models/posts.html', {'all_posts': all_posts
```