# 02 - Master Data (Configuration)

</br>

- General Ledger Accounts (Master Records)
- Operative or Company Code Chart of Accounts
- Group Chart of Accounts (Consolidated Financial Statements)
- Country Chart of Accounts  
- Account Group / Field Status
- Defined Retained Earnings
- Field Status Variant / Group of GL Accounts
- Creation of GL Accounts(1: Chart of Accounts segment and 2: Company code segment)
- Accounts Receivable (Master records) - (3: General Data Company code segment and Sales Area Segment)
- Accounts Payable (Master records) - (3: General Data Company code segment and Purchasing Area Segment)
- Bank (Master Data)

</br>


System should be prepared and setup properly first then GL accounts can be created 
how to setup the system correctly it should be done here in SPRO

SPRO > SAP Reference IMG > Financial Accounting (New) > General Ledger Accounting (New) > Master Data > G/L Accounts > Preparations > Edit Chart of Accounts List

Chart of accounts is the highest level of hierarchy for GL accounts 


- A Company code segment used by one country cannot be used by another country 
- Company Code Chart of accounts will receive the posting directly through GL accounts 
- Group Chart of Accounts and Country Chart of Accounts will receive the posting in-directly (Auto populated) through Operative Chart of Accounts  (or operating chart of accounts)


</br>

**Operative Chart of accounts** is a main chart of accounts which is operational for business  Transaction : FS00
</br>
Chart of accounts cannot be deleted when a GL posting exist it can only be blocked
</br>

**Group Chart of Accounts** is an Optional chart of accounts also called as **Consolidated financial statements** to get the total value of a company across globe in multiple country you will use this Transaction : FSP0 
</br>

**Country Chart of Accounts** is an Optional it is used for reporting purposes at country level 
</br>

**INT** is the standard template SAP as provided for Chart of accounts 
</br>

**Account group** Contains Assets, Liabilities, Expenses, Revenue (R.E.A.L) It is categorization of GL Accounts 
</br>

Number Ranges in GL accounts can be overlapped, But Number ranges in vendor master and customer master cannot be overlapped 
</br>

**Retained Earnings Account** 
</br>

</br></br>


## What is General Ledger Accounts ?

Length of GL Account number : max is 10 




</br>



</br>


</br></br>

<p align="center"> <a href="https://github.com/Octavius-Dante/SAP-FICO-2026/tree/main"> FICO-2026 Main page </a> </p>