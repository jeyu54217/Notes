# Start
```bash
pip install djangorestframework
```
```bash
INSTALLED_APPS = [
    ...
    'rest_framework',
]
```


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
