# 08 - Closing Activities

</br>

- **Month End and Year End Closing**
- **Automatic Payment Program (APP)**
- Payment Run Overview
- Payment Program Configuration
- Running the Payment Program
- Edit the payment Proposal
- Debit Balance Check
- **Automatic Dunning Program**
- Dunning Run - Overview 
- Dunning Program Configuration
- The Dunning Run
- Edit the Dunning Proposals
- Printing Dunning Notices 
- **Correspondence**
- Correspondence overview 
- Correspondence Types 


</br></br>

 ## Automatic payment program

The Automatic Payment Program (APP) in SAP Financial Accounting (FI) automates outgoing and incoming payments for vendors and customers based on pre-defined rules, due dates, and cash discount parameters

The automatic payment program was launched for product SAP R/3 in July 1992 to make customer / vendor payment activity automatic, if it was done manually that could result in human error or could not be possibly completed on time when so many company codes and so many transaction involved in single company code this could be cumbersome for the user 


#### Key Transaction Codes

**• F110:** Main transaction to execute the Automatic Payment Program (create parameters, proposals, and payment runs).

**• FBZP:** Customizing transaction to configure all APP settings (company codes, paying company codes, payment methods, and bank determination)


#### Key Configuration Steps (FBZP)

1. All Company Codes: Define sending and paying company codes, tolerances, and cash discount parameters.

2. Paying Company Codes: Specify minimum payment amounts, maximum amounts, and foreign business partner allowances.

3. Payment Methods in Country/Region: Set up payment types (e.g., Bank Transfer T, Check C, Electronic Data Interchange E) and master data requirements.

4. Payment Methods in Company Code: Configure document types, currency restrictions, and form definitions.

5. Bank Determination: Assign house banks (e.g., via FI12/FBZP), ranking orders, and bank sub-accounts.


#### Execution Steps in (F110)

1. Parameters Tab: Enter Run Date, Identification (5-character ID), Company Code, Payment Methods, and Next Posting Date.

2. Proposal Run:
	• Schedule the proposal to let SAP scan and select open invoices that are due.    
	• Review, edit, block, or unblock specific vendor/customer items as needed.

3. Payment Run:
	• Execute the payment run to post financial accounting documents, clear open items, and credit/debit accounts.

4. Payment Media / DME:
	• Generate checks, remittance advice, or Data Medium Exchange (DME) files (such as XML or flat files) to transmit to the bank.


#### Scenarios in which we pay customer

 - Customer can be a Supplier also in certain business cases so we may have to pay the customer because he is also a supplier  

 - Customer is returning the sold goods to US due to some valid reasons so we have to pay the customer

 - Customer some times over paid to our business for the transaction so that differences could be huge in number when summarized then we may have to pay it back to adjust our books to keep it clean or it looks like unlawful earnings with extra payments 




</br></br>

> [!NOTE]
> test sample 

</br></br>

</br>


</br></br>

<p align="center"> <a href="https://github.com/Octavius-Dante/SAP-FICO-2026/tree/main"> FICO-2026 Main page </a> </p>

