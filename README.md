# Python-Gpay-project
hey this is my python project

def set_pin():
   
    pin = input("set a 4 digit pin.")
    if len(pin) == 4 and pin.isdigit():
        print("UPI PIN set successfully!")
        return pin
    else:
        print("Invalid PIN. Try again.")
        return set_pin()

def verify_pin(pin):
  
    for attempt in range(3):
        entered_pin= input("Enter your UPI PIN.")
        if entered_pin == pin:
            return pin
        else:
            print("Incorrect PIN")
    print("Too many wrong attempts. Transaction blocked.")

def check_balance(name, balance, pin):
  
    if verify_pin(pin):
        print(f"{name}, your current balance is {balance}")

def send_money(balance,pin):
   
    to_user= input("Enter user UPI ID")
    amount= float(input("enter amount to send"))
                        
    if amount <= 0:
        print("invalid amount")
        return balance
    if amount > balance:
        print("Insufficient balance")
        return balance
    if verify_pin(pin):
        balance -= amount
        print(f"{amount} successfully send to {to_user}")
        print(f"Remaining balance is {balance}")
    return balance

def receive_money(balance):
 
    from_user= input("enter user name")
    amount= float(input("enter received amount"))
    if amount <= 0:
        print("invalid amount.")
        return balance
    if amount > 0:
        balance += amount
        print(f"{amount} successfully received from {from_user}")
        print(f"New balance is {balance}")
        return balance

def Gpay():
  
    name= "Raj Rathore"
    balance= int(input("enter your amojunt"))
    pin= set_pin()
  
    while True:
        print("------------Gpay menu------------")
        print("(1) Check balance")
        print("(2) Send money")
        print("(3) Receive money")
        print("(4) Exit")
        chose_option= input("enter option")

        if chose_option == "1":
            check_balance(name,balance,pin)
        elif chose_option == "2":
            balance= send_money(balance,pin)
        elif chose_option == "3":
            balance= receive_money(balance)
        elif chose_option == "4":
            print("Thanks for using Gpay")
            break
        else:
            print("Invalid option, please try again")
Gpay()
