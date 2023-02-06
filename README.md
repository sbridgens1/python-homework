# python-homework

from pathlib import Path
import csv

#Check the current directory where the Python program is executing from
print(f"Current Working Directory: {Path.cwd()}")
Current Working Directory: /Users/stephen/MONU-VIRT-FIN-PT-11-2022-U-LOLC/Homework/02-Python/PyBank/Resources

#Set the file path
csvpath = Path('../../Pybank/Resources/budget_data.csv')

#Initialize list of records
Profit_Losses = []
Each_Month = []
Month_Year = []

#Open the csv file as an object
with open(csvpath, 'r') as csvfile:
    csvreader = csv.reader(csvfile, delimiter=',')
    header = next(csvreader)
    #appending data from CSV to corresponding list
    for row in csvreader:
        Profit_Losses.append(int(row[1]))
        Month_Year.append(row[0])
        
        #interating data to calculate month on month difference and appending to list
    for variable in range(len(Profit_Losses)-1):
        difference = (Profit_Losses[variable+1]) - (Profit_Losses[variable]) 
        Each_Month.append(difference)

total_months = len(Month_Year)

net_total_amount = sum(Profit_Losses)

each_month_period = (len(Profit_Losses)-1)

average_of_the_changes = round(sum(Each_Month) / each_month_period,2)

greatest_increase_in_profits = max(Each_Month) 
greatest_decrease_in_profits = min(Each_Month)

print("Financial Analysis")
print("----------------------------")
print(f"Total Months: {total_months}")
print(f"Total: ${net_total_amount}")
print(f"Average  Change: ${average_of_the_changes}")
print(f"Greatest Increase in Profits: (${greatest_increase_in_profits}")
print(f"Greatest Decrease in Profits: (${greatest_decrease_in_profits}")

# Financial Analysis
----------------------------
Total Months: 86
Total: $38382578
Average  Change: $-2315.12
Greatest Increase in Profits: ($1926159
Greatest Decrease in Profits: ($-2196167

output_path = Path("output.txt")

with open(output_path, 'w') as file:
    file.write("Financial Analysis")
    file.write("----------------------------")
    file.write(f"Total Months: {total_months}")
    file.write(f"Total: ${net_total_amount}")
    file.write(f"Average  Change: ${average_of_the_changes}")
    file.write(f"Greatest Increase in Profits: (${greatest_increase_in_profits}")
    file.write(f"Greatest Decrease in Profits: (${greatest_decrease_in_profits}")
