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


</br></br>


## What is General Ledger Accounts ?



</br></br>



</br>


## Accounts Receivable (Master records) 



> [!NOTE]
> FI consultants wont create - Sales Area Segment in AR and Purchasing Area Segment in AP  

</br>

## Accounts Payable (Master records) 



</br>



</br>


</br></br>

<p align="center"> <a href="https://github.com/Octavius-Dante/SAP-FICO-2026/tree/main"> FICO-2026 Main page </a> </p>

