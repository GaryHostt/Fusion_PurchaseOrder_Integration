# Workshop: Fusion & Purchase orders with Oracle Integration

![](100/69.png)

How to receive business events from Fusion and create purchase orders with OIC. 

## Objectives

This lab will show how to configure ERP as an integration trigger with the ERP adapter, and how to invoke it.

### Outline
1. Configure ERP to send business events to OIC
2. Create an apiary mock endpoint
3. Create the integration
4. Performan the ERP business event
5. Test & monitor the integration 

## Reference

![](screenshots/200/8.png)

This is also how your integration will look at the end of the walkthrough.

During the walkthrough, relevant instructions will be UNDER the picture they correlate with.

## Trigger Walkthrough

### 1.	Configure ERP to send business events to OIC

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

### 2. Create the apiary mock endpoint

![](100/71.png)

After copying the apiary blue print at the bottom of this lab, you can get your base URL from the location in the screenshot above.


### 3. Create the integration to receive the PO data upon creation

Create an app driven orchestration integration. Then start the integration with your ERP connection.

### 4. Create a PO in ERP 

### 5. Verify & monitor the integration on OIC & Apiary

[Watch this video to see PO creation](https://www.youtube.com/watch?v=jCUEBjNi86k)

## Invoke

[This is the SOAP endpoint we will be using](https://docs.oracle.com/en/cloud/saas/procurement/18b/oeswp/Purchase-Order-Service-Version-2-PurchaseOrderService-svc-3.html)

## Apiary blueprint

# Further work

[Creating POs with VBCS](http://niallcblogs.blogspot.com/2019/03/695-oic-subscribing-to-fusion-erp.html)

[Using a Digital Assistant Custom skill to create a PO](https://github.com/oracle/bots-node-sdk)

```
FORMAT: 1A
HOST: https://polls.apiblueprint.org/

# PO_Creation

This is a simple API allowing the receiving of PO fields from Fusion ERP.

## Questions Collection [/purchaseOrders]

### Post a PO [POST]

You may create your own question using this action. It takes a JSON
object containing a question and a collection of answers in the
form of choices.

+ Request (application/json)

        {
            "OrderNumber": "12345",
            "POHeaderId": 1234,
            "ProcurementBusinessUnit":"12345",
            "BuyerEmail":"email@email.com"
        }

+ Response 201 (application/json)

    + Headers

            Location: /PO/2

    + Body

            {"status":"success"}

```


