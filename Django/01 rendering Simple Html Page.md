Here’s a step-by-step breakdown of how you rendered a simple HTML page in your Django project:

### 1. **Created a Django View**

- In [views.py](vscode-file://vscode-app/c:/Users/heram/AppData/Local/Programs/Microsoft%20VS%20Code/resources/app/out/vs/code/electron-browser/workbench/workbench.html), you defined a function:
```python
def homepage(request):
    return render(request, 'home.html')
```


### 2. **Created a Template**

- In [home.html](vscode-file://vscode-app/c:/Users/heram/AppData/Local/Programs/Microsoft%20VS%20Code/resources/app/out/vs/code/electron-browser/workbench/workbench.html), you created a basic HTML file:
```html
<!doctype html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <title>Document</title>
  </head>
  <body>
    <h1>Home Page</h1>
  </body>
</html>

```

### 3. **Mapped the View to a URL**

- In [urls.py](vscode-file://vscode-app/c:/Users/heram/AppData/Local/Programs/Microsoft%20VS%20Code/resources/app/out/vs/code/electron-browser/workbench/workbench.html), you added a URL pattern:
path('homepage/', views.homepage),


### 4. **Included App URLs in Project URLs**

- In [urls.py](vscode-file://vscode-app/c:/Users/heram/AppData/Local/Programs/Microsoft%20VS%20Code/resources/app/out/vs/code/electron-browser/workbench/workbench.html), you included the app’s URLs:
path('post/', include('posts.urls')),

Also add created app in Installed app list in settings.py file of the main  django app created.

