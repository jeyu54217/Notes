**CONTENTS**
- [Setting Up](#setting-up)
- [API TEST](#api-test)
- [Serializers](#serializers)
  - [Serializer](#serializer)
  - [ModelSerializer](#modelserializer)
  - [ListSerializer\* (不會直接使用, 底層幫你實作～)](#listserializer-不會直接使用-底層幫你實作)
  - [HyperlinkedModelSerializer\*](#hyperlinkedmodelserializer)
  - [BaseSerializer\*](#baseserializer)
  
# Setting Up
```bash
pip list
```
```bash
pip install djangorestframework
```
- **```settings.py```**
    ```bash
    INSTALLED_APPS = [
        ...
        'rest_framework',
    ]
    ```
    ```bash
    REST_FRAMEWORK = {

    }
    ```
- **```serializers.py```**
    ```bash
    touch ../serializers.py
    ```

# API TEST


# Serializers
## Serializer
## ModelSerializer
## ListSerializer* (不會直接使用, 底層幫你實作～)
## HyperlinkedModelSerializer*
## BaseSerializer*


```bash
from .models import <Table>
from rest_framework import serializers

# Serializers define the API representation.
class <Table>Serializer(serializers.ModelSerializer):
    class Meta:
        model = <Table>
        fields = '__all__'
        # fields = ['specified', 'fields', ]
        # exclude = ['specified', 'fields', ]
```
