in views.py to 

```python

from django.http import HttpResponseRedirect, HttpResponse

from django.shortcuts import render

from .forms import TeachersForm

from .models import Teachers

  

from django.core.paginator import Paginator

def home(request):

    if request.method == 'POST':

        form = TeachersForm(request.POST)

        if form.is_valid():

            form.save()

            print("FORM IS VALID")

        print(form.cleaned_data)

        return HttpResponseRedirect('/')

    else:

        form = TeachersForm()

    return render(request, 'teachers/teacher_home.html', {'form': form})

  

  

def thankyou(request):

    return HttpResponse("THANK YOU ...")

  

def teacher_list(request):

    teachers = Teachers.objects.all().order_by('-id')

    paginator = Paginator(teachers, 2) # Show 2 teachers per page

    page_obj = paginator.get_page(1)    

    print(page_obj)

    return render(request, 'teachers/teachers_list.html', {'teachers': page_obj})

  
  

def update_teacher(request, id):

  

    teacher = Teachers.objects.get(id=id)

    if request.method == 'POST':

        form = TeachersForm(request.POST, instance=teacher)

        if form.is_valid():

            form.save()

            return HttpResponseRedirect('/teacher/list')

    else:

        form = TeachersForm(instance=teacher)

    return render(request, 'teachers/teachers_update.html', {'teacher': teacher, 'form': form})

  
  

def delete_teacher(request, id):

    teacher = Teachers.objects.get(id=id)

    teacher.delete()

    return HttpResponseRedirect('/teacher/list')
```