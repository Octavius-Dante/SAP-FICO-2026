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

</br>

## Payment Terms and Discounts

Payment terms in SAP are 4-character keys that automate invoice due dates, cash discount percentages, and installment splits for customers and vendors

</br>

 #### Core Components

**• Baseline Date:** Starting point for calculation (document, posting, or entry date).

**• Discount Periods:** Early payment windows and respective percentages.

**• Net Due Date:** Final day full payment is required.

**• Installment Splits:** Dividing total amounts across multiple payment dates.

</br>

#### Key Configuration & Master Data

**• T-Code OBB8:** Maintain and create new payment terms globally.

**• T-Code OB88 / SPRO:** Path via Financial Accounting > Accounts Receivable/Payable > Business Transactions > Maintain Terms of Payment.

**• Business Partner (BP):** Assigned in vendor/customer master segments (FI, MM, or SD views).

</br>

#### Common Types of Payment Terms

<table>
    <tr>
        <td>Type</td>
        <td>Description</td>
        <td>SAP Example / Behavior</td>
    </tr>
    <tr>
        <td>Fixed / Net</td>
        <td>Fixed days from baseline date</td>
        <td>0001 (Immediate) or Net 30</td>
    </tr>
    <tr>
        <td>Cash Discount</td>
        <td>Percentage off if paid early</td>
        <td>2% discount within 10 days, Net 30</td>
    </tr>
    <tr>
        <td>Installment</td>
        <td>Split across custom timelines</td>
        <td>Configured via parent term &amp; OBB9</td>
    </tr>
</table>


</br>

## Cash Discounts 





</br></br>


> [!NOTE]
> test sample 

</br></br>

</br>


</br></br>

<p align="center"> <a href="https://github.com/Octavius-Dante/SAP-FICO-2026/tree/main"> FICO-2026 Main page </a> </p>

