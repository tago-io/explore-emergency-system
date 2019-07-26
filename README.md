# Emergency System
Receive alerts and get directions to the people who need help. What you will learn:
- How to use payload parser
- Generate reports
- Send  notifications and emails

## Asset Tracking requirements
To implement this application you need some items already working in your TagoIO account. If you do not have some item in the following list, please set this item up and get back to this doc. Check the list bellow:

- Device with geolocation already configured and bucket also created on TagoIO platform 🌎
- Devices used in this application must have geolocation and a help button

Short list isn't it? This application seems complicated but it's not that much! Now, let's begin the implementation. In just some minutes, everything will be up and running in your TagoIO account! First things first, let's divide the implementation in some steps:

- Dashboard duplication
- Analysis creation
- Action creation
- Tile widgets configuration
- Report configuration

Let's follow up the list in that order so, starting with the dashboard duplication.

## Dashboard Duplication 
In the explore option in TagoIO sidebar, you will see the Emergency System example, click in the 'Get this Dashboard' button. When you do this, the emergency system dashboard will go into your account and a request to associate your devices will appear like the image bellow:

IMAGE HERE IMAGE HERE IMAGE HERE IMAGE HERE

Just type in the name of the device you want to use in your asset tracking application. After that, all the widgets will already be using the correct device and ready to receive your data!

## Analysis creation
To setup this application you need to create two analysis: Notification Validation, Generate Reports and Emergency System analysis. Let's start with Notification Validation. 

### Notification validation analysis
In your account, add an analysis with your name preference and configure the environment variables with your master device's token. Copy the code from the assetLocation.js script here in Github and paste it in your analysis, save it. Now, just link this analysis with the input form in Alerts tab, like the following image:

IMAGE HERE

### Generate reports analysis
To create this analysis you need to follow the process bellow:
- Add a new analysis and name it as you want.
- Type your account and device tokens in the environment variables.
- Copy the code from generateReport.js script here in Github and paste it in your analysis.
- Link this analysis to the input form in Reports tab

Remember to enter the correct variable names in the environment variables settings:

IMAGE HERE

### Emergency System analysis
Emergency System analysis is the core of this application, it's where the notifications will be sent and the data used in reports will be inserted. To create this analysis you need to insert the environment variables as the image bellow:

IMAGE HERE

After that, get the code from emergencySystem.js available in Github and paste it in your analysis. With everything done, you should have the analyzes working. Now, let's create an action to run our assetLocation analysis.
