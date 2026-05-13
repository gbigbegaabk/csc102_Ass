# Base class
class Account:
    def __init__(self, balance):
        self.balance = balance

    # Deposit method
    def deposit(self, amount):
        self.balance += amount
        print(f"Deposited: ${amount}")

    # Withdraw method
    def withdraw(self, amount):
        self.balance -= amount
        print(f"Withdrawn: ${amount}")

    # Display balance
    def display_balance(self):
        print(f"Current Balance: ${self.balance}")


# SavingsAccount inherits from Account
class SavingsAccount(Account):

    # Constructor
    def __init__(self, balance):
        super().__init__(balance)

        # Withdrawal limit attribute
        self.withdraw_limit = 100

    # Overriding withdraw method
    def withdraw(self, amount):

        if amount > self.withdraw_limit:
            print(f"Withdrawal denied! Limit is ${self.withdraw_limit}")

        elif amount > self.balance:
            print("Insufficient balance!")

        else:
            self.balance -= amount
            print(f"Successfully withdrew: ${amount}")


# Main program
account = SavingsAccount(500)

account.display_balance()

account.withdraw(50)   # Allowed
account.display_balance()

account.withdraw(150)  # Denied
account.display_balance()
