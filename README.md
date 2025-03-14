# JMeter Performance Testing and Transaction Automation

## This repository contains two JMeter collections. One is booking.jmx that is designed to perform load test(Simulates 120,000 users logging in, creating a booking, and searching for it over a 12-hour period), Stress Test (Identifies bottleneck point by gradually increasing the number of users performing booking creation.), and performance test.Load Test . Another collections is dmoney.jmx which simulates various transactions(Deposit,SendMoney and Payment) for two different APIs.

## Technology I used:
- JDK LTS (version-17)
 
 - Apache JMeter

 - Postman 

## Setup in Apache JMeter for both APIs
  - Header Controller:

      - Add ```Accept: */*``` in the Header Controller.

- User Defined Variables:

    - Add ```secretKEY: ROADTOSDET``` in the User Defined Variables.

 ## booking API Steps
  - Login Request Configuration:
      - URL: ```https://restful-booker.herokuapp.com```
        - Method: POST
        - path: /auth`

 - Create Booking Request Configuration:
      - URL: ```https://restful-booker.herokuapp.com```
        - Method: POST
        - path: /booking
      - Extract Booking ID using JSon Extractor


  - Search Booking Request Configuration:
       - URL: ```https://restful-booker.herokuapp.com```
           - Method: GET
           - Path: /booking/${extracted id}
   - Performance Testing Configuration:
        - Gaussian Random Timer
            - Deviation: 2000ms
            - Constant Delay: 500ms

  - Run Load and Stress Tests
    
 ## Dmoney API Steps
  - Login Request Configuration:
      - URL: ```https://dmoney.roadtocareer.net```
        - Method: POST
        - path: /auth` 
  - Prepare CSV Files
       - ```deposit.csv: Contains agents and customers' phone numbers.```
       - ```sendMoney.csv: Contains sender and reciever customers' phone numbers.```
       - ```payment.csv: Contains customers and merchants' phone numbers.```
  - CSV dataset Config
    
  - Random Variable Controller

  - Transactions:
      - Create three threads for each transaction type (Deposit, Send Money, Payment).

  - Set a 120-second ramp-up time for each thread to simulate gradual load.

 - Assertions: Add assertions to verify the success of each transaction.
##  How to generate HTML Report:
- Clone this Project

- Save it inside the bin folder of Apache jmeter. 

- Open Command Promp and go to this file directory and hit the following command
  -  ```jmeter -n -t .\Booking.jmx -l .\Booking.jtl -e -o Reports```
  
 Report will be generated for the booking API inside Reports folder.


 - Open Command Promp and go to this file directory and hit the following command
     - ```jmeter -n -t .\dmoney.jmx -l .\dmoney.jtl -e -o Reports```
  
  Report will be generated for the dmoney API inside Reports folder.

## Load Test of booking API Request Summary:
 
![Screenshot (20)](https://github.com/user-attachments/assets/fc107a9d-15ca-471d-847f-07232e1c67ef)


## Stress Test of booking API Request Summary:

![Screenshot (40)](https://github.com/user-attachments/assets/9ea70397-6338-4526-967d-cab340b06fa5)


## Test Reports of booking API:

[booking-api-test-report.xlsx](https://github.com/user-attachments/files/19247759/booking-api-test-report.xlsx) 

## dmoney Api Request Summary

![Screenshot (41)](https://github.com/user-attachments/assets/a88120c1-6924-4beb-b9d8-ad3d9f631347)


