	•We Are Using UVICORN to run fast API
	
	•Create virtual Environment  
	python –m venv myenv  
	Activate Using – myenv/Scripts/activate
	
	•
	
	•Pip list will show all the
	
	•Cmd = pip install fastapi uvicorn



**You Need to create the object of the FAST API Framework to run the surver**

```python

from fastapi import FastAPI
app = FastAPI()  


def greet():
    return "Hello, welcome to the program!"

```

**To run the func app:**
```cmd
uvicorn main:app --reload
```

***CRUD(CERATE, READ, UPDATE, DELETE)*:***

```
**pydentic**
helps to data validation even no need to define constructors
```


```python
models.py

from pydantic import BaseModel
class Products(BaseModel):
    id: int
    name: str
    price: float

    # def __init__(self, id: int, name: str, price: float):
    #     self.id = id
    #     self.name = name
    #     self.price = price
```

```python
main.py

from fastapi import FastAPI
from models import Products

app = FastAPI()

  

products = [
    Products(id=1, name="Product A", price=10.99),
    Products(id=2, name="Product B", price=19.99),
    Products(id=3, name="Product C", price=5.99),
]

@app.get("/message")
def greet():
    return "Hello, welcome to the program!"
  
@app.get("/products")
def get_products():
    return products
```