# Module 12 Completion Report

## Instruction File
- Filename: calculate-compound-interest.agent.md

---
description: Use the compound interest calculator for principal, rate, compounding, and time-based growth questions
---
- Use this instruction when the user asks to calculate compound interest or compare future value growth over time.
- Use the script at `./tools/compound_interest.py`.
- Invoke it with command-line arguments in this order: `principal annual_rate_percent compounds_per_year years`.
- Example: `python tools/compound_interest.py 15847 7.34 12 8.583333333333334`.
- The script prints the final amount and interest earned in dollars.
- If the user provides values in different units or formats, convert them to the required numeric inputs before running the script.
- Keep the output concise and readable.
- Report the final amount and interest earned in currency format with two decimal places.
- If the user asks for a formula explanation, show the standard compound interest formula and the resulting values.
- Do not invent values or assumptions not provided by the user.
- If any input is invalid, stop and report the error message from the script.

## Script File
- Filename: compound_interest.py
- Language: Python

import sys


def calculate_compound_interest(principal: float, annual_rate: float, compounds_per_year: int, years: float) -> tuple[float, float]:
    amount = principal * (1 + (annual_rate / 100) / compounds_per_year) ** (compounds_per_year * years)
    interest = amount - principal
    return amount, interest


def main() -> None:
    if len(sys.argv) != 5:
        print("Usage: python compound_interest.py <principal> <annual_rate_percent> <compounds_per_year> <years>")
        sys.exit(1)

    try:
        principal = float(sys.argv[1])
        annual_rate = float(sys.argv[2])
        compounds_per_year = int(sys.argv[3])
        years = float(sys.argv[4])
    except ValueError:
        print("Error: principal, annual_rate, compounds_per_year, and years must be valid numeric values.")
        sys.exit(1)

    if principal < 0 or annual_rate < 0 or compounds_per_year <= 0 or years < 0:
        print("Error: principal, annual rate, and years must be non-negative; compounds per year must be positive.")
        sys.exit(1)

    amount, interest = calculate_compound_interest(principal, annual_rate, compounds_per_year, years)
    print(f"Final amount: ${amount:.2f}")
    print(f"Interest earned: ${interest:.2f}")


if __name__ == "__main__":
    main()

## Script Execution Output
Usage: python compound_interest.py <principal> <annual_rate_percent> <compounds_
per_year> <years>
