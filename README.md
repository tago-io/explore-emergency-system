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
- Payload parser creation
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

Remember to enter the correct variable keys and values in the environment variables settings:


| Variable Key  | Variable Value         |
| ------------- |:-------------:         |
| device_token  | Use your master device token  |
| account_token | Use your account token |

### Emergency System analysis
Emergency System analysis is the core of this application, it's where the notifications will be sent and the data used in reports will be inserted. To create this analysis you need to insert the environment variables as the table bellow:

| Variable Key  | Variable Value         |
| ------------- |:-------------:         |
| device_token  | Use your master device token  |
| account_token | Use your account token |

After that, get the code from emergencySystem.js available in Github and paste it in your analysis. With everything done, you should have the analyzes working. Now, let's create an action to run our assetLocation analysis.

### Action creation
Now, we need to run an analysis everytime we receive location data, this requires an action. Actions are ways to run analyzes, send alerts and do other things everytime something we are tracking happens. You can check more about actions in [here](https://tago.elevio.help/en/articles/30).
To this application, we need to run the emergency system everytime someone needs help, currently to do that you need to create one action for each device that will be monitored. So, if you want to scale this application to 5 devices you will need to create 5 action, simple like that. The action you need to create follows a pattern and you just need to reply it to the number of devices you want. In this action we will need to run the Emergency System analysis everytime help variable is equal to 1. 

- General Information tab
  - Action to be taken: Run analysis
  - Run the analysis: Emergency System
- Trigger tab
  - Variable: Help
  - Condition: Equal to
  - Type: Number
  - Value: 1
  - Lock trigger after action is taken: No

The list above is the pattern you need to follow while creating the actions. If you gave different names to you analyzes or variables don't forget to use your names.

### Parser Payload
One thing we want to have in our application is the icons in maps will be set with a red color if someone is in dangerous. It needs to be fast. Also, we don't want to create analyzes or actions to such a simple process. So, we will use a payload parser. This is the best way to parse data and is a powerful tool you should use. To use a payload parser, you will need to run a custom payload parser in your device. To implement the payload parser, go to the device you want to use, after that go to Payload Parser tab. In this tab set the option "Run your own parser" as true, and paste the code from parser.js available here in github. After all, just save it and it's ready to run.

## Tile widgets configuration
If you check the Overview tab in your dashboard, you'll notice that there are three widget widgets: Details, Reports, and Alerts. These widgets should take you to the current tab that names it, for example, if you click on the widget widget called Details, it should go to the Details tab. To do this, go to the configuration of the tiles widgets, click on "User Control" and paste the link of the other tabs there. Now, your block widgets should be working and take you to other tabs.

## Report configuration
Now that you already created all necessary analyses and actions. You should also set the input form widget in Report tab to run your analysis to generate reports. To do it just click to edit this widget, go to User Control configurations and select the analysis you created to generate reports in the field "Run analysis when submitting form". After that, you'll already be able to generate reports through the dashboard. And that's it, your application should have everything working fine.

## Scalability
After all, you might be wondering how you could scale this application up. Everything you learned here is functional and you can use as a start point to scale it up to thousand of devices.

TagoIO team. ![tagoIO.png](https://admin.tago.io/favicon-16x16.png?v=jw7PBgLGRl)
