## 1. Student Attendance Analysis
A college maintains the daily attendance details of its students in the form of a list containing student IDs. Some students may have attended multiple sessions on the same day. The administration wants to identify the longest continuous sequence of sessions in which no student ID is repeated. Develop a solution that determines the maximum length of such a sequence.
### Program 
```
students = [1, 2, 3, 1, 4, 5]
seen = set()
left = 0
max_length = 0
for right in range(len(students)):
    while students[right] in seen:
        seen.remove(students[left])
        left += 1
    seen.add(students[right])
    max_length = max(max_length, right - left + 1)
print("Longest sequence:", max_length)
```
### Output
<img width="1211" height="610" alt="image" src="https://github.com/user-attachments/assets/854e26df-7f1f-4b01-b265-238b2e2d0a96" />

## 2. Online Shopping Price Analysis
An online shopping application stores the prices of products viewed by a customer during a browsing session. The customer wants to identify a continuous range of products that provides the maximum possible total discount value. Given the discount values, determine the maximum value that can be obtained from any continuous range.
### Program
```
discounts = [-2, 3, -1, 5, -6, 4]
current_sum = discounts[0]
maximum_sum = discounts[0]
for i in range(1, len(discounts)):
    current_sum = max(discounts[i], current_sum + discounts[i])
    maximum_sum = max(maximum_sum, current_sum)
print("Maximum discount value:", maximum_sum)
```
### Output
<img width="968" height="391" alt="image" src="https://github.com/user-attachments/assets/606be5d5-b2db-4484-9c69-f6fd55e88478" />

## 3. Rainwater Collection System
A city installs buildings of different heights along a straight road. During rainfall, water gets collected between taller buildings. The engineering team needs to calculate the total amount of water that can remain trapped after heavy rainfall based on the heights of the buildings.
### Program
```
heights = [3, 0, 2, 0, 4]
left = 0
right = len(heights) - 1
left_max = 0
right_max = 0
water = 0
while left < right:
    if heights[left] < heights[right]:
        if heights[left] >= left_max:
            left_max = heights[left]
        else:
            water += left_max - heights[left]
        left += 1
    else:
        if heights[right] >= right_max:
            right_max = heights[right]
        else:
            water += right_max - heights[right]
        right -= 1
print("Trapped water:", water)
```
### Output
<img width="896" height="593" alt="image" src="https://github.com/user-attachments/assets/f55bae84-f7f7-4825-8b4f-3510c52c03d8" />

## 4. Employee Performance Analysis
A company stores the monthly performance scores of an employee for several months. The scores may contain both positive and negative values depending on the employee's performance. Management wants to identify the continuous period during which the employee achieved the highest overall performance.
### Program
```
scores = [-2, 3, -1, 5, -6, 4]
current = scores[0]
maximum = scores[0]
for i in range(1, len(scores)):
    current = max(scores[i], current + scores[i])
    maximum = max(maximum, current)
print("Highest overall performance:", maximum)
```
### Output
<img width="1052" height="560" alt="image" src="https://github.com/user-attachments/assets/5e2afbee-8ccf-452e-9c0d-a9eb0b5f41cc" />

## 5. Product Sales Analysis
A retail company stores the daily sales quantity of a product for several consecutive days. Due to seasonal changes, some days may have negative adjustments. The company wants to identify the period that produced the highest multiplication of sales-related values. Develop a solution to determine this maximum product.
### Program
```
sales = [2, 3, -2, 4]
maximum = sales[0]
minimum = sales[0]
answer = sales[0]
for i in range(1, len(sales)):
    value = sales[i]
    # Negative numbers can change minimum into maximum
    if value < 0:
        maximum, minimum = minimum, maximum
    maximum = max(value, maximum * value)
    minimum = min(value, minimum * value)
    answer = max(answer, maximum)
print("Maximum product:", answer)
```
### Output
<img width="997" height="447" alt="image" src="https://github.com/user-attachments/assets/9a4869a4-8ee4-4bd4-b0f7-a42de9258cd0" />

## 6. Customer Purchase History
An e-commerce application stores the product IDs purchased by a customer in chronological order. The same product may appear multiple times. The system needs to determine the longest sequence of consecutive purchases in which every product ID is unique.
### Program
```
products = [10, 20, 30, 10, 40, 50]
seen = set()
left = 0
longest = 0
for right in range(len(products)):
    while products[right] in seen:
        seen.remove(products[left])
        left += 1
    seen.add(products[right])
    length = right - left + 1
    longest = max(longest, length)
print("Longest unique purchase sequence:", longest)
```
### Output
<img width="1096" height="567" alt="image" src="https://github.com/user-attachments/assets/48165932-0b40-47f2-9df5-06fc0aa97e85" />

## 7. Bank Transaction Analysis
A bank stores transaction amounts for a customer's account. A continuous group of transactions may add up to a specific target amount. The auditing system needs to determine how many different continuous transaction groups produce exactly the specified amount.
### Program
```
transactions = [1, 2, 3, 2, 1]
target = 5
count = 0
for i in range(len(transactions)):
    total = 0
    for j in range(i, len(transactions)):
        total += transactions[j]
        if total == target:
            count += 1
print("Number of groups:", count)
```
### Output
<img width="1093" height="405" alt="image" src="https://github.com/user-attachments/assets/4e969fcf-5223-4ba3-9770-0cea0db128d1" />

## 8. Employee Skill Grouping
A company receives a list of employee skill codes represented as strings. Employees having the same set of characters in their skill codes belong to the same skill category, even if the characters appear in a different order. The HR system needs to organize employees into appropriate skill groups.
### Program
```
skills = ["eat", "tea", "tan", "ate", "nat", "bat"]
groups = {}
for skill in skills:
    key = ''.join(sorted(skill))
    if key not in groups:
        groups[key] = []
    groups[key].append(skill)
for group in groups.values():
    print(group)
```
### Output
<img width="912" height="602" alt="image" src="https://github.com/user-attachments/assets/88a34b5f-792c-410b-8306-c90436ad82fa" />

## 9. Network Packet Analysis
A network monitoring system receives packet identifiers in chronological order. The system must determine the longest sequence of consecutive packets whose identifiers form a continuous numerical sequence, regardless of their original order in the incoming data.
### Program
```
packets = [100, 4, 200, 1, 3, 2]
numbers = set(packets)
longest = 0
for num in numbers:
    if num - 1 not in numbers:
        current = num
        length = 1
        while current + 1 in numbers:
            current += 1
            length += 1
        longest = max(longest, length)
print("Longest consecutive sequence:", longest)
```
### Output
<img width="1033" height="576" alt="image" src="https://github.com/user-attachments/assets/3f5232cc-8189-4074-a9ad-6494be52a465" />

## 10. Hospital Appointment Scheduling
A hospital receives appointment requests represented by starting and ending times. Some appointments overlap with each other. The scheduling system needs to combine overlapping appointment periods so that the final schedule contains only non-overlapping time ranges.
### Program
```
appointments = [[1, 3], [2, 6], [8, 10], [9, 12]]
appointments.sort()
merged = []
for appointment in appointments:
    start = appointment[0]
    end = appointment[1]
    if not merged:
        merged.append([start, end])
    elif start <= merged[-1][1]:
        merged[-1][1] = max(merged[-1][1], end)
    else:
        merged.append([start, end])
print("Final schedule:", merged)
```
### Output
<img width="1012" height="555" alt="image" src="https://github.com/user-attachments/assets/569c6c30-b91b-4d27-9dff-7528d8294c68" />
