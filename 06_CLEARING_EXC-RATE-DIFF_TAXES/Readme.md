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


Partial Payment and Residual items (Means Remaining payments) 

**Partial Payments** will keep the original invoice document open until full amount is paid for the invoice when full amount is paid the Clearing document is generated

**Residual Payments** will close the original invoice document with what ever amount was paid  to it and open a New Open item document for remaining payments (So majorly used during period end or month end closing)


> [!NOTE]
> Residual Payment (creates a clearing document and creates another open item document and both document number will be same)

</br>

#### GL Clearing Differences 

- ✅ F-03: Clear G/L Account (Manual clearing of open items that balance to zero)
- ✅ F-04: Post with Clearing (Manually post an offsetting entry and clear open items simultaneously)


</br></br>

## Tolerance Groups for G/L 

In SAP Financial Accounting, a G/L tolerance group (configured via transaction code OBA0) Tolerance groups for general ledger (G/L) accounts in SAP define the maximum acceptable payment or clearing differences (in absolute amounts and/or percentages) that the system automatically posts to predefined gain or loss accounts during open item clearing

</br>

#### Key Details & Purpose

**• Automatic Posting:** If a clearing difference falls within the limits defined for the G/L account's tolerance group, SAP posts the difference automatically. If it exceeds the limit, you must handle it manually (e.g., via residual items, partial payments, or write-offs).

**• Separate Limits:** You can configure individual limits for debit postings and credit postings, using both fixed monetary amounts and percentage thresholds.

**• Blank Group Requirement:** You must configure a blank (default) tolerance group for your company code so that accounts without a specific assignment still fall back to standard system limits.

</br>

#### Important SAP Configuration & Transaction Codes

<table>
    <tr>
        <td>Function</td>
        <td>Transaction Code (T-Code)</td>
        <td>SPRO Path / Description</td>
    </tr>
    <tr>
        <td>Define G/L Tolerance Groups</td>
        <td>OBA0</td>
        <td>SPRO &gt; Financial Accounting &gt; General Ledger Accounting &gt; Business Transactions &gt; Open Item Clearing &gt; Clearing Differences &gt; Define Tolerance Groups for G/L Accounts</td>
    </tr>
    <tr>
        <td>Assign Tolerance Group to G/L Account</td>
        <td>FS00</td>
        <td>Company Code Segment -&gt; Control Data tab -&gt; Tolerance group field</td>
    </tr>
    <tr>
        <td>Configure Automatic Postings</td>
        <td>OBXZ</td>
        <td>Sets up the target expense or revenue accounts where clearing differences are automatically posted.</td>
    </tr>
    <tr>
        <td>Define User/Employee Tolerances (Related)</td>
        <td>OBA4</td>
        <td>Limits for document amounts, open items, and cash discounts.</td>
    </tr>
</table>



</br></br>

## Tolerance Groups for Customer 

customer tolerance group in SAP FI (Financial Accounting) defines the acceptable limits for payment and cash discount differences when clearing customer open items. If a customer's payment is slightly higher or lower than the invoice amount, the system uses these rules to automatically write off the small difference or post it to gain/loss accounts.

</br>

#### What It Controls

 For each customer tolerance group, you can specify limits for:

- Permitted payment differences: Maximum amounts and percentages (whichever is lower) for incoming payments that are underpaid or overpaid.

- Allowed cash discount differences: Tolerances for cash discounts taken outside terms or with minor discrepancies.

- Residual items: How remaining open items or short-payments are handled during manual or automatic clearing.

</br>

#### Key SAP Transactions & Configuration

**• Define Tolerance Groups (OBA3):** Create and configure customer and vendor tolerance limits per company code.

**• Assign Tolerance Group to Customer Master:**
	• SAP ERP (FD02 / XD02): Assign the group under the Company Code data -> Payment Transactions tab.
	• SAP S/4HANA (Business Partner): Assign the tolerance group inside the Business Partner role (FLCU00 or FLCU01) under Company Code -> Customer Payment Transactions.

**• Automatic Posting Accounts:** Set up the G/L accounts where small differences are automatically posted:
	• Payment difference expenses/losses: OBXI
	• Payment difference revenues/gains: OBXU

</br>

#### Default Behavior

If you leave the customer tolerance group blank in the customer master data, SAP uses the company code's default tolerance group (the entry with no name/group code defined in OBA3). If the payment difference exceeds the configured tolerance limits, SAP blocks automatic clearing and requires manual intervention (such as a write-off, partial payment, or contacting the customer).

</br></br>

## Tolerance Groups for Vendors

defines the permitted limits for payment and cash discount differences when clearing open items in accounts payable. It allows the system to automatically handle small discrepancies between invoice amounts and paid/received amounts.

</br>

#### Key Purposes

**• Automatic Write-Offs / Postings:** If a payment or invoice difference falls within the limits defined for the tolerance group, SAP automatically posts the difference to a designated expense or revenue (gain/loss) account during clearing.

**• Control & Compliance:** Prevents unauthorized or excessive write-offs and flags transactions that exceed the threshold for manual review.

**• Default Settings:** If you leave the tolerance group blank (empty) for a company code, SAP applies those default rules to all vendors where a specific group is not assigned.

</br>

#### Important SAP Transaction Codes (T-Codes)

**• Define Customer/Vendor Tolerance Groups: OBA3 (FI module)**

**• Configure Vendor-Specific Tolerances (MM-LIV / Invoice Verification): OMRX**

**• Assign Tolerance Group to Vendor Master Record:**
	• In SAP ERP / classic GUI: XK02 / MK02 (under Payment transactions view)
	• In SAP S/4HANA (Business Partner): Change BP role to vendor/supplier, go to Company Code data under Payment Transactions

</br>

#### Configuration Steps

1. **Define the Group:** Go to transaction code OBA3 (or via SPRO under Financial Accounting -> Accounts Receivable and Accounts Payable -> Business Transactions -> Outgoing Payments -> Manual Outgoing Payments -> Define Tolerance Groups for Customers/Vendors).

2. **Set Parameters:** Specify the company code, maximum permitted payment differences (in absolute amounts and/or percentages) for revenue and expense, and rules for residual items.

3. **Assign to Vendor:** Open the vendor master record (XK02 or S/4HANA Business Partner app) for your company code and input the tolerance group key.



</br></br>

## Resetting Cleared items 

To reset and reverse a cleared item in SAP, use transaction code FBRA (SAP GUI) or the Reset Cleared Items app (F2223 in SAP Fiori).


#### Key Differences: Reset vs. Reset and Reverse

**• Reset Only:** Breaks the link between an open item (like an invoice) and a clearing document (like a payment), returning the original line item status to "open" without posting a reversal.

**• Reset and Reverse:** Resets the cleared item back to an open state and automatically posts a reversal document for the clearing/payment document.


</br></br>


> [!NOTE]
> test sample 

</br></br>

</br>


</br></br>

<p align="center"> <a href="https://github.com/Octavius-Dante/SAP-FICO-2026/tree/main"> FICO-2026 Main page </a> </p>

