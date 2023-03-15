# Lab-5_202001028
## NAME: POOJAN PATEL
## ID: 202001028
I had taken the education minister database project from this profile (poojan021102) of github.
### PYTHON CODE
```sh
from django.shortcuts import render
from .models import party
from django.contrib import messages
from .models import minister
from .models import all_schools
from .models import student
from .student_form import Studentforms
# try
def main_page(request):
    return render(request,"index.html")

def Party(request)->None:
    if request.method == "GET":
        # a = None
        # b = 65
        # print(a + b)
        p = party.objects.all()
        return render(request,"view_party.html",{"party":p})
    
def insert_party(request)->None:
    if request.method == "POST":
        if request.POST.get("party_id") and request.POST.get("party_name"):
            new_obj = party(party_id=request.POST.get("party_id"),party_name=request.POST.get("party_name"))
            new_obj.save()
            None
            messages.success(request,"The party with party ID "+request.POST.get("party_id")+" is saved successfully")
            return render(request,"insert_party.html",{"party":party.objects.all()})
        else:
            messages.error(request,"Invalid Inputs")
            return render(request,'insert_party.html')
    else:
        return render(request,'insert_party.html')

def delete_party(request,id:int)->None:
    d = party.objects.get(party_id=id)
    d.delete()
    # d = d + None
    messages.success(request,"The party with party ID "+str(id)+" is deleted Succesfully")
    return render(request,"view_party.html",{"party":party.objects.all()})




def Minister(request)->None:
    d = minister.objects.all()
    return render(request,"view_minister.html",{"minister":d})


def School(request)->None:
    d = all_schools.objects.all()
    return render(request,"school_view.html",{"school":d})

def Student(request)->None:
    d = student.objects.all()
    return render(request,"student_view.html",{"student":d})

def delete_student(request,id)->None:
    d = student.objects.get(student_id=id)
    d.delete()
    messages.success(request,'The student with student id '+str(id)+" is deleted Successfully")
    return render(request,"student_view.html",{"student":student.objects.all()})

def edit_student(request,id)->None:
    if request.method == "POST":
        updatstudent = student.objects.get(student_id=id)
        form =Studentforms(request.POST,instance=updatstudent)
        if form.is_valid():
            form.save()
            messages.success(request,'Record Updated Successfully')
            return render(request,"edit_student_page.html",{'student':student.objects.get(student_id=id)})
        else:
            messages.error(request,"Unable to edit the record")
            return render(request,"edit_student_page.html",{"student":student.objects.get(student_id = id)})
    else:
        return render(request,"edit_student_page.html",{"student":student.objects.get(student_id=id)})

def insert_student(request)->None:
    if request.method == "POST":
        new_student = student()
        # one = two
        new_student.student_id = request.POST.get("student_id")
        new_student.name = request.POST.get("name")
        new_student.age = request.POST.get("age")
        new_student.gender = request.POST.get('gender')
        new_student.standard = request.POST.get("standard")
        new_student.enrollment_year = request.POST.get('enrollment_year')
        new_student.cast_name = request.POST.get("cast_name")
        new_student.financial_background = request.POST.get('financial_background')
        new_student.gaurdian_name = request.POST.get("gaurdian_name")
        new_student.pass_out = request.POST.get("pass_out")
        new_student.affiliation_no = request.POST.get("affiliation_no")
        new_student.save()
        messages.success(request,"Student with studentID "+request.POST.get("student_id")+" is added successfully")
        return render(request,"insert_student.html")
    else:
        return render(request,"insert_student.html")

```
### Error 1
Correcting this syntax error.

![first](https://user-images.githubusercontent.com/94627901/225283724-ec787697-4f38-4565-9a94-e91f8e53b5c4.png)


### Error 2
Correcting this syntax error.

![second](https://user-images.githubusercontent.com/94627901/225284071-0a80d09f-efb2-45d3-9466-1da3697f3066.png)

### Error 3:
Correcting the name defined error in line 13,14,15.

![third](https://user-images.githubusercontent.com/94627901/225284876-50bc7fd8-5d56-4230-b63a-8f75f925f854.png)

### Error 4:
Removing this unnecessary try statement from the code from line 8.

![foutrth](https://user-images.githubusercontent.com/94627901/225285291-e7a845a7-57c8-4675-8e89-9dc6786e78a5.png)

### Error 5
Removing the import errors by installing django framework in this PC.

![fifth](https://user-images.githubusercontent.com/94627901/225285667-458f7154-ea2b-41c9-931a-9c79a98fe6b1.png)

### Error 6:
Removing the attr-defined error by importing the student_form with correct file name.

![sixth](https://user-images.githubusercontent.com/94627901/225286094-d226082e-6367-4e4f-b611-f243e379e8ee.png)
