# 07 - Special G/L Transactions 

</br>

- Configuration of Special G/L Transactions
- Down Payment Received
- Down Payment Made 
- **Cash journal (Bank Accounting)**
- Cash Journal Configuration
- Cash Journal Transaction 
- **Parking and Holding Documents**
- Basics of Document Parking Versus Hold Document
- Parking Documents and Processing Parked Document 
- **Validations and Substitutions**
- Validations and Substitutions 


</br></br>

Special G/L (General Ledger) transactions in SAP are Accounts Receivable (FI-AR) and Accounts Payable (FI-AP) entries that bypass standard reconciliation accounts and post to alternative balance sheet G/L accounts. You can access official documentation and configuration references via the SAP Help Portal.


In SAP FI, a down payment (advance payment) is used when a company pays a vendor or receives money from a customer before goods or services are delivered or invoiced

</br>

#### Key Characteristics

**• Alternative Reconciliation Accounts:** Instead of posting to standard trade debtor or creditor accounts, entries route to dedicated G/L accounts (e.g., separating customer/vendor down payments from regular invoices).

**• Special G/L Indicators:** Single-character codes (such as A for down payments or F for down payment requests) flag the transaction type during posting.

**• Special Posting Keys:** These transactions use specific posting keys (such as 09, 19, 29, and 39) to dictate debit/credit and account routing

</br>

#### Classification of Special G/L Transactions

<table>
    <tr>
        <td>Type</td> 
        <td>How It Affects Books</td>
        <td>Common Examples</td>
    </tr>
    <tr>
        <td>Real-Time Posted Transactions</td>
        <td>Immediately generates accounting entries, updates the G/L, bank accounts, and customer/vendor subledgers.</td>
        <td>Customer/vendor advances, down payments, security deposits.</td>
    </tr>
    <tr>
        <td>Noted Items</td>
        <td>Statistical entries for record-keeping only; they do not update account balances or generate debit/credit entries.</td>
        <td>Down payment requests (indicator F).</td>
    </tr>
    <tr>
        <td>Statistical Postings</td>
        <td>Automatically posts offsetting entries to predefined G/L accounts.</td>
        <td>Guarantees, reserve for bad debts.</td>
    </tr>
</table>

</br>

#### Common Transaction Codes (T-Codes) For G/L creation and Special indicator setup

**• FBKP / SPRO:** Configure Special G/L indicators and assign alternative reconciliation accounts.

**• FS00:** Create or modify G/L account master records.

</br>

#### Transaction Codes (T-Codes) Customer Special G/L and Down payment postings   

**• F-37:** : Customer Down Payment Request (Optional) (noted item with no financial accounting impact).

**• F-29:** Post customer down payment (Indicator A).

**• F-32:** Clear Customer - Open items

**• FB70:** Post a Customer invoice 

**• F-39:** Clear customer down payment against an invoice.

**• F-28:** Clear customer invoice payment.

**• FBL5N :** Review customer line item displays.

</br>

#### Transaction Codes (T-Codes) Vendor Special G/L and Down payment postings   

**• F-47:** : Vendor Down Payment Request (Optional) (noted item with no financial accounting impact).

**• F-48:** Post Vendor down payment (Indicator A).

**• F-44:** Clear Vendor - Open items

**• FB60:** Post a Vendor invoice 

**• F-54:** Clear Vendor down payment against an invoice.

**• F-53:** Clear Vendor invoice payment.

**• FBL1N :** Review customer line item displays.

</br></br>

## Cash Journal (Bank Accounting) 

The cash journal in SAP (transaction code **FBCJ**) is a subledger of Financial Accounting and Bank Accounting used to manage and track all day-to-day cash transactions (such as petty cash)

</br>

#### Key Functions and Features

**• Transaction Management:** Records cash receipts and cash payments, including petty cash expenses (like travel or office supplies), customer cash payments, and vendor cash payments.

**• Automatic Balances:** Automatically calculates and displays opening balances, total receipts, total payments, and closing balances in real time.

**• General Ledger Integration:** Postings made in the cash journal automatically update the General Ledger (G/L), Accounts Receivable (AR), and Accounts Payable (AP).

**• Multi-Currency & Multi-Box Support:** Companies can run multiple cash journals per company code, maintaining a separate journal for each currency or physical cash box/branch location.

**• Two-Step Workflow:** Users can save entries in the cash journal first before posting them permanently to Financial Accounting.


> [!NOTE]
> test sample 

</br></br>

</br>


</br></br>

<p align="center"> <a href="https://github.com/Octavius-Dante/SAP-FICO-2026/tree/main"> FICO-2026 Main page </a> </p>

