**CREATE A VIEW**
````python
  

def search(request):

    # Safely get 'q' from the GET request. Defaults to an empty string if not found.

    searched = request.GET.get('q', '').strip()

    posts = None

  

    if searched:

        # '__icontains' makes the search case-insensitive (e.g., 'python' matches 'Python')

        posts = Posts.objects.filter(post_title__icontains=searched)

        # Debugging prints

        print(f"Searched: {searched}")

        print(f"Posts found: {posts}")

  

    context = {

        'searched': searched,

        'posts': posts

    }

    return render(request, 'models/search.html', context)
```
HTML:

{% extends "models/base.html" %}

  

{% block body %}

    <h1>Search</h1>

    <form action="{% url 'search' %}" method="get">

        <input type="text" name="q" value="{{ searched }}" placeholder="Search...">

        <button type="submit">Search</button>

    </form>

  

    <hr>

  

    {% if searched %}

        <h2>Results for "{{ searched }}":</h2>

        {% if posts %}

            <ul>

                {% for post in posts %}

                    <li>{{ post.post_title }}</li>

                {% endfor %}

            </ul>

        {% else %}

            <p>No posts found matching your search.</p>

        {% endif %}

    {% endif %}

{% endblock body %}