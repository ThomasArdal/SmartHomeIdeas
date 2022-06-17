# Get an email when you have left home and forgot to close a window

I have a windows that I sometimes forget to close before leaving home. It's not something I have been open about since that could cause a breakin. Until now! By combining a windows sensor with a bit of magic, my windows will never be open again with me outside my property.

## What you'll need

- A Sonoff Zigbee Window Sensor
- A Sonoff Zigbee Hub
- An IFTTT account
- A Zapier account

## Recipe

1. Connect the window sensor to the hub as described in the manual.
2. Connect the hub to Wi-Fi as described in the manual.
3. Sign into Zapier.
4. Create a new zap named *Save window opened*.
5. In the *Trigger* part select the *Webhooks by Zapier* app and the *Catch Hook* event.
6. In the *Action* part select the *Storage by Zapier* app and the *Set Value* event. In the *Key* field input *window_state*. In the Value field input *1*.
7. Save the generated webhook URL and set the Zap live.
8. Create another zap named *Save window closed* with the exact same values as the step above but with *0* in the *window_state* value.
9. Create another zap named *Send email if leaving home and forgot to close window*.
10. In the *Trigger* part select *Webhooks by Zapier* and *Catch Hook* as in the previous zaps.
11. Add a new action and select the *Storage by Zapier* app and the *Get Value* event. In the *Key* field input *window_state*.
12. Add a new action and select the *Filter by Zapier* app. In the *Only continue if* part select *Get Value in Storage by Zapier* and *Value*. In the configuration select *(Text) Exactly matches* and input the value *1*.
13. Add a new action and select the *Email by Zapier* app. Select *Send Outbound Email* and input your email and a suitable message to let yourself know that you forgot to close the window. Publish the Zap.
14. Sign into IFTTT and create a new Applet.
15. In the *If* part select the *eWeLink Smart Home* service and sign in with your eWeLink account.
16. Select *Zigbee door sensor is open or closed* and select the sensor from the dropdown.
17. In the *Which status?* dropdown select *Closed*.
18. In the *Then* part select the *Make a web request* service.
19. Input the URL of the Zap named *Save window open* and save the Applet.
20. Create another applet for the *Open" event and input the webhooks URL from the Zap you created for this event.
21. Create another applet and in the *If* part select the *Location* service.
22. Select *You exit an area* and search for your address. Create the trigger.
23. In the *Then* part select the *Make a web request* service and input the URL of the webhook provided by the *Send email if leaving home and forgot to close window* zap.
