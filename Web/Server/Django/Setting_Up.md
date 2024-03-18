**CONTENTS**
- [Install](#install)
- [Create New Project](#create-new-project)
- [ORM Migration](#orm-migration)
- [Testing](#testing)
  
# Install
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

# Start Project
- ```bash
   django-admin startproject <.../proj_name/core>
   ```
# Create App
1. ```bash
   cd <...proj_name/core>
   ```
2. ```bash
   python3 manage.py startapp <app_name>
   ```
3. ```python
   INSTALLED_APPS = [
   
        '<app_name>',
   ]
   ```
# ORM Migration
1. Create new DB **```migrations```** files based on the changes of Django models
    ```bash
    python3 manage.py makemigrations
    ```
2. Apply database migrations to the **```actual DB```** 
    ```bash
    python3 manage.py migrate
    ```
- (Optional) Examining the real sql statements in a **```migrations```** file
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
# Testing
- Test Server
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
