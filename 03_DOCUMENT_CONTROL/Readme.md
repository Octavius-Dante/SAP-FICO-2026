# 03 - Document Control

</br>

- **Document Structure**
- Header level - Document type, Number Ranges, Account type
- Item level - Posting Keys, Field Status
- **Simple Documents in Financial Accounting** 
- G/L Document Posting, Document Display, Display / Change Line items and Display balances
- **Reference Documents**
- Account Assignment Model
- Recurring Model
- Accounts Receivable Invoice, Document Display, Display / Change Line items and Display balances
- Accounts Payable Invoice, Document Display, Display / Change Line items and Display balances
- Customer / Vendor Credit Memo

</br>

Any document you find in SAP will have Header level and Item level thats how structuring was defined in SAP,
Date and other information will be common for all the items

- Header level is controlled by document type 

- Item level is controlled by posting keys 

- Document type is used to identify different type of business transaction 

- Item contains only item specific information not common info like header level

- Document Types are created at Client level valid for all the clients SAP has already delivered some set of standard document types very few cases where business disconnect with standard document type then companies create custom document type

- Document type also controls the account type , it is a customer document or vendor document, asset document o gal document ...etc

</br>

There are 2 different type of view when posting a document 

 - Entry view (How a document is posted)
 - General Ledger view (How the document can be viewed accordingly as per general ledger)

A Fi document is identified by 3 objects 

- Company code [AU01] 
- Document number [123456789]
- Fiscal year [2026]

how SAP functions for SAP number range explanation 

2024 - NR [180000000 - 189999999] 
2025 - NR [180000000 - 189999999]  

as per above number range setting same number range will be used for different Fiscal year when next year starts the number range also starts from begining  

 example : 180000025 document is the last document of 2024
in 2025 the first document created will be 1800000001

- How many types of Account types are allowed or available in Document type number is 5 

1. Asset
2. Customer
3. Vendor
4. Material
5. G/L Account 
 

Item level contains posting keys and posting key is a representation of a transaction it is a major component 

posting key can be created in sap system by understanding the existing posting keys functionality and its ingredients 

it is not advisable to change the standard sap posting key, recommended to create new

</br></br>


## What is posting in SAP ?

Posting in SAP is the official process of recording a business or financial transaction into the system's general ledger and accounting tables, creating a permanent audit trail

</br>

## General Ledger posting (FI-GL)

General ledger (G/L) posting in SAP is the core financial process of recording business transactions as debits and credits into the central accounting repository
 
G/L posting can be performed in 2 ways in SAP

 - F-02  : "General posting" - is an old way of posting the documents 
 - FB50  : "Enter GL account document" is the most user friendly way of posting 

**Other Transactions related to Posting Vie and change**

 - FB02  : Change Document 
 - FB09  : Change Line items 
 - FB03  : Display 

- **G/L document is only used for internal posting purposes**  
- **Customer and Vendor document are used for external purposes** 

</br>

**Chart of Accounts Segment:** Defines the account number, name, and general layout valid for the entire corporate structure.

**Company Code Segment:** Contains specific operational rules (such as currency or tax settings) applied when extending the account to a specific company code.


</br>

#### Core Functions 

 - **Central Repository:** Records all debits and credits across an enterprise to maintain a real-time picture of financial health.

- **Subledger Integration:** Automatically reconciles data from submodules like Accounts Payable (AP), Accounts Receivable (AR), and Asset Accounting (AA).

- **Parallel Accounting:** Supports simultaneous compliance with multiple accounting standards, such as IFRS and local GAAP.

</br>

#### Key Building Blocks

- **Chart of Accounts (COA):** A categorized list of all general ledger accounts used by a business.

- **Account Groups:** Classify accounts (e.g., assets, liabilities, revenues, expenses) and determine their number ranges and required creation fields.

- **Field Status Groups:** Control whether specific posting fields are required, optional, or hidden during data entry.


</br>

## Reference Document

Instead of creating a document from scratch it is more convenient to create a document by taking reference it reduces manual effort of filling more input fields in screen

lets say you have 100's of line item in a document manually input all 100 items is cumbersome so take a reference and change only the necessary in that 100 line items or even changing all 100 items it reduces some manual work comparing to create it from scratch 

- FKMT   : FI Acct Assignment Model Management	 

</br>

## Recurring Document 

A recurring document in SAP is a template used to automate business transactions that repeat at regular intervals with fixed amounts and accounts

</br>

#### Key Characteristics 

- **Not an Accounting Document:** Creating a recurring document does not update account balances or generate actual transaction figures; it serves purely as a reference model.- 

- **Fixed Data:** The posting key, accounts, and amounts remain constant across postings.

- **Validity Period:** Defines a start date (first run), an end date (last run), and a posting frequency (interval in months).

- FBD1: Create a recurring document
- FBD2: Change a recurring document
- FBD3: Display a recurring document
- F.14 / F.15: Execute or post recurring entries (create batch input sessions)

</br>


## Accounts Receivable (FI-AR)

**Accounts Receivable (FI-AR)** in SAP is a sub-module in SAP Financial Accounting that records, tracks, and manages all accounting data and financial transactions related to customers.

It forms the financial backbone of the **Order-to-Cash (O2C)** cycle, ensuring that money owed by customers for goods or services delivered on credit is accurately billed, collected, and reconciled.

**Customer invoice** in SAP is a formal financial document used to bill a buyer for delivered goods or provided services, record accounts receivable, and trigger revenue recognition


</br>

#### Core Characteristics

**Purpose:** Requests payment from a customer and updates financial ledgers.

**Integration:** Connects logistics (Sales and Distribution) with financial accounting (FI) in an SAP Help Portal workflow.

**Key Data:** Contains customer IDs, line items, pricing, taxes, and payment terms.

</br>

#### How Invoices are Created in SAP

- **Sales and Distribution (SD) Billing:** Generated automatically or manually via transaction VF01 (often referencing a delivery or sales order).

- **Financial Accounting (FI) Entry:** Posted directly through transactions like FB70 (for customer invoice entry) or F-22 (Customer Invoice posting) when no prior sales order exists.


</br></br>

</br>


</br></br>

<p align="center"> <a href="https://github.com/Octavius-Dante/SAP-FICO-2026/tree/main"> FICO-2026 Main page </a> </p>

