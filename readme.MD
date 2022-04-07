#Salesforce Developer Test

###### Soublox Development Team

---

**Objective**
The objective of this test is to check your ability to use all Salesforce techniques to solve problems, keep in mind that you can do this test in phases, but you can't skip the current step jump to the next, because the next will depend on the information you have previously finished.

To complete this test you need to:

```
[ ] Create a new Salesforce Developer Org
[ ] Allow all internet IP Range for System Admin Profile: From 0.0.0.0 to 255.255.255.255
[ ] Provide us the Username and Password when you finish the test
[ ] Create a fork of this repository and add all resources created to complete this test inside the repository
```

**_Aditional Information_**
We expected you will need at least 16 hours to complete this test, so keep it in mind before telling us when you have the intention to finish it.

---

####Use Case
The users from Bloxer Comporaton LLC want to have all holidays from the current year and store these holidays inside the custom objects. The Holidays data will be imported from a Webservice.
The user expects a Job that will be scheduled to run once a year, every first day of the year.
When a Task was created inside the Salesforce, the user expects a checkbox that will automatically indicate if the date selected is a holiday or not.
The users expect to see the next holiday on Home when they login to Salesforce

---

###Step 1
Create custom objects to store all holidays.

```
    Name: National Holidays
    API: National_Holidays
```

With fields:

```
    Field Name: Date
    Field Type: Date

    Field Name: Type
    Field Type: Picklist
    Options: "National" and "Local"
```

Keep in mind, that a good page Layout is always nice to have!

---

###Step 2
Now that you already have your custom object, take a look at the documentation provided below and create the Apex Class to connect to this job and return the data, your Apex Class needs to receive the Year as a parameter and inject it inside the Request Url

```
    https://brasilapi.com.br/docs#tag/Feriados-Nacionais/paths/~1feriados~1v1~1{ano}/get
```

The result of the web service indicated above will return a List of Map<String, Object>
And don't forget to create the Test Class, when we have integration is always a good job to test all return scenarios, remember to test the error code as well (404, 500) that is indicated on the documentation above.

---

###Step 3
Now let's take a look at the Scheduled Job, remember it must need to be prepared to run once a year, on the first day of the Year. Your job will consume the Apex Class you have been created in step 2, and populate the custom object you have created in step 1.

---

###Step 4
Inside the Task Object create a new field:

```
    Field Name: Is Holiday
    Type: Checkbox
```

---

###Step 5
Create a Trigger or a Flow to search for the Date of the Task Date and flag the checkbox if the date of the Task is indicated as a Holiday on the Custom Object **National Holiday**.

---

###Step 6
Create a Lightning Web Component that will show the Date, Name, and Type of the Next holiday and how many days until the holiday, like:

```
    The Next Holiday is {Name} and it will be on {date} and we have {x} day's until it
```

If the current date is the same date as the holiday, you need to show like:

```
    Enjoy your {name} holiday!
```

---

###Final Checklist
Here is a final checklist you can use to double-check all the steps we are expecting as the result of this test

```
[ ] Create a new Fresh Org
[ ] Grant access to all IPv4 from 0.0.0.0 to 255.255.255.255
[ ] Create a custom Object and fields indicated in step 1
[ ] Create the Apex Class to connect to the web service
[ ] Create the Test Class to cover all your Apex Class
[ ] Create a Mock to simulate all kinds of results (200, 404, 500)
[ ] Create a ScheduledApex Job to run once a year
[ ] Create the Test class for your ScheduledApex Job
[ ] Create the fields indicated in step 4
[ ] Create the Trigger or Flow for step 5
[ ] Create the Test Class for step 5 if applicable
[ ] Create the LWC component proposal in step 6
[ ] Commit and push everything you created on this project to Git
[ ] Submit the Git URL and the Username and Password of the Org to the HR team
```
