## 1.Print all prime numbers between input range (Ex – input 20 50, prints all prime numbers between 20 and 50).
### Program
```
start = int(input("Enter starting number: "))
end = int(input("Enter ending number: "))
print("Prime numbers:")
for num in range(start, end + 1):
    if num > 1:
        for i in range(2, num):
            if num % i == 0:
                break
        else:
            print(num, end=" ")
```
### Output
<img width="1237" height="437" alt="image" src="https://github.com/user-attachments/assets/1f096dbc-0d9f-499c-915e-539a1b71d576" />

## 2.Factorial using recursion
### Program
```
def factorial(n):
    if n == 0 or n == 1:
        return 1
    else:
        return n * factorial(n - 1)
num = int(input("Enter a number: "))
print("Factorial:", factorial(num))
```
### Output
<img width="1422" height="771" alt="image" src="https://github.com/user-attachments/assets/929537a4-af5b-4bd8-97bc-e24203aca9d1" />

##  3.Square of numbers using lambda
### Program
```
square = lambda x: x * x
num = int(input("Enter a number: "))
print("Square:", square(num))
```
### Output
<img width="1488" height="466" alt="image" src="https://github.com/user-attachments/assets/3fbc506c-8b18-4f9f-9519-1a7ba7504b78" />

##   4.Find the second largest element in a list
### Program
```
numbers = [10, 25, 8, 45, 32, 18]
numbers = list(set(numbers))
numbers.sort()
print("List:", numbers)
print("Second largest element:", numbers[-2])
```
### Output
<img width="1348" height="550" alt="image" src="https://github.com/user-attachments/assets/b45aedf4-a2ef-44cc-a1af-ac209ef9a6cb" />

## 5.Count frequency of characters in a string
### Program
```
text = input("Enter a string: ")
frequency = {}
for char in text:
    if char in frequency:
        frequency[char] += 1
    else:
        frequency[char] = 1
print("Character frequency:")
for char, count in frequency.items():
    print(char, ":", count)
```
### Output
<img width="1506" height="627" alt="image" src="https://github.com/user-attachments/assets/329770de-6006-4c22-838b-09b69f16fd0e" />

## 6.Calculate area of a circle using math library.
### Program 
```
import math
radius = float(input("Enter radius of the circle: "))
area = math.pi * radius * radius
print("Area of circle:", area)
```
### Output
<img width="1368" height="346" alt="image" src="https://github.com/user-attachments/assets/b5ce181e-b950-45e6-b208-895d3933e253" />

## 7.Reverse a string without using built‑in reverse
### Program
```
text = input("Enter a string: ")
reversed_text = ""
for char in text:
    reversed_text = char + reversed_text
print("Reversed string:", reversed_text)
```
### Output
<img width="1462" height="592" alt="image" src="https://github.com/user-attachments/assets/143a4f4e-3343-473a-923a-c2f377d61e1b" />

## 8.Remove duplicates from a list
### Program
```
numbers = [10, 20, 10, 30, 20, 40, 30]
unique_numbers = []
for num in numbers:
    if num not in unique_numbers:
        unique_numbers.append(num)
print("Original list:", numbers)
print("List after removing duplicates:", unique_numbers)
```
### Output
<img width="1493" height="466" alt="image" src="https://github.com/user-attachments/assets/5492a1d4-8f9f-4b7c-acd5-63fae63c5b62" />

## 9.Merge two dictionaries
### Program
```
dict1 = {"Name": "Indu", "Age": 21}
dict2 = {"Course": "AI&DS", "College": "Saveetha"}
merged_dict = {**dict1, **dict2}
print("Merged dictionary:")
print(merged_dict)
```
### Output
<img width="1465" height="557" alt="image" src="https://github.com/user-attachments/assets/0329e1e2-3d15-48c8-9ef5-18837ac62f3e" />

## 10.Fibonacci series using recursion
### Program
```
def fibonacci(n):
    if n <= 1:
        return n
    else:
        return fibonacci(n - 1) + fibonacci(n - 2)
num = int(input("Enter number of terms: "))
print("Fibonacci series:")
for i in range(num):
    print(fibonacci(i), end=" ")
```
### Output
<img width="1534" height="664" alt="image" src="https://github.com/user-attachments/assets/7684484f-6a65-4170-a89a-755c053b4a86" />


