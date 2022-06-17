# Get an email when you've got snail mail

Why walk to and from an empty mailbox every day? Get en mail when mail is delivered to your mailbox to reduce your daily steps.

## What you'll need

- A Sonoff Zigbee Motion Sensor
- A Sonoff Zigbee Hub
- An IFTTT account.

## Recipe

1. Connect the motion sensor to the hub as described in the manual.
2. Connect the hub to Wi-Fi as described in the manual.
3. Sign into IFTTT and create a new Applet.
4. In the *If* part select the *eWeLink Smart Home* service and sign in with your eWeLink account.
5. Select Zigbee Motion Sensor and select the motion sensor from the dropdown.
6. In the *Motion detected or not?* dropdown select *Motion detected*.
7. In the *Then* part select the *Email* service.
8. Select *Send me an email* and input a subject and body with a text indicating that you've got mail.
