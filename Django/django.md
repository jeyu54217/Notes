**CONTENTS**
- [Settting](#settting)
- [Install](#install)
- [Start](#start)
- [ORM Migration](#orm-migration)
- [Test](#test)
  
# Settting
```bash
python3 -m django --version
```
```bash
python3 -m django help
```
```bash
export DJANGO_SETTINGS_MODULE=<proj_name>.settings
```
```bash
python3 manage.py check --deploy --settings=<proj_name>.settings
```
# Install
```bash
pip install Django
```
```bash
pip uninstall django
``` 
# Start
```bash
django-admin startproject <.../proj_name_core>
```
```bash
cd <.../proj_name_core>
```
```bash
python3 manage.py startapp <app_name>
```
```python
INSTALLED_APPS = [
    # other apps
    '<app_name>',
]
```
# ORM Migration
```bash
python3 manage.py makemigrations
```
```bash
python3 manage.py migrate
```
- Examining the real sql statements in a migrations file
    ```bash
    python3 manage.py sqlmigrate <myapp> <0001_initial>
    ```
    ```sql
    BEGIN;
    --
    -- Create model MyModel
    --
    CREATE TABLE "myapp_mymodel" (
        "id" integer NOT NULL PRIMARY KEY AUTOINCREMENT,
        "name" varchar(100) NOT NULL
    );
    COMMIT;
    ``` 
# Test
```bash
python manage.py runserver 8000
```
```bash
python3 manage.py createsuperuser --email <email> --username <name>
```
- Django Shell
    ```bash
    python3 manage.py shell
    ```
    ```bash
    from <app.models> import <Table>
    ```
    ```bash
    exit()
    ```
