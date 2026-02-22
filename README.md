# BPEL Order Processing Demo - Quick Start Guide

This package contains a fully pre-configured Apache ODE BPEL engine and a SoapUI client. No coding or server configuration is required.

## Prerequisites

- Download and install the free, open-source version of SoapUI.
- You do not need to install Java; a compatible runtime is bundled in the server.

## Step 1: Start the BPEL Server

1. Extract the `apache-tomcat-9.0.115.zip` folder to your Desktop.
2. Open the unzipped folder, go into the `bin` folder, and double-click `startup.bat`.
3. A black terminal window will open. Leave this running in the background.
   - To verify it's working, go to `http://localhost:8080/ode` in your browser—you should see 1 active process.

## Step 2: Load the Mocks & Client

1. Open SoapUI.
2. Go to **File** > **Import Project** and select the three `.xml` files located in the `SoapUI_Client_Files` folder.
3. They will appear on the left side of your screen.

## Step 3: Start the Mock External Services

Our BPEL process needs to talk to external Inventory and Payment servers. We will simulate them now:

1. Double-click the grey gear icon for **InventoryBinding MockService**. A window will pop up. Click the **Green Play Button** at the top left.
2. Double-click the grey gear icon for **PaymentBinding MockService**. Click the **Green Play Button**.
   - Both services are now actively listening on port 8088.

## Step 4: Execute the Demo

1. Expand the **OrderProcessingService** project tree on the left.
2. Expand **OrderBinding** → **processOrder** and double-click **Request 1**.
3. You will see an XML payload with a Product ID, Quantity, and Credit Card ready to go.
4. Click the **Green Play Button** at the top left of this request window.
5. The BPEL engine will automatically receive the request, check the inventory mock, process the payment mock, evaluate the logic, and return `<status>Order Confirmed</status>` on your screen!
