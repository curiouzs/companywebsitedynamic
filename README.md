# Dynamic Website Design for a Manufacturing Company
## AIM:
To design a dynamic website for a chip manufacturing company.

## DESIGN STEPS:
### Step 1: 
Requirement collection.
### Step 2:
Creating the layout using HTML and CSS.
### Step 3:
Updating the sample content.
### Step 4:
Choose the appropriate style and color scheme.
### Step 5:
Validate the layout in various browsers.
### Step 6:
Validate the HTML code.
### Step 7:
Create a database model and migrate the database.
### Step 8:
Retrieve data from database and display it in a dynamic webpage.
### Step 9:
Publish the website in the given URL.

## PROGRAM:
### base.html
```
{% load static %}
<!DOCTYPE html>
<html lang="en">

<head>
    <title>TESLA INDUSTRIES</title>
    <link rel="stylesheet" href="{% static 'css/layout.css' %}">
    <link rel="icon" href="{% static 'img/cchip2.jpeg' %}" type="image/x-icon">

</head>

<body>
    <div class="container">
        <div class="banner">
            TESLA INDUSTRIES
        </div>
        <div class="menu">
            <div class="menuitem"><a href="/home">Home</a></div>
            <div class="menuitem"><a href="/products">Products</a></div>
            <div class="menuitem"><a href="/people">People</a></div>
            <div class="menuitem"><a href="/contact">Contact Us</a></div>
        </div>
        <div class="content">
            {% block content %}
            {% endblock  %}
        </div>
        <div class="footer">
            Copyright © 2021 Tesla Industries, Developed by Lokesh Krishnaa M.
        </div>
    </div>
</body>

</html>
```

### home.html
```
{% extends "website/base.html" %}


{% block content %}

<div class="homecontent">
    <h1>About Us</h1>
    <img src="/static/img/burj.jpeg" alt="Building">
    <div class="contenttext">
        Tesla Industries, provides a broad range of semiconductor and infrastructure software applications that serve the
        data center, networking, software, broadband, wireless, and storage and industrial markets. Common applications
        for its products include: data center networking, home connectivity, broadband access, telecommunications
        equipment, smartphones, base stations, data center servers and storage, factory automation, power generation and
        alternative energy systems, displays, and mainframe operations and management, and application software
        development. Some of Silicon's core technologies and products include:
        <ul>
            <li>Memory Chips</li>
            <li>SATA HDD</li>
            <li>SATA SSD </li>
            <li>Broadband Modems</li>
            <li>Wifi Devices</li>
            <li>Switching Devices</li>
            <li>Optical Sensors</li>
        </ul>
    </div>
</div>
{% endblock  %}
```
### products.html
```
{% extends "website/base.html" %}

{% block content %}
<div class="productcontent">
    <h1 id="premium">Our Premium Products</h1>
    <div class="productitems">
        {% for products in productss %}
        <div class="productitem">
            
            <div class="productsname"><strong>{{ products.name }}</strong></div>
            <div class="itemimage">
                <img src="{{ products.photo.url }}" alt="product image" height="270" width="270">
            </div>
            <div class="productsprice"><strong>RS.{{ products.price }}.00</strong></div>
            <hr>
        </div>
        {% endfor %}
    </div>
</div>
{% endblock  %}

         
```
### people.html
```  
{% extends "website/base.html" %}

{% block content %}
        <div class="row">
        {% for people in peoples %}
            <div class="column">                
                <div class="designation"><strong><u></u>{{ people.designation }}</u></strong></div>
                <img src="{{ people.photo.url }}" alt="executive image" width="270" height="270">
                <div class="membername"><strong><u>{{ people.name }}</u></strong></div>
            </div>
            {% endfor %}
        </div>
{% endblock  %}
```
### contact.html
```
{% extends "website/base.html" %}

{% block content %}

<div class="class1">
    <div>
        <img src="/static/img/contact.jpeg" alt="contact" height="180px" width="63%">
    </div>
    <div>
        <h1>
            <centre>Contact</centre>
        </h1> <br>
        <h3><strong>EMAIL:</strong> starkind@yahoo.com</h3>
        <h3><strong>PHONE:</strong> 999-888-77-66</h3>
        <h3><strong>ADDRESS</strong>: No:3 Stark Tower, New York City, USA</h3>
        <br> <br> <br>
    </div>

    <footer id="s1">Copyright &COPY; 2021 Tesla Industries, Developed by Lokesh Krishnaa M.</footer>
</div>


{% endblock %}
```

### MODELS.PY
```
from django.db import models
from django.contrib import admin

# Create your models here.
class people(models.Model):
    name = models.CharField(max_length=100)
    designation = models.CharField(max_length=100)
    photo = models.ImageField(upload_to='photos/')

class peopleAdmin(admin.ModelAdmin):
    list_display = ('name', 'designation', 'photo')

class products(models.Model):
    name = models.CharField(max_length=100)
    price = models.IntegerField()
    photo = models.ImageField(upload_to='photos/')
class productsAdmin(admin.ModelAdmin):
    list_display = ('name', 'price', 'photo')

```

### ADMIN.PY:
```
from django.contrib import admin
from .models import people,peopleAdmin
from .models import products,productsAdmin


# Register your models here.

admin.site.register(people,peopleAdmin)

admin.site.register(products,productsAdmin)

```
## OUTPUT: 
![output](./static/img/homeout.jpg)

![output](./static/img/prodout.jpg)

![output](./static/img/peopleout.jpg)

![output](./static/img/contout.jpg)

### ADMIN PAGE:

![output](./static/img/adminpeople.jpg)

![output](./static/img/adminprod.jpg)



## CODE VALIDATION REPORT:
![output](./static/img/home.jpg)

![output](./static/img/product.jpg)

![output](./static/img/people.jpg)

![output](./static/img/contactd.jpg)

## RESULT:
Thus a website is designed for the chip manufacturing company and is hosted in the URL http://loki.student.saveetha.in:8000/home HTML code is validated.