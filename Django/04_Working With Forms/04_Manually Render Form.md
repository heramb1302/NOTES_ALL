```html
  

<body>
    <h1>Teacher Home</h1>
    <form action="" method="POST">
        {% csrf_token %}
        <div>
            {{form.name.label_tag}}
            {{form.name}}
            {{form.name.errors}}
        </div>
        <br><br>
        <div>
            {{form.email.label_tag}}
            {{form.email}}
            {{form.email.errors}}
        </div>
        <br><br>
        <div>
            {{form.phone.label_tag}}
            {{form.phone}}
            {{form.phone.errors}}
        </div>
        <br><br>
        <input type="submit" value="Submit">
    </form>
</body>
```

**Instead Repetadely wrinting above ....**

```html
<body>

    <h1>Teacher Home</h1>
    <form action="" method="POST">
        {% csrf_token %}
        {% for field in form %}
        <div>
            {{field.label_tag}}
            {{field}}
            {{field.errors}}
        </div>
        {% endfor %}
        <br><br>
        <input type="submit" value="Submit">
    </form>
</body>
```
