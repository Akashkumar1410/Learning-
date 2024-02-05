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

# ther lamda function is callable
# the meaning of self  in classes #vo object jiske lie method call kliya ja rha hai 


# Banking system using opps  
import pandas as pd
import ast

class CustomerData():
    customer_data = dict()

    def save_data(self, customer_account, customer_name, balance):
        customer_account = customer_account.strip()
        if customer_account in self.customer_data:
            # Customer exists, update the balance
            self.customer_data[customer_account]['balance'] = balance
        else:
            # Customer doesn't exist, initialize the balance
            self.customer_data[customer_account] = {'name': customer_name, 'balance': balance}

    def load_data_from_excel(self):
        try:
            df = pd.read_excel('customer_data.xlsx')
            for index, row in df.iterrows():
                account_number = str(row['Account'])
                details_str = row['Details']
                details_dict = ast.literal_eval(details_str)  # Safely convert string to dictionary
                customer_name = details_dict['name']
                balance = details_dict['balance']
                self.save_data(account_number, customer_name, balance)
        except FileNotFoundError:
            print("Excel file not found. Starting with an empty customer database.")

    def display_all_details(self):
        print("\nAll Customer Details:")
        for account, details in self.customer_data.items():
            print(f'Account Number: {account} - Customer: {details["name"]} - Balance: {details["balance"]}')

        # Convert customer_data to a DataFrame and save to Excel
        df = pd.DataFrame(list(self.customer_data.items()), columns=['Account', 'Details'])
        df.to_excel('customer_data.xlsx', index=False)
        print("\nCustomer data saved to 'customer_data.xlsx'.")

class Bank(CustomerData):
    def __init__(self, aaccount, aowner, abalance=0):
        super().__init__()
        self.account = aaccount
        self.owner = aowner
        self.balance = abalance

    def deposit(self, amount):
        self.balance += amount
        print(f'Your amount {amount} has been deposited to your account.')
        print(f'Your total balance is {self.balance}')
        # Save data after each transaction
        self.save_data(self.account, self.owner, self.balance)

    def withdraw(self, credit):
        if self.balance >= credit:
            self.balance -= credit
            print(f'You withdrew {credit} and the remaining balance is {self.balance}')
            # Save data after each transaction
            self.save_data(self.account, self.owner, self.balance)
        else:
            print("Insufficient balance.")

    def details(self):
        print(f'Account Number: {self.account} - Customer: {self.owner} - Remaining Balance: {self.balance}')
        # Save data after each transaction
        self.save_data(self.account, self.owner, self.balance)

# Creating an instance of CustomerData to manage customer details
customer_manager = CustomerData()
customer_manager.load_data_from_excel()

print("Enter 'n' for new customer account\nPress 'e' for existing customer account\nPress 'd' for Deposit\nPress 'w' for Withdraw\nPress 'x' for Details\nEnter 'q' for Exit press any key for details")

account1 = None

while True:
    choice = input("*************Enter your choice***********")
    if choice == 'n':
        print("Enter the customer account number")
        account_number = input("Enter account number: ")
        print("Enter the customer name")
        customer_name = input("Enter name: ")
        if account_number.strip() not in CustomerData.customer_data:
            CustomerData.customer_data[account_number.strip()] = {'name': customer_name, 'balance': 0}  # Initialize balance to 0
            account1 = Bank(account_number, customer_name)  # Create Bank instance only if it doesn't exist
        else:
            account1 = Bank(account_number, customer_name, CustomerData.customer_data[account_number.strip()]['balance'])  # Use existing balance

    elif choice == 'e':
        print("Enter the existing customer account number")
        account_number = input("Enter account number: ")
        if account_number.strip() not in customer_manager.customer_data:
            print("Account number does not exist. Choose 'n' to create a new account.")
        else:
            existing_details = customer_manager.customer_data[account_number.strip()]
            existing_balance = existing_details['balance']
            account1 = Bank(account_number, existing_details['name'], existing_balance)

    elif choice == 'd':
        amount_for_deposit = int(input("Enter the amount you want to deposit: "))
        account1.deposit(amount_for_deposit)

    elif choice == 'w':
        if account1:
            print("Enter the amount you want to withdraw")
            amount_for_withdraw = int(input("Enter your amount: "))
            account1.withdraw(amount_for_withdraw)
        else:
            print("Create an account first (press 'n' or 'e')")

    elif choice == 'x':
        if account1:
            account1.details()
        else:
            print("Create an account first (press 'n' or 'e')")

    elif choice == 'q':
        print("Thank you for visiting.")
        break

# Continuous display of all customer names and details
customer_manager.display_all_details()



# Neural netwrok  
perceptron:-  1. Input layer 2. hidden layer 3. weight bias  4. activation function  
1.input layer take the input for the model in the  neauron   
Single layer  there is one hidden laye and one neauron  
all the procesin on thehideen layer in step 1 and step 2  
when  we are giving input to the hidden layer with the input we give weights on basis of  dataset features   and  we take on emore parameter  called bias  
# step 1( summatio of weights along with inputs  and bias )
importance of weights :Z=input * weightsn #(w1*i1 +w2*i2)  the weights is used to activate the neaurons   
Bias:- the weights are randomly initilize in some situation the weights are assigned 0  so to protext the input from 0 we give bvias with input. 


# Step 2  :- applying the activation fuction  ( for neuron activate or deactivate )
Activation function:- for a non linaer seprable problem  
sigmoid activation fucntion the output will be of z is 0 to 1    
 to reduce the error updatew the weights with new one and calculatw the loss or error    the main aim is to reduce the error to near the 0 or 0
sungle layer is used for linear seprable problem  binary classifier 


 # Multilayerd perception model ANN  
 1. forward propogation 2. backward propgation 3. activation function 4. optimizers 5 . loss function
 2. # loss Function s are
    for:- regression 1. mean suared error 2. mean absolute eror 3. huber loss
    for:-classification 1.binary cross entrophy 2. categorical cross entrophy
 5. # forward propogation:-
 6.  the parameter are usually weights and bias 
there are two bias values b1 b2 at hiddent and output layer
  after getting the output the output is goes to to set 2 whre the initial step 1 and step two are repat for the perdiction of the values  and the loss  is calculated through ther actual dependent value and thr predicted value.  
 # backward propogation:-   
  for reducing the loss to gett he accurate prediction w usually update the weights 
   the updation of the weights again is called backward propogation  the function which which is used in the simple linear regression is used in ANN weight updation  
   for reducing the error we use optimizer   and the optimizer is do backward propgation   
# epochs  
is the one iteration over the entire dataset.
suppose we have 10 k images to train a model if we give those all 10k images to mkodel fro backward and forward progragation that process is caleed epochs  
# batch 
there are batchj size  for giving the dataet to a model in batchees suppose from10000 image 1000 images are givine in batch 1 and there are toatal 10  iteration for 10000 images  
# iteration  

 
