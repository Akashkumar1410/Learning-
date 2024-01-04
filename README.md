# Learning-
Lists
# -first day of learning 3 january  2024 programs 

#program to calucte the fibonacci series <<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<
"""
def fibonacci_sequence(n):
    # if zero then simple return 0
    if n == 0:
        return [0]
    #  variable initilize to store the first two Fibonacci numbers to calculatre the result of next number s
    sequence = [0, 1]

    # Calculate Fibonacci series up to n numbers in faster way
    while len(sequence) < n:
        sequence.append(sequence[-1] + sequence[-2])

    return sequence

num_fibonacci_numbers = 100

# Calculate and print the first 100 Fibonacci numbers
result_sequence = fibonacci_sequence(num_fibonacci_numbers)
print(result_sequence)
"""


# palindrome or not <<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<
"""
a="madam"
b=a[::-1]
y = "palindrome" if b == a else "not"
print(y)
"""
# common elements of list>>>>>>>>>>>>>>>>>>>>
"""
def common_elements(list1, list2):
    # Find the common elements using set intersection return the common elements
    co_set = set(list1) & set(list2)

    # Convert back to the list in sorted order
    final_list = sorted(list(co_set))
    return final_list


list1 = [3, 5, 8, 10, 15]
list2 = [8, 12, 5, 7, 20]

result = common_elements(list1, list2)
print(result)
"""

#calculator>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
"""
def calculator(operator, num1, num2):
    if operator == '+':
        result = num1 + num2
    elif operator == '-':
        result = num1 - num2
    elif operator == '*':
        result = num1 * num2
    elif operator == '/':
        # Check for division by zero
        if num2 != 0:
            result = num1 / num2
        else:
            return "Division by zero is not allowed"
    else:
        return "Error: Unsupported operator"

    return result

# Example usage:
operator =input( "enter the op");
number1 = input("enter  1st number ")
number2 = input("enter secomnd number")
#chznging the num 1  in int
number0=int(number1)
#changing thr number 2 in int
number3=int(number2)

result = calculator(operator, number0, number3)

# Print the result
print(f"{number1} {operator} {number2} = {result}")
"""


#calculating ther sunbarray with sumn
"""
 
def sum(items):
    count=0
    for i in items:
        count +=i
    return count
print(sum([1,2,3,-4]))
"""

# calculate the factorial<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<
"""

def factorial(n):
    if n == 0 or n == 1:
        return 1
    else:
        return n * factorial(n - 1)

input_number = int(input(" enter a number"))

# Calculate the factorial of the input number
result = factorial(input_number)

print(f"The factorial of {input_number} is: {result}")
"""

# check thr number is armstring number or not
"""
def arm(num):
    number1=str(number)
    num_digits=len(number1)

    arm_num=0
    for x in number1:
        arm_num += int(x) ** num_digits
    return arm_num==number;

number=153
result= arm(number)
print('armstrong number ' if result else 'not ')
"""

# check the brackets are in corect order or not
def is_valid_parentheses(s):
    stack = []
    opening_brackets = "({["  # Opening brackets
    closing_brackets = ")}]"  # Corresponding closing brackets

    for char in s:
        if char in opening_brackets:
            stack.append(char)
        elif char in closing_brackets:
            if not stack or opening_brackets[closing_brackets.index(char)] != stack.pop():
                return False

    return not stack  # If the stack is empty, all brackets are matched

# Example usage:
input_string = "({[()]})"

# Check if the string has valid parentheses
result = is_valid_parentheses(input_string)

# Print the result
if result:
    print(f"The string '{input_string}' has valid parentheses.")
else:
    print(f"The string '{input_string}' does not have valid parentheses.")


# date 4 january 2024
create a dictionary with maximum numner
"""
x= int(input(" inout a number"))
dic=dict()
for x in range(1,x+1):
    dic[x]= x*x
print(dic)"""
# assignment 1>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
import json
print (" dictionary ")
dict1=dict()
i=1
while i<=10:
    print("press yes--y for add new and  and No--n for exit thr program :::p:: for print the values")
    x=(input(""))
    if x=='y':
        number=int(input("enter emploee number "))
        name=input(" enter the employee name ")
        salary=int(input(" enter salary"))

        married =(input("married :True or False"))

        # Convert the input to a boolean
        married1 = married.lower() == 'true'

        dict1[number]=[name,salary,married1]
    elif x=='n':
         print("exited")
         break

    elif x=='p':
        #for i in range(len(dict1)):
         print(dict1)
         break

    else:
        print(" thanks ")

file_path = r'C:\Users\HOME\PycharmProjects\data analysis\output.txt'
with open(file_path, 'w') as file:
    json.dump(dict1, file)

print(f"Data saved to '{file_path}'")

# ther ln]mda function is callable 
