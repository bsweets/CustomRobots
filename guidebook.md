# Lab Guide - CCW0604 – Getting Started with ServiceNow Automated Testing Framework

By: Shrity Verma & Joel Fischer

# Testing an order processing application
## Goal
The goal of this lab is to familiarize you with creating tests based on the provided Test Steps. You will be testing the Order processing system application that is already on your lab instance. 
Prepare for the Test

We will be using an app, which is under developemnet, called Order Tracking System. This app allows an employee to place a product order request from the company store. Allow the purchase department to track that order and maintain an inventory. We will write tests to validate the configuration of this app.

# Test whether the Module and Menu items related to app exists or not for different roles/users
## Goal
The goal of this lab is to make you familiarize with how to test menu item and modules visibility of an application in left Navigator
### Test whether the Module and Menu items related to app exists or not for employee role
1. Create a new **Test** record. Name it "Check order traking menu item exists". Right-click the header and **Save** the record.
1. Click **Add Test Step** button. ![](images/test_form_add_test_step.png)
1. Choose **Impersonate** from the list of options. Choose "Erin Smith" and click **Submit**.
1. Click **Add Test Step**. Under the **Application Navigator** section choose "Application Menu Visibility". 
1. In visible assert type select "At least these application menuss are visible".
1. In Visible application select "Order Tracking System". Click **Submit"=**
1. Click **Add Test Step**. Under the **Application Navigator** section choose "Module Visibility". 
1. In visible assert type select "At least these modules are visible".
1. In Visible Modules select "Orders" and "Products" (under Application "Order Tracking System"). Click **Submit**

<!-- ### Test whether the Module and Menu items related to app exists or not for purchase department role
1.  Create a new **Test** record. Name it "Check order traking menu item exists". Right-click the header and **Save** the record.
2.	Click **Add Test Step** button. 
3.  Choose **Impersonate** from the list of options. Choose "Paul Anderson" and click **Submit**. 
4.  Click **Add Test Step**. Under the **Application Navigator** section choose "Application Visibility". 
5.  In visible assert type select "At least these applications are visible".
6.  In Visible application select "Order processing system". Click **Submit"=**
7.  Click **Add Test Step**. Under the **Application Navigator** section choose "Module Visibility". 
8.  In visible assert type select "At least these modules are visible".
9. TODO: [select app modules]
10.  In Visible Modules select "Order" and "Returns". Click **Submit** -->

# Testing if employee Erin Smith can order a Product request item using the Service Catalog
## Goal
The Goal of this lab is to make sure employees can order the Product request item using a service catalog

1. Create a new **Test** record. Name it "Check employee can order product". Right-click the header and **Save** the record.
1. Click **Add Test Step** button. 
1. Choose **Impersonate** from the list of options. Choose "Erin Smith" and click **Submit**. 
1. Click **Add Test Step**. Under the **Service Catalog** section choose "Search for a Catalog Item".
    1. Set the Search Term to "Request product"
    1. Set Catalog to "Service Catalog"
    1. Set Category to "Product Management"
    1. Set Assert Item to "Request new product"
1.  Click **Add Test Step**. Under the **Service Catalog** section choose "Open Catalog Item".
1.  Next to the Service Catalog variable, click the mapping icon and in the step reference pop-up, select "Step 2: Search for a Catalog Item." > "Catalog Item ID". Click **Submit**
<!-- 1.  Click **Add Test Step**. Under the **Service Catalog** section choose "Set Variable Values".
1.  Select carrier as "AT&T Mobility", Color as "Slate",...... click submit -->
1. Click **Add Test Step**. Under the **Service Catalog** section choose "Set Catalog Item Quantity".
1. In the **Quantity** field select "1". Click submit
1. Click **Add Test Step**. Under the **Service Catalog** section choose "Order Catalog Item". Select Assert type as "Successfully ordered Catalog Item"

### Goal: assert business rule generated an Order

1. Click **Add Test Step** button. Choose **Impersonate** from the list of options. Choose ITIL user "Ira" and click **Submit**. 
1. Click **Add Test Step**. Under the Form category select "Open an Existing Record" select Table as "Request". Use the gear icon to back reference to step 6 in Record. Keep View as default. Click Submit
1. Click **Add Test Step**. Under the Form catagory select "Field Value Validation" select Table as "Request". In the conditions field add Filter condition "Stage is Requested" and "Requested for is"  use gear icon to back reference the impersonated user in step 1
1. Click **Add Test Step** button. Choose **Impersonate** from the list of options. Choose Approver as user "Amy" and click **Submit**. 
1. Click **Add Test Step**. Under the Form catagory select "Open an Existing Record" select table as approval. Use the gear icon to back reference to step 11 in Record. Keep View as default. Click Submit
1.  Click **Add Test Step**. Under the Form catagory select "Set Field Values". Select table as Approval and select Field Values as "State" "approved". Click **Submit**
1.  Click **Add Test Step**. Under the Form catagory select "Click a UI Action". Select table as "Request" and select UI action as "Save" and Assert type as "Form Submitted to server"


# Test when item is returned the item sold history table is updated accordingly (Business Rule testing)
## Goal
The goal of this lab is to make sure when an item is returned the inventory table is updated accordingly. A business rule is executed behind the scene to update the inventory table. This lab will test if business rule was executed correctly

### Create the test
### Run and you should see a browser console error
### Fix browser console error
### re-run the test

# Use a server side script to test that e-mail was successfully sent to the user with right content in the e-mail body
## Goal
The goal of this lab is to familarize you with options available when you encounter client JavaScript error.

# Add and use custom wait step for approval. (Custom step)
## Goal
The goal of this lab is to familiarize you on how to test a business rule.

# Add all the test created so far and schedule it
## Goal

