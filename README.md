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


**Day 5: Views & Templates**

Today was about building the public-facing pages of the website by connecting logic with presentation.

* **Views (`views.py`)**: A view is a Python function that acts as the "chef." It receives a user's web request, fetches data from the **Model** (the pantry), and passes that data to a template.
* **Templates (`templates/` folder)**: A template is an HTML file that acts as the "plating." It receives data from the **View** and uses the **Django Template Language (DTL)** to display it.
    * `{{ variable }}` is used to display a variable's value.
    * `{% for item in list %}` is used for logic, like loops.
* **The `render()` function** is the bridge that combines a template with data from a view to produce the final HTML page.

---
 **Day 6: URL Routing**
Today I learned how Django knows which view to execute for a specific web address. This is handled by the **`urls.py`** file.

* **Purpose**: The `urls.py` file is the website's "address book" or GPS. It contains a list of URL patterns and maps each one to a specific view function.
* **The `urlpatterns` list**: This is a Python list that holds all the URL routes for your app.
* **The `path()` function**: Each route is defined using `path()`.
    ```python
    from django.urls import path
    from . import views

    urlpatterns = [
        # When a user visits '/blog/', run the post_list view.
        path('blog/', views.post_list, name='post_list_page'),
    ]
    ```
This tells Django exactly what to do when a user navigates to a specific page on your site.


**Day 7: Handling User Input with Forms**

Today I learned how Django handles HTML forms to accept and process user input securely.

* **Django Forms**: The framework provides a `Form` class that represents an HTML form. It handles rendering the form fields, validating submitted data, and cleaning it up for use in your views.
* **`ModelForm`**: A powerful subclass of `Form` that automatically creates a form based on an existing **Model**. This saves you from having to redefine the form fields if they are the same as your model's fields.
* **Rendering a Form**: In a view, you create an instance of your form class and pass it to the template. In the template, you can render the entire form with all its fields and labels using a single tag, like `{{ form.as_p }}`.
* **Validation**: When a user submits a form, you can call `form.is_valid()` in your view. Django automatically runs validation checks (e.g., ensuring an email field looks like an email) and reports any errors.

---

### **Day 8: Forms, Static Files & Project Wrap-up**

Today is the final day of my foundational Django study. I'm combining the last key topics: handling user input with **Forms** and adding styles and scripts with **Static Files**.

#### 1. Handling User Input with Forms

Django provides a secure and efficient way to manage HTML forms.

* **Purpose**: Forms are used to collect data from users, such as in a contact form, a search bar, or a user registration page. Django's form system handles rendering the form fields, validating the submitted data, and cleaning it for use.
* **Creating a Form**: You define the form's fields in a `forms.py` file.
    ```python
    # forms.py
    from django import forms

    class ContactForm(forms.Form):
        name = forms.CharField(max_length=100)
        email = forms.EmailField()
        message = forms.CharField(widget=forms.Textarea)
    ```
* **Using it in a View**: The view handles the logic for both displaying the empty form and processing the submitted data.
    ```python
    # views.py
    def contact_view(request):
        if request.method == 'POST':
            form = ContactForm(request.POST)
            if form.is_valid():
                # Process the data, e.g., send an email
                print(form.cleaned_data)
                return redirect('/success/')
        else:
            form = ContactForm()
        return render(request, 'contact.html', {'form': form})
    ```

#### 2. Styling with Static Files

**Static files** are the CSS, JavaScript, and image files that make a website look good and feel interactive.

* **Configuration**: You tell Django where your static files are by setting `STATIC_URL` and `STATICFILES_DIRS` in `settings.py`. Typically, you create a `static` folder in your app's directory.
* **Using in a Template**: To link to a static file, you must first load the static tag library and then use the `static` tag.
    ```html
    {% load static %}

    <link rel="stylesheet" href="{% static 'css/main.css' %}">

    <img src="{% static 'images/logo.png' %}">
    ```

#### 3. Wrap-up & Next Steps

This week covered the essentials of building a Django application. The core concepts of **MVT, URL routing, forms, and static files** are the foundation for any project.

The journey doesn't end here. The next logical steps are:
* **Building a Full Project**: Apply these concepts to build a complete blog or to-do list application.
* **Django REST Framework (DRF)**: Learn how to build APIs with Django.
* **Deployment**: Learn how to put your application on a real web server for the world to see.

With this, my initial study week is complete. I'm ready to start building! 🚀
