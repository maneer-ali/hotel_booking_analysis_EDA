# hotel_booking_analysis_EDA

# Project Name - Hotel Booking Analysis EDA using Python
# Project Type - Hotel Booking Analysis EDA using Python

# Contribution - Individual

# Name - - Maneer Ali

# Project Summary

Almabetter Hotel Booking EDA Project Using Python || Hariom Hotel booking analysis with AlmaBetter EDA This project relates to hotel reservations and includes a variety of city hotels and resort hotels. There are 32 columns and a total of 119390 rows in this dataset. Data collection, data cleansing and manipulation, and EDA (experimental Data Analysis) are the three categories into which the workflow for data manipulation is divided. The names of some of the columns, including hotel, is_canceled, lead_time, arrival_date_year, arrival_date_month, arrival_date_week_number, arrival_date_day_of_month, and stays_in_weekend_nights, have been updated as the data collection process has progressed. This is done by coding Head(), Tail(), info(), describe(), columns(), and other methods used for data collection. As we proceed, we identify the distinct value for each column, create a list in tabular format, and also verify the dataset type for each column. Identify some columns with inaccurate data types and fix them afterward. As we discover duplicate items totaling 87396, which are later discarded from the dataset, duplicate data items must also be removed during the data cleaning phase.

We must first perform data manipulation before visualizing any data from the data source. To do that, we examined each column's null value. After checking, drop the column using the 'drop' method if we find one that has a greater percentage of null values. We are so removed from the "company" column. When there are only a few null values, we fill those null values with the necessary values using the formula.fill()

To achieve greater understanding and business goals, many charts are utilized for data visualization.

# GitHub Link -

# Problem Declaration

Have you ever thought the ideal season of the year to reserve a hotel room? Alternatively, how long should I remain to get the greatest daily rate? What if you wanted to foretell whether a hotel would unreasonably frequently receive unusual requests? You can investigate those questions using the data from hotel reservations! This data collection comprises reservation details for a city hotel and a resort hotel, as well as details like the date the reservation was made, the duration of the stay, the number of adults, kids, and/or babies, and the number of parking spaces that are available. The data is devoid of any information that may be used to identify a specific person. Investigate and evaluate the information to find crucial elements that control reservations.

# Business Assignment

Analyse the reservation data for the City Hotel and Resort Hotel to learn more about the various elements that influence a reservation. This is being done as a solo project.

# General Guidelines : -

Well-structured, formatted, and commented code is required.

Exception Handling, Production Grade Code & Deployment Ready Code will be a plus. Those students will be awarded some additional credits.

The additional credits will have advantages over other students during Star Student selection.

[ Note: - Deployment Ready Code is defined as, the whole .ipynb notebook should be executable in one go
          without a single error logged. ]
Each and every logic should have proper comments.

You may add as many number of charts you want. Make Sure for each and every chart the following format should be answered.

# Chart visualization code

* Why did you pick the specific chart?
* What is/are the insight(s) found from the chart?
* Will the gained insights help creating a positive business impact? Are there any insights that lead to negative growth? Justify with specific reason.
You have to create at least 20 logical & meaningful charts having important insights. [ Hints : - Do the Vizualization in a structured way while following "UBM" Rule.
U - Univariate Analysis,

B - Bivariate Analysis (Numerical - Categorical, Numerical - Numerical, Categorical - Categorical)

M - Multivariate Analysis ]

# 1. Know Your Data
Import Libraries


```
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
%matplotlib inline
from datetime import datetime
import seaborn as sns
import ast
```

```
from google.colab import drive
drive.mount('/content/drive')
```
Mounted at /content/drive

```
# Load Dataset
database = "/content/drive/MyDrive/Colab Notebooks/Module 1/Hotel Bookings.csv"
hotel_booking_df = pd.read_csv(database)
```
# First Dataset details
```
# Dataset First Look
hotel_booking_df
```

# Dataset Rows & Columns count
```
# Dataset Rows & Columns count
print(hotel_booking_df.index)
print('\n \n')
print(hotel_booking_df.columns)
```

RangeIndex(start=0, stop=119390, step=1)

 

Index(['hotel', 'is_canceled', 'lead_time', 'arrival_date_year',
       'arrival_date_month', 'arrival_date_week_number',
       'arrival_date_day_of_month', 'stays_in_weekend_nights',
       'stays_in_week_nights', 'adults', 'children', 'babies', 'meal',
       'country', 'market_segment', 'distribution_channel',
       'is_repeated_guest', 'previous_cancellations',
       'previous_bookings_not_canceled', 'reserved_room_type',
       'assigned_room_type', 'booking_changes', 'deposit_type', 'agent',
       'company', 'days_in_waiting_list', 'customer_type', 'adr',
       'required_car_parking_spaces', 'total_of_special_requests',
       'reservation_status', 'reservation_status_date'],
      dtype='object')
```
# Dataset Info
hotel_booking_df.info()
```

<class 'pandas.core.frame.DataFrame'>
RangeIndex: 119390 entries, 0 to 119389
Data columns (total 32 columns):
 #   Column                          Non-Null Count   Dtype  
---  ------                          --------------   -----  
 0   hotel                           119390 non-null  object 
 1   is_canceled                     119390 non-null  int64  
 2   lead_time                       119390 non-null  int64  
 3   arrival_date_year               119390 non-null  int64  
 4   arrival_date_month              119390 non-null  object 
 5   arrival_date_week_number        119390 non-null  int64  
 6   arrival_date_day_of_month       119390 non-null  int64  
 7   stays_in_weekend_nights         119390 non-null  int64  
 8   stays_in_week_nights            119390 non-null  int64  
 9   adults                          119390 non-null  int64  
 10  children                        119386 non-null  float64
 11  babies                          119390 non-null  int64  
 12  meal                            119390 non-null  object 
 13  country                         118902 non-null  object 
 14  market_segment                  119390 non-null  object 
 15  distribution_channel            119390 non-null  object 
 16  is_repeated_guest               119390 non-null  int64  
 17  previous_cancellations          119390 non-null  int64  
 18  previous_bookings_not_canceled  119390 non-null  int64  
 19  reserved_room_type              119390 non-null  object 
 20  assigned_room_type              119390 non-null  object 
 21  booking_changes                 119390 non-null  int64  
 22  deposit_type                    119390 non-null  object 
 23  agent                           103050 non-null  float64
 24  company                         6797 non-null    float64
 25  days_in_waiting_list            119390 non-null  int64  
 26  customer_type                   119390 non-null  object 
 27  adr                             119390 non-null  float64
 28  required_car_parking_spaces     119390 non-null  int64  
 29  total_of_special_requests       119390 non-null  int64  
 30  reservation_status              119390 non-null  object 
 31  reservation_status_date         119390 non-null  object 
dtypes: float64(4), int64(16), object(12)
memory usage: 29.1+ MB

```
# Dataset Duplicate Value Count, to remove these values, we use function drop.duplicate to delete duplicate rows.
hotel_booking_df.drop_duplicates(inplace = True)

# total rows = 119390, Duplicate Rows = 31994
uni_num_of_rows = hotel_booking_df.shape[0]

uni_num_of_rows # now unique rows = 87396
```

87396

```
hotel_booking_df.reset_index() #View unique data
```
# Missing Values/Null Values

```
# Missing Values/Null Values Count
null_value = hotel_booking_df.isnull() == True
hotel_booking_df.fillna(np.nan, inplace = True)

hotel_booking_df # we replace all the null value as NaN.
```

```
# Visualizing the missing values
miss_values =hotel_booking_df.isnull().sum().sort_values(ascending=False)
miss_values # We have check the count of null value in individual columns
```

company                           82137
agent                             12193
country                             452
children                              4
reserved_room_type                    0
assigned_room_type                    0
booking_changes                       0
deposit_type                          0
hotel                                 0
previous_cancellations                0
days_in_waiting_list                  0
customer_type                         0
adr                                   0
required_car_parking_spaces           0
total_of_special_requests             0
reservation_status                    0
previous_bookings_not_canceled        0
is_repeated_guest                     0
is_canceled                           0
distribution_channel                  0
market_segment                        0
meal                                  0
babies                                0
adults                                0
stays_in_week_nights                  0
stays_in_weekend_nights               0
arrival_date_day_of_month             0
arrival_date_week_number              0
arrival_date_month                    0
arrival_date_year                     0
lead_time                             0
reservation_status_date               0
dtype: int64

# What did you know about your dataset?
A single file in this data collection analyses different booking details between two hotels: a city hotel and a resort hotel. includes details like the date the reservation was made, the number of people staying, the number of adults, kids, and/or babies, and the number of parking spaces available, among other things. There are 32 columns and 119390 rows in the entire dataset. Dataset contains duplicate items, such as 31944, which is later removed.Every column in this dataset has a data type, such as an integer, a float, or a text. We note that some of these data types are inaccurate and eliminate those columns afterward.We calculate the distinct value for each column, which represents the actual values for each column.

# 2. Understanding Your Variables

```
# Dataset Columns
df_column = hotel_booking_df.columns
df_column
```

Index(['hotel', 'is_canceled', 'lead_time', 'arrival_date_year',
       'arrival_date_month', 'arrival_date_week_number',
       'arrival_date_day_of_month', 'stays_in_weekend_nights',
       'stays_in_week_nights', 'adults', 'children', 'babies', 'meal',
       'country', 'market_segment', 'distribution_channel',
       'is_repeated_guest', 'previous_cancellations',
       'previous_bookings_not_canceled', 'reserved_room_type',
       'assigned_room_type', 'booking_changes', 'deposit_type', 'agent',
       'company', 'days_in_waiting_list', 'customer_type', 'adr',
       'required_car_parking_spaces', 'total_of_special_requests',
       'reservation_status', 'reservation_status_date'],
      dtype='object')

```
# Dataset Describe
hotel_booking_df.describe()
```

# Variables Description
# Description of individual Variable

The columns and the data it represents are listed below:

**hotel** : Name of the hotel (Resort Hotel or City Hotel)

**is_canceled** : If the booking was canceled (1) or not (0)

**lead_time:** Number of days before the actual arrival of the guests

**arrival_date_year :** Year of arrival date

**arrival_date_month :** Month of month arrival date

**arrival_date_week_number :** Week number of year for arrival date

**arrival_date_day_of_month :** Day of arrival date

**stays_in_weekend_nights :** Number of weekend nights (Saturday or Sunday) spent at the hotel by the guests.

**stays_in_week_nights :** Number of weeknights (Monday to Friday) spent at the hotel by the guests.

**adults :** Number of adults among guests

**children :** Number of children among guests

**babies :** Number of babies among guests

**meal :** Type of meal booked

**country :** Country of guests

**market_segment :** Designation of market segment

**distribution_channel :** Name of booking distribution channel

**is_repeated_guest :** If the booking was from a repeated guest (1) or not (0)

**previous_cancellations :** Number of previous bookings that were cancelled by the customer prior to the current booking

**previous_bookings_not_canceled :** Number of previous bookings not cancelled by the customer prior to the current booking

**reserved_room_type :** Code of room type reserved

**assigned_room_type :** Code of room type assigned

**booking_changes :** Number of changes/amendments made to the booking

**deposit_type :** Type of the deposit made by the guest

**agent :** ID of travel agent who made the booking

**company :** ID of the company that made the booking

**days_in_waiting_list :** Number of days the booking was in the waiting list

**customer_type :** Type of customer, assuming one of four categories

**adr :** Average Daily Rate, as defined by dividing the sum of all lodging transactions by the total number of staying nights

**required_car_parking_spaces :** Number of car parking spaces required by the customer

**total_of_special_requests :** Number of special requests made by the customer

**reservation_status :** Reservation status (Canceled, Check-Out or No-Show)

**reservation_status_date :** Date at which the last reservation status was updated

# Check Unique Values for each variable.

```
# Check Unique Values for each variable.
print(hotel_booking_df.apply(lambda col: col.unique())) # We have describes unique value in all individual column.
```

hotel                                                    [Resort Hotel, City Hotel]
is_canceled                                                                  [0, 1]
lead_time                         [342, 737, 7, 13, 14, 0, 9, 85, 75, 23, 35, 68...
arrival_date_year                                                [2015, 2016, 2017]
arrival_date_month                [July, August, September, October, November, D...
arrival_date_week_number          [27, 28, 29, 30, 31, 32, 33, 34, 35, 36, 37, 3...
arrival_date_day_of_month         [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14...
stays_in_weekend_nights           [0, 1, 2, 4, 3, 6, 13, 8, 5, 7, 12, 9, 16, 18,...
stays_in_week_nights              [0, 1, 2, 3, 4, 5, 10, 11, 8, 6, 7, 15, 9, 12,...
adults                            [2, 1, 3, 4, 40, 26, 50, 27, 55, 0, 20, 6, 5, 10]
children                                            [0.0, 1.0, 2.0, 10.0, 3.0, nan]
babies                                                             [0, 1, 2, 10, 9]
meal                                                    [BB, FB, HB, SC, Undefined]
country                           [PRT, GBR, USA, ESP, IRL, FRA, nan, ROU, NOR, ...
market_segment                    [Direct, Corporate, Online TA, Offline TA/TO, ...
distribution_channel                     [Direct, Corporate, TA/TO, Undefined, GDS]
is_repeated_guest                                                            [0, 1]
previous_cancellations            [0, 1, 2, 3, 26, 25, 14, 4, 24, 19, 5, 21, 6, ...
previous_bookings_not_canceled    [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13,...
reserved_room_type                                   [C, A, D, E, G, F, H, L, P, B]
assigned_room_type                             [C, A, D, E, G, F, I, B, H, P, L, K]
booking_changes                   [3, 4, 0, 1, 2, 5, 17, 6, 8, 7, 10, 16, 9, 13,...
deposit_type                                   [No Deposit, Refundable, Non Refund]
agent                             [nan, 304.0, 240.0, 303.0, 15.0, 241.0, 8.0, 2...
company                           [nan, 110.0, 113.0, 270.0, 178.0, 240.0, 154.0...
days_in_waiting_list              [0, 50, 47, 65, 122, 75, 101, 150, 125, 14, 60...
customer_type                         [Transient, Contract, Transient-Party, Group]
adr                               [0.0, 75.0, 98.0, 107.0, 103.0, 82.0, 105.5, 1...
required_car_parking_spaces                                         [0, 1, 2, 8, 3]
total_of_special_requests                                        [0, 1, 3, 2, 4, 5]
reservation_status                                   [Check-Out, Canceled, No-Show]
reservation_status_date           [2015-07-01, 2015-07-02, 2015-07-03, 2015-05-0...
dtype: object
# 3. Data Wrangling
```
#lets check, what is the percentage of null value in each column, starting from company

percentage_company_null = miss_values[0] / uni_num_of_rows*100
percentage_company_null
```
93.98256213098998
```
#to fill the NaN value in the column, let's check which colomns has null value, we have already stored the same.
miss_values[:5]
```
company               82137
agent                 12193
country                 452
children                  4
reserved_room_type        0
dtype: int64
```
# It is better to drop the column 'company' altogether since the number of missing values is extremely high compared to the number of rows.

hotel_booking_df.drop(['company'], axis=1, inplace=True)
```

```
# now let's check for agent

percentage_agent_null = miss_values[1] / uni_num_of_rows*100
percentage_agent_null
```

13.951439425145315

```
# As we have seen, there is minimul null values in agent, Lets fill these value by taking mode of the all values

hotel_booking_df['agent'].fillna(value = 0, inplace = True)
hotel_booking_df['agent'].isnull().sum() # we re-check that column has no null value
```

0

```
#Check the percentage null value in country col

percentage_country_null = miss_values[2] / uni_num_of_rows*100
percentage_country_null
```

0.5171861412421621

```
# We have less null vlues in country col, so we will replace null from 'other' as country name.

hotel_booking_df['country'].fillna(value = 'others', inplace = True)
hotel_booking_df['country'].isnull().sum() # we re-check that column has no null value
```

0

```
#Check the percentage null value in children col

percentage_children_null = miss_values[3] / uni_num_of_rows*100
percentage_children_null
```

0.004576868506567806

```
#let's check whether database having any other null value

hotel_booking_df.isnull().sum() # As we have seen, no column has any null value
```

hotel                             0
is_canceled                       0
lead_time                         0
arrival_date_year                 0
arrival_date_month                0
arrival_date_week_number          0
arrival_date_day_of_month         0
stays_in_weekend_nights           0
stays_in_week_nights              0
adults                            0
children                          4
babies                            0
meal                              0
country                           0
market_segment                    0
distribution_channel              0
is_repeated_guest                 0
previous_cancellations            0
previous_bookings_not_canceled    0
reserved_room_type                0
assigned_room_type                0
booking_changes                   0
deposit_type                      0
agent                             0
days_in_waiting_list              0
customer_type                     0
adr                               0
required_car_parking_spaces       0
total_of_special_requests         0
reservation_status                0
reservation_status_date           0
dtype: int64

```
#Change in datatype for required columns

#showing the info of the data to check datatype
hotel_booking_df.info()
```

<class 'pandas.core.frame.DataFrame'>
Int64Index: 87396 entries, 0 to 119389
Data columns (total 31 columns):
 #   Column                          Non-Null Count  Dtype  
---  ------                          --------------  -----  
 0   hotel                           87396 non-null  object 
 1   is_canceled                     87396 non-null  int64  
 2   lead_time                       87396 non-null  int64  
 3   arrival_date_year               87396 non-null  int64  
 4   arrival_date_month              87396 non-null  object 
 5   arrival_date_week_number        87396 non-null  int64  
 6   arrival_date_day_of_month       87396 non-null  int64  
 7   stays_in_weekend_nights         87396 non-null  int64  
 8   stays_in_week_nights            87396 non-null  int64  
 9   adults                          87396 non-null  int64  
 10  children                        87392 non-null  float64
 11  babies                          87396 non-null  int64  
 12  meal                            87396 non-null  object 
 13  country                         87396 non-null  object 
 14  market_segment                  87396 non-null  object 
 15  distribution_channel            87396 non-null  object 
 16  is_repeated_guest               87396 non-null  int64  
 17  previous_cancellations          87396 non-null  int64  
 18  previous_bookings_not_canceled  87396 non-null  int64  
 19  reserved_room_type              87396 non-null  object 
 20  assigned_room_type              87396 non-null  object 
 21  booking_changes                 87396 non-null  int64  
 22  deposit_type                    87396 non-null  object 
 23  agent                           87396 non-null  float64
 24  days_in_waiting_list            87396 non-null  int64  
 25  customer_type                   87396 non-null  object 
 26  adr                             87396 non-null  float64
 27  required_car_parking_spaces     87396 non-null  int64  
 28  total_of_special_requests       87396 non-null  int64  
 29  reservation_status              87396 non-null  object 
 30  reservation_status_date         87396 non-null  object 
dtypes: float64(3), int64(16), object(12)
memory usage: 21.3+ MB

```
#total stay in nights
hotel_booking_df['total_stay_in_nights'] = hotel_booking_df ['stays_in_week_nights'] + hotel_booking_df ['stays_in_weekend_nights']
hotel_booking_df['total_stay_in_nights'] # We have created a col for total stays in nights by adding week night & weekend nights
```

0         0
1         0
2         1
3         1
4         2
         ..
119385    7
119386    7
119387    7
119388    7
119389    9
Name: total_stay_in_nights, Length: 87396, dtype: int64

```
# We have created a col for revenue using total stay * adr
hotel_booking_df['revenue'] = hotel_booking_df['total_stay_in_nights'] *hotel_booking_df['adr']
hotel_booking_df['revenue']
```

0            0.00
1            0.00
2           75.00
3           75.00
4          196.00
           ...   
119385     672.98
119386    1578.01
119387    1103.97
119388     730.80
119389    1360.80
Name: revenue, Length: 87396, dtype: float64

```
# Also, for information, we will add a column with total guest coming for each booking
hotel_booking_df['total_guest'] = hotel_booking_df['adults'] + hotel_booking_df['children'] + hotel_booking_df['babies']
hotel_booking_df['total_guest'].sum()
```

176990.0

```
# for understanding, from col 'is_canceled': we will replace the value from (0,1) to not_canceled, is canceled.

hotel_booking_df['is_canceled'] = hotel_booking_df['is_canceled'].replace([0,1], ['not canceled', 'is canceled'])
hotel_booking_df['is_canceled']
```

0         not canceled
1         not canceled
2         not canceled
3         not canceled
4         not canceled
              ...     
119385    not canceled
119386    not canceled
119387    not canceled
119388    not canceled
119389    not canceled
Name: is_canceled, Length: 87396, dtype: object

```
#Same for 'is_repeated_guest' col
hotel_booking_df['is_repeated_guest'] = hotel_booking_df['is_repeated_guest'].replace([0,1], ['not repeated', 'repeated'])
hotel_booking_df['is_repeated_guest']
```

0         not repeated
1         not repeated
2         not repeated
3         not repeated
4         not repeated
              ...     
119385    not repeated
119386    not repeated
119387    not repeated
119388    not repeated
119389    not repeated
Name: is_repeated_guest, Length: 87396, dtype: object

```
#Now, we will check overall revenue hotel wise
hotel_wise_total_revenue = hotel_booking_df.groupby('hotel')['revenue'].sum()
hotel_wise_total_revenue
```

hotel
City Hotel      18774101.54
Resort Hotel    15686837.77
Name: revenue, dtype: float64

```
hotel_booking_df[['hotel', "revenue"]]
```

We only made a few changes to the data.

----**Columns added** -----

We have seen that a few columns are needed in the data for analytical purposes, and these columns can be evaluated.

a) **Number of Guests:** We may assess the overall number of guests and income by using these columns. This value is obtained by summing the total number of adults, children, and infants.

b) **Income:** ADR and total guests are multiplied to find revenue. This column will be used to examine each hotel's growth and profitability.

----**Columns deleted** -----

a)**company:** As we can see, this column almost has no data. As a result, we had to eliminate this column because it had no bearing on the analysis.

**Replace values in columns by**

is cancelled, isn't cancelled, and is a repeat visitor: As we've seen, these columns only hold the value of 0,1 to indicate that the boycott is now being cancelled. These values (0,1) from "Cancelled" & "Not cancelled" are changed. The same procedure is used to change 0,1 from "Repeated" and "Not repeated" in the column "is_repeated_guest". These values will now facilitate greater comprehension during visualisation.

----**Changes to the values' data types in columns** --

a) **Agent & Kids:** We verified that these columns contain float values, which don't make sense in the data because they represent the guest count and agent ID. Therefore, we have updated the 'float' data type of these columns to 'Integer'.

----**Removed duplicate entries and is_null values** --

a) Data wrangling must be done before any data from the data set can be visualised.

Data wrangling must be done before any data from the data set can be visualised. We have examined each column's null value in order to determine that. After checking, drop the column using the 'drop' method if we find one that has a greater percentage of null values. We are so removed from the "company" column. When there are only a few null values, we fill those null values with the necessary values using the.fillna() function.

b) In the same, we looked to see whether there was any data duplication and discovered that a few rows had duplicate data. As a result, we used the.drop_duplicates() method to delete those rows from the data set.

By doing this, we have eliminated any unnecessary data.

# 4. Data Visualisation, Storytelling, and Chart Experimental Design: Identify the relationships between variables
# Chart-1

```
# Let's create a function which will give us bar chart of data respective with a col.
def get_count_from_column_bar(df, column_label):
  df_grpd = df[column_label].value_counts()
  df_grpd = pd.DataFrame({'index':df_grpd.index, 'count':df_grpd.values})
  return df_grpd


def plot_bar_chart_from_column(df, column_label, t1):
  df_grpd = get_count_from_column(df, column_label)
  fig, ax = plt.subplots(figsize=(14, 6))
  c= ['g','r','b','c','y']
  ax.bar(df_grpd['index'], df_grpd['count'], width = 0.4, align = 'edge', edgecolor = 'black', linewidth = 4, color = c, linestyle = ':', alpha = 0.5)
  plt.title(t1, bbox={'facecolor':'0.8', 'pad':3})
  plt.legend()
  plt.ylabel('Count')
  plt.xticks(rotation = 15) # use to format the lable of x-axis
  #plt.xlabel(column_label)f
  plt.show()
```
```
# Chart - 1 visualization code

def get_count_from_column(df, column_label):
  df_grpd = df[column_label].value_counts()
  df_grpd = pd.DataFrame({'index':df_grpd.index, 'count':df_grpd.values})
  return df_grpd

# plot a pie chart from grouped data
def plot_pie_chart_from_column(df, column_label, t1, exp):
  df_grpd = get_count_from_column(df, column_label)
  fig, ax = plt.subplots(figsize=(14,9))
  ax.pie(df_grpd.loc[:, 'count'], labels=df_grpd.loc[:, 'index'], autopct='%1.2f%%',startangle=90, labeldistance = 1.2, explode = exp)
  plt.title(t1, bbox={'facecolor':'0.8', 'pad':3})
  ax.axis('equal')
  plt.legend()
  plt.show()
```

```
exp1 = [0.05,0.05]
plot_pie_chart_from_column(hotel_booking_df, 'hotel', 'Booking percentage of Hotel by Name', exp1)
```

Why did you pick the specific chart?
**To present the data that in which hotel more booking have been done.**

What is/are the insight(s) found from the chart?
**Here, we found that the booking number is Higher in City Hotel which is 61.12% than Resort Hotel which is 38.87%. Hence we can say that City hotel has more consumption**

Will the gained insights help creating a positive business impact? Are there any insights that lead to negative growth? Justify with specific reason.
**Yes, for both Hotels, this data making some positive business impact : -**

**City Hotel :- Provided more services to attract more guest to increase more revenue.**

**Resort Hotel :- Find solution to attract guest and find what city hotel did to attract guest.**

# Chart - 2

```
# Chart - 2 visualization code
exp4 = [0,0.1]
plot_pie_chart_from_column(hotel_booking_df, 'is_canceled', 'Cancellation volume of Hotel', exp4)
```

Why did you pick the specific chart?
**In this chart, we presented the cancellation rate of the hotels booking**

What is/are the insight(s) found from the chart?
**Here, we found that overall more than 25% of booking got cancelled**

Will the gained insights help creating a positive business impact? Are there any insights that lead to negative growth? Justify with specific reason.
**Here, we can see, that more than 27% booking getting cancelled.**

**Solution: We can check the reason of cancellation of a booking & need to get this sort on business level**

# Chart 3

```
# Chart - 3 visualization code
plot_bar_chart_from_column(hotel_booking_df, 'distribution_channel', 'Distibution Channel Volume')
```

Why did you pick the specific chart?
**The following chart represent maximum volume of booking done through which channel to represnt the numbers in descending order we chose bar graph**

What is/are the insight(s) found from the chart?
**As clearly seen TA/TO(Tour of Agent & Tour of operator) is highest, recommending to continue booking through TA/TO**

Will the gained insights help creating a positive business impact? Are there any insights that lead to negative growth? Justify with specific reason.
**Yes this shows positive business impact.**

**Higher the number of TA/TO will help to increase the revenue generation of Hotel.**

# Chart -4

```
# Chart - 4 visualization code
exp2 = [0.2, 0,0,0,0,0,0,0,0,0,0,0]
plot_pie_chart_from_column(hotel_booking_df, 'arrival_date_month', 'Month-wise booking', exp2)
```

Why did you pick the specific chart?
**To show the percentage share of booking in each month,on overall level**

What is/are the insight(s) found from the chart?
**The above percentage shows month May, July and Aug are the highest booking months due to holiday season. Recommending aggressive advertisement to lure more and more customers.**

Will the gained insights help creating a positive business impact? Are there any insights that lead to negative growth? Justify with specific reason.
**Yes, with increased volume of visitors will help hotel to manage revenue in down time, will also help employee satisfaction and retention.**

# Chart-5
```
# Chart - 5 visualization code
exp3 = [0,0.2]
plot_pie_chart_from_column(hotel_booking_df, 'is_repeated_guest', 'Guest repeating status', exp3)
```

Why did you pick the specific chart?
**To show the percentage share of repeated & non-repeated guests.**

What is/are the insight(s) found from the chart?
**Here, we can see that the number of repeated guests is very less as compared to overall guests**

Will the gained insights help creating a positive business impact? Are there any insights that lead to negative growth? Justify with specific reason.
**We can give alluring offers to non-repetitive customers during Off seasons to enhance revenue**

# Chart-6

```
# Chart - 6 visualization code
plot_bar_chart_from_column(hotel_booking_df, 'assigned_room_type', 'Assigment of room by type')
```

Why did you pick the specific chart?
**To show distribution by volume, which room is alotted.**

What is/are the insight(s) found from the chart?
**This chart shows room type 'A' is most prefered by guest.**

Will the gained insights help creating a positive business impact? Are there any insights that lead to negative growth? Justify with specific reason.
**Yes, Positive impact because 'A','D','E' is more prefered by guest due to better services offered in room type.**

# Chart-7
```
market_segment_df = pd.DataFrame(hotel_booking_df['market_segment'])
market_segment_df_data = market_segment_df.groupby('market_segment')['market_segment'].count()
market_segment_df_data.sort_values(ascending = False, inplace = True)
plt.figure(figsize=(15,6))
y = np.array([4,5,6])
market_segment_df_data.plot(kind = 'bar', color=['r', 'g', 'y', 'b', 'pink', 'black', 'brown'], fontsize = 20,legend='True')
```

Why did you pick the specific chart?
**In this chart, we have seen market segment by which hotel has booked**

What is/are the insight(s) found from the chart?
**Online TA has been used most frequently to book hotel by the guest.**

Will the gained insights help creating a positive business impact? Are there any insights that lead to negative growth? Justify with specific reason.
**Yes, it is creating positive business impact that guests are using Online TA market segment as most prefered to book hotels.**

# Chart-8

```
# Chart - 8 visualization code
guest_country_wise = pd.DataFrame(hotel_booking_df[['country','total_guest']])
guest_country_wise_df = guest_country_wise.groupby(['country'])['total_guest'].sum()
guest_country_wise_df.sort_values(ascending = False, inplace = True)
top_10_country_by_guest = guest_country_wise_df.head(10)
[ ]
plt.figure(figsize=(12,6))
sns.barplot(x=top_10_country_by_guest.index, y=top_10_country_by_guest).set(title='Top 10 Countries by Guest')
print("\n\nPRT = Portugal\nGBR = Great Britain & Northern Ireland\nFRA = France\nESP = Spain\nDEU = Germany\nITA = Italy\nIRL = Ireland\nBRA = Brazil\nBEL = Belgium\nNLD = Netherland")
```

1 Why did you choose the particular chart? We have observed that the majority of visitors come from which countries.

**A chart of the top 10 nations is displayed.**

2. What insight(s) were discovered from the chart? As we can see, the majority of the visitors are from Portugal.

3 Will the learned insights assist to a favorable commercial impact? Exist any insights that result in a decline in growth? Provide a specific justification.

**To increase the number of customers, we can increase our marketing efforts and provide enticing deals to visitors from Portugal.**

# Chart-9

```
average_adr = hotel_booking_df.groupby('hotel')['adr'].mean()
average_adr
plt.subplots(figsize=(8, 5))
average_adr.plot(kind = 'barh', color = ('g', 'r'))
plt.xlabel("Average ADR", fontdict={'fontsize': 12, 'fontweight' : 5, 'color' : 'brown'})
plt.ylabel("Hotel Name", fontdict={'fontsize': 12, 'fontweight' : 5, 'color' : 'Brown'} )
plt.title("Average ADR of Hotel", fontdict={'fontsize': 12, 'fontweight' : 5, 'color' : 'Green'} )
```

This code calculates the total revenue generated by each hotel in the DataFrame hotel_booking_df and creates a bar plot to visualize and compare the revenue for different hotels.

Let's break down the code step by step:

plt.figure(figsize=(8, 5))

This line creates a new matplotlib figure with a specified size of 8 inches in width and 5 inches in height. This figure will be used as the canvas for the bar plot.

hotel_wise_revenue = hotel_booking_df.groupby('hotel')['revenue'].sum()

The DataFrame hotel_booking_df is grouped by the 'hotel' column, and then the sum() function is applied to the 'revenue' column for each group to calculate the total revenue for each hotel. The result is a pandas Series where the hotel names are used as the index, and the corresponding values represent the total revenue for each hotel.

ax = hotel_wise_revenue.plot(kind='bar', color=('black', 'green'))

The plot() function from pandas is used to create a bar plot. The 'kind' argument is set to 'bar', indicating that the plot should be a vertical bar chart. The 'color' argument is provided as a tuple containing the colors black ('black') and green ('green') to differentiate the bars.

plt.xlabel("Hotel", fontdict={'fontsize': 12, 'fontweight': 5, 'color': 'Brown'})

This line sets the x-axis label for the plot to "Hotel". The fontdict parameter is used to customize the label's font size, font weight, and color.

plt.ylabel("Total Revenue", fontdict={'fontsize': 12, 'fontweight': 5, 'color': 'Brown'})

This line sets the y-axis label for the plot to "Total Revenue". The fontdict parameter is used to customize the label's font size, font weight, and color.

plt.title("Total Revenue", fontdict={'fontsize': 12, 'fontweight': 5, 'color': 'Green'})

This line sets the plot title to "Total Revenue". The fontdict parameter is used to customize the title's font size, font weight, and color.

plt.show()

The show() function from matplotlib is called to display the bar plot on the screen.

The resulting bar plot will have hotel names on the x-axis and the corresponding total revenue values on the y-axis. The bars will be colored black and green to differentiate the revenue values for different hotels.

# Chart-10

```
plt.figure(figsize = (8,5))
hotel_wise_revenue = hotel_booking_df.groupby('hotel')['revenue'].sum()
hotel_wise_revenue
ax = hotel_wise_revenue.plot(kind = 'bar', color = ('black', 'green'))
plt.xlabel("Hotel", fontdict={'fontsize': 12, 'fontweight' : 5, 'color' : 'Brown'})
plt.ylabel("Total Revenue", fontdict={'fontsize': 12, 'fontweight' : 5, 'color' : 'Brown'} )
plt.title("Total Revenue", fontdict={'fontsize': 12, 'fontweight' : 5, 'color' : 'Green'} )
```

**1.Why did you choose the particular chart?**

To provide the two hotels' average ADRs

**2.What insight(s) were discovered from the chart?**

The average ADR of a city hotel is higher than a resort hotel, hence the city hotel will generate more profit and income.

**3.Will the learned insights contribute to a favourable commercial impact? Exist any insights that result in a decline in growth? Provide a specific justification.**

Here, we can promote the City Hotel more to draw in more guests and increase revenue.

## Chart-11

```
# Chart - 10 visualization code
plt.figure(figsize = (12,6))
sns.scatterplot(y = 'total_stay_in_nights', x = 'adr', data = hotel_booking_df[hotel_booking_df['adr'] < 1000])
plt.show() #
```
**1.Why did you choose the particular chart?**

To compare and illustrate how total stay days compare to ADR

**2.What insight(s) were discovered from the chart?**

Here, we discovered that if guest stay days are decreasing, ADR is increasing.

# Chart-12

```
# Chart - 12 visualization code
plt.figure(figsize = (12,10), dpi = 100)
hotel_wise_meal = hotel_booking_df.groupby(['hotel', 'meal'])['meal'].count().unstack()
hotel_wise_meal.plot(kind ='bar', figsize = (12,8))
hotel_wise_meal
```

**1.Why did you choose the particular chart?**

To display the visitor's preferred dining experience hotel-wise

**2.What insight(s) were discovered from the chart?**

**As you can see, guests at both hotels prefer the BB (Bed & Breakfast) meal. In order to increase customer retention and draw in new customers, the hotel can serve more delicious meals during this dinner.**

# Chart - 13 - Correlation Heatmap

```
# Correlation Heatmap visualization code
corr_df = hotel_booking_df[['lead_time','previous_cancellations', 'previous_bookings_not_canceled', 'total_guest',
                    'booking_changes', 'days_in_waiting_list', 'adr', 'required_car_parking_spaces', 'total_of_special_requests']].corr()
f, ax = plt.subplots(figsize=(12, 12))
sns.heatmap(corr_df, annot = True, fmt='.2f', annot_kws={'size': 10},  vmax=1, square=True, cmap="YlGnBu")
```

**1.Why did you choose the particular chart?**

To comprehend the relationships among various numerical quantities

**2.What insight(s) were discovered from the chart?**

The axis's highest corelation value is 39% positive and its lowest correlation value is -9% negative.

# 5. The answer to the business objective
The following business aim was met :

In order for the hotel industry to prosper, a few factors must be taken into account, including high revenue generation, customer happiness, and employee retention.

By using a pie chart distribution, we can demonstrate to the client which months generate the most money.

Increasing revenue by using a bar chart to show which types of rooms are most frequently booked and when visitors are most likely to travel.

As a result, the customer can be properly prepared in advance, minimising long-term complaints and contributing to further improvement of their hospitality.

To encourage clients to contact offices for bulk reservations during the off-season, outliers such as larger visitor numbers than average were sprinkled across the plot. This helped generate more money.

We can display the visitor arrivals trend at client venues, allowing clients to schedule visitors in advance for their entertainment and leisure activities.

In order for the percentages underneath those numbers to be improved by a variety of mediums, we were also able to correlate the values indicating the maximum and minimum % between them.

# Conclusion :-
City Hotel generates greater income and profit and appears to be more popular among travellers.

Compared to the other months, the majority of reservations are made in July and August.

Travellers favour accommodation Type A over all other accommodation types.

Portugal and the United Kingdom make the most reservations.

The majority of visitors stay in hotels for 1-4 days.

The City Hotel keeps a larger number of visitors.

About one-fourth of all reservations are cancelled. City Hotel is the source of more cancellations.

Compared to returning consumers, new guests frequently cancel reservations.

Booking cancellations are unaffected by lead time, waiting list length, or client assignment of a reserved room.

Corporate has the most percentage of repeated guests while TA/TO has the least whereas in the case of cancelled bookings TA/TO has the most percentage while Corporate has the least.

The length of the stay decreases as ADR increases probably to reduce the cost.

### Hurrah! You achieved your EDA Capstone Project successfully!!!
