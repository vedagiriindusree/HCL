## 1.Write a function calculate(a, b, operation) that performs addition, subtraction, multiplication, or division based on the supplied operation.
### Program
```
def calculate(a, b, operation):
    if operation == "add":
        return a + b
    elif operation == "subtract":
        return a - b
    elif operation == "multiply":
        return a * b
    elif operation == "divide":
        if b != 0:
            return a / b
        else:
            return "Cannot divide by zero"
    else:
        return "Invalid operation"
a = int(input("Enter first number: "))
b = int(input("Enter second number: "))
operation = input("Enter operation: ")
print("Result:", calculate(a, b, operation))
```
### Output
<img width="1262" height="702" alt="image" src="https://github.com/user-attachments/assets/18eb88e5-7635-4a8a-a3db-76fa9233cb42" />

## 2.Write a function sum_numbers(*args) that accepts any number of arguments and returns their sum.
### Program
```
def sum_numbers(*args):
    total = 0
    for num in args:
        total += num
    return total
print("Sum:", sum_numbers(10, 20, 30, 40, 50))
```
### Output
<img width="1293" height="385" alt="image" src="https://github.com/user-attachments/assets/2a7b1c9f-9f4a-42b1-8638-f9df70aec341" />

## 3.Write a function employee(**args) that accepts employee information such as name, ID, department and salary, then displays the information.
### Program
```
def employee(**args):
    print("Employee Information:")
    for key, value in args.items():
        print(key, ":", value)
employee(
    name="Indu",
    ID=101,
    department="AI&DS",
    salary=35000
)
```
### Output
<img width="1303" height="590" alt="image" src="https://github.com/user-attachments/assets/dfbabc7d-8d22-48bd-8dc7-f7782b60fe70" />

## 4.Write a function remove_duplicates(lst) that returns a list containing only unique elements while preserving their original order.
### Program
```
def remove_duplicates(lst):
    unique = []
    for item in lst:
        if item not in unique:
            unique.append(item)
    return unique
numbers = [10, 20, 10, 30, 20, 40, 30, 50]
print("Original list:", numbers)
print("List after removing duplicates:", remove_duplicates(numbers))
```
### Output
<img width="1346" height="527" alt="image" src="https://github.com/user-attachments/assets/4670c2d5-5428-450b-9614-2e10b52a6be6" />

## 5.Using a lambda function, sort a list of tuples based on the second element. Example: [(1,5), (2,3), (4,1)].
### Program
```
numbers = [(1, 5), (2, 3), (4, 1)]
sorted_list = sorted(numbers, key=lambda x: x[1])
print("Original list:", numbers)
print("Sorted list:", sorted_list)
```
### Output
<img width="1468" height="616" alt="image" src="https://github.com/user-attachments/assets/ac1b9f4f-8fe7-4918-afc5-c54d8e8ddbc4" />
