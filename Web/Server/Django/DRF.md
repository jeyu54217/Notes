- [Serializers](#serializers)
  - [Core Features](#core-features)
  - [Types](#types)
    - [Serializer](#serializer)
    - [BaseSerializer](#baseserializer)
    - [ModelSerializer](#modelserializer)
    - [ListSerializer](#listserializer)
    - [HyperlinkedModelSerializer](#hyperlinkedmodelserializer)
  - [Usage Scenarios](#usage-scenarios)
  - [Implementing a Serializer](#implementing-a-serializer)
  - [Advanced Features](#advanced-features)
- [Generic Views](#generic-views)
  - [Core Features](#core-features-1)
  - [Commonly Used Generic Views](#commonly-used-generic-views)
    - [**CreateAPIView**](#createapiview)
    - [**ListAPIView**](#listapiview)
    - [**RetrieveAPIView**](#retrieveapiview)
    - [**DestroyAPIView**](#destroyapiview)
    - [**UpdateAPIView**](#updateapiview)
    - [**ListCreateAPIView**](#listcreateapiview)
    - [**RetrieveUpdateAPIView**](#retrieveupdateapiview)
    - [**RetrieveDestroyAPIView**](#retrievedestroyapiview)
    - [**RetrieveUpdateDestroyAPIView**](#retrieveupdatedestroyapiview)
  - [Advantages](#advantages)
  - [Customization](#customization)



# Serializers
  - Handle conversion between complex data types like querysets and model instances, and Python datatypes that can then be easily rendered into JSON, XML, or other content types. 

## Core Features
- **Data Conversion:** Convert complex data types to Python datatypes that can be easily rendered into JSON or other content types.
  - This allows for a seamless transition between frontend and backend data handling.
- **Validation:** Serializers include validation logic to ensure that incoming data is correct and secure.
  - This significantly reduces the amount of boilerplate code required for data validation.
- **Deserialization:** Convert incoming data back into complex types, after validating it.
  - Useful for creating or updating model instances.

## Types

### Serializer
- The base class for all serializers in DRF, providing the core functionality for field declaration, data serialization, deserialization, and validation.
  - **Field Declaration:** Define the fields that should be serialized/deserialized.
  - **Serialization:** Convert model instances or other complex datatypes into Python datatypes that can then be easily rendered into JSON, XML, or other content types.
  - **Deserialization:** Process incoming data, validate it, and convert it into complex types like model instances.
  - **Validation:** Includes mechanisms for validating incoming data either at the field level or object level.

### BaseSerializer
- The fundamental building block upon which all other serializer classes are built. It provides the core functionality but does not include any automatic field determination or model integration.
  - **Maximum Flexibility:** Allows for complete control over serialization and deserialization processes, making it suitable for highly custom serialization scenarios.
  - **Manual Field Declaration:** Requires explicit declaration of all fields, without any automatic field type inference.
  - **Custom Serialization and Deserialization:** Ideal for complex data structures that do not directly map to Django models or when custom data processing is needed.

### ModelSerializer
- A shortcut class that automatically determines the set of fields based on the model.
  - **DRY Principle:** Helps adhere to the "Don't Repeat Yourself" principle by deriving the serializer fields from the model attributes.
  - **Default Implementations:** Provides default `create()` and `update()` implementations, making it easier to create API endpoints for CRUD operations on models.
  - **Field Mapping:** Automatically maps model fields to corresponding serializer fields.
  - **Validation:** Includes default validations derived from the model, such as field lengths and unique constraints.
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


### ListSerializer
- A serializer class for handling lists of objects. It is not used directly by developers but is instead automatically applied by DRF when dealing with `many=True` on serializer fields.
  - **Automatic Implementation:** DRF utilizes ListSerializer to handle bulk create, update, and delete operations when dealing with lists of objects.
  - **Underlying Mechanism:** Provides a way to serialize and deserialize querysets and lists of objects, applying validation to each item in the list.

### HyperlinkedModelSerializer
- A variant of ModelSerializer that uses hyperlinks to represent relationships, rather than primary keys.
  - **Hyperlinking API:** Ideal for creating browsable web APIs, as it emphasizes on using URLs to navigate between related resources.
  - **URL Fields:** Automatically includes a `url` field using Django's `HyperlinkedIdentityField`, and converts foreign keys and many-to-many relationships to `HyperlinkedRelatedField`.
  - **Browsable:** Enhances the API's usability and navigability in web browsers.


## Usage Scenarios
- **APIs for CRUD Operations:** Use ModelSerializer for quick and efficient creation of APIs for CRUD operations on Django models.
- **Nested Relationships:** Handle nested object relationships in your API, providing a detailed and structured response.
- **Data Validation and Transformation:** Use serializer fields and validation methods to ensure that incoming data adheres to specific rules before saving to the database.
- **Custom Response Formats:** Create custom serializers to format the API responses in a specific way, tailored to the needs of the frontend.

## Implementing a Serializer
- **Define a Serializer Class:** Specify the model it serializes and the fields to include.
  - This can be a subset of the model's fields, all fields, or additional computed fields.
- **Use Serializer Methods:** Override `create()` and `update()` methods to define how instances are created or modified when calling `serializer.save()`.
- **Validation:** Implement field-level or object-level validation by overriding the `validate_<fieldname>()` methods or the `validate()` method, respectively.

## Advanced Features
- **Custom Fields:** Create custom serializer fields for transforming data in a way that differs from the model field.
- **Dynamic Fields:** Dynamically modify fields included in a serialized output, useful for APIs that serve different clients with different data needs.
- **Read-only and Write-only Fields:** Specify fields that are only used for serialization or deserialization, optimizing performance and security.



# Generic Views

- Built-in DRF views that provide ready-to-use implementations for common API patterns, designed to simplify the process of building API endpoints, reducing the amount of code developers need to write.

- | Feature                | APIView                                              | Generic Views                                         |
|------------------------|------------------------------------------------------|-------------------------------------------------------|
| **Foundation**         | Subclass of Django's View class, providing a way to handle HTTP methods explicitly. | Build upon the APIView, offering a higher level of abstraction with pre-built methods for CRUD operations. |
| **Use Case**           | Best suited for endpoints requiring custom business logic or when you need full control over the request handling. | Ideal for standard CRUD operations on a model with minimal additional code. |
| **Flexibility**        | Highly flexible, allowing for granular control over request parsing, response rendering, and exception handling. | Less flexibility than APIView but simplifies implementation by using mixins and generic classes. |
| **Code Verbosity**     | More verbose, requiring explicit definition of request handling for each HTTP method. | Less verbose, as common patterns are encapsulated within mixins and generic classes. |
| **Boilerplate Code**   | Requires more boilerplate code for standard CRUD operations. | Reduces boilerplate code significantly by using pre-defined mixins and methods. |
| **Method Handling**    | You need to explicitly define methods for GET, POST, etc., and handle the request and response flow within each method. | Pre-defined methods for handling GET, POST, PUT, DELETE, etc., are automatically provided based on the generic view or mixin used. |
| **Customization**      | High degree of customization possible, making it suitable for complex API logic. | Customizable to an extent through overriding pre-defined methods and attributes but generally follows a prescribed pattern. |
| **Direct Model Mapping** | No direct model mapping, offering the freedom to handle data in any form. | Directly maps to a Django model, assuming that each request operates on a specific model or a queryset. |
| **Learning Curve**     | Steeper learning curve due to the need for more detailed understanding of request/response lifecycle. | Easier to use for beginners, especially for standard database operations, due to abstraction and pre-built methods. |

  
## Core Features
- **CRUD Operations:** 
- Generic views offer straightforward implementations for creating, retrieving, updating, and deleting objects in RESTful APIs.
- **Serialization:** 
- Automatically handles serialization and deserialization of data using the specified serializer class. (don't have to manually convert data to JSON or parse JSON data.)
- **Permission Handling:** 
- Supports integration with DRF's permissions system, allowing for easy configuration of access controls for each view.

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

