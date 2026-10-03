# 06 - Clearing, Exchange Rate Differences, Taxes

</br>

- Posting with Clearing - Incoming and Outgoing payments (Cash Discounts)
- Account Clearing - Credit Memo
- **Exchange Rate Differences**
- **Taxes (Input tax and Output tax)**
- **Clearing - Payment Differences**
- Payment Differences - Partial Payment and Residual Items
- Tolerance Groups (G/L, Customers / Vendors)
- Reset Cleared Items

</br></br>

## Posting with Clearing - Incoming and Outgoing payments (Cash Discounts)

Posting with clearing in SAP matches open items (like invoices) against offsetting entries (like payments or credit memos) to zero out and close customer or vendor accounts

Create a Discount Payment terms in OBB8 and assign it to Customer in FD02 / XD02 company code -> payment transaction tab -> payment terms

so when posting document using this customer will pick this payment terms in case payment terms is suppressed in FB70 Transaction then Find the GL involved for this document in details tab and locate the G/L Account number Open the GL in FS00 transaction and view the field status group assigned for this G/L lcoate the Field status group number in tab (Create/bank/interest) then Open OBC4 and view the Field status groupand here the mising field can be located 

</br>

#### SAP Clearing Overview

**• Incoming Payments:** Clears customer receivables (e.g., via F-28 or Clear Incoming Payments Fiori App).

**• Outgoing Payments:** Clears vendor payables (e.g., via F-53 or Clear Outgoing Payments Fiori App).

**• Transfer Posting with Clearing:** Adjusts non-cash differences like bad debt write-offs

</br>

#### Incoming Payments Process (Customer)

**• Access Transaction:** Use GUI code F-28 or the Fiori app.

**• Header Data:** Enter company code, posting date, and bank G/L account.

**• Allocation:** Input payment amount and customer account details.

**• Select Open Items:** Choose specific invoices to match against the payment.

**• Simulate & Post:** Check that the unassigned balance is zero, then save the journal entry.

</br>

#### Outgoing Payments Process (Vendor)

**• Access Transaction:** Use GUI code F-53 or the Fiori app.

**• Header Data:** Enter document date, company code, and bank account.

**• Selection:** Specify the vendor and select open payable items or credit memos.

**• Assign Amounts:** Allocate payment to the correct invoice lines.

**• Simulate & Post:** Verify balance reaches zero before final posting.


</br>

</br></br>


> [!NOTE]
> test sample 

</br></br>

</br>


</br></br>

<p align="center"> <a href="https://github.com/Octavius-Dante/SAP-FICO-2026/tree/main"> FICO-2026 Main page </a> </p>

