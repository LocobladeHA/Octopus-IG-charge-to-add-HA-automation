# Octopus Intelligent Go Charge-to-add Automation

When Octopus control your home wall charger, you have to tell them how much charge to add each time you plug in. This can become a bit onerous having to go into the Octopus app all the time, particularly if you have more than one car with different battery sizes.

This is a Home Assistant automation and sensors that will automate that process of telling Octopus Intelligent Go the amount of charge required to meet the car's target charge state when Octopus is controlling the charger.
To use this you'll need the following integrations:
* Octopus Energy integration https://github.com/BottlecapDave/HomeAssistant-OctopusEnergy
* HA integration for your car
* HA integration for your charger (optional)

Ideally your own car's HA integration gives you the following two attributes:
* Car current state of charge %
* Car target state of charge %
* Car plugged in status

If your car integration doesn't expose the target state of charge, use the manual version of the sensor and either set the target in the sensor itself (e.g. 90%), or create a input_number helper so you can control that value from a dashboard input card. If your car doesn't tell you when it's plugged in, you can trigger the automation from your charger integration plugged in state instead

If you have more than one car you charge at home, create two sensors and two automations to control both.
