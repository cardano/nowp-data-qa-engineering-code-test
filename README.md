# NOW: Pensions Data QA Engineering Code Test

### Instructions
For questions 1-2 you are free to choose Python 3.x or Java 11.

* Do not use any third party dependencies except PyTest for Python, and JUnit/Hamcrest for Java.
* If using Java, please use Java 11 and the included build.gradle
* Code should be covered with adequate tests
* Code should be readable and clean
* For question 3 please provide a .sql file with your queries inside. Please state which SQL dialect you used.
* For question 4 please provide a text file containing your answer. If you would like to include a diagram, please scan/take a photo of it and reference the image file in your submission.
* For question 5 please include one or more .feature files in the directory ./question-5
* Please submit your answers as a ZIP file.

### Question 1: 
Implement a function that takes three lists of strings as parameters. The first argument is a list of words that can be used as a subject in a sentence, the second – as a predicate, and the third – as an object. The function must return a string that contains all the sentences in the alphabetical order that can be constructed using the provided subjects, predicates and objects. (Note that the words in the list of subjects are not necessarily in the alphabetical order, and the same applies to the lists of predicates and objects.) Each sentence must be ended by ”.” and the sentences must be separated by ” ”. (Alphabetical order has usual and common meaning, but if you have doubts about it, see test cases below for examples.)

#### Indicative test cases (Python):

``` python 
assert generate_sentences(["Mark", "Mary"], ["hates", "loves"], ["apples", "bananas"])) == "Mark hates apples. Mark hates bananas. Mark loves apples. Mark loves bananas. Mary hates apples. Mary hates bananas. Mary loves apples. Mary loves bananas."
```

``` python
assert generate_sentences(["Vlad", "John"], ["drives"], ["car", "motorcycle", "bus"])) == "John drives bus. John drives car. John drives motorcycle. Vlad drives bus. Vlad drives car. Vlad drives motorcycle."
```

#### Indicative test cases (Java 11):

``` java
assertThat(generateSentences(List.of("Mark", "Mary"), List.of("hates", "loves"), List.of("apples", "bananas")), is("Mark loves apples. Mark loves bananas. Mary hates apples. Mary hates bananas. Mary loves apples. Mary loves bananas."));
```

``` java
assertThat(generateSentences(List.of("Vlad", "John"), List.of("drives"), List.of("car", "motorcycle", "bus")), is( "John drives bus. John drives car. John drives motorcycle. Vlad drives bus. Vlad drives car. Vlad drives motorcycle."));
```

### Question 2: 
Implement a class Airplane that keeps track of the following features of an airplane:

* consumption: an integer representing number of litres consumed per km of distance
* position (x, y): a pair of integers representing a position of the plane on a map. Can be a tuple if chosen language supports tuples (assume that the airplane can only be in one of the positions of the 1 km x 1 km grid)
* fuel level: a floating point number representing the current fuel level in litres

##### Implement the following methods:

* `constructor`: takes four integer parameters (in the specified sequence) `initX, initY, consuption and initial fuel level` where initX/initY represents initial location of the plane, cons represents the consumption (litre/km) and initial fuel level represents the initial fuel level.

* `goto`: takes two integer parameters X and Y representing the location where the plane needs to go to. If the airplane has enough fuel to travel there from its current location, the method moves it there, updates remaining fuel level, and returns True. Otherwise, the plain does not move and False is returned.

* `refuel`: takes one integer parameter indicating how many litres of fuel are added. No value returned.

Assume that the airplane travels in a direct line between two positions (X1, Y1) and
(X2, Y2). The distance between two locations is computed as the square root of ((X2 − X1)^2 + (Y 2 − Y 1)^2)


### Question 3: 
Consider the following relational database tables to store information about athletes and their birthplaces.

#### City

|city_id|city_name|city_country|city_population|city_hemisphere|
|:-----:|:-------:|:----------:|:-------------:|:-------------:|
|1      |Sao Paulo| Brazil| 12110000| S|
|2      |Toronto |Canada |2732000| N|

#### Athletes

|athlete_id|athlete_first_name|athlete_last_name|athlete_birthplace|athlete_sex|
|:--------:|:----------------:|:---------------:|:----------------:|:---------:|
|1 |Neymar |Silva| 1| M|
|2 |Natalie |Spooner |2| F|

##### Table “City” description: 
“city_id” is primary key and numeric,
“city_population” is numeric, while “city_name”, “city_country” and
“city_hemisphere” are text fields.

##### Table “Athletes” description: 
“athlete_id” is primary key and numeric,
“athlete_birthplace” is numeric, while “athletes_first_name”,
“athletes_last_name”, “athletes_sex” are text fields. The
“athlete_birthplace” is a foreign key and references the “city_id” field
of the “City” table.

#### Give SQL statements for the following:
a. Insert a new city to include, id: 3, name: Tokyo, Country: Japan, Population: 9,2 million, Hemisphere: North.

b. Update Tokyo population to 9,73 million.

c. Query the city table for the cities in the northern hemispher and with population greater than 10 million.

d. Query the city table for the sum of the populations of cities in the northern hemisphere.

e. Query for athletes first name, last name and birth place.

f. Query for all athletes who were born in the southern hemisphere. 

g. Query for female athletes born in a city with population over 5 million.

h. Query for the athlete born in a city that has the highestpopulation.

### Question 4:

Consider the following scenario:

You have joined a company as a test automation consultant for a system at ACME Finance plc. Currently all testing that is conducted is manual. You have been tasked with automating as much of the testing as possible.

The system under test is used to measure the quality of the data within the organisation. It takes change tracking data from the Data Warehouse as an input. A batch process (built in Java with Spring Batch) runs on a daily basis, overnight to capture the changes, and measure the quality of the data using a series of rules, implemented in Java. The rules yield a set of errors and warnings for each field that breeches a rule, and persists these exceptions in a database. The data in said database is surfaced in a dashboard for people business users to examine.

Prepare a report to advise the client how an automated test solution could be implemented to provide rapid feedback and regression testing of the system detailed above.

**Please consider:**
* Approach and strategy
* Technologies utilised
* Techniques used
* Additional questions you would need to ask

### Question 5

Consider the following scenario:

The Data Governanace Manager has approached you, and asked you to prepare some requirements in BDD/Cucumber format for the following set of validation rules:

A payroll file is comprised of the following fields:
First Name (String, maximum of 20 characters, required, only a-z)
Last Name (String, maximum of 20 characters, required, only a-z, - and ' ')
Date of Birth (Date, format DD/MM/YYYY, required, can't be in the future, member must be 16 but less than 92 years old)
National insurance number (String, maximum of x characters, must start with x or y or z)
Gross pay (Money, must be positive, required, can't be more than contribution amount)
Contribution amount (Money, must be positive, required, can't be more more than gross pay)

Write a set of BDD scenarios/requirements for the above scenario.

Please submit your answer as a set of .feature files, broken down/grouped as you see fit.
