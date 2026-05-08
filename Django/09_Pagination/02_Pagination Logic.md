*views.py(teachers)*
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

    page_number = request.GET.get('page',1)

    page_obj = paginator.get_page(page_number)

    print(page_obj)

    print(page_obj.has_previous())

    print(page_obj.has_next())

  

    return render(request, 'teachers/teacher_list_pagination.html', {'teachers': page_obj})

  
  

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

*teachers_list_pagination.html*
```html
    <!DOCTYPE html>

<html lang="en">

  

<head>

    <meta charset="UTF-8">

    <meta name="viewport" content="width=device-width, initial-scale=1.0">

    <title>Teachers List</title>

</head>

  

<body>

  

    <h1>Teachers List New With Pagination</h1>

    <table border="1">

        <thead>

            <tr>

                <th>Name</th>

                <th>Email</th>

                <th>Phone</th>

                <th>Bio</th>

                <th>Edit/Delete</th>

            </tr>

        </thead>

        <tbody>

            {% for teacher in teachers %}

            <tr>

                <td>{{teacher.name}}</td>

                <td>{{teacher.email}}</td>

                <td>{{teacher.phone}}</td>

                <td>{{teacher.bio}}</td>

                <td><a href="{% url 'teacher_update' teacher.id %}">Edit</a> | <a

                        href="{% url 'teacher_delete' teacher.id %}">Delete</a></td>

            </tr>

            {% endfor %}

        </tbody>

  

    </table>

</body>

  

        <a href="{% url 'teacher_home' %}">Add More Teachers</a>

  

        <!-- Pagination Controls -->

        {% if teachers.has_other_pages %}

        <nav aria-label="Page navigation">

            <ul class="pagination" style="justify-content:center; margin-top:20px;">

                {% if teachers.has_previous %}

                    <li class="page-item">

                        <a class="page-link" href="?page={{ teachers.previous_page_number }}">Prev</a>

                    </li>

                {% else %}

                    <li class="page-item disabled">

                        <span class="page-link">Prev</span>

                    </li>

                {% endif %}

  

                {% for num in teachers.paginator.page_range %}

                    {% if teachers.number == num %}

                        <li class="page-item active"><span class="page-link">{{ num }}</span></li>

                    {% else %}

                        <li class="page-item"><a class="page-link" href="?page={{ num }}">{{ num }}</a></li>

                    {% endif %}

                {% endfor %}

  

                {% if teachers.has_next %}

                    <li class="page-item">

                        <a class="page-link" href="?page={{ teachers.next_page_number }}">Next</a>

                    </li>

                {% else %}

                    <li class="page-item disabled">

                        <span class="page-link">Next</span>

                    </li>

                {% endif %}

            </ul>

        </nav>

        {% endif %}

</body>

  

</html>
```