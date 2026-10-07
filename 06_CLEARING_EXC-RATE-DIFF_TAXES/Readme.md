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

so when posting document using this customer will pick this payment terms in case payment terms is suppressed in FB70 Transaction then Find the GL involved for this document in details tab and locate the G/L Account number Open the GL in FS00 transaction and view the field status group assigned for this G/L locate the Field status group number in tab (Create/bank/interest) then Open OBC4 and view the Field status group and here the missing field can be located 

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


#### Payment terms and cast Discount 

**Account Clearing:** Offsetting existing line items with no new posting. 

**Post with Clearing:** Entering a payment while simultaneously closing the open invoice.

- Post with clearing AR (F-32) 
- Post with clearing AP (F-44) 
- Post with clearing G/L (F-04)
- Incoming payment (F-28)
- Outgoing Payment (F-53)
- Reversal posting AR/AP (FB08)

</br>

## Exchange rate Differences

When open items in a foreign currency are cleared, SAP automatically calculates and posts realized exchange rate gains or losses to designated G/L accounts.

Account numbering sample

- Exchange Rate Realized Loss - 5810
- Exchange Rate Un Realized Loss - 5815
- Exchange Rate Realized Gain - 6810
- Exchange Rate Un Realized Gain - 6815
- Balance sheet Adjustment - 1099

Postings are done automatically 

</br></br>

### A realized exchange rate loss

 Transaction recorded at a higher exchange rate and payment for that transaction cleared at a lower exchange rate this difference of reduced value of the exchange rate is a loss due to exchange rate fluctuation in the market. Vice versa of this is A realized exchange rate Gain

**In other words A realized exchange rate loss is an Actual Loss**

In case of Receivable 

- Higher exchange rate transaction -> lower exchange rate (payment) receivable is a Loss (Actual Payment Received)
    
##### Example : 

Transaction Value of Euro on Jan 1st 1 euro = 100 INR - Transaction recorded date 

Transaction Value of Euro on Feb 1st 1 euro = 90 INR - Payment for transaction 
(Actual Payment Received)

</br>

In Case of Payable

- Lower exchange rate transaction -> Higher exchange rate (payment) payable is a Loss (Actual Payment Done)

##### Example : 

Transaction Value of Euro on Jan 1st 1 euro = 100 INR - Transaction recorded date 

Transaction Value of Euro on Feb 1st 1 euro = 110 INR - Payment for transaction 
(Actual Payment Done)

</br></br>

### A realized exchange rate Gain

Transaction recorded in a lower exchange rate and payment cleared in a higher exchange rate results in gain because of the growth of the exchange rate value gives a higher yield profit because of boost in currency value

**In other words A realized exchange rate Gain is an Actual Gain**

In case of Receivable 

- Lower exchange rate transaction -> Higher exchange rate (payment) receivable is a Gain (Actual Payment Received)

##### Example : 

Transaction Value of Euro on Jan 1st 1 euro = 100 INR - Transaction recorded date 

Transaction Value of Euro on Feb 1st 1 euro = 110 INR  - Payment for transaction (Actual Payment Received)

</br>

In Case of Payable

- Higher exchange rate transaction -> Lower exchange rate (payment) payable is a Gain (Actual Payment Done)

##### Example : 

Transaction Value of Euro on Jan 1st 1 euro = 100 INR - Transaction recorded date 

Transaction Value of Euro on Feb 1st 1 euro = 90 INR  - Payment for transaction (Actual Payment Done)

</br></br>

### An Unrealized exchange rate loss

An Unrealized exchange rate loss In SAP occurs when open items or foreign currency balances are revalued at the closing period rate, creating a paper loss before settlement.

**In other words An Unrealized exchange rate loss is not an Actual Loss it is a Bookkeeping record of awaiting receivable (Transaction happened at higher exchange rate and now exchange rate value is going down) if received it will be a loss, since payment is not received or cleared its just assessed in books for record**

In case of Receivable 

- Higher exchange rate transaction -> lower exchange rate (payment) receivable is a Loss (Assessed for book but not received)

In Case of Payable

- Lower exchange rate transaction -> Higher exchange rate (payment) payable is a Loss (Assessed for book but not paid)


</br></br>

### An Unrealized exchange rate Gain 

An Unrealized exchange rate Gain in SAP is a paper gain recorded during period-end foreign currency valuation for open items that have not yet been settled or cleared.

**In other words An Unrealized exchange rate Gain is not an Actual Gain it is a Bookkeeping record of awaiting receivable (Transaction happened at lower exchange rate and now exchange rate value is going up) if received it will be a Gain, since payment is not received or cleared its just assessed in books for record**

In case of Receivable 

- Lower exchange rate transaction -> Higher exchange rate (payment) receivable is a Gain (Assessed for book but not received)

In Case of Payable

- Higher exchange rate transaction -> Lower exchange rate (payment) payable is a Gain (Assessed for book but not paid)


Document clearing (payment run via F-53 or FB05)


</br></br></br>


#### Understanding the Process

- Trigger: Period-end foreign currency valuation.
- Purpose: Financial reporting accuracy.
- Reversal: Automatic reverse posting next period.
- Key T-Code: F.05 


</br>

#### Core Mechanics

**• The Trigger:** Exchange rate changes between the original posting date and the clearing date.

**• The Calculation:** SAP compares the local currency amount posted initially versus the value at the clearing exchange rate.

**• The Result:** SAP automatically generates a balancing line item for the realized gain or loss.

</br>

#### Configuration & Setup

**• Account Determination:** Configured via transaction OBA1 (or transaction key KDF).

**• Exchange Rates:** Maintained in table via transaction OB08.

**• Tolerance Groups:** Handled through configuration to manage small rounding or payment differences.

</br>

#### Common Issues & Troubleshooting

**• Massive/Unexpected Diffs:** Often caused by manual local currency overrides or incorrect rates in OB08 on the clearing day.

**• Valuation Carryover:** Prior foreign currency valuations (F.05 / advanced valuation) might leave delta balances that interact with clearing logic.

**• Local Currency Settings:** Check the "No Exch. Rate Diff. When Clearing in LC" indicator if clearing foreign currency with local currency creates unwanted delta entries.

</br></br>

## Taxes 

Taxes in SAP refer to the automated calculation, posting, and reporting of statutory financial charges (such as VAT, GST, sales tax, or withholding tax) integrated across business modules like Financial Accounting (FI), Sales and Distribution (SD), and Materials Management (MM).

**- Input Tax (Purchases from Vendor) - Assets** (When your Purchases are More than your sales you can claim that taxes Revenue and Customs) standard rate 20%

**- Output Tax (Sales to customer) - Liability** (When your Sales is more than your purchases then you have to pay taxes to Revenue and Customs) standard rate 20%

**- Zero 0% Tax** (Need to produce the transaction documents which are Involved with 0% evidence when you are making the claim)

**- Exempt from Tax** (Not required to produce the evidence like a transaction donation to a charitable organization , non-profit organization)


</br>

 ##### Core Components of SAP Tax

**- Tax Codes (FTXP):**
	    • Defines specific tax rates and rules per country.
	    • Determines whether a transaction is input or output tax.

**- Calculation Procedures:**        
        Defines step sequences and condition types for computing tax bases.

**- Tax Accounts Determination: (OB40)**        
        Automatically maps computed tax values to designated General Ledger (G/L) accounts.

**Tax Jurisdiction Codes:**        
        Manages multi-level regional tax authorities (e.g., state, county, city).

</br>

#### Condition Techniques in SAP TAX (Customization) OBYZ 

- Step 1 - Allowed Fields 
- Step 2 - Condition Tables 
- Step 3 - Access Sequence 
- Step 4 - Condition Types
- Step 5 - Procedure 

</br></br>

- 1 OBYZ - [**Condition Table**, **Access Sequence**, **Condition Types**, **Procedures**] 
                 
                 Procedure = [Condition Type, Account Key] 
                 Condition Types = [Calculation Rules with Access Sequence]
                 Access Sequence = [Tables and Key Fields involved for tax evaluation]
                 Condition Table = []

- 2 OBBG - [**Procedure** Assignment to a Country]
- 3 FTXP - [**Tax Code** identified with or without Tax Jurisdiction depends on country , info about tax code's **Tax category** Input or Output tax]
- 4 OB40 - [**Account Key / Transaction /Process Keys**, **Chart of accounts**, **G/L assignment to Tax codes**]

</br>

#### Calculation of Taxes during a document posting 

- **Gross Procedure** Tax calculated within the Entered amount and total valuation remains same as entered amount 

Example : Entered amount is 15000 of a document posting then tax setting is 20%  then total value will be calculated like this 

                 Tax rate = 20
                 Tax calculation value (TCV) = 100 + 20

                 ( Base amount = (Entered Amount x 100) / 120  )
                 ( Tax Value = Base amount x 20% )
                 ( Base amount + Tax value = Entered Amount )

</br>

- **Net Procedure** Tax calculated with the entered amount and total valuation is increased 

Example : Entered amount is 15000 of a document posting then tax setting is 20%  then total value will be calculated like this 

                 ( Tax value = entered amount x 20% )
                 ( Total value = Entered amount + tax value )

                 ( 3000 = 15000 x 20% )
                 ( 18000 = 15000 + 3000)

</br></br>


## Clearing - Payment Differences

- Customer FBL5N to view , FB70 create invoice Doc. and do the payment F-28
- Vendor FBL1N to view , FB60 create invoice Doc. and do the payment F-43
- GL FBL3N to view , FB50 create G/L posting Doc. and (F-03, F-04) used for manual clearing of G/L posting

</br>

#### GL Clearing Differences 

- ✅ F-03: Clear G/L Account (Manual clearing of open items that balance to zero)
- ✅ F-04: Post with Clearing (Manually post an offsetting entry and clear open items simultaneously)









</br></br>


> [!NOTE]
> test sample 

</br></br>

</br>


</br></br>

<p align="center"> <a href="https://github.com/Octavius-Dante/SAP-FICO-2026/tree/main"> FICO-2026 Main page </a> </p>

