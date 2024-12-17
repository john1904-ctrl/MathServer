# Ex.05 Design a Website for Server Side Processing
## Date:
29/11/2024
## AIM:
 To design a website to calculate the power of a lamp filament in an incandescent bulb in the server side. 


## FORMULA:
P = I<sup>2</sup>R
<br> P --> Power (in watts)
<br> I --> Intensity
<br> R --> Resistance

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

## PROGRAM :
```
math.html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Lamp Power Calculator</title>
    <style>
        body {
            margin: 0;
            padding: 20px;
            background: linear-gradient(120deg, #3b82f6, #06b6d4);
            font-family: 'Arial', sans-serif;
            color: #ffffff;
        }

        h1 {
            text-align: center;
            font-size: 36px;
            margin-bottom: 20px;
            color: #fff;
        }

        form {
            display: grid;
            grid-template-columns: 1fr 2fr;
            gap: 15px;
            max-width: 700px;
            margin: 0 auto;
        }

        label {
            font-size: 16px;
            font-weight: bold;
            align-self: center;
        }

        input {
            padding: 10px;
            border: none;
            border-radius: 5px;
            font-size: 14px;
            outline: none;
        }

        input:focus {
            box-shadow: 0 0 5px rgba(0, 0, 0, 0.3);
        }

        button {
            grid-column: span 2;
            padding: 12px;
            background-color: #2563eb;
            color: white;
            border: none;
            border-radius: 5px;
            font-size: 16px;
            cursor: pointer;
            transition: background-color 0.3s;
        }

        button:hover {
            background-color: #1e40af;
        }

        .result {
            grid-column: span 2;
            margin-top: 20px;
            font-size: 18px;
        }

        .result input {
            background: rgba(255, 255, 255, 0.1);
            border: 1px solid #fff;
            color: #fff;
            text-align: center;
        }    
    </style>
</head>
<body>
    <h1 align="center">Lamp Power Calculator</h1>
    <form method="POST">
        {% csrf_token %}
        <label for="intensity">Intensity (W/m²):</label>
        <input type="text" id="intensity" name="intensity" placeholder="Enter intensity" value="{{ I }}">

        <label for="resistance">Resistance (Ω):</label>
        <input type="text" id="resistance" name="resistance" placeholder="Enter resistance" value="{{ R }}">

        <button type="submit">Calculate</button>

        <div class="result">
            <label for="power">Calculated Power (W):</label>
            <input type="text" id="power" value="{{ power }}" readonly>
        </div>
    </form>
</body>
</html>


view.py

from django.shortcuts import render 
def power(request): 
    context={} 
    context['power'] = "0" 
    context['I'] = "0" 
    context['R'] = "0" 
    if request.method == 'POST': 
        print("POST method is used")
        I =float( request.POST.get('intensity','0'))
        R = float(request.POST.get('resistance','0'))
        print('request=',request) 
        print('intensity=',I) 
        print('resistance=',R) 
        power = (((I)**2) * (R))
        context['power'] = power 
        context['I'] = I
        context['R'] = R 
        print('Power=',power) 
    return render(request,'mathapp/math.html',context)

urls.py

from django.contrib import admin 
from django.urls import path 
from mathapp import views 
urlpatterns = [ 
    path('admin/', admin.site.urls), 
    path('areaofrectangle/',views.power,name="areaofrectangle"),
    path('',views.power,name="areaofrectangleroot")
]
```


## SERVER SIDE PROCESSING:
![alt text](<Screenshot (51).png>)


## HOMEPAGE:
![alt text](<Screenshot (50).png>)

## RESULT:
The program for performing server side processing is completed successfully.
