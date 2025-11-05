# college-event-registration-and-management-system
College-Event-Management-System Project 
from django.shortcuts import render,redirect, HttpResponseRedirect
from django.contrib.auth import logout, login
from. models import customuser , staffs,students, AdminHod
from django.contrib.auth.hashers import check_ passwsord
