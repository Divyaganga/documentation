---
title : Salesforce Service Cloud
sidebar_label : Salesforce Service Cloud
---

## 1. Scope of Integration

Yellow.ai Integration with Salesforce CRM allows you to seamlessly connect your Salesforce CRM instance with yellow.ai platform. Any customer who has a Salesforce CRM account will be able to seamlessly connect their Salesforce instance with yellow.ai using oAuth. This connector enables users to receive events for Salesforce objects, both system defined and custom objects. Furthermore, this connector with enable you to take actions, such as create, update etc. on the objects.

> **Supported Version**
This integration will support the latest version releases, latest one being 52.0

## 2. Use-cases

Following are the use-cases which are currently accommodated in this Integration:

### 2.1 Integration with oAuth 2.0

Yellow.ai does not store the client’s credentials and leverages oAuth 2.0 approach for integrating with client’s Salesforce account.
​
While integrating, yellow.ai navigates the user to the login page of Salesforce, i.e. login.salesforce.com or to the subdomain which was already used in the same browser. If you want to integrate in some other instance, clear your cookies and retry login in from yellow.ai platform.

### 2.2 Take actions with Salesforce Nodes

- You can store a new record or store data in any of your custom objects. 
- The actions are not limited to the system defined Salesforce Objects, you can also use Custom Objects. 
- Functionalities to update and search for records using a particular parameter is also available.

![](https://cdn.yellowmessenger.com/BeijaEmjIOPY1659940145073.png)

- On-click of the Salesforce CRM node, you can customize the object and action type along with the attributes that you wish to pass.

![](https://cdn.yellowmessenger.com/H7KDA72IA3iB1659940427212.png)

![](https://cdn.yellowmessenger.com/pBD9bJOeipap1659940497555.png)

![](https://cdn.yellowmessenger.com/rrvyShcKtbKe1659940554939.png)

### 2.3 Receive Events from Salesforce

This feature is coming soon to the platform...

## 3. Configuration

Configuring the integration with Salesforce CRM is straightforward. Follow the steps defined below to integrate:

### 3.1 Navigate to Integrations Tab

- Inside your project, navigate to the **Configuration** tab. 
-  Click the **Integrations** Tab. 
-  Search for **Salesforce CRM**.
​
![](https://i.imgur.com/E9LZ68M.png)

Click [here](https://www.youtube.com/watch?v=_Sp4bzTpjMI) to learn more.

### 3.2 Connect to the Salesforce account

- Click **Connect** and select **Connect with Salesforce**. 
- You will be prompted to login to your Salesforce account.

![](https://i.imgur.com/2ucDsE7.gif)

Voila! You are now connected with your Salesforce account.


For more information, click [here](https://developer.salesforce.com/docs/atlas.en-us.api_rest.meta/api_rest/api_rest_eol.htm).