# Django REST API

## Description

This repository is a Software of Application with Python, Django, etc.

## Installation

Using Django, djangorestframework,etc preferably.

## DataBase

Using SQLite3 preferably.

## Apps

Using pipenv.

## Usage

```html
$ git clone https://github.com/DanielArturoAlejoAlvarez/django-rest-api.git
[NAME APP]
```

Follow the following steps and you're good to go! Important:

![alt text](https://camo.githubusercontent.com/63cff5254d7b948dea095696bc62092b2379f29f/68747470733a2f2f7261772e6769746875622e636f6d2f69637963616e646c652f7375626c696d652d646a616e676f2d6c6f6f6b75702f6d61737465722f64656d6f2e676966)

## Coding

### Models

```python
...
from django.db import models

class Language(models.Model):
    name = models.CharField(max_length=100)
    paradigm = models.CharField(max_length=128)

    def __str__(self):
        return self.name
...
```

### Controllers

```python
...
from rest_framework import serializers
from .models import Language 

class LanguageSerializer(serializers.HyperlinkedModelSerializer):
    class Meta:
        model = Language 
        fields = ('id','url','name','paradigm')
...
```

### Views

```python
...
from django.shortcuts import render
from rest_framework import viewsets 

from .models import Language 
from .serializers import LanguageSerializer

class LanguageView(viewsets.ModelViewSet):
    queryset = Language.objects.all()
    serializer_class = LanguageSerializer

...
```

### Routes 

```python
...
from django.urls import path,include

from . import views
from rest_framework import routers

router = routers.DefaultRouter()
router.register('languages', views.LanguageView)

urlpatterns = [
    path('', include(router.urls))
]
...
```

## Contributing

Bug reports and pull requests are welcome on GitHub at https://github.com/DanielArturoAlejoAlvarez/django-rest-api. This project is intended to be a safe, welcoming space for collaboration, and contributors are expected to adhere to the [Contributor Covenant](http://contributor-covenant.org) code of conduct.

## License

The gem is available as open source under the terms of the [MIT License](http://opensource.org/licenses/MIT).
````
