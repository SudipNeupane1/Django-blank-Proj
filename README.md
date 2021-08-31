# Create  a Local  and Blank Django Project


## A guide for creating a Dajngo project for use in both Local and Production environment

___

**NOTE** *cd ~/* is an mac/linux command.


1. create Dev Directory for General Project Storage

   ```
        cd ~/
        mkdir Dev && Dev
   ```
2. Create Virtual Environment

    ```
        cd ~/Dev
        pyhton3 -m venv my_env
        cd my_env
    ``` 
        activate on Mac/Linux
    ```
        source bin/activate
    ```
3. Install Django and Start Project

    ```
        pip install django 

        mkdir  proj && proj

        django-admin.py startproject djapp.
    ```

4. Create New Settings Module The purpose of this is to create a settings module that works for both local and production use. (optional)

    ```
        # currently working in 
        # ~/Dev/my_env/proj/djapp/ on mac/linux
        
        cd djapp
        mkdir settings && cd settings
    ```
    Create *__init.py__*   within new Settings folder to make it a module.Add the following:
    
    ```
        # current working in 
        # ~/Dev/my_env/proj/djapp/settings/ on mac/linux 
        echo "from .base import *
        from .production import *
        try:
            from .local import *
        except:
            pass
        " > __init__.py
    ```
    Change **BASE_DIR** in **settings.py**:
    ```
        BASE_DIR = os.path.dirname(os.path.dirname(os.path.abspath(__file__)))
        # to
        BASE_DIR = os.path.dirname(os.path.dirname(os.path.dirname(os.path.abspath(__file__))))
    ```
    Move default __settings.py__ into new __settings__ module and rename __settings.py__ to __base.py__:

    ```
        # mac/linux
        mv ~/Dev/my_env/proj/djapp/settings.py ~/Dev/my_env/proj/settings/base.py:

    ```
    Copy Local settings (local.py)to make new (base.py & productions.py)file:
    ```
        #mac/linux
        cp ~/Dev/my_env/proj/djapp/settings/base.py ~/Dev/my_env/proj/djapp/settings/local.py
        cp ~/Dev/my_env/proj/djapp/settings/base.py ~/Dev/my_env/proj/djapp/settings/production.py
    ```
5. Some other common installations (optional):

    ```
        # for a postgresql database
        pip install psycopg2

        #for a mysql database
        pip install MySql-python

        # for use on heroku
        pip install gunicorn dj-database-url

        pip install django-crispy-forms
        pip install pillow

    ```

6. Create __requirements.txt__ file

    ``` 
        pip freeze > requirements.txt
    ```

7. Run Migrations & Createsuperuser
    ```
        python mange.py migrate
        python mange.py createsuperuser

    ```

That's it.




        



    





