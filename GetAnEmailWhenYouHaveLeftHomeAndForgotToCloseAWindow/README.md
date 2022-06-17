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
3. Mount the sensor on the window that you forget to close.
4. Sign into Zapier.
5. Create a new zap named *Save window opened*.
6. In the *Trigger* part select the *Webhooks by Zapier* app and the *Catch Hook* event.
7. In the *Action* part select the *Storage by Zapier* app and the *Set Value* event. In the *Key* field input *window_state*. In the Value field input *1*.
8. Save the generated webhook URL and set the Zap live.
9. Create another zap named *Save window closed* with the exact same values as the step above but with *0* in the *window_state* value.
10. Create another zap named *Send email if leaving home and forgot to close window*.
11. In the *Trigger* part select *Webhooks by Zapier* and *Catch Hook* as in the previous zaps.
12. Add a new action and select the *Storage by Zapier* app and the *Get Value* event. In the *Key* field input *window_state*.
13. Add a new action and select the *Filter by Zapier* app. In the *Only continue if* part select *Get Value in Storage by Zapier* and *Value*. In the configuration select *(Text) Exactly matches* and input the value *1*.
14. Add a new action and select the *Email by Zapier* app. Select *Send Outbound Email* and input your email and a suitable message to let yourself know that you forgot to close the window. Publish the Zap.
15. Sign into IFTTT and create a new Applet.
16. In the *If* part select the *eWeLink Smart Home* service and sign in with your eWeLink account.
17. Select *Zigbee door sensor is open or closed* and select the sensor from the dropdown.
18. In the *Which status?* dropdown select *Closed*.
19. In the *Then* part select the *Make a web request* service.
20. Input the URL of the Zap named *Save window open* and save the Applet.
21. Create another applet for the *Open" event and input the webhooks URL from the Zap you created for this event.
22. Create another applet and in the *If* part select the *Location* service.
23. Select *You exit an area* and search for your address. Create the trigger.
24. In the *Then* part select the *Make a web request* service and input the URL of the webhook provided by the *Send email if leaving home and forgot to close window* zap.
