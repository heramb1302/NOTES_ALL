```python
from django.http import HttpResponse
from django.shortcuts import render
# Create your views here.
def set(request):
    response = render(request, "students/home.html")
    response.set_cookie('theme','dark',)
    response.set_cookie('name','Heramb',max_age=5)
    return response

def get(request):
    theme = request.COOKIES['theme']
    return HttpResponse(f"Cookie is{theme}")
    
def delete_cookie(request):
    response =  HttpResponse("Deleted")
    response.delete_cookie("theme")
    return response
```

**We can also update the cookie by using set_cookie() if we want to update previous cookie**