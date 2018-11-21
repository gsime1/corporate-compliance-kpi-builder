# Transparency International Italia 
## Transparency in Corporate Reporting (Italy) Index
### Background 

Transparency International (TI) is one of the pioneers in the fight for a more transparent corporate reporting. Being the leader of anti-corruption standards in the world, the Business Inegrity team of TI created what are now known in the compliance industry the [Business Principles for Countering Bribery (BPCB)](https://www.transparency.org/whatwedo/publication/business_principles_for_countering_bribery) and its [Commentary](https://www.transparency.org/files/content/publication/2015_BusinessPrinciplesCommentary_EN.pdf) which act as a go to resource for multinationals designing their anti-corruption programmes. 

Based on the best practices laid down in the BPCP, the Business Integrity team developed a questionnaire to assess the level of adherence of multinationals to the BPCB, giving birth to the [Transparency in Corporate Reporting (TRAC)](https://www.transparency.org/files/content/feature/2016_TRACEMM_Index.png), a study which has already been conducted several times in [2009](https://www.transparency.org/whatwedo/publication/transparency_in_reporting_on_anti_corruption_a_report_on_corporate_practice), [2011](https://www.transparency.org/whatwedo/publication/promoting_revenue_transparency_2011_report_on_oil_and_gas_companies), [2012](https://www.transparency.org/news/feature/shining-a-light-on-the-worlds-biggest-companies), [2013](https://www.transparency.org/news/feature/emerging_market_multinational_companies_ready_for_prime_time), [2014](https://www.transparency.org/news/feature/global_companies_global_transparency), [2015](https://www.transparency.org/whatwedo/publication/transparency_in_corporate_reporting_assessing_the_worlds_largest_telecommun), and [2016](https://www.transparency.org/news/feature/emerging_markets_pathetic_transparency). 

This year, the Italian branch of TI carried out the second iteration of its TRAC, assessing the transparency and strength of anti-corruption programmes of 50 Italian Multinationals, whose final report can be downloaded here across 61 questions, divided in 10 sections:
1. Public Committment against Corruption (5 questions)
2. Anti-Corruption Programme (9 questions)
3. Code of Conduct (10 questions)
4. Whistleblowing (10 questions)
5. Lobbying (6 questions)
6. Conflict of Interests (6 questions)
7. Political Contribution (4 questions)
8. Organisational Transparency (5 questions)
9. Anti-corruption training (8 questions)
10. Sustainble Projects Transparency (4 questions)

## The Data 
### Data collection

The data was collected in a Google Spreadsheet. Every row represented one company which was assessed across 61 questions, divided in the aforementioned 10 sections. In order to assess the questions, it was necessary to look for the information in several document types, such as:
* Annual Reports, 
* Sustainbility Reports, 
* 231 Model, 
* Anti Corruption Programme Documents, 
* Code of Ethics, 

To speed up the search, we used the google search engine capabilities, which allows to search file types and key words in the same domain: 
* `in: URL filetype:pdf keyword` would search for keywork in all PDF files in the URL domain. 
* `in: URL keyword`would search for keyword in the whole URL domain. 

In the methodology of Transparency International Italia, the TRAC Index is the average of the results of the 10 sections a company has been assessed on. Each section has a different number of questions (see list above) and the section result is the weighted average of the questions scores obtained. 

### Database structure

We created a Google spreadsheet of 51x244. Each one of the 61 questions could be graded in one of the three following scales:
* 0-1,
* 0-1-2,
* 0-1-2-3. 

For every question, we created 5 columns 
* Score: integer type. 
* Source: string type indicating the type of document the information was found in (Annual Report etc.)
* URL: string type indicating the URL of the Source. 
* Comment: string type explaining why the company had obtained the given score. 
* Space: Empty column to allow for grouping and minimizing columns. 

The way the column names were given in the Google Spreadsheet is this:
`ColumnName_SectionNumber_QuestionNumber` example: Score_1_3 would be the Score of the 3rd question of Section 1. 

### Data Extraction, Transformation and Loading (ETL) Pipeline. 

The objective of this pipeline is to:
1) Extract the raw data from the Google Spreadsheet and create a raw data and a scores only dataframes. 
2) Use the scores only dataframe to calculate the results of every section, and create a sections results dataframe. 
3) Use the sections results dataframe to group the companies by sector, recalculate the sections results by group, and 
   store these results in a sectors dataframe. 
4) Use the raw data from the Google Spreadsheet to create a .docx for every one of the companies, collating together all 
   information in the raw data in a document, creating a company profile. 
5) Create 3 spidercharts for every company, one plotting the sections results of the company only, one plotting the sections    
   results of the company with the averages results of sections in the sector of the company, and one plotting the company 
   sections results with the averages results of the sections of all companies in the sample. 
6) Create a folder strucutre where to store the dataframes as .csv and the company profiles as .docx and the visulations as  
   .png. 
   
### Deliverables
File structure created on the computer. 

## Set-up 

### Working with the Google API
Activate Google API
Get a client.json 
Get a key.json 

### Software set-up
Windows 
Unix

## Reusability 
### How to change data
### How to add data
### How to replicate the study with new data
