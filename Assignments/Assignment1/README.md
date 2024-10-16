


flowchart TD
    Start([Start]) --> InputLoan["Input Loan Amount (P), Annual Interest Rate (r), Loan Period (n), Monthly Income"]
    
    InputLoan --> CalcMonthlyPayment["Calculate Monthly Payment (M) using formula: M = (P × r/12) / (1 - (1 + r/12)^(-12n))"]
    
    CalcMonthlyPayment --> CheckAffordable{Is M <= 30% of Monthly Income?}
    
    CheckAffordable -- Yes --> PaymentLoopStart["For each month in loan period:"]
    PaymentLoopStart --> MonthlyPayment["Deduct Monthly Payment (M)"]
    MonthlyPayment --> CheckRemaining{Remaining Loan Balance > 0?}
    CheckRemaining -- Yes --> PaymentLoopStart
    CheckRemaining -- No --> SuccessMsg["Loan Repayment Successful!"]
    
    CheckAffordable -- No --> WarnUser["Warning: Payment may not be affordable."]
    WarnUser --> UserChoice{Continue with Payment?}
    
    UserChoice -- Yes --> PaymentLoopStart
    UserChoice -- No --> FailMsg["Loan Default: Adjust Loan Period or Payment Plan."]
    
    SuccessMsg --> End([End])
    FailMsg --> End([End])


