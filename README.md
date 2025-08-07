# webdev-notes
My personal notes and study log for learning server-side development.

Day-1 
notes on Django basics
Day-2 
starting a Django project
Day 3
notes on Django Apps & Migrations
Day 4: The Django Admin Site**

Today I explored one of Django's most powerful "batteries": the **Admin Site**. It's an automatic, professional-grade interface for managing the data in your models.

Activating the Admin: To make a model appear in the admin site, you must register it in your app's `admin.py` file.
    ```python
    from django.contrib import admin
    from .models import Post

    admin.site.register(Post)
    ```
**Creating an Admin User**: You need to create a "superuser" account to access the admin interface.
    ```bash
    python manage.py createsuperuser
    ```
* **Result**: After registering the model and creating a superuser, you can log in at `/admin/` and get a full CRUD (Create, Read, Update, Delete) interface for your data without writing any front-end code.

---


Today I learned how Django knows which view to execute for a specific web address. This is handled by the **`urls.py`** file.

* **Purpose**: The `urls.py` file is the website's "address book" or GPS
