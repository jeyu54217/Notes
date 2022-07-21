

```bash
python -m django help
```
```bash
python -m django --version
```
```bash
python manage.py createsuperuser
```
```bash
pip install Django
```
```bash
django-admin startproject <pj_name>
```
```bash
python manage.py startapp <app_name>
```

```bash
python3 manage.py makemigrations
```
```bash
python3 manage.py migrate
```
```bash
python manage.py runserver 8000
```
```bash
python manage.py sqlmigrate <app_label> <migration_name 0001>
https://docs.djangoproject.com/en/4.0/ref/django-admin/#sqlmigrate
```

```bash
python manage.py migrate --settings=Demo.settings.settings_local
```
```bash
export DJANGO_SETTINGS_MODULE=Demo.settings.settings_local
```
```bash
python manage.py check
```
```bash
python manage.py check --deploy --settings=Demo.settings.settings_prod
```