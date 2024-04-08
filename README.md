# MSDS460_Assignment_1
from pulp import*

#define problem and variables
model = LpProblem("Diet Problem", LpMinimize)
b = LpVariable("Burrito", 0, None, LpContinuous)
o = LpVariable("Oats", 0, None, LpContinuous)
y = LpVariable("Yogurt", 0, None, LpContinuous)
t = LpVariable("Tofu", 0, None, LpContinuous)
s = LpVariable("Shake", 0, None, LpContinuous)

#objective function
model += 3.13 * b + 0.38 * o + 1.31 * y + 0.41 * t + 1.30 * s

#constraints
model += 560 * b + 55 * y + 15 * t + 210 * s <= 35000 #Sodium (mg)
model += 290 * b + 150 * o + 120 * y + 90 * t + 220 * s >= 14000 #Energy(kcal)
model += 18 * b + 5 * o + 17 * y + 9 * t + 15 * s >= 350 #Protein (g)
model += 0.3 * b + 10 * s >= 140 #Vitamin D (mcg)
model += 130 * b + 20 * o + 200 * y + 130 * t + 325 * s >= 9100 #Calcium (mg)
model += 3.1 * b + 1.5 * o + 1.44 * t + 3.6 * s >= 126 #Iron (mg)
model += 370 * b + 150 * o + 260 * y + 94 * t + 470 * s >= 32900 #Potassium (mg)

#solve
model.solve()

for v in model.variables:
    print(v.name, "=", v.varValue, "servings")
    
print("Price =", "$",value(model.objective))


![big sur burrito](https://github.com/mtrimble27/MSDS460_Assignment_1/assets/72757621/79fdfb5b-9adf-4f55-b4ae-df1c7fcf7d1e)
![oats](https://github.com/mtrimble27/MSDS460_Assignment_1/assets/72757621/7a83c3be-d9da-4f86-b8a1-25ba45300596)
![yogurt](https://github.com/mtrimble27/MSDS460_Assignment_1/assets/72757621/0725b770-8060-4fcc-ac05-2897f122e1ee)
![tofu](https://github.com/mtrimble27/MSDS460_Assignment_1/assets/72757621/13082b19-82da-4a6e-9b41-64477573dc98)
![Carnation Breakfast Shake](https://github.com/mtrimble27/MSDS460_Assignment_1/assets/72757621/fe35f672-1bc3-47a4-9804-f4eead70a5da)
