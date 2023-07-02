Question 1: Use yfinance to Extract Stock Data
Using the Ticker function enter the ticker symbol of the stock we want to extract data on to create a ticker object. The stock is Tesla and its ticker symbol is TSLA.

# Create a ticker object for Tesla
ticker = yf.Ticker("TSLA")
# Create a ticker object for Tesla
ticker = yf.Ticker("TSLA")
Using the ticker object and the function history extract stock information and save it in a dataframe named tesla_data. Set the period parameter to max so we get information for the maximum amount of time.

# Extract stock information for the maximum amount of time
tesla_data = ticker.history(period="max")
# Extract stock information for the maximum amount of time
tesla_data = ticker.history(period="max")
Reset the index using the reset_index(inplace=True) function on the tesla_data DataFrame and display the first five rows of the tesla_data dataframe using the head function. Take a screenshot of the results and code from the beginning of Question 1 to the results below.

# Reset the index of the DataFrame
tesla_data.reset_index(inplace=True)

# Display the first five rows of the DataFrame
tesla_data.head()
# Reset the index of the DataFrame
tesla_data.reset_index(inplace=True)
​
# Display the first five rows of the DataFrame
tesla_data.head()
​
index	Date	Open	High	Low	Close	Volume	Dividends	Stock Splits
0	0	2010-06-29	1.266667	1.666667	1.169333	1.592667	281494500	0	0.0
1	1	2010-06-30	1.719333	2.028000	1.553333	1.588667	257806500	0	0.0
2	2	2010-07-01	1.666667	1.728000	1.351333	1.464000	123282000	0	0.0
3	3	2010-07-02	1.533333	1.540000	1.247333	1.280000	77097000	0	0.0
4	4	2010-07-06	1.333333	1.333333	1.055333	1.074000	103003500	0	0.0

Question 2: Use Webscraping to Extract Tesla Revenue Data
Use the requests library to download the webpage https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-PY0220EN-SkillsNetwork/labs/project/revenue.htm Save the text of the response as a variable named html_data.

response = requests.get(url)
html_data = response.text
import requests
​
# Download the webpage and save the response as html_data
url = "https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-PY0220EN-SkillsNetwork/labs/project/revenue.htm"
response = requests.get(url)
html_data = response.text
Parse the html data using beautiful_soup.

from bs4 import BeautifulSoup

# Assuming you have already saved the HTML data in the variable html_data
soup = BeautifulSoup(html_data, 'html.parser')
from bs4 import BeautifulSoup
​
# Assuming you have already saved the HTML data in the variable html_data
soup = BeautifulSoup(html_data, 'html.parser')
​
Using BeautifulSoup or the read_html function extract the table with Tesla Quarterly Revenue and store it into a dataframe named tesla_revenue. The dataframe should have columns Date and Revenue.

Click here if you need help locating the table
    
Below is the code to isolate the table, you will now need to loop through the rows and columns like in the previous lab
    
soup.find_all("tbody")[1]
    
If you want to use the read_html function the table is located at index 1

# Find the table with Tesla Quarterly Revenue
table = soup.find_all('table')[1]

# Use the read_html function to extract the table into a DataFrame
tesla_revenue = pd.read_html(str(table))[0]

# Set the column names
tesla_revenue.columns = ['Date', 'Revenue']
​
# Find the table with Tesla Quarterly Revenue
table = soup.find_all('table')[1]
​
# Use the read_html function to extract the table into a DataFrame
tesla_revenue = pd.read_html(str(table))[0]
​
# Set the column names
tesla_revenue.columns = ['Date', 'Revenue']
​
Execute the following line to remove the comma and dollar sign from the Revenue column.

tesla_revenue['Revenue'] = tesla_revenue['Revenue'].replace({',': '', '\$': ''}, regex=True)
Display the last 5 row of the tesla_revenue dataframe using the tail function. Take a screenshot of the results.

tesla_revenue.tail(5)
tesla_revenue.tail(5)
Date	Revenue
49	2010-06-30	28
50	2010-03-31	21
51	2009-12-31	NaN
52	2009-09-30	46
53	2009-06-30	27

Question 3: Use yfinance to Extract Stock Data
Using the Ticker function enter the ticker symbol of the stock we want to extract data on to create a ticker object. The stock is GameStop and its ticker symbol is GME.

# Create a ticker object for Tesla
ticker = yf.Ticker("GME")
​
Using the ticker object and the function history extract stock information and save it in a dataframe named gme_data. Set the period parameter to max so we get information for the maximum amount of time.

gme_data = ticker.history(period="max")

# Extract stock information for the maximum amount of time
gme_data = ticker.history(period="max")
​
Reset the index using the reset_index(inplace=True) function on the gme_data DataFrame and display the first five rows of the gme_data dataframe using the head function. Take a screenshot of the results and code from the beginning of Question 3 to the results below.

# Reset the index of the DataFrame
gme_data.reset_index(inplace=True)

# Display the first five rows of the DataFrame
gme_data.head()
# Reset the index of the DataFrame
gme_data.reset_index(inplace=True)
​
# Display the first five rows of the DataFrame
gme_data.head()
Date	Open	High	Low	Close	Volume	Dividends	Stock Splits
0	2002-02-13	1.620128	1.693350	1.603296	1.691666	76216000	0.0	0.0
1	2002-02-14	1.712707	1.716074	1.670626	1.683250	11021600	0.0	0.0
2	2002-02-15	1.683250	1.687458	1.658002	1.674834	8389600	0.0	0.0
3	2002-02-19	1.666418	1.666418	1.578047	1.607504	7410400	0.0	0.0
4	2002-02-20	1.615920	1.662210	1.603296	1.662210	6892800	0.0	0.0

Question 4: Use Webscraping to Extract GME Revenue Data
Use the requests library to download the webpage https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-PY0220EN-SkillsNetwork/labs/project/stock.html. Save the text of the response as a variable named html_data.

import requests
​
# Download the webpage and save the response as html_data
url = "https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-PY0220EN-SkillsNetwork/labs/project/revenue.htm"
response = requests.get(url)
html_data = response.text
​
Parse the html data using beautiful_soup.

from bs4 import BeautifulSoup
​
# Assuming you have already saved the HTML data in the variable html_data
soup = BeautifulSoup(html_data, 'html.parser')
Using BeautifulSoup or the read_html function extract the table with GameStop Quarterly Revenue and store it into a dataframe named gme_revenue. The dataframe should have columns Date and Revenue. Make sure the comma and dollar sign is removed from the Revenue column using a method similar to what you did in Question 2.

Click here if you need help locating the table
    
Below is the code to isolate the table, you will now need to loop through the rows and columns like in the previous lab
    
soup.find_all("tbody")[1]
    
If you want to use the read_html function the table is located at index 1

# Find the table with Tesla Quarterly Revenue
table = soup.find_all('table')[1]
​
# Use the read_html function to extract the table into a DataFrame
gme_revenue = pd.read_html(str(table))[0]
​
# Set the column names
gme_revenue.columns = ['Date', 'Revenue']
Using BeautifulSoup or the read_html function extract the table with GameStop Quarterly Revenue and store it into a dataframe named gme_revenue. The dataframe should have columns Date and Revenue. Make sure the comma and dollar sign is removed from the Revenue column using a method similar to what you did in Question 2.

Display the last five rows of the gme_revenue dataframe using the tail function. Take a screenshot of the results.

gme_revenue.tail(5)
Date	Revenue
49	2010-06-30	$28
50	2010-03-31	$21
51	2009-12-31	NaN
52	2009-09-30	$46
53	2009-06-30	$27

Question 5: Plot Tesla Stock Graph
Use the make_graph function to graph the Tesla Stock Data, also provide a title for the graph. The structure to call the make_graph function is make_graph(tesla_data, tesla_revenue, 'Tesla'). Note the graph will only show data upto June 2021.

tesla_data.plot(x="Date", y="Open")
tesla_data = tesla.history(period="1mo")
tesla_data.head()
tesla_data.reset_index(inplace=True)
tesla_data.plot(x="Date", y="Open")
<AxesSubplot:xlabel='Date'>

Question 6: Plot GameStop Stock Graph
Use the make_graph function to graph the GameStop Stock Data, also provide a title for the graph. The structure to call the make_graph function is make_graph(gme_data, gme_revenue, 'GameStop'). Note the graph will only show data upto June 2021.

gme_data = ticker.history(period="max")
gme_data.head()
gme_data.reset_index(inplace=True)
gme_data.plot(x="Date", y="Open")
<AxesSubplot:xlabel='Date'>
