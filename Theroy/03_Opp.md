## Functional programming
In it we use functions instead to sepearate the functionality from the data for example

def remaining_fuel (intial , kilometers , ratio):
    return intial - kilometer * ratio      See we hv separated the data and the functionality we are not adding any data we are just perform the calculation on the given data


## OOP
In oop instead of all the programms being bundled up in one file and creating a mess it devided the program based on the logic into groups called objects
Each object has its own data and functionality the data is called properties and the functionality is called methods

The basic pillars of OOP include
- Encapsulation : It mean encapsulating data into the object so each can handle its own entties example (lexer has its own properties , parser ) both of them can hv different data making our life easier
- Abstraction : Simplifying the inner functionality hidding away all the functionality lexer = lexer().tokenize we are hiding all the functionality on how its working
- Inheritane : It mean inherting different things from the parent class into the child class to allow the resueability
- Polymorphism : Making function behaves different depending on whoes calling it meaning that if i hv a function called sound and the dog object call it it should return woof while when cat return it should return meow

## OOP IN PYTHON
Class payment():
    intial_balance = 1000 # since intital balance is same we do not need to add it as input everytime this is called class variable
    def __init__(self,recepient,amount):
        self.recepient = recepient
        self.amount = amount

    def check(self ):
        return payment.intial_balance - self.amount

    ## Class methood
    @classmethood  # using the methoods we can add the function to the class directly that will not need the insitance or the object to be caleed
    def updatebalance(cls , new_balance):
        cls.intial_balance = new _ balance
payment1 = payment("awais",12) # payment 1 is the object of the payment class and it has all data
payment.updatebalace(1000) # we are updating the balance directly  of the class