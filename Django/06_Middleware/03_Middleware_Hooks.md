**Present only in class based middleware. So class based middleware is mostly used.**
![[Pasted image 20260505155521.png]]


create a middleware.py file:
```python
from django.http import HttpResponse

  

class CustomClassMiddleware:
    def __init__(self, get_response):
        self.get_response = get_response
        #one time configuration and initialization
        print("One time configuration and initialization")

    def __call__(self, request):
        print("Before view (request)")
        response = self.get_response(request)
        print("After view (response)")
        return response

    def process_view(self, request, view_func, view_args, view_kwargs):
        print("Processing view")
        print(request.method)
        print("View function:", view_func.__name__)
        return HttpResponse("View processed")

```


![[Pasted image 20260505162847.png]]

```python
from django.http import HttpResponse
class CustomClassMiddleware:
    def __init__(self, get_response):
        self.get_response = get_response
        #one time configuration and initialization
        print("One time configuration and initialization")
  
    def __call__(self, request):
        print("Before view (request)")
        response = self.get_response(request)
        print("After view (response)")
        return response

    def process_exception(self, request, exception):
        print("Exception occurred:", exception)
        return HttpResponse("An error occurred while processing the request.")
```

![[Pasted image 20260505163304.png]]

 in view:
 ```python
 from django.http import HttpResponse

from django.shortcuts import render

from django.template.response import TemplateResponse

# Create your views here.

def set(request):

    #raise Exception("An error occurred while processing the request.")

    response = TemplateResponse(request, "students/home.html")

    response.set_cookie('theme','dark',)

    response.set_cookie('name','Heramb',max_age=5)

  

    return response
 ```


in middleware:
```python
from django.http import HttpResponse

  

class CustomClassMiddleware:

    def __init__(self, get_response):

        self.get_response = get_response

  

        #one time configuration and initialization

        print("One time configuration and initialization")

  

    def __call__(self, request):

        print("Before view (request)")

        response = self.get_response(request)

        print("After view (response)")

        return response

    def process_template_response(self, request, response):

        print("Processing template response")

        return response
```