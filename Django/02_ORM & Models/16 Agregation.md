

In [4]: from django.db.models import Avg

In [6]: data.aggregate(Avg('id'))
Out[6]: {'id__avg': 2.5}


In [7]: from django.db.models import Max, Min, Sum

In [8]: data.aggregate(Sum('id'))
Out[8]: {'id__sum': 5}


In [9]: Posts.objects.filter(id__gte=2).aggregate(Max('id'))
Out[9]: {'id__max': 3}

In [11]: Posts.objects.aggregate(Max('id'))
Out[11]: {'id__max': 3}

In [12]: Posts.objects.aggregate(max=Max('id'))
Out[12]: {'max': 3}
