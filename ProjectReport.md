# E-Commerce Fraud Analysis Using R
## Introduction
In this project, I chose to analyze e-commerce fraud data, sourced from Kaggle. The data
was synthetically generated using Python. The world has a heavy reliance on e-commerce, and as
such it is important to recognize the leading factors that contribute to fraud. There are many factors
at play when making an online transaction, such as where you are buying from, the device you are
using, and the payment method, among many other things.
This dataset contains the following columns: Transaction ID, Customer ID, Transaction
Amount, Transaction Date, Payment Method, Product Category, Quantity, Customer Age, Customer
Location, Device Used, IP Address, Shipping Address, Billing Address, Is Fraudulent, Account Age
Days, and Transaction Hour. The dataset has 1,472,952 rows. As such, I had to trim the data to
make it easier to process. One main issue I ran into during this process was running out of memory
on my computer to process.
Once the data was trimmed, I was left with ID, Transaction Amount, Transaction Date,
Payment Method, Product Category, Quantity, Customer Location, Customer Age, Device Used, Is
Fraudulent, Account Age Days, and Transaction Hour. This trim also allowed me to focus
specifically on these factors for my analysis.
## Questions of Interest
I approached this project with several questions of interest. The driving question I asked is
“what factors lead to fraudulent transactions?” Additionally, I created questions related to specific
aspects of the data. Are young people more likely to be scammed than older people? IS there a
certain type of item that is frequently fraudulently sold? Are certain payment methods more fraud
resistant? Does price matter, or are larger purchases fraudulent as frequently as larger purchases?
## Analysis
For my analysis, I relied on four libraries: tidyverse, ggplot2, patchwork, and plotly.
Following the cleaning of the data, I started my analysis. First, I plotted transaction amounts over
time to determine what day had the highest valued transactions. As seen in figure 1, transaction
amounts peak in late January. This is a nice entry point into the analysis. We can select transactions
from this specific data range to determine what day this was.
I plotted the transactions from January 1, 2024 to Jan 31, 2024, seen in figure 2. According to this
graph, the day with the highest valued transactions was January 26, 2024. Let’s look at two factors
on this day.
First, we will investigate product categories. There are five categories in this dataset: clothing,
electronics, health & beauty, home & garden, and toys & games. Figure 3 plots the proportion offraudulent transactions for these five categories. As seen in figure 3, health & beauty had the
highest level of fraud on January 26th. I had initially thought that something like clothing or
electronics would be higher, given the number of fakes that exist of these products.
We can now turn to the payment methods used on January 26th. This may unearth a trend.
On January 26th, the most frauded transactions were completed using debit cards, seen in figure 4.
This is in line with my expectations, as debit cards are typically less secure than other forms of
payment, like PayPal, as they are done on-site and don’t always have strict verification methods in
place if transactions are not made through a trusted vendor.
To continue, we can count the number of health & beauty transactions that were made with
debit cards. My R script counted 826 transactions. We can now calculate the percentage of these
that were fraudulent. 4.12% of these specific transactions were fraudulent. This doesn’t seem like a
lot, but in the grand scheme of things it is quite large in terms of the number of people getting
frauded. 34 people were victims of fraud in this case.
Since we have determined a trend, we can now determine if it continues throughout the
year, not just on the day with the highest number of transactions. To do this, we can use a similar
script to perform the same operations on the entire dataset. Over the course of the data range,
there were 73,475 health & beauty transactions made with debit cards. Of those transactions, 3679
were fraudulent, equaling 5.01 %. This is inline with the data from January 26th. I don’t want to
conclude that a factor leading to fraud is purchasing health & beauty products, so let’s just focus on
debit card purchases.
Based on figure 4, we already know that debit cards are the most frequently frauded
payment methods. We can perform similar operations to draw more conclusions. Using another R
script, we can calculate that 5.02 of all purchases made with debit cards were fraudulent. Of the
368,429 debit card purchases recorded, 18,313 were fraudulent, equaling 4.97%. Again, a small
percentage but on a dataset this large that has a massive impact.
Thus, it can be concluded that credit cards have the largest rate of fraud across the entire
data range. We can now look at some other factors and interesting aspects of this data, such as the
most common ages that experience fraud.
By filtering the cleaned data to select only Customer_Age and Is_Fraudulent, we can plot
these values. Figure 5 is the resultant graph. I was very surprised by this. The data created a bell
curve. This was the opposite of what I expected. I had assumed that older people (>50 years) and
younger people (<20 years) would have experienced fraud at a higher level than those residing in the
middle. This could be due to the data being synthetic, however we can roll with it for further
investigation.
Let’s combine this age data and the credit card data to see if we can extract another trend. I
selected all transactions that were made by people from age 25 to age 45. My R script calculated
that 3.54% of debit card transactions made by people in that age range were fraudulent. The
percentage of debit card fraud is relatively standard across the board.
## Conclusion
This analysis of e-commerce fraud data aimed to identify factors that contribute to
fraudulent transactions. By analyzing the data using R, several trends were revealed. My analysis
showed that health and beauty transactions made with debit cards were particularly fraud-prone,
with 4.12 percent of such transactions made on January 26, 2024 (the date with the highest volume
of transactions) being fraudulent. This trend carried through the entire dataset, with 5.01 percent of
all health and beauty transactions made with debit cards being fraudulent. Through additional
analysis, it was revealed that debit cards were the most frequently targeted payment methods
across the board, with 5.02 percent of all debit card transactions being fraudulent. Although these
percentages are small, the dataset is very large with 1,472,952 unique transactions making these
percentages have a large impact. Contrary to my expectations, the analysis of age vs fraud
percentage revealed a bell curve, showing that individuals aged 25-45 experienced higher levels of
fraud than both younger and older people. While certain factors such as payment method and
product category contributed to fraud percentages, this analysis also opened my eyes to how
complex fraud prediction is.
