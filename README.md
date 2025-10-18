# Octopus Intelligent Go Charge-to-add Automation

When Octopus control your home wall charger, you need to log onto the Octopus App to tell them how much charge to add each time you plug in. This can become a bit onerous, particularly if you have more than one car with different battery sizes where 50% added in Octopus doesn't equal 50% added to the car that's trying to charge.

This is a Home Assistant automation and some companion sensors that will automate that process of telling Octopus Intelligent Go the amount of charge required to meet the car's target charge state when Octopus is controlling the charger.
To use this you'll need the following integrations:
* Octopus Energy integration https://github.com/BottlecapDave/HomeAssistant-OctopusEnergy
* HA integration for your car
* HA integration for your charger (optional)

Ideally your own car's HA integration gives you the following three attributes:
* Car current state of charge %
* Car target state of charge %
* Car plugged in status

If your car integration doesn't expose the target state of charge, use the manual version of the sensor and either set the target in the sensor itself (e.g. 90%), or create a input_number helper so you can control that value from a dashboard input card. If your car doesn't tell you when it's plugged in, you can trigger the automation from your charger integration plugged in state instead

If you have more than one car you charge at home, create two sensors and two automations to control both along with a condition to determine which car is plugged in, so only one automation will complete

Here's my charging dashboard for some inspiration, showing the various sensors and integrations in action. 
![My Dashboard](https://github.com/LocobladeHA/Octopus-IG-charge-to-add-HA-automation/blob/main/ChargeDashboard.png)

This was taken whilst my Polestar is half way through an IOG charge. The "Charge Required" sensor updates real time hence why the Polestar value 53% is lower than the 61% Octopus "Charge Requested", which was set by the the automation as the amount required when first plugged in. 
The Target % is set manually on the Polestar as its integration doesn't expose the target charge %. That means this value won't override what the car is set to, whereas the Cupra integration does expose that value and allow it to be modified so the button under the Cupra section shows what the car peak charge level is set to and can be used to adjust that value rather than go to the car or use the Cupra app.
