# Feature File and Manual Test Scenerio Examples

#### Author: 
Created By Akash Tyagi. Reach me out at: akashdktyagi@gmail.com

---
#### Usefull links:
* [https://medium.com/javascript-scene/behavior-driven-development-bdd-and-functional-testing-62084ad7f1f2]https://medium.com/javascript-scene/behavior-driven-development-bdd-and-functional-testing-62084ad7f1f2
* [http://www.thinkcode.se/blog/2016/06/22/cucumber-antipatterns]http://www.thinkcode.se/blog/2016/06/22/cucumber-antipatterns

## Introduction: 

* Behavior Driven Development (BDD) is an agile software development practice – introduced by Dan North in 2006 – that encourages collaboration between everyone involved in developing software: developers, testers, and business representatives such as product owners or business analysts.

* BDD aims to create a shared understanding of how an application should behave by discovering new features based on concrete examples. Key examples are then formalized with natural language following a Given/When/Then structure.

* Gherkin is the most commonly used syntax for describing examples with Given/When/Then in plain text files, called feature files. Gherkin scenarios can be automated to validate the expected behavior. At this point, BDD tools – such as SpecFlow – come in handy. Automated acceptance tests, however, are an optional by-product of using BDD, not the sole purpose.

* Automated Gherkin scenarios are “green” when up-to-date and in sync with system behavior. Whenever the updated system stops producing the expected behavior, the affected scenario turns red to alert the team. This failure can be caused by new behavior that contradicts with previous requirements or the updates introducing unwanted side-effects. In any case, the team must fix this mismatch to make all scenarios green again. When the team follows this practice, Gherkin documentation grows with the system, providing an always up-to-date specification of its behavior. This is also called “Living Documentation”, here you can view an example.

* To summarize, Behavior Driven Development can be defined as follows: BDD is an agile software engineering practice that supports feature discovery and encourages collaboration among developers, testers and business participants in a software development team. BDD is facilitated through examples expressed in natural-language constructs expressing the expected system behavior, and automation validating these examples as acceptance tests.

---
### Sample Feature file and Scenarios for "Application Travel Planner Application"

* Below is the list of Sample Feature File and Scenarios. 
* These Scenarios are taken from a "Travel Planner and Sharer" application. 
* Note, these scenarios are not perfectly written but can provide some insights on how to write user stories and can be usefull to the beginners.
* These Scenarios are created by Business People to explain the functionality and feature of the application.
* And they are not Automation/Dev Ready. That is they need to be refined further and had to be re-structured to use in the Automation test Scnerio Feature file.

Few Screen shots of the application to give some perspective.

> ![Image](Screenshot%202020-11-23%20at%201.19.17%20PM.png)

> ![Image](Screenshot%202020-11-23%20at%201.19.31%20PM.png)

> ![Image](Screenshot%202020-11-23%20at%201.19.52%20PM.png)

> ![Image](Screenshot%202020-11-23%20at%201.20.00%20PM.png)

> ![Image](Screenshot%202020-11-23%20at%201.19.40%20PM.png)


#### Feature : Create a Travel Plan

```gherkin
Feature: Traveller is able to create his travel plans by adding multiple legs to his plan
This feature should implement below user stories.

# User Story - 1
Given Traveller is logged in and is at profile page: Feature - Profile Page 
When Traveller click on “Create My Travel Plan” Button
Then Traveller is able to see the “Create My Travel Plan” Page
And Traveller should be able to see ”Title” text field and enter the title for the travel plan

# User Story - 2
Given Traveller is logged in and is at profile page: Feature - Profile Page 
When Traveller click on “Create My Travel Plan” Button
Then Traveller is able to see the “Create My Travel Plan” Page
And Traveller should be able to see “Add” button
And Traveller should be able to see “Save” button
And New Travel Plan ID should be generated and displayed to the user

# User Story - 3
Given Traveller is on “Create My Travel Plan” Page
When Traveller clicks on “Add” 
Then a prompt should come up asking whether to add Travel Leg or Travel Activity

# User Story - 4
Given Traveller is on “Create My Travel Plan” Page
When Traveller clicks on “Add Travel Leg”
Then Travel Leg is added with below fields
|Traveller Names|ToLocation|FromLocation|Date|BookingStatus|BookingReferences|

# User Story - 5
Given Traveller is on “Create My Travel Plan” Page
When Traveller clicks on “Add Travel Leg”
And Traveller fills travel details for Travel Leg 1
And Traveller clicks on “Save” Button for Travel Leg 1
Then Travel Leg 1 details are saved in the DB

# User Story - 6
Given Traveller is on “Create My Travel Plan” Page
And Traveller has Travel Leg 1 details already filled and saved
When Traveller fills travel details for Travel Leg 2
And Traveller clicks on “Save” Button for Travel Leg 1
Then Travel Leg 2 details are saved in the DB
And Travel Leg 1 Details should not be modified

# User Story - 7
Given Traveller is on “Create My Travel Plan” Page
When Traveller clicks on “Add Travel Activity”
And Traveller fills travel details for Travel Activity 1
And Traveller clicks on “Save” Button for Travel Activity 1
Then Travel Activity 1 details are saved in the DB

# User Story - 8
Given Traveller is on “Create My Travel Plan” Page
And Traveller has Travel Leg 1 details already filled and saved
When Traveller fills travel details for Travel Activity 1
And Traveller clicks on “Save” Button for Travel Activity 1
Then Travel Activity 1 details are saved in the DB
And Travel Leg 1 Details should not be modified

# User Story - 9
Given Traveller is on “Create My Travel Plan” Page
When Traveller clicks on 'Add Travel Activity'
Then Activity Title shall be text field
And Activity Category shall be dropdown
And Location shall be text field
And From/To Time shall be date time field
And Cost shall be number field
And Tagging shall be tag field
And Review shall be text field
And Star shall be dropdown

# User Story - 10
Given Traveller is on “Create My Travel Plan” Page
And Traveller has Travel Leg 1 details and Travel Leg 2 details already filled and saved
And Traveller has Travel Leg 2 details already filled and saved
When Traveller wants to replace Travel Leg 2 with Travel Activity 1
Then Traveller shall click cancel button on Travel Leg 2
And Travel Leg 2 should disappear from page
And Traveller shall click Add button and select 'Add Travel Activity' button
And Travel Activty 1 shall be created
And User shall click 'Save' button
And Travel Leg 2 shall be replaced with Travel Activity 1 in DB

```
#### Feature - Edit Travel Plan
```gherkin
Feature: User is able to edit travel plan by updating details in any legs of his plan
This feature should implement below user stories.

# User Story - 1
Given Traveller is logged in
And Traveller is at profile page
When Traveller click on a Travel Plan to edit
Then Traveller is able to all the details of the Travel Plan being loaded
And editable fields are described in: Feature - Create Travel Plan Requirement 
```

#### Feature User Sign-in and Sign-Up
```gherkin
Feature - User have to sign in or sign up before being able to use features of website
Implements below user stories:

# User Story - 1
Given Traveller is not logged in
When Traveller types the URL of this system
Then Traveller will be directed to sign in/sign up page
And Traveller will have to sign in or sign up before using system features

# User Story - 2
Given Traveller is not logged in
And Traveller has not signed up
When Traveller lands on sign in/sign up page
Then Traveller will click on sign up link
And Traveller will email, username, address on sign up page 

# User Story - 3
Given Traveller is not logged in
And Traveller has not signed up
When Traveller enters sign up details
Then Traveller will receive confirmation email

# User Story - 4
Given Traveller is not logged in
And Traveller has signed up
When Traveller enters user name and password
Then Traveller will be directed to profile page as described in Feature - Profile Page 
```

#### Feature - Profile Page
```gherkin
Feature: After Feature - Sign In/Sign Up is done, user is redirected here
Implements below user stories:

# User Story - 1
Given Traveller is logged in
When Traveller lands on this page
Then Traveller will be able see three things:
'Create Travel Plan' button
'Travel Plan Assistant' button 
Edit Travel Plans table with list of all Travel Plans belonging to user

# User Story - 2
Given Traveller is logged in
And Traveller wants to create a travel plan manually
When Traveller clicks on Create Travel Plan button 
Then Traveller will be redirected to following feature: Feature - Create Travel Plan Requirement 

# User Story - 3
Given Traveller is logged in
And Traveller wants to use automated travel plan builder
When Traveller clicks on 'Travel Plan Assistant' button 
Then Traveller will be redirected to following feature: Feature - Input Parameters for Automated Travel Building 

# User Story - 4
Given Traveller is logged in
And Traveller wants to edit existing travel plan
When Traveller clicks on travel plan in travel plan table
Then Traveller will be redirected to following feature: Feature - Edit Travel Plan 
```

#### Feature: Automated Travel Plan Generator Feature

```gherkin
Feature: When User wants to use automated travel builder, user will input desired parameters

As a part of this ticket, only below attributes are to be included:
For Input
Country Preference
Category Preference
Tagging Preferences
Cost for Whole Trip
Start Date and End Date
Keywords to search for (Description)
Below are User Stories:

# User Story - 1
Given Traveller is logged in and is at profile page: Feature - Profile Page
When Traveller click on “Travel Plan Assistant” Button
Then Traveller is able to see the “Travel Plan Assistant” Page
And Traveller should be able to see "Generate Plan” button

# User Story - 2
Given Traveller is logged in and is at profile page: Feature - Profile Page
When Traveller click on “Travel Plan Assistant” Button
Then Traveller is able to see the “Travel Plan Assistant” Page
And Country Preference shall be dropdown
And Category Preference shall be dropdown
And Tagging Preference shall be tagging
And Cost for Whole Trip shall be number field
And Start/End date shall be date fields

# User Story - 3
Given Traveller is at “Travel Plan Assistant” page
When Traveller enters all the preferences
Then Traveller shall click on “Generate Plan” button
And Traveller will see a message saying: “Your Plan is being generated. You will see it in profile page”
And Traveller will see a link to go to profile page

# User Story - 4
Given Traveller is at “Travel Plan Assistant” page
When Traveller click on “Generate Plan” button
Then the Plan shall also be generated from external data
```

#### Feature - Automated Travel Building Publish

```gherkin
Feature: After user inputs parameters: Feature - Input Parameters for Automated Travel Building , system will publish a suggested plan to user profile page
Note: More than one plan can be generated
Below are the User Stories:

# User Story - 1
Given Traveller has clicked on “Generate Plan” button
When Traveller goes back to profile page: Feature - Profile Page 
Then Traveller is able to see the system generated Plans in “Edit Travel Plans” table
And Traveller should be able to click on the Plan and go into it to further customize

# User Story - 2
Given Traveller has clicked on “Generate Plan” button
When Traveller goes back to profile page: Feature - Profile Page 
Then Traveller is able to see the system generated Plans with title format: “Generated plan at time (insert timestamp)”
And Traveller should be able to click on the Plan and go into it to further customize

# User Story - 3
Given Traveller has clicked on system Generated Plan with title format: “Generated plan at time (insert timestamp)”
When Traveller goes into the page
Then Traveller will see details of plan just like in: Feature - Create Travel Plan Requirement 
And Traveller will also see a text: "Generated by System with parameters" + (insert all parameters). This text will be at the top of the Plan.
```