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

</br></br>

## Parking and Holding transactions for Posting 


Document parking in SAP FI (Financial Accounting) is a feature that lets users save incomplete or unverified accounting documents in the system and assign them a real document number without updating general ledger (GL) account balances or financial reports.

</br>

#### SAP Transactions which supports Parking 

- FB50: G/L Account Posting (Park option available)
- FB60: Vendor Invoice (Park option available)
- FB65: Vendor Credit Memo (Park option available)
- FB70: Customer Invoice (Park option available)
- FB75: Customer Credit Memo (Park option available)
- F-90: Asset Acquisition / Purchase (Park option available)
- F-65: Enter Parked Document (General document parking entry screen)
- F-02 / FV50 / FV60: Document entry variations supporting park or specific parking transaction codes (e.g., FV60 for parking vendor invoices).

</br>

#### Transaction to handle Parking documents 

- FBV1 / FV50: Park a document
- FBV2: Change a parked document
- FBV3: Display a parked document
- FBV0: Post or delete a parked document

</br></br>

#### Document Hold

**• Purpose:** Used for personal interruptions or when a document is incomplete and you need to step away or wait for more information (e.g., missing a cost center or bank details).

**• Document Number:** You manually assign a temporary name or number when saving. It does not generate a true SAP FI document number.

**• Visibility & Workflow:** Private. It is tied strictly to the user who created it; other users cannot view, edit, or workflow-approve it.

**• Common T-Codes:** F-50, FB50 (depending on entry method).

</br>

#### Document Park

**• Purpose:** Used for formal review, dual verification, or multi-tier approval workflows (e.g., an invoice exceeds a user's posting limit and must be reviewed by a manager).

**• Document Number:** The system automatically assigns a real SAP document number upon parking.

**• Visibility & Workflow:** Shared. It is visible across the system to other authorized users and can be routed through SAP workflow, modified, rejected, or posted by a second person.

**• Common T-Codes:** FBV1, FV50, F-02.

</br>

#### Key Differences at a Glance


<table>
    <tr>
        <td>Feature</td>
        <td>Document Hold</td>
        <td>Document Park</td>
    </tr>
    <tr>
        <td>Primary Use Case</td>
        <td>Personal draft / waiting for clarification</td>
        <td>Formal review, dual control, or approval</td>
    </tr>
    <tr>
        <td>Document Number</td>
        <td>User-defined temporary name/number</td>
        <td>Official SAP document number generated</td>
    </tr>
    <tr>
        <td>Visibility</td>
        <td>Only visible/accessible to the creator</td>
        <td>Visible to other users / approvers in the system</td>
    </tr>
    <tr>
        <td>Workflow Support</td>
        <td>None</td>
        <td>Supported (can trigger approvals/releases)</td>
    </tr>
    <tr>
        <td>GL / Balance Impact</td>
        <td>None</td>
        <td>None (until officially posted)</td>
    </tr>
</table>

</br></br>

> [!NOTE]
> test sample 

</br></br>

</br>


</br></br>

<p align="center"> <a href="https://github.com/Octavius-Dante/SAP-FICO-2026/tree/main"> FICO-2026 Main page </a> </p>

