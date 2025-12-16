# Ex.04 Design a Website for Server Side Processing
## Date:16-12-2025
## AIM:
To create a web page to calculate vehicle mileage and fuel efficiency using server-side scripts.

## FORMULA:
M = D / F
<br> M --> Mileage (in km/l)
<br> D --> Distance Travelled (in km)
<br> F --> Fuel Consumed (in l)

## DESIGN STEPS:

### Step 1:
Clone the repository from GitHub.

### Step 2:
Create Django Admin project.

### Step 3:
Create a New App under the Django Admin project.

### Step 4:
Create python programs for views and urls to perform server side processing.

### Step 5:
Create a HTML file to implement form based input and output.

### Step 6:
Publish the website in the given URL.

## PROGRAM:
```
math.html

<html>
<head>
    <title>Mileage Calculator</title>
    <style>
        body 
        {
            background: linear-gradient(rgb(254, 4, 4), black);
        }
        .id1 
        {
            text-align: center;
            color: black;
        }
        .box 
        {
            text-align: center;
            width: 30%;
            background:linear-gradient(rgb(5, 255, 80),blue);
            border: dashed 4px rgb(251, 254, 255);
            padding: 15px;
            margin: 50px auto;
            border-radius: 25px;
        }
    </style>
</head>
<body>
    <h1 class="id1">Mileage Calculation!</h1>
    <div class="box">
        <h2>Calculator</h2>
        <h3>MOTHISH.S(25010659)</h3>

        <form method="post">
            {% csrf_token %}
            <label>distance travelled..</label>
            <br>
            <input type="number" name="distance"> Km
            <br>
            <br>
            <label>fuel consumed</label>
            <br>
            <input type="number" name="liters"> L
            <br>
            <br>
            <button type="submit">Calculate</button>
            <br>
            <br>
            <label>kilometre travelled per Litre</label>
            <br>
            <input type="number" name="Mileage" value={{miles}}>Km/L
        </form>
    </div>
</body>
</html>

view.py

from django.shortcuts import render
def fmiles(request):
    km = int(request.POST.get('distance', 0))
    l = int(request.POST.get('liters', 0))
    miles = km / l if request.method == 'POST' and l != 0 else 0
    print("kilometers =", km)
    print("liters =", l)
    print("Mileage =", miles)
    return render(request, 'mathapp/math.html', {'km': km, 'l': l, 'miles': miles})

urls.py

from django.urls import path
from mathapp import views

urlpatterns = [
    path('', views.fmiles, name='fmiles'),
]
```

## OUTPUT - SERVER SIDE:
![alt text](<Screenshot 2025-12-16 092435.png>)

## OUTPUT - WEBPAGE:
![alt text](<Screenshot 2025-12-16 092427.png>)

## RESULT:
The a web page to calculate vehicle mileage and fuel efficiency using server-side scripts is created successfully.
