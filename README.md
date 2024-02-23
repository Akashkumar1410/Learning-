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
# back propogation  
choose a loss funtion to now the error or accuracy of the model the main aim is to reduce the error like mSE in back propogation the aim is to update the weights annd biases   formula is  weight new = weight old - learning rate 
# memorizitation 
the meaning of the memorization is to store the weights and biases for thr future use to make the program faster but iht has a disadvantgae it take  more memory 
 # batch gradient decent   and  tthr stocastic gradient decent  
 if we use the batch size as  1 then is called the BGD and if we uset the batch size based on the number of rows  then is called SGD  
 the SGD is more accurate to give the accurate result   on doing the SGD the loss will be in unstable nature but in the  BGD the loss is in thr stable manner   
 SGD is used thr random values to update the weights   
 but in the BGD  the updatiion is based on all the dataset  
 but the SGD is useful but this not givve the accurate result  but the SGD is not stuck in the local minima   but the BGD has chances to stuck innthe local minima nad do not reach to the global minima  
 # mini batch Gradient decent  
 it is best of both SGD BGD is we have 320 row   we pass 10 batches  in 32 epoch
 # Vanishing gradiennt decent problem  
  it means  in sometimewe update the weights after some time the weights hould not be chnaged   or the loss is not reduced that problem is called VGD it is motly occues  while we use the sigmoid activation fucntiopn   becaue sigmoid givethe value in 0 and 1 threshhold 0.5   this make to stop the learning to the model   
   # how to recognize the VGDP
   1. focus on the loss if the loss is not  decerese in the epoch thennn there id a problem of the VGDP
   2. plot the graph of the weights and epochs fi the weights in the consistent mannner then therse is oronblem of the VGDP
#  how to hadle the VGDP 
1. reduce the complixity of thr model but iff we reduce the complixity we can not ble to solve the comolex problems and patterns
2. using the relu activation function relu has if there is negative then the value will be 0 and if there is positive then the value is 1  but here si 1 problem if the activation will be 0  the derivative will also be 0 this is called the dying relu . but to resolve this the leaky relu came in existense
3.  till now we we givwe the weights in random numner   but there are some techniques to initilizatio ther weights  1 is glorat and 2 is xavier  tecjnique

# how to improve the neural network   
1. fine turning the NN hyperparameter.  :- number of hidde layer ,, number of neuron per layer ,, Learning rate and optimizer  . activation function  and last the epochs . meanns how many epooch run on the model
# number of hidden layer:-  
use the number of hideen layer woith less  neurons  extend the number of layer  till themodel is overfitted   whrn the model will be overfitthen stop.  
use the the sufficeint amunt of neurns in the hidden layer  if there is ooverfittin in the model htne  reduce the number of neurons   
# batch size  
if we use the mini batch sizs  like 8 to 32 in epoch  will be  slow but  give the  etter result  
if we use the larger batch size like 8192  will give the faster reuslt and some time its not give the good reslt  but there is solution to imporve :-warming up the learning rate or learning rate scheduler  increase the learning rate on evevry epoch iteratiin  
 in summary first uset the greater batch size  if we donnt got the better result then shift to the lesser  bathc size.  
# epoch   
 apply the larger number of epoch with early stoppin  
 # prevvent the model from the overfitting   
 # overfitting is th problem where the model is give the good result onn the testing results of the datset but when you give the unseen or new data  then the model will not give the good result  plot the decision boundry on the training data and the testing data (plot_decision_regions)

 1. "early stopping" means to observe the accuracy of the model when there is no change in the accueacy of the modle on ongoin epoch thenb stop   there is a method  in keras " callback" feature    to deal with the overfitting uset he dropout methods
 2. regularization :- l1 and l2
 3. dropout is the ethod to precent from overfitting :-  dropout means  the suppose there are 10 epoch in the moodel  adn in the eveery epoch we can remove some nodes in thr  hidden layer and the input layer    soo  iot means in every epoch we can use the different artichure of neuron network.dropout lyer is initiloze by P =0.5 means thr 50% of the  nodes the value is changable on the user input or devlepor  this process is called ensemmble learning   and the droput is appplied on the training data not on the testing data 
 4.  we compare the dropout with the random forest algorithm.
 5.  
# Normalization  
normalization id the technique to make the diffrent scales data in one same scled data  usually it is calledd the data scaling    
# dropouts :-  
dropout are applied while making the model   if the model is overfittinh  the P or drooput value is to be increase and if thr  model is under fitting the dropout or the P value is to be decrease  
  hint first strat apply the dropout onnthe last nodel or layer if we got some good result then we should apply on the other layers also  
whuile working with the CNN drop is to be 0.4 or 0.5 % is give good result   
while working with the RNN 0.2 or 0.3 value is give the good reslut 
while woriking withn the ANN 0.1 --0.5  will give the good result 

# regularization ( is the technique to prevent the model from the over fitting ) (L1 and L2)  
the L2 is the cmost commomn in the deep learning 
the  term penality is used in the regularizing  penality is the value   square of all the weights and sum of all that eights in the loss function.   this make the weigts to the zeros values  near to the zero .in the code  of firdt layer (kernal_regularizer=tensorflow .kears.regularizers.L2(0.03))   

# activation function  
 if wr dont have the activation fucntion the model wil wrok like a linear model   
  sigmoiid is used only in the output layer whrn problem is binary classification in today time  
  relu activation fucntion   
in the hiden layer the relu fucntion is mostly used   
dying relu is the dis advantage because it make the dead neuron  
why dying relu is occured :- because it make the updted weights to 0 thismake the model to dont klearn  something from thr inputs  
 soltions :- set low  learning rate , set the bias to the positive values ,  dont use the relu instead use the different varients of the relu   
 # varients of  relu  :-
 lineaar:-nleaky relu , parametric relu   nonlinearr relu :- exponential relu , scaled relu   
  leaky relu :-  if value of Z is positive then the value of Z will e Z and if the Value of Z is in the negativve 0.01 time of Z  
   adv ..  unnbounded , non dying relu problem , close to 0 centred    
   expontial relu  :-
    some time it perfome the better then the relu  its close to 0 center and its faster  better in test set data  its always continous    
    SELU:-  coverge faster.      
# weights initilozation techniques  :-  
wrong techniques of weights initilizationn:-0 initiliazation set all thw weights to 0   
good methods to initize the weights :-  
1. Xavier  and  glorat initilizatio techniques whichis uniform and Normal  with using (Tanh activation function)
2. He initiloiazaton technique which is uniform and normal   using (relu activation fucnction)
 in keras  both of above are implemented

# batch normalization :- it is the technique which is used for make faster to the trianing pprecess of the moodel or neuron network  its maks the normal form of the  input to the next hidden layer   and this make the good output result    it is used with the moini batch grdient decent and it work layer by layer   
 add the (batchNormalization()) method in the keras in fron of every layer  
 withthe help of batch normallization we can achieve higher accuracy in very less epochs   

 # OptimiZers  
 it is the techniques of increase the speed of the tarinig of the model  thr batch GD SGD and MIni BGD is also an optimers 
 1. learning rate  schdule is one method  of optimizer
 2. momentum
 3. adagrad adAPTIVE GRADIENT 
 4. NAG (Nesterov-accelerated Adaptive Moment Estimation)
 5. rms prop
 6. adam
# to learn the optimizer first study the EWM exponantial weighted moving average     which is efine in python programming in pandas   with the helkp of (EWM(alpha=0.9)) we can calculat the EWM  
#  momentum  
momentum is good at high curvature consistet graduate noisy data  or it can not stuck in the local minima 
if the pervious gradients wil take the point to the positive direcetion then the model will fastly go to that point   
 # adagrad  
 in this we do not fix the learning rate we can change the learning rate on the basisi of situation
 it is use when the scale of th input feature is very different 
  when most of thr dataoiunt in inputs are 0 that situation is called sparse.  whenn there is sparse it will create a priblem called alongated bowl problem
   sometime  in our input feature most of the data feature or opints are 0 in that situation we can usse the adagrad algorithnm because in thtat situation it will gove good reault




