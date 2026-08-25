# SAP Fico 2026 - Training data

- This SAP training in Github is a compilation of materials from internet and books and other best practices followed in blogs all these materials are referred for learning SAP FICO in 2026 pooled in one place for reference 

- This training material is an extended reading blog with a broken down sequence of Configuring and using essential T-Code for day today business activities 

- Any SAP GUI based transaction may not be looking correct in FIORI based app but it will have all the essential contents if some section are tabs are missing then it could be restricted by configuration setup in Fiori app

- Major crux of this blog, some of the transaction and activities which are not part of any training material or internet blogs or any SAP press books are explained by experienced subject matter experts from industry, discussed with them and included here wil be labelled (*SME)

- Solution and guides included from blogs will be labelled as (*BLOG)
- Solution and guides from UDemy training videos will be labelled as (*UDEMY)
- SAP Press Book based solutions will be labelled ad (*SAPPRESS)

</br>

## Categories of FICO 

- Financial Accounting (FI - Finance)
- Management Accounting (CO - Controlling)
- Asset Accounting (FI-AA) sub module of FI
- Funds management (Focuses specifically on budgetary accounting) (PSM-FM)

</br>

Funds management : It belongs to SAP PSM (Public Sector Management), which works alongside FI and CO in the broader SAP financial ecosystem

</br>

## Section Definitions

configuration is the first major phase when setting up SAP Financial Accounting (FI) before you can create master data or post daily transactions.First Steps in SAP FI ConfigurationConfiguration begins in the SAP Customizing Implementation Guide (SPRO). It builds the structural and rule-based foundation of the system.

- Enterprise Structure: Define organizational units like companies, company codes, and business areas, and link them together.

- Global Settings: Set up core rules such as fiscal year variants, posting periods, currencies, and field status variants.

- General Ledger (G/L) Setup: Establish the chart of accounts, account groups, and document number ranges.

- Submodule Configuration: Configure specific rules for Accounts Payable (AP), Accounts Receivable (AR), and Asset Accounting (AA).

</br>

## Core Sub-Modules 

- General Ledger Accounting (FI-GL): The central repository that records all financial transactions and generates statutory financial statements like the Balance Sheet and Profit & Loss statement.

- Accounts Payable (FI-AP): Manages all vendor transactions, including invoice processing, credit memos, employee expense vendor records, and automatic payment programs.

- Accounts Receivable (FI-AR): Tracks all customer data, incoming payments, dunning (collection) procedures, and credit management limits.

- Asset Accounting (FI-AA): Controls the lifecycle of fixed assets, including acquisitions, retirements, transfers, and automated depreciation runs.

- Bank Accounting (FI-BL): Handles cash management, house bank configurations, bank statements, and electronic payment processing.

</br>

## SAP Implementation Document types and purposes (*UDEMY)

- Business Blue print can be broken down into multiple documents when Standard SAP process is fit with business process of the company then PDT, COE, CSD is prepared when business process cases are UNfit for SAP standard process this GAP is addressed by customization 
 
  **Standard Process :**

    - PDD (Process definition document) developed by business team for business understanding or by consultants
    - COE (Configuration Object element) if SAP standard process is applicable at global level 
    - CSD (Configuration Specification Document) if SAP standard process is applicable at regional or local level
 
  **Customized Process :**

    - FS (Functional Specification) prepared by Functional consultant to address a business process gap it is a Custom development blue print
    - TS (Technical Specification) prepared by Technical consultant to give briefing about how this business gap was addressed with what technical objects and how it is functioning. 

</br>

## SAP Post-Implementation types of testing (*UDEMY)

 - Unit Testing (UT) - UTP (Unit Testing plan )
 - Integration Testing (ITC) 
 - Development Testing (DT)
 - User Acceptance Testing (UAT) 
 - Regression Testing (RT) 
 - Retrofit Testing (RTT)

</br>

SCC4 - SAP Client creation T-code
SCC1 - Cross Client transport import

## Table of contents 

- [Basic Settings](https://github.com/Octavius-Dante/SAP-FICO-2026/tree/main/01_BASIC_SETTINGS)
- 



</br></br></br></br>

# <p align="center"> END OF THE OVERVIEW PAGE </P>

</br></br></br>
