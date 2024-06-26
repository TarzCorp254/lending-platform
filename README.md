# Lending Platform Module

This module implements a simple lending platform on the Sui blockchain. It allows users to act as lenders and borrowers, facilitating the creation, management, and repayment of loans. Below, you will find an overview of the structures, functions, and usage instructions for this module.

## Overview

### Structures

- **Lender**
  - `id: UID` - Unique ID for the lender
  - `name: String` - Name of the lender
  - `balance: Balance<SUI>` - Balance of the lender in SUI tokens
  - `lender: address` - Address of the lender

- **Borrower**
  - `id: UID` - Unique ID for the borrower
  - `name: String` - Name of the borrower
  - `borrower: address` - Address of the borrower
  - `balance: Balance<SUI>` - Balance of the borrower in SUI tokens

- **Loan**
  - `id: UID` - Unique ID for the loan
  - `borrower_id: ID` - ID of the borrower
  - `lender_id: ID` - ID of the lender
  - `borrower: address` - Address of the borrower
  - `lender: address` - Address of the lender
  - `loan_amount: u64` - Amount of the loan
  - `interest_rate: u64` - Interest rate of the loan
  - `loan_time: u64` - Time when the loan was given
  - `due_time: u64` - Due time for the loan repayment
  - `repaid_amount: u64` - Amount repaid so far

### Error Codes

- `EInsufficientFunds: u64 = 1` - Insufficient funds error
- `EInvalidCoin: u64 = 2` - Invalid coin error
- `ENotLender: u64 = 3` - Not a lender error
- `EInvalidLoan: u64 = 4` - Invalid loan error
- `ENotBorrower: u64 = 5` - Not a borrower error
- `EInvalidRepayment: u64 = 6` - Invalid repayment error

### Functions

- `create_lender(ctx: &mut TxContext, name: String)`
  - Creates a new lender with the specified name.

- `create_borrower(ctx: &mut TxContext, name: String)`
  - Creates a new borrower with the specified name.

- `deposit_funds(lender: &mut Lender, amount: Coin<SUI>, ctx: &mut TxContext)`
  - Deposits funds into a lender's account.

- `request_loan(borrower: &mut Borrower, lender: &mut Lender, loan_amount: u64, interest_rate: u64, loan_time: u64, due_time: u64, ctx: &mut TxContext) -> Loan`
  - Requests a loan from a lender.

- `repay_loan(borrower: &mut Borrower, lender: &mut Lender, loan: &mut Loan, repayment_amount: u64, ctx: &mut TxContext)`
  - Repays a loan.

- `withdraw_funds(lender: &mut Lender, amount: u64, ctx: &mut TxContext)`
  - Withdraws funds from a lender's account.

- `get_lender_balance(lender: &Lender) -> &Balance<SUI>`
  - Gets the balance of a lender.

- `get_borrower_balance(borrower: &Borrower) -> &Balance<SUI>`
  - Gets the balance of a borrower.

## Usage

### Creating a Lender

To create a new lender, call the `create_lender` function with the transaction context and the lender's name:

```rust
create_lender(ctx, "Lender Name");
```

### Creating a Borrower

To create a new borrower, call the `create_borrower` function with the transaction context and the borrower's name:

```rust
create_borrower(ctx, "Borrower Name");
```

### Depositing Funds

To deposit funds into a lender's account, call the `deposit_funds` function with the lender, amount to deposit, and transaction context:

```rust
deposit_funds(&mut lender, amount, ctx);
```

### Requesting a Loan

To request a loan, call the `request_loan` function with the borrower, lender, loan amount, interest rate, loan time, due time, and transaction context:

```rust
let loan = request_loan(&mut borrower, &mut lender, loan_amount, interest_rate, loan_time, due_time, ctx);
```

### Repaying a Loan

To repay a loan, call the `repay_loan` function with the borrower, lender, loan, repayment amount, and transaction context:

```rust
repay_loan(&mut borrower, &mut lender, &mut loan, repayment_amount, ctx);
```

### Withdrawing Funds

To withdraw funds from a lender's account, call the `withdraw_funds` function with the lender, amount to withdraw, and transaction context:

```rust
withdraw_funds(&mut lender, amount, ctx);
```

### Getting Lender Balance

To get the balance of a lender, call the `get_lender_balance` function with the lender:

```rust
let balance = get_lender_balance(&lender);
```

### Getting Borrower Balance

To get the balance of a borrower, call the `get_borrower_balance` function with the borrower:

```rust
let balance = get_borrower_balance(&borrower);
```

## License

This project is licensed under the MIT License.
```

This `README.md` file provides a comprehensive overview of the module, its structures, functions, and usage instructions.# lending-platform
