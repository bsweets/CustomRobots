# Lab Guide - CCW0604 – Getting Started with ServiceNow Automated Testing Framework

By: Shrity Verma & Joel Fisher

# Testing a Form
## Goal
The goal of this lab is to familiarize you with creating tests based on the provided Test Steps. You will be testing the Media Library application that is already on your lab instance. 
Prepare for the Test 
1.	Create a new user called "Media Library Test User".
2.	Add all of the roles needed for the application (begin with 'x_snc_media') 
3.	Change your application

### Write your First Test 
1.	Create a new **Test** record. Name it "Media Form Test". Right-click the header and **Save** the record.
2.	Click **Add Test Step** button. <insert image>
3.  Choose **Impersonate** from the list of options. Choose "Media Library Test User" and Submit. 
4.  Add another **Test Step**. Under the **Form** section choose "Open a New Form". Choose "Media" as the table then **Submit** the record. 
5.	Add another Test Step. Also under Form choose "Field State Validation". Under "Visible" add "Creator", "Title" and "Type" to the slushbucket. Under "Mandatory" add "Title". Under "Not Mandatory" add Test"Creator" and "Type". **Submit** the record. 
6.	Click the **Run Test** button. Examine the results after the run. Did the Test pass or not? Did this match your expectations? Why or why not? 

# Trouble shooting failure
## Goal
The goal of this lab is to familiarize you on what to do when test fails. 

# Testing a Service Catalog
## Goal
The goal of this lab is to familiarize you on how to test a service catalog. 

# Testing Left Navigator
## Goal
The goal of this lab is to familiarize you on how to test Left navigation. 

# Managing Clide side JavaScript errors
## Goal
The goal of this lab is to familarize you with options available when you encounter client side Java script error.

# Testing a business rule
## Goal
The goal of this lab is to familiarize you on how to test a business rule.

# Creating a custom ATF test
## Goal
The goal of this lab is to familiarize you with how to create custom ATF server side step

# Using Server side script
## Goal
The goal of this lab is to familiarize you on how to use this framework to create tests using scripts

# Create a Test Suite and Schedule it
## Goal
The goal of this lab is to create a test suite with all the tests created in this lab and schedule the tests


