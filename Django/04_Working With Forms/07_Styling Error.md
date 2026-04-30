
```html
/head>

  

<body>

    <h1>Teacher Home</h1>

    <div class="container">

        {{form.non_field_errors}}

        <form action="" method="POST">

            {% csrf_token %}

            {% for field in form %}

            <div class="form-control">

                {{field.label_tag}}

                {{field}}

                {% for error in field.errors %}

                <div class="btn btn-danger">{{error}}</div>

                {% endfor %}

            </div>

            <br><br>

            {% endfor %}

  

            <input type="submit" class="btn btn-primary" value="Submit">

        </form>

    </div>

</body>
```