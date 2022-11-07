
### Django Shell
```bash
python3 manage.py shell
```
```bash
from <app.models> import <Table>
```
```bash
exit()
```


```
>>> print(type(User.objects.filter(user_name = '??')))
<class 'django.db.models.query.QuerySet'>
>>> print(bool(User.objects.filter(user_name = '??')))
False
>>> print(bool(User.objects.filter(user_name = 'test_user_01')))
True


>>> User.objects.filter(user_name = 'test_user_01', user_password = "321")
<QuerySet [<User: User object (6)>]>
>>> User.objects.filter(user_name = 'test_user_01', user_password = "3211")
<QuerySet []>
>>> User.objects.filter(user_name = 'test_user_01').get(user_name = 'test_user_01',user_password = "321")
<User: User object (6)>
>>> User.objects.filter(user_name = 'test_user_01').get(user_name = 'test_user_01',user_password = "3211")
Traceback (most recent call last):
  File "<console>", line 1, in <module>
  File "/Users/jy-m1/Library/Mobile Documents/com~apple~CloudDocs/code/code/django_jwt_demo/lib/python3.10/site-packages/django/db/models/query.py", line 650, in get
    raise self.model.DoesNotExist(
app.models.User.DoesNotExist: User matching query does not exist.


>>> User.objects.filter(user_name = 'test_user_01', user_password = "3211").id
Traceback (most recent call last):
  File "<console>", line 1, in <module>
AttributeError: 'QuerySet' object has no attribute 'id'
>>> User.objects.filter(user_name = 'test_user_01', user_password = "3211").get()
Traceback (most recent call last):
  File "<console>", line 1, in <module>
  File "/Users/jy-m1/Library/Mobile Documents/com~apple~CloudDocs/code/code/django_jwt_demo/lib/python3.10/site-packages/django/db/models/query.py", line 650, in get
    raise self.model.DoesNotExist(
app.models.User.DoesNotExist: User matching query does not exist.
>>> User.objects.filter(user_name = 'test_user_01', user_password = "321").get()
<User: User object (6)>
```
