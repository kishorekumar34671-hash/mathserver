# Ex.05 Design a Website for Server Side Processing
# Date:30.09.2025
# AIM:
To design a website to calculate the power of a lamp filament in an incandescent bulb in the server side.

# FORMULA:
P = I2R
P --> Power (in watts)
 I --> Intensity
 R --> Resistance

# DESIGN STEPS:
## Step 1:
Clone the repository from GitHub.

## Step 2:
Create Django Admin project.

## Step 3:
Create a New App under the Django Admin project.

## Step 4:
Create python programs for views and urls to perform server side processing.

## Step 5:
Create a HTML file to implement form based input and output.

## Step 6:
Publish the website in the given URL.

# PROGRAM :
```
math.html 

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Lamp Power Calculator</title>
    <style>
        body { 
            font-family: Arial, sans-serif; 
            background: #f0f0f0; 
            text-align: center; 
            margin-top: 80px;
        }
        .box {
            background: white;
            padding: 20px;
            border-radius: 10px;
            width: 350px;
            margin: auto;
            box-shadow: 0px 0px 10px rgba(0,0,0,0.2);
        }
        input, button {
            padding: 8px;
            margin: 8px;
            width: 80%;
        }
        button {
            background: #007BFF;
            color: white;
            border: none;
            cursor: pointer;
        }
        button:hover {
            background: #0056b3;
        }
        h2 {
            color: green;
        }
    </style>
</head>
<body>
    <div class="box">
        <h1>Power Calculator</h1>
        <form method="post">
            {% csrf_token %}
            <input type="number" step="any" name="intensity" placeholder="Enter Current (I in Amps)" required><br>
            <input type="number" step="any" name="resistance" placeholder="Enter Resistance (R in Ohms)" required><br>
            <button type="submit">Calculate Power</button>
        </form>

        
            <h2>Power = {{ power }} W</h2>
        
    </div>
</body>
</html>

views.py

from django.shortcuts import render

def kishore(request):
    power = 'I2R'
    if request.method == "POST":
        try:
            I = float(request.POST.get("intensity", 0))
            R = float(request.POST.get("resistance", 0))
            power = I**2 * R
            print("Current (I):", I)          # Debug print
            print("Resistance (R):", R)      # Debug print
            print("Calculated Power:", power) # Debug print
        except ValueError:
            power = "Invalid input"
            print("Error: Invalid input")     # Debug print
    return render(request, "math.html", {"power": power})

urls.py

from django.contrib import admin
from django.urls import path
from get import views

urlpatterns = [
    path('admin/', admin.site.urls),
     path('', views.kishore, name='kishore'),
]




```
# SERVER SIDE PROCESSING:
![alt text](<Screenshot 2025-09-30 133412.png>)
# HOMEPAGE:
![alt text](<Screenshot 2025-09-30 110809.png>)


# RESULT:
The program for performing server side processing is completed successfully.
