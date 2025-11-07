# college-event-registration-and-management-system
College-Event-Management-System Project 
from django.shortcuts import render,redirect, HttpResponseRedirect
from django.contrib.auth import logout, login
from. models import customuser , staffs,students, AdminHod
from django.contrib.auth.hashers import check_ passwsord

def home(request):
  return render(request, 'home.html')

def contact(request):
  return render(request, 'contact.html')

def loginuser(request):
return render(request, 'login_page.html')

def dologin(request):
  email_id=request.GET.get('email')
  password=request.GET.get('password')

  if not (email_id and password):
    messages.error(request, "please provide all the details!!")
    return render(request,  'login_page.html')

  if password !=confirm_password:
     messages.error(request, 'Both passwords should watch!!')
     return render(request, 'registration.html')

  if customuser.objects.filter(email=email_id).exists():
    messages.error(request, 'Both  passwords should match!!')
    return render(request, 'restration.html')

  user_type = get_user_type_from_email(email_id)

  if user_type is none:
     messages.error(request, "Email must be like: 'john.student@college.com',
  'rahul.staff@institute.edu' or 'principal.hod@university.org'")
         return render(request,  'registration.html')

    username = email_id.split('@')[0].split('..')[0]

    if CustomUser.objects.filter(email=email_id).exists():
      messages.error(request,'user with this email already exists.please choose a different email.')
      return render(request,  'registration.html')

user = CustomUser()
user.username = username
user.email = email_id
user.first_name=first_name
user.last_name=last_name
user.user_type= user_type
user.set_password(password)
user.save()

if user_type ==CustomUser.STAFF :
   staFFs.objects.create(admin=user)
   elif user_type ==customuser.students
