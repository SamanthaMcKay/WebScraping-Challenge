# WebScraping-Challenge
------------
## Project Description

### Goal
Learn how to use BeautifulSoup and Splinter for webscaping and data analysis. 

------------
## Credits
I used ChatGPT when I got stuck. The data used was from The Mars News websiteLinks to an external site. is operated by edX Boot Camps LLC for educational purposes only. The news article titles, summaries, dates, and images were scraped from NASA's Mars NewsLinks to an external site. website in November 2022. Images are used according to the JPL Image Use PolicyLinks to an external site., courtesy NASA/JPL-Caltech.

------------
## Softwares Used
### Libraries
Splinter
BeautifulSoup
MatPlotLib
Pandas
Pathlib

### Language
Python

### Software
VSCode
GitLens

------------
## Code Explanation with Figures/Visualizations
## Part 1: Mars News
- Used the chromedriver with Splinter's browser to open up a browser and visit the url specified in the assignment.
- Inspected the html to determine how to access the information needed for the assignment.
- Created a BeautifulSoup object and parsed the html with html.parser.
- Extracted all of the elements from the class "image_and_description_container" because that was where the titles and snippets of the news articles were. Saved this information to a variable.
- Using the previous variable, saved another variable to found all of the elements with the class "list_text" from the "image_and_description_container" and saved them without <div>s.
- Using a for loop and an empty list, went through each row, found the content_title, saved the text of the content title into a variable, found the article teaser, saved the text of the artivle teaser to a variable, and created a dictionary with the key value pairs of 'title': the article title, and 'preview': the article snippet. The dictionary entries for the current row were then appended to the previously empty list.
- Quit the browser.

## Part 2: Mars Data 
- Used the chromedriver with Splinter's browser to open up a browser and visit the url specified in the assignment.
- Inspected the html to determine how to access the information needed for the assignment.
- Created a BeautifulSoup object and parsed the html with html.parser.

### HTML Portion
- Found the table that contained all the relevant data and saved the table to a variable.
- Created a variable to store all of the rows with the tag <tr>.
- Initialized empty lists for the mars data and the titles of the columns for the future dataframe.
- Initialized a skip variable because the first row contains the headers and needs to be skipped when collecting the mars data.
- Used a for loop to find all rows with the tag <th> and used another for loop, with an if statement, to append the titles for the columns to the empty list and skip the title for loop if no data was present with the tag <th> in that row.
- Used to skip variable to skip the first line.
- Within the first for loop, found all rows with the tag <td>, and started another list so I could compile a list within a list to make dictionary creation easier.
- Used another for loop to check if the row had data, and if it did have data, appended the text of the row to the newest list or else continue.
- Once the previous loop was concluded, the newest list was appended to another list called mars_data.

### Pandas DataFrame
- Used the mars_data list within a list and the mars_title list to create a Pandas Dataframe.
- Adjusted the datatypes of each column to match the values that they contained.
- Answered the following questions:
### 1. How many months are there on Mars? There are 12 months on Mars.
### 2. How many Martian days' worth of data are there? There are 1867 Martian days worth of data.
### 3. What is the average low temperature by month on Mars and what month has the highest and which month has the lowest average temperature? see the chart below for monthly averages. The month with the lowest average temperature is month 3 and the month with the highest average temperature was month 8, based on the minimum temperature data in the dataset.

![image](https://github.com/SamanthaMcKay/WebScraping-Challenge/assets/132176159/9655edfb-26b6-4f31-a10d-4ca794ff725b)

### 4. What is the average atmospheric pressure by month on Mars? Which month had the highest average atmospheric pressure and which month had the lowest average atmospheric pressure? See the chart below for monthly average. The month with the highest average pressure was Month 9 and the lowest average pressure was Month 6.

![image](https://github.com/SamanthaMcKay/WebScraping-Challenge/assets/132176159/2d0e2519-fa3e-4d94-8870-95855b0aa1bf)

### 5. How many terrestrial (earth) days are there in a Martian year? There are approximately 687 Earth days in a Martian year. 
This was calculated based off of when the solar longitude(ls) is the same after non-consecutive days. I filtered the data for when the ls was zero and calculated based on the number of Earth days that passed before the ls went back to the same value. 


## Conclusion
I learned much about BeautifulSoup and Splinter. I was previously unaware of the idxmax() and idxmin() functions but found them very useful. I searched how many months is a year on Mars and got a result of 24 months, which conflicts with the information in the dataset. I think that it could have been more accurate to include other temperature metrics that were available elsewhere in the database. The minimum temperature recorded is not always the most accurate representation of the overall temperature on a planet at a specific location as atmospheric considerations, such as the nature of the ozone of a planet, can greatly affect how drastically a temperature changes during a planet's day. I would like to explore the relationship between the temperature of the planet and the atmospheric pressure to see what correlation exists. 
