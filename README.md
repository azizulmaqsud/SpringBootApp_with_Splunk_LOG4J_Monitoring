# Integrate SpringBootApp with Splunk LOG4J Monitoring
## Step 1: login splunk
Login http://localhost:8000
## Step 2: Create Data input (source type: log4j)
Settings > data input > HTTP event collector > global settings > Create token > log4j > review > submit 
## Step 3: process index 
## Step 4: create dashboard 
## Nutshell: 
Token > index > Application > logs collected in index > Dashboard 

Splunk runs in port 8000 but index runs in port 8088

# Here I used:

Token: ………………….. 

Port: 8088

Source: log4j

Index: ………………

Source name: http-event-logs

## Springboot application here has controller class, service class, database class
- Clone the java code > Check for exclusion of default spring boot logging and add log4j2 as dependency 
- Add logger statements 
- Import org.apache.logging.log4j.logger;
  
In eclipse, run as maven build > goals: clean install -DskipTests > build success 

Then run as Spring boot app > started at port 9090
## Open postman:

Add POST method http://localhost:9090/orders

Add BODY > raw > JSON 

{

“id”: 1001,

“name”:”iphone”,

“qty”:”1”,

“price”: 1500

}

ADD GET http://localhost:9090/orders

ADD GET http://localhost:9090/orders/1001 

ADD GET http://localhost:9090/orders/1002 

Postman Response status should be ‘200 OK’ , or if error then ‘500 internal server error’. And, eclipse console will say ERROR exception: order not found with id : 1000000000000001 (its imaginary and wrong id)

# Step 5: Search in Splunk with query
 
 index=”springbootProjectName”OrderService:getOrder
 
 index=”springbootProjectName” AND (EXCEPTION OR ERROR)
# Spring boot high level: 
In high level, if client hits www.productcompany.com then traffic goes through Controller > Service > DB 

## Thank You!
# Stay Connected !!

https://www.youtube.com/channel/UCNwP7KEElaJ7cdDTLP-KbBg

https://www.linkedin.com/in/azizul-maqsud/

https://azizulmaqsud-1684501031000.hashnode.dev/

https://medium.com/@azizulmaqsud

https://twitter.com/Sohail2me

https://github.com/azizulmaqsud


<a href="https://www.buymeacoffee.com/azizulmaqsud"><img src="https://img.buymeacoffee.com/button-api/?text=Buy me a coffee&emoji=&slug=scaleupsaas&button_colour=FFDD00&font_colour=000000&font_family=Cookie&outline_colour=000000&coffee_colour=ffffff" /></a>


# SpringBootApp_with_Splunk_LOG4J_Monitoring
