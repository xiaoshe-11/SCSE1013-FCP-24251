
```mermaid
flowchart TD
    Start([Start]) --> InputDetails[/Enter Loan Amount, Interest Rate, Loan Period, Monthly Income/]

    InputDetails --> CalcMonthlyPayment["Calculate Monthly Payment  M = (P × r/12) / (1 - (1 + r/12)^(-12n))"]

    CalcMonthlyPayment --> AffordableCheck{Is M <= 30% of Monthly Income?}

    AffordableCheck -- Yes --> MonthlyLoop["For each month in loan period:"]
    MonthlyLoop --> DeductPayment["Deduct Monthly Payment from Balance"]
    DeductPayment --> BalanceCheck{Remaining Loan Balance > 0?}

    BalanceCheck -- Yes --> MonthlyLoop
    BalanceCheck -- No --> Success[/Loan Fully Repaid Successfully/]

    AffordableCheck -- No --> Warning[/Warning: Payment may not be affordable/]
    Warning --> ContinueDecision{Continue with Payment?}

    ContinueDecision -- Yes --> MonthlyLoop
    ContinueDecision -- No --> Fail[/Loan Default: Adjust Loan Plan/]

    Success --> End([End])
    Fail --> End([End])
