# Workshop: Fusion Triggers & Invokes

![](100/69.png)

## Trigger via business events

This lab will show how to configure ERP as an integration trigger.


## Objectives

•	Create an integration to listen for a business event in ERP

### Outline
1. Configure ERP to send business events to OIC
2. Create the integration
3. Performan the ERP business event
4. Test & monitor the integration 

## Reference

![](200/8.png)

This is also how your integration will look at the end of the walkthrough.

During the walkthrough, relevant instructions will be UNDER the picture they correlate with.

# Walkthrough

## 1.	Configure ERP to send business events to OIC

View these links from the a-team to learn how to configure ERP to send business events to OIC. 

[Using Business Events in Fusion-based SaaS with Oracle Integration Cloud - Part 1](https://blogs.oracle.com/imc/subscribe-to-business-events-in-fusion-based-saas-applications-from-oracle-integration-cloud-oic-part-1-prerequisites)

[Using Business Events in Fusion-based SaaS with Oracle Integration Cloud - Part 2](http://www.ateam-oracle.com/using-business-events-with-integration-cloud-part-2)

After doing the above configuration, you can create the connection with the adapter in OIC. 

![](200/1.png)

In OIC, select the Oracle ERP cloud adapter.


![](200/2.png)

Name your connection.


![](200/3.png)

Configure your connection details, all of these fields need to be filled out. [Further details on the fields are here.](https://docs.oracle.com/en/cloud/paas/integration-cloud-service/icser/creating-connection.html#GUID-1B92F72F-4AA8-4C2B-9E93-8F9760EEE859)



## 2. Create the integration to receive the item creation data 


Create an app driven orchestration integration. Then start the integration with your ERP connection.

![](200/4.png)

Give a name to your endpoint. 


![](200/5.png)

Configure the request page to receive busienss events from ERP cloud, then select item create event. 


![](200/6.png)

You do not need to configure a response to be received. 

![](200/7.png)

This is the summary of the item create event subscription.


![](200/13.png)

Below your ERP connection, click the plus sign and place your SOAP-CPQ connection configured in lab 100. Configure it exactly the same. 


![](200/8.png)

After doing that, your integration should look like this, open the mapper by pressing the pen button that appears after clicking the mapper. 


![](200/9.png)

This is how your mapper should appear after it is completed. See lab 100 for how to create the 'attribute(@table_name) field. For the other fields, map: 

ItemId -> ProductID
OrganizationCode -> Division
ItemNumber -> ProductName
ItemDescription -> Description
ApprovalStatusValue -> ApprovalStatus
CreationDate -> CreationDate

Lastly, don't forget to specify a field for tracking. 

## 3. Create an item in ERP 

[Watch this video to see PO creation](https://www.youtube.com/watch?v=jCUEBjNi86k)


![](200/14.png)

From the ERP homepage, navigate to the Product Information Management suite.

![](200/15.png)

Click the side bar on the right. 

![](200/16.png)

Click on create item.

![](200/17.png)

These details can vary per your use case, here we select these fields. 
![](200/18.png)

Press yes if you get this warning. 
![](200/19.png)

Enter the details for your item. 

![](200/20.png)

Save and close. This will trigger the business event that a new item was created. The information will be passed to Oracle Integration. 

## 4. Verify & monitor the integration

![](200/21.png)

On the monitoring page you should see a completed integration. 

![](200/22.png)

Clicking on the tracking shows green for each stage of the integration. 

![](200/23.png)

Viewing the activity stream allows you to view the payloads at each step. 

![](200/24.png)

The audit trails shows the actions that occured in the integration.

![](200/25.png)

Looking at the data table in CPQ, you can see the new row with our information from ERP. 

You can watch the Demo1 video to confirm that you completed the lab successfully. 


## Invoke

https://docs.oracle.com/en/cloud/saas/procurement/18b/oeswp/Purchase-Order-Service-Version-2-PurchaseOrderService-svc-3.html

https://blogs.oracle.com/cloud-infrastructure/using-terraform-to-manage-your-apis

CREATE TABLE Opportunity (
   POHeaderId VARCHAR2(255),
   OrderNumber VARCHAR2(255),
   BuyerName VARCHAR2(255),
   BuyerEmail VARCHAR2(255),
   ItemNumber VARCHAR2(255),
   ItemId VARCHAR2(255)
);

