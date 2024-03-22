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
### **CreateAPIView**
- **Purpose:** Exclusive for endpoints intended to create new model instances.
- **Functionality:** Comes equipped with a POST method handler.
- **Inheritance:** Extends from `GenericAPIView` and incorporates `CreateModelMixin`.

### **ListAPIView**
- **Purpose:** Designed for read-only endpoints that display a collection of model instances.
- **Functionality:** Features a GET method handler.
- **Inheritance:** Builds upon `GenericAPIView` and utilizes `ListModelMixin`.

### **RetrieveAPIView**
- **Purpose:** Serves read-only endpoints focused on presenting a single model instance.
- **Functionality:** Provides a GET method handler.
- **Inheritance:** Derived from `GenericAPIView` and includes `RetrieveModelMixin`.

### **DestroyAPIView**
- **Purpose:** Dedicated to delete-only endpoints for removing a single model instance.
- **Functionality:** Offers a DELETE method handler.
- **Inheritance:** A subclass of `GenericAPIView` that extends `DestroyModelMixin`.

### **UpdateAPIView**
- **Purpose:** Reserved for update-only endpoints to modify a single model instance.
- **Functionality:** Supports PUT and PATCH method handlers.
- **Inheritance:** An extension of `GenericAPIView` with `UpdateModelMixin`.

### **ListCreateAPIView**
- **Purpose:** Handles read-write endpoints to list collections of model instances or create new ones.
- **Functionality:** Equipped with GET and POST method handlers.
- **Inheritance:** Extends `GenericAPIView`, `ListModelMixin`, and `CreateModelMixin`.

### **RetrieveUpdateAPIView**
- **Purpose:** Suitable for endpoints that either read or update a single model instance.
- **Functionality:** Provides GET, PUT, and PATCH method handlers.
- **Inheritance:** A combination of `GenericAPIView`, `RetrieveModelMixin`, and `UpdateModelMixin`.

### **RetrieveDestroyAPIView**
- **Purpose:** Ideal for endpoints that allow reading or deleting a single model instance.
- **Functionality:** Comes with GET and DELETE method handlers.
- **Inheritance:** Merges `GenericAPIView`, `RetrieveModelMixin`, and `DestroyModelMixin`.

### **RetrieveUpdateDestroyAPIView**
- **Purpose:** For endpoints that enable reading, updating, or deleting a single model instance.
- **Functionality:** Features GET, PUT, PATCH, and DELETE method handlers.
- **Inheritance:** Integrates `GenericAPIView`, `RetrieveModelMixin`, `UpdateModelMixin`, and `DestroyModelMixin`.


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

