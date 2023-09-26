# Hotel_booking_analysis_EDA


# Project Summary

Almabetter Hotel Booking EDA Project Using Python || Hariom Hotel booking analysis with AlmaBetter EDA This project relates to hotel reservations and includes a variety of city hotels and resort hotels. There are 32 columns and a total of 119390 rows in this dataset. Data collection, data cleansing and manipulation, and EDA (experimental Data Analysis) are the three categories into which the workflow for data manipulation is divided. The names of some of the columns, including hotel, is_canceled, lead_time, arrival_date_year, arrival_date_month, arrival_date_week_number, arrival_date_day_of_month, and stays_in_weekend_nights, have been updated as the data collection process has progressed. This is done by coding Head(), Tail(), info(), describe(), columns(), and other methods used for data collection. As we proceed, we identify the distinct value for each column, create a list in tabular format, and also verify the dataset type for each column. Identify some columns with inaccurate data types and fix them afterward. As we discover duplicate items totaling 87396, which are later discarded from the dataset, duplicate data items must also be removed during the data cleaning phase.

We must first perform data manipulation before visualizing any data from the data source. To do that, we examined each column's null value. After checking, drop the column using the 'drop' method if we find one that has a greater percentage of null values. We are so removed from the "company" column. When there are only a few null values, we fill those null values with the necessary values using the formula.fill()

To achieve greater understanding and business goals, many charts are utilized for data visualization.

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
