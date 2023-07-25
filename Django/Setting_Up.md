**CONTENTS**
- [Settting Up](#settting-up)
- [Create New Project](#create-new-project)
- [ORM Migration](#orm-migration)
- [Test](#test)
  
# Settting Up
- **Check**
    ```bash
    python3 -m django --version
    ```
- **Install**
    ```bash
    pip install Django
    ```
- **Uninstall**
    ```bash
    pip uninstall django
    ```
```bash
export DJANGO_SETTINGS_MODULE=<proj_name>.settings
```
```bash
python3 manage.py check --deploy --settings=<proj_name>.settings
```

# Create New Project
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
- Create new DB **```migrations```** files based on the changes of Django models
    ```bash
    python3 manage.py makemigrations
    ```
- Apply database migrations to the **```actual DB```** 
    ```bash
    python3 manage.py migrate
    ```
- Examining the real sql statements in a **```migrations```** file
    ```bash
    python3 manage.py sqlmigrate <app_name> <0001_initial>
    ```
    - e.x.
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
