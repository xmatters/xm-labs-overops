# OverOps
[OverOps](https://www.overops.com/) is a leading monitoring solution that provides direct insight into code level issues. This integration leverages the [Webhook alerts](https://doc.overops.com/docs/outgoing-webhook) to fire events into xMatters. 

---------

<kbd>
  <img src="https://github.com/xmatters/xMatters-Labs/raw/master/media/disclaimer.png">
</kbd>

---------

An updated version of this integration is available, supporting the latest version of OverOps and based on xMatters Flow Designer so you can easily connect other tools to your toolchain. [Learn more](http://help.xmatters.com/integrations/#cshid=OverOps).

---------

# Pre-Requisites
* OverOps Account 
* xMatters account - If you don't have one, [get one](https://www.xmatters.com)!

# Files
* [OverOps.zip](OverOps.zip) - Workflow zip with inbound integration and message templates
* [overops.png](overops.png) - Overops image for Step.

# Installation

## xMatters set up
1. Login to the xMatters instance as a developer and navigate to the Developer tab. 
2. Next to the OverOps Workflow, click Edit > Integration Builder and expand the Inbound Integrations.
3. Click on the Flows tab, followed by the **New Exception** flow. Click on the Inbound from OverOps Step on the canvas. Copy the URL and save this for later. 
4. Click on the Forms tab and under the `New Exception` form click Edit > Layout. Enter the default recipients and click Save Changes. (An alternative to defaulting the recipients is to create a new [Subscription Form](https://help.xmatters.com/OnDemand/xmodwelcome/communicationplanbuilder/subscriptionforms.htm?cshid=SubscriptionFormListPlace))

## OverOps set up
1. Login to OverOps and click Settings > Alerts:
2. Select Webhook
3. Paste in the url copied from the xMatters Workflow. 
4. Click Apply.
5. Go back to the main page of OverOps.
6. Click your username (found in the upper right), followed by Manage alerts.
7. Create an alert here that uses the xMatters Webhook as the Alert Channel.
   
# Testing
If everything is correctly configured, then when an error is thrown by code that is watched by OverOps, the webhook will fire into the xMatters integration builder, the script will run and a new event will be created, targeting the default recipient and notifications will be sent out. 
There will be two response options:
1. Acknowledge - Acknowledge the notification and stop device and group escalations
2. Ignore - Ignore the notification and immediately escalate to the next recipient in the group. 

# Troubleshooting
The first step of troubleshooting would be to enable the Email notification type in the Alert. This will send an email as well as the webhook. If the code faults and no email is sent, then OverOps is not triggering the Alert. 

If the email is sent, then investigate the Activity Log in the Flow Designer. If an entry corresponds with roughly the time the email from OverOps was sent, then check for any errors. 

If there are no errors and an event was created then note the event ID and track down that event in the Event Report. The Event Log will have any other information about who was notified. 

