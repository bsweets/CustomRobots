
# Testing a Custom Robots application
The goal of this lab is to familiarize you with creating tests based on the provided Test Steps. We will be using an app - currently under development - called "Custom Robots". This app allows a buyer to order robots parts via service catalog. It enables the seller to track and approve the order. We will write tests to validate critical use cases of this app.

# Exercise 1: Setup
## Exercise 1(a) Log in to your provided instance
1. Navigate to the unique instance URL provided to you.
2. Log on with provided credentials.

## Exercise 1(b) Run test suites
1. On your instance, locate and find the **Automated Test Framework->Suites** module and open it.
2. Open the **Child B** says **A test suite with only successful tests within it** suite. Note the message that says "Running tests and test suites is disabled. Enable Tests and Test Suites Here". By default running the Automated Test Framework is disabled on any instance. Click the link to open the properties page.
 ![](2018-04-23-15-10-11.png)
3. Enable test suite execution and scheduled execution. Enable test debugging properties and set screenshot capture mode to **Disable for all steps**. Click **Save** at the bottom of the page.
    ![Testing Framework Properties](2018-04-22-19-19-27.png)
    **Note** - in general it is good practice to enable screenshots for failed tests. For the purposes of this lab will will disable that for both speed of execution and bandwidth reasons.

4. Go back to Automated Test Framework-> Suites and open "Child B" test suite 
5. Click the **Run Test Suite** button.
    ![Run test suite modal](2018-04-22-18-35-14.png)
6. Click **Run Test Suites**
![](2018-04-27-18-49-16.png)

7. Watch the tests as they run in the opened Client Test Runner
8. Return to the original browser window. Click the **Go To Result** button and inspect the results.
    ![](2018-04-27-15-26-08.png)
9. Click on the record to open it
![](2018-04-27-15-27-28.png) 
10. You should see browser console error. Add it to ignore list by clicking "Add all client errors to ignored list"
![](2018-04-27-15-18-14.png)
11. Navigate to "Automated Test Framework->Suite"
12. Open the **Child B** says **Test Suite with Several Successful Members** 
13. Click the **Run Test Suite** button.

# Exercise 2: Application Navigation Testing
The goal of this section is to familiarize with how to test menu item and modules visibility of an application in application navigator
1. Click the **Tests** module
  
  ![Automated Test Framework -> Test](2018-04-22-18-38-44.png)

2. Click **New**. 

![New Button](2018-04-22-18-40-04.png)

3. In the **Name** add "Application Visibility" in the Description add "Test to see whether application Custom Robots and Module Orders are visible" 
4. Click **Save** to save the record

![Application Visibility Test](2018-04-22-18-41-47.png)

5. Click **Add Test Step** button. 

![Add Test Step](2018-04-22-18-43-14.png)

6. In the **Server** category Choose **Impersonate** from the list of options. Click **Next**

![Test Category](2018-04-22-18-45-00.png)
7. Choose "Abel Tuter" and Click **Submit** or **Update**

![Impersonate Test Step](2018-04-22-18-47-08.png)

8. Click **Add Test Step**. Under the **Application Navigator** category choose "Application Menu Visibility". Click **Next**
9. In Visible assert type select "At least these application menus are visible"
10. In Visible application select "Custom Robots". Click **Submit** or **Update**
![](2018-04-22-18-49-30.png)
11. Click **Add Test Step**. Under the **Application Navigator** category choose "Module Visibility"
12. In Visible assert type select "At least these modules are visible"
13. In Visible Modules select "Orders" Click **Submit** or **Update**
![](2018-04-22-18-50-53.png)
14. Click **Run Test** button
![](2018-04-22-18-51-52.png)
15. Click **Run Test** in the "Pick a browser" model window.
![](2018-04-22-18-53-33.png)
16. Expected Result - Test should be successful.. Click [X]
![](2018-04-27-19-00-42.png)

# Exercise 3: Service Catalog testing
## Exercise 3(a) Order Catalog Item
The Goal of this section is to make sure buyer can order parts to build custom robots using the service catalog

1. Create a new **Test** record. Name it "Order Custom Robot". Right-click the header and **Save** the record
2. Click **Add Test Step** button
3. In the **Server** category choose **Impersonate** from the list of options. Choose "Abel Tuter" and Click **Submit** or **Update**
4.  Click **Add Test Step**. In the **Service Catalog** category choose "Open Catalog Item"
5. Add "Customized Robot" using the reference 
![](2018-04-27-23-01-19.png)

6. Click **Submit** or **Update**
7. Click **Add Test Step**. Under the **Service Catalog** category choose "Set Variables Values"
     1. Select "choose_arms " as "Articulated Clamps"
     1. Select "choose_body" as "360 rotating platform"
     1. Select "choose_head" as "Floating orb with LED face"
     1. Select "choose_legs" as "Levitation Drive" and click **Submit** or **Update**

    ![](2018-04-22-19-09-13.png)

8. Click **Add Test Step**. Under the **Service Catalog** category choose "Order Catalog Item". Click **Next**
9. Select Assert type as "Successfully ordered Catalog Item" and click **Submit** or **Update**

![](2018-04-22-19-12-16.png)

10. Click **Run Test** button
11. Click **Run Test** in the "Pick a browser" model window.
12. Test should be successful.

## Exercise 3(b) : Test approval of the order
The Goal of this section is to make sure the above order goes thru the approval process

1. Go to "Automated Test Framework->Tests"
2. Click "Order Custom Robot" Test in the Test Module. 
3. Click **Copy Test** button. Change the Name to "Check for Approvals" Click **Update**

![](2018-04-23-11-31-55.png)

4. Open "Check for Approvals" test
5. Click **Add Test Step**  Under **Server** category choose **Impersonate** from the list of options. Choose "ITIL User" and click **Submit**
6. Click **Add Test Steps**. Under **Forms** category choose "Open Existing Record"
    1. In "Table" select "Request" In the "Record section"  click the bback reference icon ![](2018-04-22-15-37-05.png) map it to "Step 4" Click **Submit**
    ![](2018-04-27-23-03-30.png)
7. Click **Add Test Steps**. Under **Forms** category choose "Field Value Validation" 
    1. Select "Table" as "Request"
    1. In "Condition" dropdown select "Stage" "is" "Requested"
    1. Click "And" Button
    1. In the dropdown select "Requested for" "is" using back referencing icon map it to step 1 Click **Submit**
      ![](2018-04-24-15-13-58.png)
8. Click **Add Test Step**  Under **Server** category choose **Impersonate** from the list of options. Choose "Eric Schroeder" and click **Submit**
9. Click **Add Test Step**  Under **Server** category choose **Record Query** step
    1. Select "Table" as "Approval[sysapproval_approver]"
    1. In the condition dropdown select "Approving" "is" using the back referencing icon map it to "step 4" and click **Submit**
    ![](2018-04-24-15-06-22.png)
10. Click **Add Test Step**   Under **Forms** category choose **Open Existing Record** step
    1. Select "Table" as "Approval"
    1. In The Record using the back referencing icon map it to step 10 and click **Submit**
    ![](2018-04-24-15-10-19.png)
11. Click **Add Test Step**   Under **Forms** category choose **Set Field Values** step
    1. Select "Table" as "Approval"
    1. In "Field Value" select "State" "Approved" and click **Submit**
     ![](2018-04-24-15-08-02.png)
12. Click **Add Test Step**   Under **Forms** category choose **Click a UI Action** step
    1. Select "Table" as "Request [sc_request]"
    1. Select "UI Action" as "Save" from the reference option
    1. Select Assert type as "Form submitted to server" and click **Submit**
    ![](2018-04-24-15-12-05.png)

13. Click **Run Test** button
14. Click **Run Test** in the "Pick a browser" model window.
15. The test should bbe successful.

# Exercise 4: Business rule testing

The goal of this section is to demonstrate testing a business rule that generates an Order upon request approval. 

1. Go to "Automated Test Framework->Tests"
2. Click "Check for Approvals" Test in the Test Module. 
3. Click **Copy Test** button. Change the Name to "Order created in order table" 
4. Click **Add Test Step**. Under the **Server** category select "Record Query" 
5. In the Table option select "Order" table
6. In the condition drop down select "Show Related Fields" column. Click the drop down again select "Request Item ==> Requested Item fields"
![](2018-04-24-15-19-10.png)
7. Click the drop down again select "Request"
![](2018-04-24-15-21-38.png)
8. Select Step 4 using back reference in the condition
![](2018-04-24-15-23-21.png)
9. Click **Submit** button
10. Click **Update**
11. Click **Run Test** button
12. Click **Run Test** in the "Pick a browser" model window.
13. Test should be successful


# Exercise 5: Run Server Script 
## Goal
The goal of this section is to make sure when an item is shipped an e-mail was sent with right content in it. We will use Run Server Side script test step to test that e-mail was sent once order was shipped.

1. Navigate to "Automated Test Framework -> Test"
1. Create a new **Test** record. Name it "Check e-mail Notification". Right-click the header and **Save** the record
2. Click **Add Test Step**  Under the **Server** category choose **Impersonate** from the list of options. Choose "Abel Tuter" and click **Submit**
3. Click **Add Test Step**. Under the **Server** category choose **Record Insert** step click **Next**
      1. Select table as Order
      1. Add "Arms" as "Adaptable multi-tool arms"
      1. Add "Body" as "360 rotating platform"
      1. Add "Head" as "360º rotatable dome with accessory ports"
      1. Add "legs" as "Arachnid legs"
      1. Add "Status" as "Open"
      1. Add "Buyer" as "Abel Tuter" the screen should look like below and click **Update** or **Submit**
![](2018-04-25-16-29-08.png)

4. Click **Add Test Step**. Under the **Server** category choose **Record Update** step click **Next**
5. Using back reference select step 2 
    1. Add Field Values as "Shipped" and value as "javascript:gs.nowDateTime()".  Click **Update** or **Submit**

   ![](2018-04-25-16-30-46.png)
         **Note** We are using dynamic date on order update
6. Click **Add Test Step**. Under the **Server** category choose **Run Server Side Script** step click **Next**
7. Copy below code in the script box and click **Update** or **Submit**

```javascript

     (function(outputs, steps, stepResult, assertEqual) {
	// specify first step sys_id
	var firstStepSysId = 'a598fe3b732113003c7ceeadfff6a7c5';

	// get order from first step
	var orderId = steps(firstStepSysId).record_id;
	var order = new GlideRecord('sn_custom_robots_order');
	order.get(orderId);
    var assertOrderExists = {
          name: "assert order exists",
          shouldbe: 1,
          value: order.getRowCount(),
    };
    assertEqual(assertOrderExists);
	gs.info('found order: ' + order.sys_id);

	// get buyer's first name from order
	var user = new GlideRecord('sys_user');
	user.get(order.buyer);
    var assertUserExists = {
          name: "assert user exists",
          shouldbe: 1,
          value: user.getRowCount(),
    };
    assertEqual(assertUserExists);
	gs.info("found buyer: " + user.sys_id + ", first name: " + user.first_name);

	// wait for email to be created from business rule after order updated to shipped
	var counter = 0;
	while (counter++ < 20) {
		// check if email found
		var email = new GlideRecord('sys_email');
		email.addQuery('subject', 'LIKE', '%' + order.request_item.request + '%');
		email.query();
		if (email.next()) {
			gs.info('email body contents first 200 chars: \n' + email.body.substring(0,200));
			var assertEmailContainsBuyerFirstName = {
			name: "email body contains recipient first name",
			shouldbe: true,
			value: (email.body.indexOf(user.first_name) != -1),
			};
			assertEqual(assertEmailContainsBuyerFirstName);
			return true;
		}
		gs.sleep(1000);
	}
	// if reached here, the email wasn't sent or took longer than 20 seconds
	stepResult.setOutputMessage("Failed to find email in 20 seconds");
	return false;

})(outputs, steps, stepResult, assertEqual);
// uncomment the next line to execute this script as a jasmine test
//jasmine.getEnv().execute();
```
8. Right click "Record Insert" step in the test and copy sys_id like below
![](2018-04-27-21-53-48.png)
9. Copy the sys_id in this line "var firstStepSysId = 'a598fe3b732113003c7ceeadfff6a7c5';" 
![](2018-04-27-21-56-03.png)
10. Click **Run Test** button
11. Test should be successful

# Exercise 6: Create a new Step Configurations
## Goal
The goal of this section is to create new step config and use that step in an existing test. The Step approves the request

1. Navigate to **Automated Test Framework->Administration->Step Configurations**
 ![](2018-04-26-16-52-34.png)
2. Click **New**
3. Fill up the form as below
   1. Name as "Approve Request"
   1. Step environment as "Server-Independent"
   1. Category as "Server"
   1. Template Reminder as "Approves this request by group approver"
   1. HTML description as "Approves this request by group approver"
   1. Order as 100
![](2018-04-27-12-21-02.png)
4. In the "Description generation script" make sure you see below code if not add it
```javascript
function generateDescription() {
    // the global variable 'step' represents the current glide record
    var description = "";
	// your code here
	return description;
}
 generateDescription();
```
5. In the "Step execution script" box add following code
```javascript
(function executeStep(inputs, outputs, stepResult, timeout) {
	
	var request = new GlideRecord('sc_request');
	request.get(inputs.u_request);
	var groupApprover = new GlideRecord('sys_user');
	groupApprover.get(inputs.u_group_approver);
	
	// wait for approval to appear
	var counter = 0;
	while (counter++ < 60) {
		var approval = new GlideRecord('sysapproval_approver');
		approval.addQuery('document_id', request.sys_id);
		approval.addQuery('state', 'requested');
		approval.query();
		if (approval.next()) {
			approval.state = 'approved';
			if (approval.update()) {
				stepResult.setOutputMessage(gs.getMessage("successfully approved request '{0}' for user {1}", [request.number, groupApprover.name]));
				stepResult.setSuccess();
				return;
			} else {
				stepResult.setOutputMessage(gs.getMessage("failed to approve request '{0}' for user {1}", [request.number, groupApprover.name]));
				stepResult.setFailed();
				return;
			}
		}
		gs.sleep(1000);
	}
	stepResult.setOutputMessage("failed to find approver");
	stepResult.setFailed();
	return;
	

}(inputs, outputs, stepResult, timeout));
```
6. Click **Submit**
7. Open "Approve Request" record
8. Under related list "Input Variables" click **New**
![](2018-04-27-12-28-14.png)
9. Add
   1. Type: Reference
   1. Label: Request
   1. Column Name: u_request
   1. Under Reference Specification related list pick Reference as Request (sc_request)
   ![](2018-04-27-22-35-16.png)
10. Click **Submit** or **Update**
11. Under related list "Input Variables" click **New**
12. Create second input variable select
   1. Type: Reference
   1. Label: Group approver
   1. Name: u_group_approver
   1. Under Reference Specification:
   1. Reference: sys_user (User)
  ![](2018-04-27-22-37-36.png)
13. Click **Submit** or **Update**
**Now we will use this new step created in our test to approve the request**
14. Navigate to "Automated Test Framework -> Tests"
15. Click "Order Custom Robot" Test in the Test Module. 
16. Click **Copy Test** button. Change the Name to "Approve Order using Custom Step" 
17. Click **Add Test Step**. Under the **Server** category look for the new step added "Approve Request" 
18. Back reference to step 4 and select "Group approver" as "Eric Schroeder"
       ![](2018-04-27-12-41-56.png)
19. Click **Submit** or **Update**
20. Click **Add Test Step**. Under the **Server** category select "Record Query" Step
    1. Select table as "order" table
    1. Dot walk to "Request Item.Request" like we did in exercise 4 step 5 & 6 and back reference to step 4 and then click **Submit or Next** 
      ![](2018-04-27-12-46-22.png)
21. Click **Run Test** button
22. Click **Run Test** in the "Pick a browser" model window.
23. Test should be successful

# Exercise 7: Create and Schedule Test Suite
## Goal
1. Navigate to **Automated Test Framework->Suites** 
![](2018-04-26-16-55-52.png)
2. Click **New** 
3. Add Name as "My Lab Test Suite"
![](2018-04-27-14-45-25.png)
4. In the Related List "Test Suite Tests" Click **New**
![](2018-04-27-14-47-21.png)
5. Select  "Application Visibility" Click **Submit**
![](2018-04-27-14-48-19.png)
6. Repeat Step 4 and 5 and add below test to the suite
    1. Order Custom Robot
    1. Check e-mail Notification
    1. Check for approvals
    1. Order created in order table
    1. Approve order using custom step
    ![](2018-04-27-14-54-37.png)
7. Navigate to "Automated Test Framework ->  Schedules"
8. Click **New**
9. Add Name as "My Lab Test Schedule"
10. Click **Save**
11. Click **New**
12. Using Lookup list add "MyL ab Test Suite"
![](2018-04-27-15-05-24.png)
13. Navigate to "Automated Test Framework -> Run-> Scheduled Client Test Runner" Right Click and select "Open Link in New Tab"
14. Go back to main tab and navigate to "Automated Test Framework ->Schedules"
15. Open "My Lab Test Schedule"
16. Click **Execute Now**

*** Congratulations you have successfully completed the lab ***