
```mermaid
flowchart TD
    Start([Start]) --> InputDetails[/Enter Loan Amount (P), Annual Interest Rate (r), Loan Period (n), Monthly Income/]

    InputDetails --> CalcMonthlyPayment["Calculate Monthly Payment (M)"]
    CalcMonthlyPayment --> Formula["M = (P × r/12) / (1 - (1 + r/12)^(-12n))"]

    Formula --> AffordableCheck{Is M <= 30% of Monthly Income?}

    AffordableCheck -- Yes --> MonthlyLoop["For each month in loan period:"]
    MonthlyLoop --> DeductPayment["Deduct Monthly Payment (M) from Balance"]
    DeductPayment --> BalanceCheck{Remaining Loan Balance > 0?}

    BalanceCheck -- Yes --> MonthlyLoop
    BalanceCheck -- No --> Success[/Loan Fully Repaid Successfully!/]

    AffordableCheck -- No --> Warning[/Warning: Payment may not be affordable!/]
    Warning --> ContinueDecision{Continue with Payment?}

    ContinueDecision -- Yes --> MonthlyLoop
    ContinueDecision -- No --> Fail[/Loan Default: Adjust Loan Period or Payment Plan/]

    Success --> End([End])
    Fail --> End([End])
