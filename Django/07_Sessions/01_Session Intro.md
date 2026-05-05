![[Pasted image 20260505170306.png]]
![[Pasted image 20260505170318.png]]
![[Pasted image 20260505170344.png]]

**Code:**
```python
from django.http import HttpResponse

from django.shortcuts import render

  

# Create your views here.

def home(request):

    request.session['name']='heramb'

    return HttpResponse("Welcome to the Session Tutorial Home Page!")

  

def set(request):

    request.session['name']='heramb'

    request.session['age']=22

    return HttpResponse("Session variables 'name' and 'age' have been set.")

  

def get(request):

    name=request.session.get('name')

    age=request.session.get('age')

    return HttpResponse(f"Welcome {name} (Age: {age}) to the Session Tutorial Get Page!")

  

def delete(request):

    if 'name' in request.session:

        del request.session['name']

    if 'age' in request.session:

        del request.session['age']

    return HttpResponse("Session variables 'name' and 'age' have been deleted.")

  

def flush_delete(request):

    request.session.flush()

    return HttpResponse("All session data has been flushed (deleted).")
```

**Session Methods :**
****in same file****

```python
from django.http import HttpResponse
from django.shortcuts import render
# Create your views here.
def home(request):
    request.session['name']='heramb'
    return HttpResponse("Welcome to the Session Tutorial Home Page!")

def set(request):
    request.session['name']='heramb'
    request.session['age']=22
    request.session.set_expiry(5)# Set session to expire in 5 seconds
    print(f"The Session will expire in {request.session.get_expiry_age()} seconds.")  # Print the remaining time until session expires
    print(f"The Session will expire at {request.session.get_expiry_date()}.")  # Print the exact date and time when session will expire
    return HttpResponse("Session variables 'name' and 'age' have been set.")

def get(request):
    name=request.session.get('name')
    age=request.session.get('age')
    return HttpResponse(f"Welcome {name} (Age: {age}) to the Session Tutorial Get Page!")

def delete(request):
    if 'name' in request.session:
        del request.session['name']
    if 'age' in request.session:
        del request.session['age']
    return HttpResponse("Session variables 'name' and 'age' have been deleted.")
  
def flush_delete(request):
    request.session.flush()
    request.session.clear_expired()  # Clear expired sessions
    return HttpResponse("All session data has been flushed (deleted).")
``` 