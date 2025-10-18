# ⚡ Flash Loan System (Solidity)

A simple and educational **Flash Loan Smart Contract** built with **Solidity**.  
This project demonstrates how a user can borrow tokens **without collateral**, provided the borrowed amount is **repaid within the same transaction block**.

> ⚠️ **Disclaimer:** This contract is for **educational and demonstration purposes only**.  
> It is **not secure for production use** and should **not** be deployed with real assets.

---

## 🧠 Overview

A **flash loan** allows users to borrow cryptocurrency instantly and without collateral, as long as they repay the borrowed amount before the transaction ends.  
If the borrower fails to repay the loan within the same transaction, the entire operation **reverts automatically**, ensuring the lender’s funds remain safe.

This project includes two main contracts:

- **`FlashLoanProvider`** → Lends tokens temporarily.
- **`FlashLoanReceiver`** → Borrows tokens, performs actions, and repays instantly.

---

## 🏗️ Smart Contract Details

### **1. FlashLoanProvider**
- Holds the token liquidity pool.
- Provides flash loans to borrowers.
- Ensures repayment before the transaction completes.

### **2. FlashLoanReceiver**
- Requests a flash loan from the provider.
- Executes custom logic using borrowed tokens (like arbitrage or liquidation).
- Repays the loan before the transaction ends.

---

## 🧩 Key Solidity Features Demonstrated

| Concept | Description |
|----------|-------------|
| **Interfaces (IERC20)** | Defines token transfer and balance functions. |
| **State Variables** | Used to store token and provider addresses. |
| **External Calls** | Borrower logic is executed via low-level `.call()`. |
| **Require Statements** | Validate repayment and security checks. |
| **Access Control** | Only owner or provider can call sensitive functions. |

---

## ⚙️ How It Works

1. **Deploy** an ERC-20 token (or use an existing testnet token).  
2. **Deploy `FlashLoanProvider`**, passing the token address in the constructor.  
3. **Fund** the provider contract with tokens (the loan pool).  
4. **Deploy `FlashLoanReceiver`**, linking it to the provider and token address.  
5. **Call `startFlashLoan(amount)`** on the receiver contract.  
6. The provider transfers the tokens, calls the receiver’s logic, and checks repayment.

If repayment fails, the transaction **automatically reverts**, so no funds are lost.

---

## 💻 Example Functions

| Contract | Function | Description |
|-----------|-----------|-------------|
| `FlashLoanProvider` | `flashLoan(uint amount, address borrower, bytes calldata data)` | Executes a flash loan transaction. |
| `FlashLoanReceiver` | `startFlashLoan(uint amount)` | Starts the flash loan request. |
| `FlashLoanReceiver` | `executeOperation(uint amount)` | Executes borrower’s logic during the loan. |

---

## 🧪 Testing in Remix

You can test this contract easily using **Remix IDE**:

1. Open [Remix IDE](https://remix.ethereum.org/).  
2. Create a new file and paste this contract code.  
3. Deploy a simple ERC-20 token (for example, from OpenZeppelin).  
4. Deploy the **`FlashLoanProvider`** with the token’s address.  
5. Transfer some tokens to the provider contract.  
6. Deploy the **`FlashLoanReceiver`** with the provider and token addresses.  
7. Call `startFlashLoan(100)` to simulate borrowing and repayment.

---

## 🧰 Technologies Used

- **Solidity** `^0.8.0`
- **Remix IDE** (for testing)
- **OpenZeppelin ERC-20 Interface**
- **Ethereum Virtual Machine (EVM)**

---

## 📄 Lic
