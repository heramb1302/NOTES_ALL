
```python 
models.py:

  

from pydantic import BaseModel

class Products(BaseModel):
    id: int
    name: str
    price: float
    #     self.id = id
    #     self.name = name
    #     self.price = price
```

```python

main.py:

from fastapi import FastAPI
from models import Products
from pydantic import BaseModel
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

@app.get("/products/{product_id}")
def get_product(product_id: int):
    for product in products:
        if product.id == product_id:
            return product
    return {"message": "Product not found"}


@app.post("/products")
def create_product(product: Products):
    products.append(product)
    return product

@app.put("/products")
def update_product(product_id: int, updated_product: Products):
    for i in range(len(products)):
        if products[i].id == product_id:
            products[i] = updated_product
            return updated_product
    return {"message": "Product not found"}

@app.delete("/products/{product_id}")
def delete_product(product_id: int):
    for i in range(len(products)):
        if products[i].id == product_id:
            deleted_product = products.pop(i)
            return deleted_product
    return {"message": "Product not found"}
```