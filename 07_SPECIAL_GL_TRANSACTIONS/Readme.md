# 07 - Special G/L Transactions 

</br>

Special G/L (General Ledger) transactions in SAP are Accounts Receivable (FI-AR) and Accounts Payable (FI-AP) entries that bypass standard reconciliation accounts and post to alternative balance sheet G/L accounts. You can access official documentation and configuration references via the SAP Help Portal.

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


#### Common Transaction Codes (T-Codes)

**• FBKP / SPRO:** Configure Special G/L indicators and assign alternative reconciliation accounts.

**• FS00:** Create or modify G/L account master records.

**• F-29:** Post customer down payment (Indicator A).

**• F-39:** Clear customer down payment against an invoice.

**• FBL5N / FBL1N:** Review customer or vendor line item displays.

</br></br>


> [!NOTE]
> test sample 

</br></br>

</br>


</br></br>

<p align="center"> <a href="https://github.com/Octavius-Dante/SAP-FICO-2026/tree/main"> FICO-2026 Main page </a> </p>

