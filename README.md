# homeassistant-pushover-notification-cam-snapshot
<b>Sends a pushover notification with snapshot attached from your doorbell security cam.</b>
<br>
<br>
<br><b>Requirements for this automation:</b>
<ol>
<li>Pushover integration set up in Homeassistant. 
<br>See https://www.home-assistant.io/integrations/pushover/
<li>Security cam feed already available to homeassistant to capture the snapshot, in this case we will use the snapshot service available natively to Homeassistant.
<br>In my case, I use Frigate to run object detection on rtsp streams out of my Unifi Protect security cams. Note that this requires the Frigate server and Frigate integration inside Homeassistant. In my case, I am running the Frigate server exterior to Homeassistant in an LXC container in Docker.
<br>Note that if you want to trigger the automations based on a certain object detected, that entity will need to be available in Homeassistant. In this example, the automation is triggered when a person is detected in an certain zone within the frame, for a certain period of time.
<br>See here for Frigate documentation: https://github.com/blakeblackshear/frigate
</ol>
<br><b>Instructions:</b>
<br><ol>
<li>In Homeassistant, create an automation, copy the pushover_doorbell_snapshot.yaml file from this repository and save the automation. Note that you will have to edit the binary sensor names, device ID's, and filepaths for both saving the snapshot, and path to send it in the pushover action.</li>
<li>In my automation I had a condition using the binary.window_sensor (which is actually the front door's open/close sensor) to only trigger if the door had been shut for 10 minutes.</li>
<li>Now test your automation!</li>
</ol>
<br>Note that this snapshot method is simpler than the MQTT method used in my other repository homeassistant-android-tv-camera-notification.
