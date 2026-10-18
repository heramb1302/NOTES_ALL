
All queries will be handled by SQL alchemy which is ORM model.

**Install sql alchemy and driver for postgre sql:**

```cmd
pip install sqlalchemy psycopg2
pip install sqlalchemy psycopg
pip install "psycopg[binary]"
```

**Complete Programme:**

```python

main.py:

from fastapi import FastAPI, Depends, HTTPException
from models import Products
from database import session,engine
import database_models
from sqlalchemy.orm import Session

app = FastAPI()

database_models.Base.metadata.create_all(bind=engine)
# products = [
#     Products(id=1, name="Product A", price=10.99),
#     Products(id=2, name="Product B", price=19.99),
#     Products(id=3, name="Product C", price=5.99),
# ]

def get_db():
    db = session()
    try:
        yield db
    finally:
        db.close()

@app.get("/message")
def greet():
    return "Hello, welcome to the program!"

@app.get("/products")
def get_products(db: Session = Depends(get_db)):
    db_products = db.query(database_models.Products).all()
    return db_products

@app.get("/products/{product_id}")
def get_product(product_id: int, db: Session = Depends(get_db)):
    product = db.query(database_models.Products).filter(database_models.Products.id == product_id).first()
    if not product:
        raise HTTPException(status_code=404, detail="Product you are looking for not found \n this is a custom message")
    return product


@app.post("/products")
def create_product(product: Products, db: Session = Depends(get_db)):
    db.add(database_models.Products(**product.model_dump()))
    db.commit()
    db.refresh(product)
    return product
  
@app.put("/products/{product_id}")
def update_product(product_id: int, updated_product: Products, db: Session = Depends(get_db)):
    db_product = db.query(database_models.Products).filter(database_models.Products.id == product_id).first()

    if not db_product:
        raise HTTPException(status_code=404, detail="Product not found")
    else:
        db_product.name = updated_product.name
        db_product.price = updated_product.price
        db.commit()
        db.refresh(db_product)
        return db_product
    return {"message": "Product updated successfully"}

@app.delete("/products/{product_id}")
def delete_product(product_id: int, db: Session = Depends(get_db)):
    db_product = db.query(database_models.Products).filter(database_models.Products.id == product_id).first()
    if not db_product:
        raise HTTPException(status_code=404, detail="Product not found")
    else:
        db.delete(db_product)
        db.commit()
        return {"message": "Product deleted successfully"}

@app.delete("/products")
def delete_all_products(db: Session = Depends(get_db)):
    db.query(database_models.Products).delete()
    db.commit()
    return {"message": "All products deleted successfully"}
```

```python

database_models.py

from sqlalchemy.ext.declarative import declarative_base

from sqlalchemy import Column, Integer, String, Float

  

Base = declarative_base()

  

class Products(Base):

    __tablename__ = "products"

  

    id = Column(Integer, primary_key=True, index=True)

    name = Column(String, index=True)

    price = Column(Float, index=True)
    
```

```python

database.py

from sqlalchemy.orm import sessionmaker

from sqlalchemy import create_engine

  
  

db_url = "postgresql://postgres:heramb1302@localhost:5432/FastAPI"  # Replace with your actual database URL

engine = create_engine(db_url)

session = sessionmaker(autocommit=False, autoflush=False, bind=engine)

  

#autocommit=False: This means that changes made to the database within a session will not be automatically committed. You need to explicitly call session.commit() to save changes.

#autoflush=False: This means that changes made to the database within a session will not be automatically flushed to the database. Flushing is the process of sending pending changes to the database. You can call session.flush() to manually flush changes.

#bind=engine: This specifies the database engine that the session will be bound to. The engine is responsible for managing the connection to the database.
```

```python
models.py:

from sqlalchemy.orm import sessionmaker

from sqlalchemy import create_engine

  
  

db_url = "postgresql://postgres:heramb1302@localhost:5432/FastAPI"  # Replace with your actual database URL

engine = create_engine(db_url)

session = sessionmaker(autocommit=False, autoflush=False, bind=engine)

  

#autocommit=False: This means that changes made to the database within a session will not be automatically committed. You need to explicitly call session.commit() to save changes.

#autoflush=False: This means that changes made to the database within a session will not be automatically flushed to the database. Flushing is the process of sending pending changes to the database. You can call session.flush() to manually flush changes.

#bind=engine: This specifies the database engine that the session will be bound to. The engine is responsible for managing the connection to the database.
```

***END OF THE SIMPLE FAST API in Python***

