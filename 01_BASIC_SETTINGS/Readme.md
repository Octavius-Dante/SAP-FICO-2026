# 01 - Basic Settings (Configuration)

</br>

- Configuring the Enterprise - Organizational units / Enterprise Structure
- Variant Principle 
- Fiscal Year (With Shortened Fiscal Year)
- Posting Periods Variant (Open and Close Posting Periods)
- Currencies

</br>

## Definitions   

### What is Company code in SAP ?

Company Code (for external purposes) A company code represents an independent balancing/legal accounting entity. An example would be a company with independent accounts within a corporate group. Financial statements required by law can be created at company code level. Therefore, a company code is the minimum structure necessary in SAP ERP Financial. In an international business, operations are often scattered across numerous countries. Since most government and tax authorities require the registration of a legal entity for every company, a separate company code is usually created per country.

</br>

company code is tied to a specific country, currency, and local commercial/tax law.

SPRO > Enterprise Structure > Definition > Financial Accounting > Define Company

- Transaction : OX02 - Creating Company Code 
- Transaction : EC01 - Used to copy an existing company code in SAP to create a new company code 

</br>

### What is Business Area in SAP ?

Organizational Units also known as Business Area used (for internal purposes) Business areas represent separate areas of operation within an organization and can be used across company codes. They are balancing entities that can create their own set of financial statements for internal purposes. It is therefore possible to save and evaluate transaction figures for each business area. The use of business areas is optional.

</br>

Business area is part of finance but it is not assigned to a company code (client level) it is independent 

SPRO > Enterprise Structure > Definition > Financial Accounting > Define Business Area
SPRO > Enterprise Structure > Definition > Financial Accounting > Consolidated Business Area 

- Transaction : OX03 - Create Business area 
- Transaction : OCC1 - Consolidated Business areas

</br>

After Defining Business Area it needs to be activated in SPRO

SPRO > Financial Accounting > Financial Accounting Global Settings > Business Area > Enable Business Area Balance Sheet

- Transaction : OB65 - Business Area Financial statements

</br>

When we Copy the business Area Global parameters are also copied

SPRO > Financial Accounting Global Settings (New)> Global Parameters for Company Code> Enter Global Parameters

- Transaction : OBY6 - Company Code global data overview to view the components of the company code in detail

</br>

### What is Functional Area in SAP ?

SAP is an account assignment characteristic that classifies operating expenses by their specific business function, such as production, Administration, Sales and Distribution, Marketing, and Research and Development (R&D).

Functional Area is tightly involved with controlling.

</br>

### What is Variant Principle ?

The variant principle in SAP Financial Accounting (FI) is a three-step method used to assign common configuration properties to one or more company codes or business objects without repeating the setup for each one

</br>

Common Applications in SAP FI

- Fiscal Year Variants (FYV): Defines how a company's financial year is structured, including the number of normal posting periods (e.g., 12) and special adjustment periods (up to 4). 

There are 2 types of fiscal year variant 

    - a calendar year (Jan–Dec) 
    - a non-calendar year (e.g., April–March).

There is another category called **Special posting periods** which are 4 and it happens during year end closing it allows the user to post from past dates 
(example : user is in MARCH-2024 can post entries dated back to sep-2023, oct-2023) 

</br>

1 special posting period represents 3 normal posting period that means 
(it represents a Quarterly period)

1 = [1,2,3], 2 = [4,5,6], 3 = [7,8,9], 4 = [10,11,12]

Calendar fiscal year has 12 posting periods 
Non calendar fiscal year has 12 + 4 special posting period = total of 16 posting periods

Physical year which gets closed earlier than usual for certain businesses in those cases SAP has introduces something called **Shortened Fiscal year** 
which falls under **Year Dependent** 

- sap provided template for Calendar fiscal year - 'K4'
- sap provided template for Shortened fiscal year - 'AA'
- sap provided template for NON-Calendar fiscal year - 

</br>

- Posting Period Variants (PPV): Controls which accounting posting periods are open or closed for transaction data entry, categorized by account types (Assets, Customers, Vendors, etc.).


</br>

- Field Status Variants (FSV): Controls the display and behavior (optional, mandatory, or suppressed) of fields during document entry.

</br>

## Assignment  

after completing all the definition of config now all the defined objects required to be assigned for business usage

following Assignments can be defined

SPRO > Enterprise Structure > Assignments > 

- Assign company code to company
- Assign company code to credit control area
- Assign business area to consolidation business area
- Assign company code to financial management area
- Assign Profit Center to Company Code

</br></br>

<p align="center"> <a href="https://github.com/Octavius-Dante/SAP-FICO-2026/tree/main"> FICO-2026 Main page </a> </p>