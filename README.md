Role Responsibilities

Project Manager Oversees progress, ensures timely completion.
Lead Developer Implements major code improvements. - Tapulgo
Refactoring Specialist Identifies technical debt and suggests improvements. - Arao
Git Manager Manages Git operations (branching, commits, documentation).
Tester/Documenter Writes test cases and updates documentation. - Arao

Poor Naming Conventions – Variables had unclear names like sss, pagibig, and tax, making the code harder to understand.
Lack of Modular Functions – The original code used a single function to handle all calculations, reducing maintainability and making debugging more difficult.
Hardcoded Values Instead of Dynamic Inputs – Fixed values like sss = 1200 and tax = 1875 were directly written in the code instead of being dynamically calculated or configurable.
No Error Handling – The program lacked validation, meaning invalid inputs (e.g., text or negative numbers) could cause crashes.
Code Duplication – Similar calculations (e.g., total deductions and net salary) were repeated instead of using reusable functions.

Improve code readability

def compute_salary_deductions(gross_salary):
    """
    Computes salary deductions and net salary.
   
    Parameters:
        gross_salary (float): The monthly salary input by the user.


    Returns:
        None: Prints the deduction breakdown and net salary.
    """
    social_security_system = 1200  # Fixed SSS contribution
    philhealth_contribution = (gross_salary * 0.05) / 2  # 5% of salary divided by 2
    pagibig_fund = 100  # Fixed Pag-IBIG contribution
    income_tax = 1875  # Assumed fixed value for simplicity


    total_deductions = social_security_system + philhealth_contribution + pagibig_fund + income_tax
    net_salary = gross_salary - total_deductions


    print("\n💰 Salary Breakdown")
    print(f"Gross Salary: {gross_salary:,.2f}")
    print(f"SSS Deduction: {social_security_system:,.2f}")
    print(f"PhilHealth Deduction: {philhealth_contribution:,.2f}")
    print(f"Pag-IBIG Deduction: {pagibig_fund:,.2f}")
    print(f"Tax Deduction: {income_tax:,.2f}")
    print(f"Total Deductions: {total_deductions:,.2f}")
    print(f"🟢 Net Salary: {net_salary:,.2f}\n")




def get_valid_salary():
    """
    Prompts the user to enter a valid salary and handles incorrect inputs.


    Returns:
        float: A valid positive salary.
    """
    while True:
        try:
            salary_input = float(input("Enter your monthly salary: "))
            if salary_input <= 0:
                print("❌ Salary must be a positive number. Please try again.")
            else:
                return salary_input
        except ValueError:
            print("❌ Invalid input. Please enter a numeric salary amount.")


# Get validated user input
salary = get_valid_salary()
compute_salary_deductions(salary)


Key Takeaways:
Renamed variables for clarity (e.g., sss → social_security_system), improved formatting and indentation, added docstrings, and formatted numerical output for better readability.

Convert to modular functions 
def compute_sss():
    return 1200


def compute_philhealth(salary):
    return (salary * 0.05) / 2


def compute_pagibig():
    return 100


def compute_tax():
    return 1875  # Assuming fixed value for simplicity


def compute_total_deductions(salary):
    sss = compute_sss()
    philhealth = compute_philhealth(salary)
    pagibig = compute_pagibig()
    tax = compute_tax()
    return sss + philhealth + pagibig + tax, sss, philhealth, pagibig, tax


def compute_net_salary(salary):
    total_deductions, sss, philhealth, pagibig, tax = compute_total_deductions(salary)
    net_salary = salary - total_deductions
   
    print("Gross Salary:", salary)
    print("SSS Deduction:", sss)
    print("PhilHealth Deduction:", philhealth)
    print("Pag-IBIG Deduction:", pagibig)
    print("Tax Deduction:", tax)
    print("Total Deductions:", total_deductions)
    print("Net Salary:", net_salary)


salary = float(input("Enter your monthly salary: "))
compute_net_salary(salary)
Key Takeaways:
roke down the large function into reusable functions (compute_sss(), compute_tax(), etc.), reducing code duplication and making the program easier to maintain and modify.

Implement OOP 
class SalaryCalculator:
    def __init__(self, salary):
        self.salary = salary
        self.sss = 1200
        self.philhealth = (salary * 0.05) / 2
        self.pagibig = 100
        self.tax = 1875  # Assuming fixed value for simplicity
        self.deductions = self.sss + self.philhealth + self.pagibig + self.tax
        self.net_salary = self.salary - self.deductions


    def display_deductions(self):
        print("Gross Salary:", self.salary)
        print("SSS Deduction:", self.sss)
        print("PhilHealth Deduction:", self.philhealth)
        print("Pag-IBIG Deduction:", self.pagibig)
        print("Tax Deduction:", self.tax)
        print("Total Deductions:", self.deductions)
        print("Net Salary:", self.net_salary)


if _name_ == "_main_":
    salary = float(input("Enter your monthly salary: "))
    calculator = SalaryCalculator(salary)
    calculator.display_deductions()
Key Takeaways:
Encapsulated logic into a SalaryCalculator class, using __init__() to store salary and deductions, and display_deductions() to improve structure, scalability, and reusability.
