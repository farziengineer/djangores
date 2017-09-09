# Django Resources

## Is Django MVC?
https://docs.djangoproject.com/en/dev/faq/general/#django-appears-to-be-a-mvc-framework-but-you-call-the-controller-the-view-and-the-view-the-template-how-come-you-don-t-use-the-standard-names <br>

https://stackoverflow.com/questions/6621653/django-vs-model-view-controller

```
Model = Model in Django
Views = Templates in Django
Controller = Views in Django
```

## What happens when you type a URL in your Django powered website <br>

https://docs.djangoproject.com/en/1.11/topics/http/urls/#how-django-processes-a-request <br>

## Forward slash at the end of url in django

https://stackoverflow.com/questions/4438064/django-url-with-automatic-slash-adding <br>
https://stackoverflow.com/questions/1596552/django-urls-without-a-trailing-slash-do-not-redirect


## Reverse resolution of URLs

1. Hard coding of URLs is an anti-pattern.
2. It is non-scalable and error prone.
3. Violates the DRY philosopy of Django.

https://docs.djangoproject.com/en/1.11/topics/http/urls/#reverse-resolution-of-urls

Django provides tools for performing ```URL``` reversing that match the different layers where URLs are needed:

1. In templates: Using the ```url```  template tag.
2. In Python code: Using the ```reverse()``` function.
3. In higher level code related to handling of URLs of Django model instances: The ```get_absolute_url()``` method.

Example for reverse url in templates.
```html
<a href="{% url 'news-year-archive' 2012 %}">2012 Archive</a>
{# Or with the year in a template context variable: #}
<ul>
{% for yearvar in year_list %}
<li><a href="{% url 'news-year-archive' yearvar %}">{{ yearvar }} Archive</a></li>
{% endfor %}
</ul>
```
Example for reverse url in python code.
```python
from django.urls import reverse
from django.http import HttpResponseRedirect

def redirect_to_year(request):
    # ...
    year = 2006
    # ...
    return HttpResponseRedirect(reverse('news-year-archive', args=(year,)))
```

## URL namespaces

https://docs.djangoproject.com/en/1.11/topics/http/urls/#url-namespaces <br>
URL namespaces allow you to uniquely reverse named URL patterns even if different applications use the same URL names. It’s a good practice for third-party apps to always use namespaced URLs. <br> 
A good example of namespacing: <br>
https://stackoverflow.com/questions/19171570/a-real-example-of-url-namespace

# Object Oriented 

Python functions are **first class** . <br>
Python functions are **closure** . <br>

## First class functions in python
A language is said to support first class functions which supports passing the function to another function, returning functions from another functions and setting functions to variables. <br>
[ What is first class function in Python SO ](https://stackoverflow.com/questions/27392402/what-is-first-class-function-in-python) <br>
https://www.youtube.com/watch?v=kr0mpwqttM0&list=PLzTAO9z9xIreYGpvZpQqmE_z12ijDqFun&index=1

## Closures
https://www.youtube.com/watch?v=swU3c34d2NQ&index=2&list=PLzTAO9z9xIreYGpvZpQqmE_z12ijDqFun <br>
First Class Functions are just the concept that functions can be used like any other objects in your code. Closures use first class functions in a specific manner.

In simple terms a ```closure``` is a ```inner function``` that remembers and has access to variables in ```local scope``` in which it was created even if ```outer function``` has finished execution.

**Objects are data with methods attached, closures are functions with data attached.**
```python
def make_counter():
    i = 0
    def counter(): # counter() is a closure
        nonlocal i
        i += 1
        return i
    return counter

c1 = make_counter()
c2 = make_counter()

print (c1(), c1(), c2(), c2())
# -> 1 2 1 2
```
[ What is a closure SO ](https://stackoverflow.com/questions/13857/can-you-explain-closures-as-they-relate-to-python)




## Difference between calling a function first class and closure.
https://stackoverflow.com/questions/37531840/swift-any-difference-between-closures-and-first-class-functions


## Decorators in Python
https://stackoverflow.com/questions/739654/how-to-make-a-chain-of-function-decorators/1594484#1594484

## Yield in Python
https://stackoverflow.com/questions/231767/what-does-the-yield-keyword-do/231855#231855

## Metaclasses in Python
https://stackoverflow.com/questions/100003/what-is-a-metaclass-in-python

