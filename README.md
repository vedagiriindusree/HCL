## Question 1 – Student Marks Array
The marks obtained by five students in a subject are given as [78, 65, 89, 56, 92]. Create a NumPy array and display the array along with its basic properties.

### Program 
```
import numpy as np
marks = np.array([78, 65, 89, 56, 92])
print("Marks:", marks)
print("Number of elements:", marks.size)
print("Shape:", marks.shape)
print("Data type:", marks.dtype)
print("Number of dimensions:", marks.ndim)
```
### Output
<img width="1388" height="590" alt="image" src="https://github.com/user-attachments/assets/e9630a01-0193-46f1-ac2d-e1a8c9d27b39" />

## Question 2 – Student Marks Access
The marks of five students are stored in a NumPy array as [72, 85, 64, 90, 76]. Write a program to access and display specific student marks using NumPy indexing and slicing.

### Program
```
import numpy as np
marks = np.array([72, 85, 64, 90, 76])
print("Marks:", marks)
print("First student:", marks[0])
print("Third student:", marks[2])
print("Last student:", marks[-1])
print("First three students:", marks[:3])
print("Second to fourth students:", marks[1:4])
```
### Output
<img width="1471" height="402" alt="image" src="https://github.com/user-attachments/assets/4751ec58-9803-4448-b5f2-10d991bf5f57" />

## Question 3 – Subject-wise Marks
The marks obtained by five students in three subjects are given below. Create a NumPy array to represent the data and reshape it into an appropriate matrix format.
[78, 85, 90, 65, 72, 80, 88, 91, 84, 56, 62, 70, 95, 89, 92]

### Program 
```
import numpy as np
marks = np.array([
    78, 85, 90,
    65, 72, 80,
    88, 91, 84,
    56, 62, 70,
    95, 89, 92
])
matrix = marks.reshape(5, 3)
print("Original array:")
print(marks)
print("\nMarks matrix:")
print(matrix)
```
### Output
<img width="1408" height="372" alt="image" src="https://github.com/user-attachments/assets/044ef760-8ff3-4225-be98-33e6273f1ce3" />

## Question 4 – Internal and External Marks
The internal and external examination marks of five students are stored in two NumPy arrays. Write a program to calculate the final marks of each student using NumPy array operations.

### Program
```
import numpy as np
internal = np.array([20, 18, 22, 19, 21])
external = np.array([65, 70, 60, 68, 72])
final_marks = internal + external
print("Internal marks:", internal)
print("External marks:", external)
print("Final marks:", final_marks)
```
### Output
<img width="1202" height="397" alt="image" src="https://github.com/user-attachments/assets/e7942b0e-1ee6-4d41-a6b9-ad221f533d7a" />

## Question 5 – Pass Percentage Analysis
The marks obtained by five students are [45, 78, 56, 32, 91]. Using NumPy Boolean masking, identify the students who have secured 50 marks or above.

### Program
```
import numpy as np
marks = np.array([45, 78, 56, 32, 91])
passed = marks[marks >= 50]
print("Marks:", marks)
print("Students scoring 50 or above:", passed)
```
### Output
<img width="1276" height="382" alt="image" src="https://github.com/user-attachments/assets/825e1605-c176-4b45-a40e-1e73ea479148" />

## Question 6 – Average Marks
The marks of five students in three subjects are represented using a NumPy matrix. Write a program to calculate the average marks of each student.

### Program
```
import numpy as np
marks = np.array([
    [78, 85, 90],
    [65, 72, 80],
    [88, 91, 84],
    [56, 62, 70],
    [95, 89, 92]
])
average = np.mean(marks, axis=1)
print("Marks matrix:")
print(marks)
print("\nAverage marks of each student:")
print(average)
```
### Output
<img width="1461" height="416" alt="image" src="https://github.com/user-attachments/assets/706bf9d3-b5f1-44ce-b412-e4cdd62aa7ed" />

## Question 7 – Class Performance Statistics
The marks obtained by five students are [67, 82, 91, 74, 58]. Using NumPy statistical functions, determine the total, average, highest, lowest, and standard deviation of the marks.

### Program
```
import numpy as np
marks = np.array([67, 82, 91, 74, 58])
print("Marks:", marks)
print("Total:", np.sum(marks))
print("Average:", np.mean(marks))
print("Highest:", np.max(marks))
print("Lowest:", np.min(marks))
print("Standard deviation:", np.std(marks))
```
### Output
<img width="1357" height="370" alt="image" src="https://github.com/user-attachments/assets/6613123d-8251-4d24-8947-df0d3dc2defb" />

## Question 8 – Subject-wise Performance
The marks of five students in three subjects are stored in a NumPy matrix. Write a program to calculate the total marks obtained in each subject using an appropriate axis operation.

### Program
```
import numpy as np
marks = np.array([
    [78, 85, 90],
    [65, 72, 80],
    [88, 91, 84],
    [56, 62, 70],
    [95, 89, 92]
])
subject_total = np.sum(marks, axis=0)
print("Marks matrix:")
print(marks)
print("\nTotal marks in each subject:")
print(subject_total)
```
### Output
<img width="1200" height="440" alt="image" src="https://github.com/user-attachments/assets/4895ef4b-ba14-4568-a0ec-4a01a80ec707" />

## Question 9 – Student-wise Performance
The marks of five students in three subjects are stored in a NumPy matrix. Write a program to calculate the total marks obtained by each student using an appropriate axis operation.

### Program
```
import numpy as np
marks = np.array([
    [78, 85, 90],
    [65, 72, 80],
    [88, 91, 84],
    [56, 62, 70],
    [95, 89, 92]
])
student_total = np.sum(marks, axis=1)
print("Marks matrix:")
print(marks)
print("\nTotal marks of each student:")
print(student_total)
```
### Output
<img width="1281" height="508" alt="image" src="https://github.com/user-attachments/assets/93b83a67-5605-486e-9feb-b58462704c42" />

## Question 10 – Student Ranking
The total marks obtained by five students are [245, 278, 219, 290, 256]. Use NumPy sorting and indexing operations to arrange the marks in order and determine the ranking of the students.

### Program
```
import numpy as np
marks = np.array([245, 278, 219, 290, 256])
sorted_marks = np.sort(marks)[::-1]
ranking = np.argsort(marks)[::-1]
print("Original marks:", marks)
print("Marks in descending order:", sorted_marks)
print("\nStudent ranking:")
for rank, index in enumerate(ranking, start=1):
    print("Rank", rank, "- Student", index + 1, "-", marks[index])
```
### Output
<img width="1326" height="482" alt="image" src="https://github.com/user-attachments/assets/737842b6-dfa6-47f0-82fc-ee4aa88b9f8c" />

## Question 11 – Duplicate Marks Analysis
The marks obtained by five students are [85, 92, 85, 76, 92]. Use NumPy functions to identify the unique marks obtained by the students.

### Program 
```
import numpy as np
marks = np.array([85, 92, 85, 76, 92])
unique_marks = np.unique(marks)
print("Marks:", marks)
print("Unique marks:", unique_marks)
```
### Output
<img width="1230" height="277" alt="image" src="https://github.com/user-attachments/assets/8de0a679-0da9-41d7-8272-bd15fedb959a" />

## Question 12 – Missing Marks
The marks of five students are represented as [78, 85, np.nan, 92, 67], where np.nan represents a missing mark. Write a NumPy program to calculate the average marks without considering the missing value.

### Program
```
import numpy as np
marks = np.array([78, 85, np.nan, 92, 67])
average = np.nanmean(marks)
print("Marks:", marks)
print("Average without missing value:", average)
```
### Output
<img width="1322" height="286" alt="image" src="https://github.com/user-attachments/assets/cef11ce7-9257-4d31-a4e9-6d12e3d61d42" />

## Question 13 – Grade Classification
The marks obtained by five students are [95, 82, 74, 61, 45]. Using NumPy conditional operations, classify the students into appropriate grade categories based on their marks.

### Program
```
import numpy as np
marks = np.array([95, 82, 74, 61, 45])
grades = np.select(
    [
        marks >= 90,
        marks >= 80,
        marks >= 70,
        marks >= 60
    ],
    [
        "A",
        "B",
        "C",
        "D"
    ],
    default="F"
)
print("Marks:", marks)
print("Grades:", grades)
```
### Output
<img width="1287" height="486" alt="image" src="https://github.com/user-attachments/assets/84f67a03-4800-410d-952b-b8e4fffec848" />

## Question 14 – Random Marks Generation
Generate marks for five students using NumPy's random number generation functionality. Perform basic statistical analysis on the generated marks.

### Program
```
import numpy as np
np.random.seed(10)
marks = np.random.randint(40, 101, size=5)
print("Randomly generated marks:", marks)
print("Total:", np.sum(marks))
print("Average:", np.mean(marks))
print("Highest:", np.max(marks))
print("Lowest:", np.min(marks))
print("Standard deviation:", np.std(marks))
```
### Output
<img width="1370" height="472" alt="image" src="https://github.com/user-attachments/assets/cd2e10dd-eb38-4696-812a-69cc1d8a0e78" />

## Question 15 – Student Performance Analysis
The marks of five students in three subjects are stored in a NumPy array. Develop a program to perform a complete student performance analysis by calculating the total marks, average marks, highest marks, lowest marks, and identifying students who perform above the class average.

### Program
```
import numpy as np
marks = np.array([
    [78, 85, 90],
    [65, 72, 80],
    [88, 91, 84],
    [56, 62, 70],
    [95, 89, 92]
])
total = np.sum(marks, axis=1)
average = np.mean(marks, axis=1)
highest = np.max(marks, axis=1)
lowest = np.min(marks, axis=1)
class_average = np.mean(total)
above_average = np.where(total > class_average)[0] + 1
print("Marks matrix:")
print(marks)
print("\nTotal marks:", total)
print("Average marks:", average)
print("Highest marks:", highest)
print("Lowest marks:", lowest)
print("\nClass average total:", class_average)
print("Students above class average:", above_average)
```
### Output
<img width="1442" height="606" alt="image" src="https://github.com/user-attachments/assets/813d9fa9-70ab-4f08-8773-e714ca954bae" />
