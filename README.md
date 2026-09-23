# HCL
## 1. Write a Python program which accepts a sequence of comma separated 4 digit binary numbers as its input and then check whether they are divisible by 5 or not. The numbers that are divisible by 5 are to be printed in a comma separated sequence. Example: 0100,0011,1010,1001 Then the output should be: 1010
### Program
```
numbers = input().split()
result = []
for num in numbers:
    if int(num, 2) % 5 == 0:
        result.append(num)
print(','.join(result))
```
### Output
<img width="1530" height="782" alt="image" src="https://github.com/user-attachments/assets/c0950f08-aa21-4831-9ef6-1851705c5977" />

## 2. Write a Python program that accepts a sentence and calculate the number of letters and digits.Suppose the following input is supplied to the program: hello world! 123 Then, the output should be: LETTERS 10 DIGITS 3
### Program 
```s = input()
letters = 0
digits = 0
for char in s:
    if char.isalpha():
        letters += 1
    elif char.isdigit():
        digits += 1
print("LETTERS", letters)
print("DIGITS", digits)
```
### Output
<img width="1533" height="786" alt="image" src="https://github.com/user-attachments/assets/3049f6f9-47de-4318-8a4a-859579a2caa9" />

## 3.Write a program which can compute the factorial of a given numbers.The results should be printed in a comma-separated sequence on a single line.Suppose the following input is supplied to the program:8 Then, the output should be:40320
### Program 
```
n=int(input())
fact=1
for i in range(1,n+1):
    fact *= i
print(fact)
```
### Output
<img width="1520" height="773" alt="image" src="https://github.com/user-attachments/assets/b18c7064-0127-4d2c-a082-7ad2eea5e65a" />
