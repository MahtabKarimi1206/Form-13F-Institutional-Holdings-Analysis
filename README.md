# Form-13F-Institutional-Holdings-Analysis

In this repo, I extract data from 13F filings using the EDGAR API and save them into a PostgreSQL database managed with pgAdmin.

📏Who are institutional investors?

Institutional investors are large entities that invest significant amounts of money on behalf of their clients. 
Examples include hedge funds and pension funds. ◼

📏What is form 13F filing? 

 Since 1978, institutional investment managers—including hedge funds—that exercise investment discretion over accounts with at least $100 million must file Form 13F with the SEC each quarter, within 45 days of quarter-end, as required by Section 13(f) of the Exchange Act. ◼

📏Where to get institutional investor data?

EDGAR provides an API to access these filings, which include data on filing companies and their holdings. The filing company is the institutional investor, and the holdings are the companies whose stocks they own.

▷What is the structure of the data? 
      I save the API data in two main tables: one for filings and one for holdings. These tables can be joined using filing_id.
      The filings table includes: 

      
      ```
      | Filings table         | Holdings table    |
      |-----------------------|------------------|
      | filing_id (PRIMARY KEY) | filing_id       |
      | cik                   | name_of_issuer   |
      | filer_name            | cusip            |
      | period_of_report (date) | cik             |
      |                       | title_of_class   |
      |                       | value            |
      |                       | shares           |
      |                       | put_call         |
      ```
