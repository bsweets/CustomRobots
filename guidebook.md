
# Testing a Robot Parts Ordering system application
## Goal
The goal of this lab is to familiarize you with creating tests based on the provided Test Steps. You will be testing the Robot Parts Ordering system application that is already on your lab instance. 
Prepare for the Test

We will be using an app - currently under development - called "Order Tracking System". This app allows an employee to place a product order request via service catalog. It enables the purchase department to track that order and maintain a product inventory. We will write tests to validate critical use cases of this app.

## Log in to your provided instance
1. Navigate to the unique instance URL provided to you.
1. Log on with provided credentials.

## Run test suites
1. On your instance, locate and find the **Automated Test Framework->Suites** module and open it.
1. Open the **Test Suite with Several Successful Members** suite. Note the message that says "Running tests and test suites is disabled. Enable Tests and Test Suites Here". By default running the Automated Test Framework is disabled on any instance. Click the link to open the properties page.
1. Enable test suite execution and scheduled execution. Enable test debugging properties and set screenshot capture mode to **Disable for all steps**. Click **Save** at the bottom of the page.
    ![Testing Framework Properties](images/testing-properties.png)
    **Note** - in general it is good practice to enable screenshots for either all tests or failed tests. For the purposes of this lab will will disable that for both speed of execution and bandwidth reasons.

1. Click the **Run Test Suite** button.
    ![Run test suite button](images/run_test_suite.png)
1. Look at the modal window that opens. Click **Run Test Suite**.
    ![Run test suite modal](images/modal-run-test-suite.png)
1. Watch the tests as they run in the opened Client Test Runner
1. Return to the original browser window. Click the **Go To Result** button and inspect the results.
    ![Test results](images/test-results.png)
1. Navigate back to **Suites** and open the record for **Parent Suite With A Failing Child**
1. Run that and inspect the results.
1. Look at the records under **All Test Suite Results** and examine the differences between successful and failed tests.

# Test whether the Module and Menu items related to app exists or not for different roles/users
## Goal
The goal of this section is to familiarize with how to test menu item and modules visibility of an application in application navigator
### Test whether the Module and Menu items related to app exists or not for employee role
1. Create a new **Test** record. Name it "Check order tracking app menu exists". Right-click the header and **Save** the record
1. Click **Add Test Step** button. ![](images/test_form_add_test_step.png)
1. Choose **Impersonate** from the list of options. Choose "Erin Smith" and click **Submit**
1. Click **Add Test Step**. Under the **Application Navigator** category choose "Application Menu Visibility"
1. In Visible assert type select "At least these application menus are visible"
1. In Visible application select "Order Tracking System". Click **Submit"=**
1. Click **Add Test Step**. Under the **Application Navigator** category choose "Module Visibility"
1. In Visible assert type select "At least these modules are visible"
1. In Visible Modules select "Orders" and "Products" (under Application "Order Tracking System"). Click **Submit**

# Testing if employee Erin Smith can request the app's Service Catalog item
## Goal
The Goal of this section is to make sure employees can order a product using the service catalog

1. Create a new **Test** record. Name it "Check employee can order any product". Right-click the header and **Save** the record
1. Click **Add Test Step** button
1. Choose **Impersonate** from the list of options. Choose "Erin Smith" and click **Submit**
1. Click **Add Test Step**. Under the **Service Catalog** category choose "Search for a Catalog Item"
    1. Set the Search Term to "Request product"
    1. Set Catalog to "Service Catalog"
    1. Set Category to "Product Management"
    1. Set Assert Item to "Request new product"
1.  Click **Add Test Step**. Under the **Service Catalog** category choose "Open Catalog Item"
1.  Next to the Service Catalog variable, click the mapping icon and in the step reference pop-up, select "Step 2: Search for a Catalog Item." > "Catalog Item ID". Click **Submit**
1. Click **Add Test Step**. Under the **Service Catalog** category choose "Set Catalog Item Quantity"
1. In the **Quantity** field select "1". Click submit
1. Click **Add Test Step**. Under the **Service Catalog** category choose "Order Catalog Item". Select Assert type as "Successfully ordered Catalog Item"

# Testing that an order is generated after approving a request from the catalog item
## Goal
The goal of this section is to demonstrate testing a business rule that generates an Order upon request approval.

1. Click **Add Test Step** button. Choose **Impersonate** from the list of options. Choose ITIL user "Ira" and click **Submit** 
1. Click **Add Test Step**. Under the Form category select "Open an Existing Record" select Table as "Request". Use the gear icon to back reference to step 6 in the test. Keep View as its default value. Click **Submit**
1. Click **Add Test Step**. Under the Form catagory select "Field Value Validation" select Table as "Request". In the conditions field add Filter condition "Stage is Requested" and "Requested for is"  use gear icon to back reference the impersonated user in step 1
1. Click **Add Test Step** button. Choose **Impersonate** from the list of options. Choose Approver as user "Amy" and click **Submit**
1. Click **Add Test Step**. Under the Form catagory select "Open an Existing Record" select table as approval. Use the gear icon to back reference to step 11 in Record. Keep View as default. **Click Submit**
1.  Click **Add Test Step**. Under the Form catagory select "Set Field Values". Select table as Approval and select Field Values as "State" "approved". Click **Submit**
1.  Click **Add Test Step**. Under the Form catagory select "Click a UI Action". Select table as "Request" and select UI action as "Save" and Assert type as "Form Submitted to server"


# Test when item is returned the item sold history table is updated accordingly (Business Rule testing)
## Goal
The goal of this section is to make sure when an item is returned the inventory table is updated accordingly. A business rule is executed behind the scene to update the inventory table. This lab will test if business rule was executed correctly

1. Create the test
1. Run and you should see a browser console error
1. Fix browser console error
1. re-run the test

# Use a server side script to test that e-mail was successfully sent to the user with right content in the e-mail body
## Goal
The goal of this section is to familarize you with options available when you encounter client-side JavaScript error.

# Add and use custom wait step for approval. (Custom step)
## Goal
The goal of this section is to demonstrate testing a business rule.

# Add all the test created so far and schedule it
## Goal

