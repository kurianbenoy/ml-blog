---
toc: true
layout: post
description: A minimal example of using markdown with fastpages.
categories: [django]
title: Introduction to Django 2.0
---

# Introduction to Django 2.0


[Do check this Article if you didnt like this article](https://medium.com/@kurianbenoy1998/an-intro-to-django-2-a09d0dbf656d)



In this article , I will be covering some of the main features of Django 2.0

URL Mapping
## Django 2.0

from django.urls import path
from . import views
urlpatterns = [
 path(‘articles/2003/’, views.special_case_2003),
 path(‘articles/<int:year>/’, views.year_archive),
 path(‘articles/<int:year>/<int:month>/’, views.month_archive),
 path(‘articles/<int:year>/<int:month>/<slug:slug>/’, views.article_detail),
]
## Django 1.11

urlpatterns = [
 url(r’^articles/2003/$’, views.special_case_2003),
 url(r’^articles/([0–9]{4})/$’, views.year_archive),
 url(r’^articles/([0–9]{4})/([0–9]{2})/$’, views.month_archive),
 url(r’^articles/([0–9]{4})/([0–9]{2})/([0–9]+)/$’, views.article_detail),
]
2) New Database features

There are a lot of new features. I am covering just the basic one for now and will keep on adding later

1) Aggregation with Filter

**Django 2.0**

from django.contrib.auth.models import User
from django.db.models import Count, F
User.objects.aggregate(
 total_users=Count(‘id’),
 total_active_users=Count(‘id’, filter=F(‘is_active’)),
)
django 1.11

from django.contrib.auth.models import User
from django.db.models import (
 Count,
 Sum,
 Case,
 When,
 Value,
 IntegerField,
)
User.objects.aggregate(
 total_users=Count(‘id’),
 total_active_users=Sum(Case(
 When(is_active=True, then=Value(1)),
 default=Value(0),
 output_field=IntegerField(),
 )),
)
And lot more DBMS features are there, you can refer this page:

https://docs.djangoproject.com/en/2.0/ref/models/querysets/

Then there are new features to calculate rank like Windows function :

https://docs.djangoproject.com/en/2.0/ref/models/database-functions/#window-functions

A mobile Friendly Admin Site


Ya this image show how mobile friendly the new django admin page is . Earlier people used to shift away from django admin site and make their own pages, now the time has come to adore it.

References

Django 2.0 release notes | Django documentation | Django

Django 2.0 will be the last release series to support Python 3.4. If you plan a deployment of Python 3.4 beyond the…
docs.djangoproject.com	
https://docs.djangoproject.com/en/2.0/

https://docs.djangoproject.com/en/1.11/

;
