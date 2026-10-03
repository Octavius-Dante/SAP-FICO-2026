# 04 - Posting Control

</br>

- Default Values : Document Type and Posting Key
- Document changes
- Document Change control
- Document Reversal
- Normal Reverse Posting
- Negative Reversal Posting
- Payment Terms and Cash Discounts

</br></br>

Default values for Document posting is defined by SAP and  cannot be redefined or modified it can be only viewed as information 

Transaction : OBU1 - Default document settings 


Control Header field and Item fields of a document during change it can be defined in SAP transaction for restriction purpose once a document is created not all the fields can be changed some of them are restricted this restriction can be defined

Transaction : OB32 


line items should be carefully chosen with account types defined in OB32 

        A - Assets 
        D - Customers 
        M - Materials 
        K - Vendors 
        S - G/L accounts 

</br>

#### SPRO PATH : 


**Permit Negative posting** 

Financial Accounting (New) > General Ledger Accounting (New) > Business Transactions > Adjustment Posting/Reversal > Permit Negative posting 


**Reasons for Reversal**

Financial Accounting (New) > General Ledger Accounting (New) > Business Transactions > Adjustment Posting/Reversal > Define Reasons for Reversal 


</br>

- Normal Reverse posting is for Customer invoice (FB70) AR
- Negative Reverse posting is for Vendor invoice (FB60) AP
- Normal Reversal and Negative Reversal both are performed in (FB08)

In the background credit memo is posted and reversal document is created in SAP when reversal processing happens 

Go to FB03 and enter the original invoice which was reversed and see the document flow in (Environment -> Display Document Flow)

</br></br>


> [!NOTE]
> test sample 

</br></br>

</br>


</br></br>

<p align="center"> <a href="https://github.com/Octavius-Dante/SAP-FICO-2026/tree/main"> FICO-2026 Main page </a> </p>

