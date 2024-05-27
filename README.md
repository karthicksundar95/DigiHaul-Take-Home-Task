# DigiHaul Take Home Task
Analysis of lead time and predictive modelling of potential delay in shipments
<h1 align='Center'>
<img src="https://assets.digihaul.com/images/logo.png" align="center"/>
</h1>

## Problem Statement

Road haulage is essential for the people and businesses of the UK. Approximately 90% of all goods transported by land in Great Britain are moved directly by road. DigiHaul is a digital transport business, specialising in managing, consolidating and integrating data from both Carriers and Shippers to deliver seamless end-to-end logistics service.
Shippers book shipments on the DigiHaul platform, detailing the scheduled collection and delivery time windows / locations and required vehicle types for carriers to consider. Once a carrier accepts a job and collection is scheduled, DigiHaul’s driver app facilitates real-time tracking of shipments through GPS signals, subject to carriers granting permissions for location logging.

#### Mission:
As a digital transport business DigiHaul is specializes in managing, consolidating, and integrating data from both
Carries and Shippers to provide a seamless end-t-end logistics service
-   Shippers book shipments on the DiguHaul platform, specifying collection and delivery time windows, locations, and   required vehicle types
Carriers: accept jobs and schedule collection
DigiHaul’s driver app: facilitates real-time tracking via GPS (contingent on carrier permissions for logging)

#####   Task 1: (Operational KPI)
KPI: On-time collection and delivery
What percentage of shipments met the on-time delivery threshold (no later than 30 minutes past the scheduled window) from October 1st to December 31st, 2023?

#####   Task 2: (Time delay notifications)
KPI: Timely communication of potential delays to shippers
Identify which shippers should be automatically notified about the delays and when thy should be notified

#####   Task 3: (Predictive)
Predict the likelihood of delays for shipments listed in “New_bookings.csv” dataset

## File structure:
1. Task 1.ipynb : python notebook with analysis, solutions and documentation to find the percentage of shipments delivered on time
2. Task 2.ipynb : python notebook to analyse and strategize the heuristic for whom and when to send notification on potential delays
3. Task 3.ipynb : python notebook with model training and testing for new booking data for potential delay or not
4. Digihaul_Karthick_Sundar_Coimbatore_Krishnaraaj.pptx: Power point presentation which include all the analysis finding structured to address non-technical audience

## Input data:

Three datasets are provided for working with the tasks and each one of them are in .csv format

1. gps_data.csv: contains GPS logging(latitude and longitude) for each shipment along with the timestamp details

2. shipment.csv: contains all the details about each shipment initiated, with the details of shipper, details of carries, collection and delivery - postcode, latitude, longitude and time

3. new booking.csv: contains only new shipment booking done by the shippers

## Design & Approach:

### Task 1 :

Operational teams rely heavily on KPIs like on-time collection and on-time delivery to gauge carrier performance. What percentage of shipments met the on-time delivery threshold (arriving no later than 30 minutes past the scheduled delivery window) between October 1st and December 31st, 2023? Please outline your assumptions.


Steps:
1. Assumptions and application of "time filter" on data 
2. Assumptions on delivery details from "GPS" data
3. Data transformation from GPS and delivery data
4. Calculation of distance matric on GPS data
5. Assumptions and heuristics on distance threshold for delivery
6. Calculation of delivery time and validation against delivery threshold
7. Profiling the delivery data based on distance and time heuristics 
8. Calculating percentage of shipments met the on-time delivery threshold

### Task 2 :

Timely communication of potential delays is crucial for shippers. During the 3-month period from 1st Oct to 31st Dec 2023, which shipper(s) should be notified automatically regarding potential late delivery of which shipments, and at what times?


Steps:
1. Getting all GPS logs for valid delivery data from the previous question
2. Use Google distance API to calculate distance and ETA between current geo location and destination location
3. Constraint and sample creation
4. Analysis to identify the threshold for allowed range of time difference between target time and google ETA 
5. Whom and when to send?

### Task 3 :

A python class called "PotentialDelayPrediction" is created with methods that help in entire modelling process, right from pre-processing, feature engineering, train test split, model building and validation. The code is available in the notebook with proper documentation following PEP8 standards.
