
**We pass the widget in form to set the custom CSS**

```html
<!DOCTYPE html>

<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.8/dist/css/bootstrap.min.css" rel="stylesheet"
        integrity="sha384-sRIl4kxILFvY47J16cr9ZwB07vP4J8+LH7qKQnuqkuIAvNWLzeN8tE5YBujZqJLB" crossorigin="anonymous">

</head>
<body>
    <h1>Teacher Home</h1>
    <div class="form-control">
        <form action="" method="POST">
            {% csrf_token %}
            {% for field in form %}
            <div class="form-control">
                {{field.label_tag}}
                {{field}}
                {{field.errors}}
            </div>
            <br><br>
            {% endfor %}
            <input type="submit" class="btn btn-primary" value="Submit">
        </form>
    </div>
</body>
</html>
```