# Introduction
This documentation explains the API testing suite for the thetestingworldapi.com which contains a Postman collection and environment designed to facilitate API testing for various functionalities related to management details of student. The API allows operations such as fetching student details, creating new students, retrieving specific students, adding technical skills, and managing student addresses. 

# Summary    
I have completed an API test of Get all students, Create a Student, Get Specific created student, Create technical skills, Create student's address and finally Get student details
https://thetestingworldapi.com/   
<p align="center">
  <img src="https://github.com/DiPaGh0sH/API_Testing_of_Testing-World_for_StudentDetails_using_Postman/blob/master/Summary_in_Command.png?raw=true" />
</p>
 

Here in this API testing student details viewed and different tests were performed for different HTTP methods like POST, GET, DELETE, PUT.

**Summary:** Total 6 Test Scripts and 22 assertions were done. All of them passed with 0 failed tests and 0 skipped tests. The number of iteration was 1.


# Requirements  
**Java**  
https://www.oracle.com/java/technologies/downloads/   
**Postman**   
https://www.postman.com/   
**Node JS**   
https://nodejs.org/en/    



# Assertions Details    
#### Get Student
**Tests Script**
```bash
var JsonData = pm.response.json()
console.log(JsonData.length)

var status_code = pm.response.code
if(status_code==200){
pm.test("200 ; STATUS : SUCCESS", function () {
    pm.response.to.have.status(200);
});
}
else if(status_code==201){
    pm.test("201 ; STATUS : CREATED", function () {
    pm.response.to.have.status(201);
})}
else if(status_code==202){
    pm.test("202 ; STATUS : ACCEPTED", function () {
    pm.response.to.have.status(202);
})}
else if(status_code==400){
    pm.test("400 ; STATUS : BAD REQUEST", function () {
    pm.response.to.have.status(400);
})}
else if(status_code==401){
    pm.test("401 ; STATUS : UNAUTHORIZED", function () {
    pm.response.to.have.status(401);
})}
else if(status_code==402){
    pm.test("402 ; STATUS : PAYMENT REQUIRED", function () {
    pm.response.to.have.status(402);
})}
else if(status_code==403){
    pm.test("403 ; STATUS : FORBIDDEN", function () {
    pm.response.to.have.status(403);
})}
else if(status_code==404){
    pm.test("404 ; STATUS : NOT FOUND", function () {
    pm.response.to.have.status(404);
})}
else if(status_code==405){
    pm.test("405 ; STATUS : METHOD NOT ALLOWED", function () {
    pm.response.to.have.status(405);
})}
else if(status_code==500){
    pm.test("500 ; STATUS : INTERNAL SERVER ERROR", function () {
    pm.response.to.have.status(500);
})}
else if(status_code==501){
    pm.test("501 ; STATUS : NOT IMPLEMENTED", function () {
    pm.response.to.have.status(501);
})}
else if(status_code==502){
    pm.test("502 ; STATUS : BAD GATEWAY", function () {
    pm.response.to.have.status(502);
})}
else if(status_code==503){
    pm.test("503 ; STATUS : SERVICE UNAVAILABLE", function () {
    pm.response.to.have.status(503);
})}
```
#### Create Student
**Body**
```bash   
{ 
"first_name": "{{first_name}}", 
"middle_name": "{{middle_name}}", 
"last_name": "{{last_name}}", 
"date_of_birth": "{{date_of_birth}}" 
}
```

**Pre-Request Scripts**

```bash   
var firstname = pm.variables.replaceIn("{{$randomFirstName}}")
console.log("First Name: "+firstname)
pm.environment.set("first_name",firstname)

var lastname = pm.variables.replaceIn("{{$randomLastName}}")
console.log("Middle Name: "+lastname)
pm.environment.set("middle_name",lastname)

var lastname = pm.variables.replaceIn("{{$randomLastName}}")
console.log("Last Name: "+lastname)
pm.environment.set("last_name",lastname)

const moment = require('moment')
const today = moment()
console.log(today.format("YYYY-MM-DD"))
pm.environment.set("date_of_birth", today.add(2,'d').format("YYYY-MM-DD"))
```
**Tests Script**
```bash
var jsonData = pm.response.json()
pm.environment.set("id", jsonData.id)
console.log(jsonData.id)

var JsonData = pm.response.json()

var status_code = pm.response.code
if(status_code==200){
pm.test("200 ; STATUS : SUCCESS", function () {
    pm.response.to.have.status(200);
});
}
else if(status_code==201){
    pm.test("201 ; STATUS : CREATED", function () {
    pm.response.to.have.status(201);
})}
else if(status_code==202){
    pm.test("202 ; STATUS : ACCEPTED", function () {
    pm.response.to.have.status(202);
})}
else if(status_code==400){
    pm.test("400 ; STATUS : BAD REQUEST", function () {
    pm.response.to.have.status(400);
})}
else if(status_code==401){
    pm.test("401 ; STATUS : UNAUTHORIZED", function () {
    pm.response.to.have.status(401);
})}
else if(status_code==402){
    pm.test("402 ; STATUS : PAYMENT REQUIRED", function () {
    pm.response.to.have.status(402);
})}
else if(status_code==403){
    pm.test("403 ; STATUS : FORBIDDEN", function () {
    pm.response.to.have.status(403);
})}
else if(status_code==404){
    pm.test("404 ; STATUS : NOT FOUND", function () {
    pm.response.to.have.status(404);
})}
else if(status_code==405){
    pm.test("405 ; STATUS : METHOD NOT ALLOWED", function () {
    pm.response.to.have.status(405);
})}
else if(status_code==500){
    pm.test("500 ; STATUS : INTERNAL SERVER ERROR", function () {
    pm.response.to.have.status(500);
})}
else if(status_code==501){
    pm.test("501 ; STATUS : NOT IMPLEMENTED", function () {
    pm.response.to.have.status(501);
})}
else if(status_code==502){
    pm.test("502 ; STATUS : BAD GATEWAY", function () {
    pm.response.to.have.status(502);
})}
else if(status_code==503){
    pm.test("503 ; STATUS : SERVICE UNAVAILABLE", function () {
    pm.response.to.have.status(503);
})}
```   
#### Get Specific Student  
**Tests Script**
```bash
var status_code = pm.response.code
if(status_code==200){
pm.test("200 ; STATUS : SUCCESS", function () {
    pm.response.to.have.status(200);
});
var jsonData = pm.response.json()
pm.test("ID Validation", function () {
    pm.expect(jsonData.data.id).to.eql(Number(pm.environment.get("id")));
});
pm.test("First Name Validation", function () {
    pm.expect(jsonData.data.first_name).to.eql(pm.environment.get("first_name"));
});
pm.test("Middle Name Validation", function () {
    pm.expect(jsonData.data.middle_name).to.eql(pm.environment.get("middle_name"));
});
pm.test("Last Name Validation", function () {
    pm.expect(jsonData.data.last_name).to.eql(pm.environment.get("last_name"));
});
pm.test("Date of Birth Validation" ,function () {
    pm.expect(jsonData.data.date_of_birth).to.eql(pm.environment.get("date_of_birth"));
});
}
else if(status_code==201){
    pm.test("201 ; STATUS : CREATED", function () {
    pm.response.to.have.status(201);
})}
else if(status_code==202){
    pm.test("202 ; STATUS : ACCEPTED", function () {
    pm.response.to.have.status(202);
})}
else if(status_code==400){
    pm.test("400 ; STATUS : BAD REQUEST", function () {
    pm.response.to.have.status(400);
})}
else if(status_code==401){
    pm.test("401 ; STATUS : UNAUTHORIZED", function () {
    pm.response.to.have.status(401);
})}
else if(status_code==402){
    pm.test("402 ; STATUS : PAYMENT REQUIRED", function () {
    pm.response.to.have.status(402);
})}
else if(status_code==403){
    pm.test("403 ; STATUS : FORBIDDEN", function () {
    pm.response.to.have.status(403);
})}
else if(status_code==404){
    pm.test("404 ; STATUS : NOT FOUND", function () {
    pm.response.to.have.status(404);
})}
else if(status_code==405){
    pm.test("405 ; STATUS : METHOD NOT ALLOWED", function () {
    pm.response.to.have.status(405);
})}
else if(status_code==500){
    pm.test("500 ; STATUS : INTERNAL SERVER ERROR", function () {
    pm.response.to.have.status(500);
})}
else if(status_code==501){
    pm.test("501 ; STATUS : NOT IMPLEMENTED", function () {
    pm.response.to.have.status(501);
})}
else if(status_code==502){
    pm.test("502 ; STATUS : BAD GATEWAY", function () {
    pm.response.to.have.status(502);
})}
else if(status_code==503){
    pm.test("503 ; STATUS : SERVICE UNAVAILABLE", function () {
    pm.response.to.have.status(503);
})}

```   
#### Create Technical Skills
**Body**
```bash
{ 
"id": 1, 
"language": [ 
"{{language_code_1}}", 
"{{language_code_2}}" 
], 
"yearexp": "{{yearexp}}", 
"lastused": "{{lastused}}", 
"st_id": {{id}}
}
```

**Pre-Request Scripts**

```bash   
var language_1 = pm.variables.replaceIn("{{$randomLocale}}")
console.log("Language 1: "+language_1)
pm.environment.set("language_code_1",language_1)

var language_2 = pm.variables.replaceIn("{{$randomLocale}}")
console.log("Language 2: "+language_2)
pm.environment.set("language_code_2",language_2)

var year_exp = pm.variables.replaceIn("{{$randomInt}}")
console.log("Year of Experience: "+year_exp)
pm.environment.set("yearexp",year_exp)

const moment = require('moment')
const today = moment()
console.log(today.format("YYYY-MM-DD"))
pm.environment.set("lastused", today.format("YYYY-MM-DD"))

```
**Tests Script**
```bash
var status_code = pm.response.code
if(status_code==200){
pm.test("200 ; STATUS : SUCCESS", function () {
    pm.response.to.have.status(200);
});
}
else if(status_code==201){
    pm.test("201 ; STATUS : CREATED", function () {
    pm.response.to.have.status(201);
})}
else if(status_code==202){
    pm.test("202 ; STATUS : ACCEPTED", function () {
    pm.response.to.have.status(202);
})}
else if(status_code==400){
    pm.test("400 ; STATUS : BAD REQUEST", function () {
    pm.response.to.have.status(400);
})}
else if(status_code==401){
    pm.test("401 ; STATUS : UNAUTHORIZED", function () {
    pm.response.to.have.status(401);
})}
else if(status_code==402){
    pm.test("402 ; STATUS : PAYMENT REQUIRED", function () {
    pm.response.to.have.status(402);
})}
else if(status_code==403){
    pm.test("403 ; STATUS : FORBIDDEN", function () {
    pm.response.to.have.status(403);
})}
else if(status_code==404){
    pm.test("404 ; STATUS : NOT FOUND", function () {
    pm.response.to.have.status(404);
})}
else if(status_code==405){
    pm.test("405 ; STATUS : METHOD NOT ALLOWED", function () {
    pm.response.to.have.status(405);
})}
else if(status_code==500){
    pm.test("500 ; STATUS : INTERNAL SERVER ERROR", function () {
    pm.response.to.have.status(500);
})}
else if(status_code==501){
    pm.test("501 ; STATUS : NOT IMPLEMENTED", function () {
    pm.response.to.have.status(501);
})}
else if(status_code==502){
    pm.test("502 ; STATUS : BAD GATEWAY", function () {
    pm.response.to.have.status(502);
})}
else if(status_code==503){
    pm.test("503 ; STATUS : SERVICE UNAVAILABLE", function () {
    pm.response.to.have.status(503);
})}
```
#### Create Student Address
**Body**
```bash   
{ 
"Permanent_Address": { 
"House_Number": "{{House_Number}}",
"City": "{{City}}",
 "State": "{{State}}", 
"Country": "{{Country}}",
"PhoneNumber": [ 
{ 
"Std_Code": "{{Std_Code}}",
"Home": "{{Home}}",
 "Mobile": "{{Mobile}}" 
},
{ 
"Std_Code": "{{Std_Code_1}}",
"Home": "{{Home_1}}", 
"Mobile": "{{Mobile_1}}" 
} 
] 
},
"stId": {{id}}
}
```

**Pre-Request Scripts**

```bash   
var house_number = pm.variables.replaceIn("{{$randomInt}}")
console.log("House Number: "+house_number)
pm.environment.set("House_Number",house_number)

var city = pm.variables.replaceIn("{{$randomCity}}")
console.log("CITY: "+city)
pm.environment.set("City",city)

var state = pm.variables.replaceIn("{{$randomStreetName}}")
console.log("STATE: "+state)
pm.environment.set("State",state)

var country = pm.variables.replaceIn("{{$randomCountry}}")
console.log("COUNTRY: "+country)
pm.environment.set("Country",country)

var std_code = pm.variables.replaceIn("{{$randomCountryCode}}")
console.log("STD CODE 1: "+std_code )
pm.environment.set("Std_Code",std_code )

var home = pm.variables.replaceIn("{{$randomStreetAddress}}")
console.log("HOME 1: "+home )
pm.environment.set("Home",home)

var mobile = pm.variables.replaceIn("{{$randomPhoneNumberExt}}")
console.log("MOBILE No. 1: "+mobile )
pm.environment.set("Mobile",mobile)

var std_code1 = pm.variables.replaceIn("{{$randomCountryCode}}")
console.log("STD CODE 2: "+std_code1 )
pm.environment.set("Std_Code_1",std_code1 )

var home1 = pm.variables.replaceIn("{{$randomStreetAddress}}")
console.log("HOME 2: "+home1 )
pm.environment.set("Home_1",home1)

var mobile1 = pm.variables.replaceIn("{{$randomPhoneNumberExt}}")
console.log("MOBILE No. 2: "+mobile1 )
pm.environment.set("Mobile_1",mobile1)

```
**Tests Script**
```bash
var status_code = pm.response.code
if(status_code==200){
pm.test("200 ; STATUS : SUCCESS", function () {
    pm.response.to.have.status(200);
});
var jsonData = pm.response.json()
pm.test("Status Validation", function () {
    pm.expect(jsonData.status).to.eql("true");
});
pm.test("MSG Validation", function () {
    pm.expect(jsonData.msg).to.eql("Add  data success");
});
pm.t
}
else if(status_code==201){
    pm.test("201 ; STATUS : CREATED", function () {
    pm.response.to.have.status(201);
})}
else if(status_code==202){
    pm.test("202 ; STATUS : ACCEPTED", function () {
    pm.response.to.have.status(202);
})}
else if(status_code==400){
    pm.test("400 ; STATUS : BAD REQUEST", function () {
    pm.response.to.have.status(400);
})}
else if(status_code==401){
    pm.test("401 ; STATUS : UNAUTHORIZED", function () {
    pm.response.to.have.status(401);
})}
else if(status_code==402){
    pm.test("402 ; STATUS : PAYMENT REQUIRED", function () {
    pm.response.to.have.status(402);
})}
else if(status_code==403){
    pm.test("403 ; STATUS : FORBIDDEN", function () {
    pm.response.to.have.status(403);
})}
else if(status_code==404){
    pm.test("404 ; STATUS : NOT FOUND", function () {
    pm.response.to.have.status(404);
})}
else if(status_code==405){
    pm.test("405 ; STATUS : METHOD NOT ALLOWED", function () {
    pm.response.to.have.status(405);
})}
else if(status_code==500){
    pm.test("500 ; STATUS : INTERNAL SERVER ERROR", function () {
    pm.response.to.have.status(500);
})}
else if(status_code==501){
    pm.test("501 ; STATUS : NOT IMPLEMENTED", function () {
    pm.response.to.have.status(501);
})}
else if(status_code==502){
    pm.test("502 ; STATUS : BAD GATEWAY", function () {
    pm.response.to.have.status(502);
})}
else if(status_code==503){
    pm.test("503 ; STATUS : SERVICE UNAVAILABLE", function () {
    pm.response.to.have.status(503);
})}
```  

#### Get Final Student Details 
**Tests Script**
```bash

var status_code = pm.response.code
if(status_code==200){
pm.test("200 ; STATUS : SUCCESS", function () {
    pm.response.to.have.status(200);
});
var jsonData = pm.response.json()
pm.test("Validation of Language 1" ,function () {
    pm.expect(jsonData.data.TechnicalDetails[0].language[0]).to.eql(pm.environment.get("language_code_1"));
});
pm.test("Validation of Language 2" ,function () {
    pm.expect(jsonData.data.TechnicalDetails[0].language[1]).to.eql(pm.environment.get("language_code_2"));
});
pm.test("Validation of Year of Experience", function () {
    pm.expect(jsonData.data.TechnicalDetails[0].yearexp).to.eql(pm.environment.get("yearexp"));
});
pm.test("Validation of House Number", function () {
    pm.expect(jsonData.data.Address[0].Permanent_Address.House_Number).to.eql(pm.environment.get("House_Number"));
});
pm.test("Validation of City", function () {
    pm.expect(jsonData.data.Address[0].Permanent_Address.City).to.eql(pm.environment.get("City"));
});
pm.test("Validation of House Country", function () {
    pm.expect(jsonData.data.Address[0].Permanent_Address.Country).to.eql(pm.environment.get("Country"));
});
pm.test("Validation of Mobile No. 1" ,function () {
    pm.expect(jsonData.data.Address[0].Permanent_Address.PhoneNumber[0].Mobile).to.eql(pm.environment.get("Mobile"));
});
pm.test("Validation of Mobile No. 2" ,function () {
    pm.expect(jsonData.data.Address[0].Permanent_Address.PhoneNumber[1].Mobile).to.eql(pm.environment.get("Mobile_1"));
});
pm.test("Validation of Current Address" ,function () {
    pm.expect(jsonData.data.Address[0].Current_Address).to.eql(null);
});
}
else if(status_code==201){
    pm.test("201 ; STATUS : CREATED", function () {
    pm.response.to.have.status(201);
})}
else if(status_code==202){
    pm.test("202 ; STATUS : ACCEPTED", function () {
    pm.response.to.have.status(202);
})}
else if(status_code==400){
    pm.test("400 ; STATUS : BAD REQUEST", function () {
    pm.response.to.have.status(400);
})}
else if(status_code==401){
    pm.test("401 ; STATUS : UNAUTHORIZED", function () {
    pm.response.to.have.status(401);
})}
else if(status_code==402){
    pm.test("402 ; STATUS : PAYMENT REQUIRED", function () {
    pm.response.to.have.status(402);
})}
else if(status_code==403){
    pm.test("403 ; STATUS : FORBIDDEN", function () {
    pm.response.to.have.status(403);
})}
else if(status_code==404){
    pm.test("404 ; STATUS : NOT FOUND", function () {
    pm.response.to.have.status(404);
})}
else if(status_code==405){
    pm.test("405 ; STATUS : METHOD NOT ALLOWED", function () {
    pm.response.to.have.status(405);
})}
else if(status_code==500){
    pm.test("500 ; STATUS : INTERNAL SERVER ERROR", function () {
    pm.response.to.have.status(500);
})}
else if(status_code==501){
    pm.test("501 ; STATUS : NOT IMPLEMENTED", function () {
    pm.response.to.have.status(501);
})}
else if(status_code==502){
    pm.test("502 ; STATUS : BAD GATEWAY", function () {
    pm.response.to.have.status(502);
})}
else if(status_code==503){
    pm.test("503 ; STATUS : SERVICE UNAVAILABLE", function () {
    pm.response.to.have.status(503);
})}
```   

# Create Test Suites   

### Using Newman   


  Newman is a command-line Collection Runner for Postman. It enables you to run and test a Postman Collection directly from the command line.
#### Install Command    
```bash
npm install -g newman    
```
#### Run Command    
- newman run “Path/CollectionName.json” -e Path/EnvironmentName.json
- newman run “Collection Link” -e “Path”/EnvironmentName.json    

#### Create HTML Report  
 
#### Install Command      
```bash
npm install -g newman-reporter-html
```
**or**   
```bash
npm install -g newman-reporter-htmlextra    
```
#### Report Run Command      
- newman run CollectionName.json -e EnvironmentName.json -r cli,html    
**or**    
- newman run CollectionName.json -e EnvironmentName.json -r cli,htmlextra

#### Newman Report File htmlextra
 <p align="center">
  <img src="https://github.com/DiPaGh0sH/API_Testing_of_Testing-World_for_StudentDetails_using_Postman/blob/master/newman/All%20SS%20of%20Report/1.png?raw=true"/>
 <img src="https://github.com/DiPaGh0sH/API_Testing_of_Testing-World_for_StudentDetails_using_Postman/blob/master/newman/All%20SS%20of%20Report/2.png?raw=true"/>
 <img src="https://github.com/DiPaGh0sH/API_Testing_of_Testing-World_for_StudentDetails_using_Postman/blob/master/newman/All%20SS%20of%20Report/3.png?raw=true"/>
    <img src="https://github.com/DiPaGh0sH/API_Testing_of_Testing-World_for_StudentDetails_using_Postman/blob/master/newman/All%20SS%20of%20Report/6.png?raw=true"/>
    <img src="https://github.com/DiPaGh0sH/API_Testing_of_Testing-World_for_StudentDetails_using_Postman/blob/master/newman/All%20SS%20of%20Report/7.png?raw=true"/>
    <img src="https://github.com/DiPaGh0sH/API_Testing_of_Testing-World_for_StudentDetails_using_Postman/blob/master/newman/All%20SS%20of%20Report/8.png?raw=true"/>
<img src="https://github.com/DiPaGh0sH/API_Testing_of_Testing-World_for_StudentDetails_using_Postman/blob/master/newman/All%20SS%20of%20Report/9.png?raw=true"/>
<img src="https://github.com/DiPaGh0sH/API_Testing_of_Testing-World_for_StudentDetails_using_Postman/blob/master/newman/All%20SS%20of%20Report/10.png?raw=true"/>
<img src="https://github.com/DiPaGh0sH/API_Testing_of_Testing-World_for_StudentDetails_using_Postman/blob/master/newman/All%20SS%20of%20Report/11.png?raw=true"/>
<img src="https://github.com/DiPaGh0sH/API_Testing_of_Testing-World_for_StudentDetails_using_Postman/blob/master/newman/All%20SS%20of%20Report/12.png?raw=true"/>
  <img src="https://github.com/DiPaGh0sH/API_Testing_of_Testing-World_for_StudentDetails_using_Postman/blob/master/newman/All%20SS%20of%20Report/13.png?raw=true"/>
<img src="https://github.com/DiPaGh0sH/API_Testing_of_Testing-World_for_StudentDetails_using_Postman/blob/master/newman/All%20SS%20of%20Report/14.png?raw=true"/>
<img src="https://github.com/DiPaGh0sH/API_Testing_of_Testing-World_for_StudentDetails_using_Postman/blob/master/newman/All%20SS%20of%20Report/15.png?raw=true"/>
<img src="https://github.com/DiPaGh0sH/API_Testing_of_Testing-World_for_StudentDetails_using_Postman/blob/master/newman/All%20SS%20of%20Report/16.png?raw=true"/>
<img src="https://github.com/DiPaGh0sH/API_Testing_of_Testing-World_for_StudentDetails_using_Postman/blob/master/newman/All%20SS%20of%20Report/17.png?raw=true"/>
<img src="https://github.com/DiPaGh0sH/API_Testing_of_Testing-World_for_StudentDetails_using_Postman/blob/master/newman/All%20SS%20of%20Report/4.png?raw=true"/>
  <img src="https://github.com/DiPaGh0sH/API_Testing_of_Testing-World_for_StudentDetails_using_Postman/blob/master/newman/All%20SS%20of%20Report/5.png?raw=true"/></p>


