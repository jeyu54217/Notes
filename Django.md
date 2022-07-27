
### General
```bash
python -m django help
```
```bash
python -m django --version
```
```bash
export DJANGO_SETTINGS_MODULE=<proj_name>.settings
```

### Start
```bash
pip install Django
```
```bash
django-admin startproject <proj_name>
```
```bash
python manage.py startapp <app_name>
```
```bash
python manage.py sqlmigrate <app_label> <migration_name 0001>
```
https://docs.djangoproject.com/en/4.0/ref/django-admin/#sqlmigrate
### Merge
```bash
python manage.py makemigrations
```
```bash
python manage.py migrate --settings=<proj_name>.settings
```
```bash
python manage.py check --deploy --settings = <proj_name>.settings
```
### Test
```bash
python manage.py runserver 8000
```
```bash
python manage.py createsuperuser
```
