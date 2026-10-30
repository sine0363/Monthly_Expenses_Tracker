# Monthly Budget Tracker

A simple Python program that tracks monthly spending against a fixed budget. You enter expenses by category, and the program tells you how much you have left to spend. It was built in Google Colab as a way to practice Python fundamentals.

## How it works

Each month starts with a salary of **R7,000**. Two amounts are set aside automatically before any spending:

| Item | Rule | Amount |
|---|---|---|
| Tithes | 10% of salary | R700 |
| Savings (for a new PC) | 5% of salary | R350 |
| **Spendable amount** | Salary - tithes - savings | **R5,950** |

You then log expenses until you type `quit`. After every expense, the program shows how much of the spendable amount is left. If your spending goes over R5,950, it shows a warning message instead of a negative number.

## Expense categories

- food
- rent
- toiletries
- entertainment
- accounts
- transport
- clothing

Category names are **not case sensitive** and extra spaces are ignored, so `Food`, `FOOD`, and `  food ` all work. Anything not on the list is rejected and you are asked again.

## Example session

```
Enter your category (or 'quit'): Food
Enter the amount spent on a category: 100
Remaining: R5850.00
Enter your category (or 'quit'): holiday
That category doesn't exist. Try again.
Enter your category (or 'quit'): rent
Enter the amount spent on a category: abc
The amount must be a number.
Enter the amount spent on a category: 2500
Remaining: R3350.00
Enter your category (or 'quit'): quit
Total spent: R2600.00
```

## Running it

1. Open the notebook in [Google Colab](https://colab.research.google.com).
2. Run the cells in this order (or use **Runtime → Run all**):
   1. Constants (salary, tithes, savings, spendable amount, categories)
   2. `get_amount()`
   3. `add_expense()`
   4. The main loop
3. Follow the prompts. Type `quit` at the category prompt to finish.

No installation or extra libraries are needed. It uses only built-in Python.

## Code structure

| Part | What it does |
|---|---|
| Constants | Stores the salary, tithes, savings, spendable amount, and the list of valid categories. |
| `get_amount()` | Asks for an amount and keeps asking until the user enters a positive number. |
| `add_expense(total_spent)` | Asks for a category, validates it, gets the amount, updates the running total, and prints what is left. Returns the new total and a flag that says whether the user quit. |
| Main loop | Calls `add_expense()` repeatedly until the user quits, then prints the total spent. |

## Python concepts practiced

- Variables, constants, and f-string formatting
- Lists and the `in` operator
- `while` loops and `break`
- Functions, parameters, and return values (including returning two values)
- String cleanup with `.strip()` and `.lower()`
- Input validation with `try` / `except ValueError`

## Planned improvements

- [ ] `show_summary()` function that prints the total spent, the amount remaining, and the exceeded message in one place
- [ ] PC savings goal: enter the PC price and show how many months are left to save at R350 per month
- [ ] Spending totals per category
- [ ] Save data to a file so progress carries over between sessions
- [ ] Per-category budgets

## Notes

- The spending limit counts as exceeded only when the remaining amount is **below R0**. Spending exactly R5,950 leaves R0 and is allowed.
- Data is not saved between runs yet. Restarting the main loop starts a new month.
