**Create a file middleware.py**
```python
def CustomFunstionMiddleware(get_response):
    #one time configuration and initialization
    print("One time configuration and initialization")
    
    def middleware(request):

        print("Before view (request)")
        response = get_response(request)
        print("After view (response)")
        
        return response
    return middleware
```


# Class based middleware
```python
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
```