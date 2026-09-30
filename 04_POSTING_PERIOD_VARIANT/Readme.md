# 04 - Posting Period Variant

</br>

- Materials management view on company codes
- **Posting authorizations**
- Definition and Assignment of Tolerance Groups to users/ Employees
- **Customizing for Line items Layout and Screen Variant for Line Item display and Reporting**

</br></br>

## Posting period variant ?

A posting period variant in SAP is a control tool that opens and closes accounting periods so users only post financial transactions in the correct time frame. It stops accidental entries into closed months or past years.

</br>

#### How It Works

- **Reusable Code:** You create a 4-character code (like 1000) and assign it to one or more company codes

- **Account Types:** SAP uses specific letters to control posting access:

        • +: All account types (must be open first)
        • A: Assets
        • D: Customers
        • K: Vendors/Suppliers
        • M: Materials
        • S: General Ledger

- **Period Ranges:** It sets a starting period/year and an ending period/year for regular operations (periods 1–12) and special year-end adjustment periods (13–16).

</br>

#### Key Transactions and Apps

• OBBO: Transaction code to define a new posting period variant.

• OB52: Transaction code to open and close posting periods for the variant.

• Manage Posting Periods: The SAP Fiori app used in modern SAP S/4HANA systems to handle period statuses.

</br>

## Material Master Period Management

 controls inventory posting periods to ensure that stock movements and valuations are recorded in the correct financial timeframe

</br>

#### Key Transaction Codes

• MMPV: Closes the current Materials Management (MM) posting period and opens the next one sequentially. You cannot skip periods.

• MMRV: Displays the current open MM period and allows or disallows back-postings (postings to the previous period).

• OB52: Manages financial (FI) posting periods, which must align with MM period controls, specifically for account type M (materials).

</br>

#### Core Operations

• **Closing and Opening Periods (MMPV):** Run monthly to advance the material ledger control record. Enter your company code along with the target period and year.

• **Allowing Previous Period Postings (MMRV):** Check the "Allow posting to previous period" box if goods movements must be posted to the prior month.

• **Background Scheduling:** High-volume enterprises often schedule MMPV via background jobs (using program RMMPERI via SM37) to automate period rollover at month-end


</br></br>


> [!NOTE]
> test sample 

</br></br>

</br>


</br></br>

<p align="center"> <a href="https://github.com/Octavius-Dante/SAP-FICO-2026/tree/main"> FICO-2026 Main page </a> </p>

