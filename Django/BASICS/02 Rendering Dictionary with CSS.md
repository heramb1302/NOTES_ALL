
```python
def postpage(request):

    return render(request, 'posts/postpage.html', {'posts': posts})
---------------------------------------------------------------------
<!doctype html>

<html lang="en">

  

<head>

    <meta charset="UTF-8" />

    <meta name="viewport" content="width=device-width, initial-scale=1.0" />

    <title>Library Posts</title>

    <link href="https://fonts.googleapis.com/css2?family=Outfit:wght@300;400;600&display=swap" rel="stylesheet">

    <style>

        :root {

            --primary: #6366f1;

            --primary-hover: #4f46e5;

            --bg: #f8fafc;

            --text-main: #1e293b;

            --text-muted: #64748b;

            --white: #ffffff;

            --border: #e2e8f0;

        }

  

        body {

            font-family: 'Outfit', sans-serif;

            background-color: var(--bg);

            color: var(--text-main);

            margin: 0;

            padding: 40px 20px;

            display: flex;

            flex-direction: column;

            align-items: center;

        }

  

        .container {

            width: 100%;

            max-width: 900px;

        }

  

        h1 {

            font-weight: 600;

            font-size: 2.5rem;

            margin-bottom: 2rem;

            text-align: center;

            background: linear-gradient(to right, var(--primary), #a855f7);

            -webkit-background-clip: text;

            background-clip: text;

            -webkit-text-fill-color: transparent;

        }

  

        .table-container {

            background: var(--white);

            border-radius: 16px;

            box-shadow: 0 10px 25px -5px rgba(0, 0, 0, 0.05), 0 8px 10px -6px rgba(0, 0, 0, 0.05);

            overflow: hidden;

            border: 1px solid var(--border);

        }

  

        table {

            width: 100%;

            border-collapse: collapse;

            text-align: left;

        }

  

        thead {

            background-color: #f1f5f9;

        }

  

        th {

            padding: 16px 24px;

            font-weight: 600;

            color: var(--text-muted);

            font-size: 0.875rem;

            text-transform: uppercase;

            letter-spacing: 0.05em;

        }

  

        td {

            padding: 20px 24px;

            border-bottom: 1px solid var(--border);

            vertical-align: top;

        }

  

        tr:last-child td {

            border-bottom: none;

        }

  

        tr:hover {

            background-color: #f8fafc;

        }

  

        .post-id {

            font-weight: 600;

            color: var(--primary);

            background: #eef2ff;

            padding: 4px 10px;

            border-radius: 6px;

            font-size: 0.875rem;

        }

  

        .post-title {

            font-weight: 600;

            color: var(--text-main);

            margin-bottom: 4px;

            display: block;

        }

  

        .post-content {

            color: var(--text-muted);

            font-size: 0.9375rem;

            line-height: 1.6;

        }

  

        .nav-link {

            display: inline-block;

            margin-top: 2rem;

            color: var(--primary);

            text-decoration: none;

            font-weight: 500;

            transition: all 0.2s;

        }

  

        .nav-link:hover {

            color: var(--primary-hover);

            transform: translateX(-4px);

        }

    </style>

</head>

  

<body>

    <div class="container">

        <h1>Welcome to Library</h1>

  

        <div class="table-container">

            <table>

                <thead>

                    <tr>

                        <th style="width: 80px;">ID</th>

                        <th>Post Details</th>

                    </tr>

                </thead>

                <tbody>

                    {% for post in posts %}

                    <tr>

                        <td>

                            <span class="post-id">#{{ post.id }}</span>

                        </td>

                        <td>

                            <span class="post-title">{{ post.title }}</span>

                            <div class="post-content">{{ post.content }}</div>

                        </td>

                    </tr>

                    {% endfor %}

                </tbody>

            </table>

        </div>
        <a href="/home/" class="nav-link">← Back to Homepage</a>
    </div>
</body>

</html>
```