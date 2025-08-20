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
      I save the API data in two main tables: one for filings and one for holdings. These tables can be joined using filing_id:
  
      ```
      | Filings table            |
      |--------------------------|
      | filing_id (PRIMARY KEY)  |
      | cik                      |
      | filer_name               |
      | period_of_report (date)  |

      ```
       ```
      | Holdings table    |
      |------------------ |
      | filing_id         |
      | name_of_issuer    |
      | cusip             |
      | cik               |
      | title_of_class    |
      | value             |
      | shares            |
      | put_call          |
      ```

 📏How to get the institutional investors data? 

 One straightforward way is to write Python code to retrieve the data (in JSON format) and then save it in a CSV file. The problem is that the volume of this data can be very large and consume a lot of RAM when used later in other scripts. To handle this, I use a PostgreSQL database to retrieve and store the data. This also allows me to leverage SQL tools to work with it more efficiently.  ◼

 📏What do I do in this repo to get this data? 
 
As mentioned earlier, I use Python, PostgreSQL, and the EDGAR API to retrieve and store the data in an efficient and reusable way.
In general, I follow two steps:

▨Set up and implement a PostgreSQL server.

▨Use Python to retrieve the data from the API and save it into the database.
The picture below shows a schematic of the overall process:

![Process Diagram](images/General_View.png)

 
      
     
      
      
