This repository is my personal study log as I dive into the world of web development with Python and Django.
I'll be documenting my journey here, one day at a time.

Day 1: Why Django?
Django, a high-level Python web framework. 
---The "Batteries-Included" Philosophy 

Django's motto is that it comes with "batteries-included." This means it provides built-in tools for almost everything you'd need to build a complex website right out of the box:
* An admin interface
* User authentication (signing up, logging in/out)
* A system to talk to databases (the ORM)
* Form handling and security features

This approach helps with rapid development because you don't have to find and configure third-party libraries for common tasks.

The MVT Architecture (Model-View-Template)

Django follows a design pattern called MVT:
* Model: The data structure.
     This is how you define what your data looks like (e.g., a blog post has a title, content, and a publication date).
     The model is the single, definitive source of your data.
  
* View: The business logic.
     The view receives a web request, interacts with the models to get the necessary data, and passes that data to a template.
  
* Template: The presentation layer. This is the HTML file with special Django tags.
    It takes the data from the view and renders the final webpage that the user sees.

My Key Takeaways for Today:
* Django is designed for building big, data-driven applications quickly and securely.
* The MVT pattern separates the data (Model), logic (View), and presentation (Template), which keeps the code organized.
