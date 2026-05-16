```

python.exe .\manage.py shell

>>> from relations.models import Husband, Wife
>>> h = Husband.objects.get(name='h1')
>>> h
<Husband: h1>
>>> Wife.objects.create(name="w1", husband=h)
<Wife: w1>
```


```
django.core.exceptions.FieldError: Cannot resolve keyword 'huband' into field. Choices are: husband, husband_id, id, name
>>> Wife.objects.get(husband=h)
<Wife: w1>
```


# Related Objects Querry
```
>>> h = Husband.objects.get(name='h1')
>>> <Wife: w1>
>>> 
```