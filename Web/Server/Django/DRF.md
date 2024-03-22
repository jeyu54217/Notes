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

# Generic Views in Django Rest Framework (DRF)

## Introduction
- Built-in DRF views that provide ready-to-use implementations for common API patterns, designed to simplify the process of building API endpoints, reducing the amount of code developers need to write.

  
## Core Features
### 1. **CRUD Operations:** Generic views offer straightforward implementations for creating, retrieving, updating, and deleting objects in RESTful APIs.
### 2. **Serialization:** Automatically handles serialization and deserialization of data using the specified serializer class. (don't have to manually convert data to JSON or parse JSON data.)
### 3. **Permission Handling:** Supports integration with DRF's permissions system, allowing for easy configuration of access controls for each view.

## Commonly Used Generic Views
### **ListAPIView:** For listing a queryset or all objects.
### **RetrieveAPIView:** For reading a single model instance.
### **CreateAPIView:** For creating new model instances.
### **DestroyAPIView:** For deleting model instances.
### **UpdateAPIView:** For updating model instances.
### **ListCreateAPIView:** A combination that allows listing objects or creating a new object.
### **RetrieveUpdateAPIView:** Allows reading or updating a model instance.
### **RetrieveDestroyAPIView:** Allows reading or deleting a model instance.
### **RetrieveUpdateDestroyAPIView:** Combines reading, updating, and deleting a model instance into a single endpoint.

## Advantages
- **Efficiency:** Significantly reduces the amount of boilerplate code required for API development.
- **Consistency:** Promotes a consistent approach to building APIs, making it easier to maintain and understand the codebase.
- **Flexibility:** While providing a structured framework for API development, generic views are also flexible, allowing for customization to meet specific requirements.

## Customization
- Generic views can be customized through various mechanisms:
  - **Serializer Class:** Specify a custom serializer class to control the serialization and deserialization behavior.
  - **Queryset:** Define the queryset that the view should operate on, allowing for fine-grained control over the data returned by the API.
  - **Permission Classes:** Customize the permission checks performed on the view, ensuring that only authorized users can access or modify data.
  - **Filter Backends:** Integrate filtering, searching, and ordering functionalities by specifying filter backends.

