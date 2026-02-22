# BPEL Order Processing Demo - Quick Start Guide

This package contains a fully portable Apache ODE BPEL engine and a SoapUI client. Everything is pre-configured, and a compatible Java runtime is embedded in the server so no installation or coding is required on your end.

## Prerequisites

- Download and install the free, open-source version of SoapUI.

## Step 1: Download the Files

1. Go to the BPEL Order Processing Demo Google Drive folder: https://drive.google.com/drive/folders/1uWMTYmK0XS-tDe5C4dyCiWGO2zgKErUP?usp=sharing
2. Download both zip files: `apache-tomcat-9.0.115.zip` and `SoapUI_Client_Files.zip`.
3. Extract both zip files to your Desktop.

## Step 2: Start the BPEL Server

1. Open the extracted `apache-tomcat-9.0.115` folder.
2. Go into the `bin` folder and double-click `startup.bat`.
3. A black terminal window will open. Leave this running in the background.
   - To verify the server is running, open a web browser and go to `http://localhost:8080/ode` — you should see "1 active process" listed.

## Step 3: Load the Client & Mocks in SoapUI

1. Open SoapUI.
2. Go to **File** > **Import Project** (or press **Ctrl+I**).
3. Navigate to your extracted `SoapUI_Client_Files` folder and import the three `.xml` projects one by one. They will appear in the left-hand navigation panel.

## Step 4: Start the Mock External Services

Our BPEL process orchestrates two external Web services (Inventory and Payment). We need to turn on our simulated versions of them:

1. In the left panel, double-click the grey gear icon for **InventoryBinding MockService**. A new window will pop up. Click the **Green Play Button** at the top left of that window.
2. Double-click the grey gear icon for **PaymentBinding MockService**. Click the **Green Play Button** in its window.
   - Both services are now actively running and listening on port 8088.

## Step 5: Execute the Demo

1. In the left panel, expand the **OrderProcessingService** project tree.
2. Expand **OrderBinding** → **processOrder** and double-click **Request 1**.
3. You will see an XML payload pre-filled with a Product ID, Quantity, and Credit Card.
4. Click the **Green Play Button** at the top left of the request window.
5. The BPEL engine will automatically receive the request, invoke the inventory mock, process the payment mock, evaluate the workflow logic, and return `<status>Order Confirmed</status>` on the right side of your screen!
