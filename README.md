# OpenVPN (OPNSense)
OpenVPN DSM for QRadar

This DSM config will support parsing and alerting for the following OpenVPN event types "Connection reset", "WARNING: Bad encapsulated packet", "TCP connection established", "peer info", "authenticated", "Peer Connection Initiated", "could not authenticate", "requires the local group VPN", "TLS Auth Error", and "WARNING: Failed running command". If you have any questions you can create an issue for the GitHub project or open a question/reply on the IBM QRadar CE forms located at: https://ibm.biz/qradarceforums

# OPNSense Changes
1. Enable VPN logging by selecting System - Settings - Logging and selecting the check box next to VPN (PPTP, IPsec, OpenVPN) events.
2. Select VPN - OpenVPN - Servers - (Your VPN Server) - Verbosity Level and ensure it is set to 1 (default).
NOTE: Without this setting some events might not be mapped or parsed correctly. You can adjust this but additional events will need to be parsed/mapped or they will come into QRadar as unknown.

# QRCE Changes
1. Create a new custom DSM called (OpenVPN) using the DSM editor option under the admin settings window.
2. Once the custom DSM has been created close the window and click the Log Source Extensions option in the admin settings.
3. Click Add near the top right corner
4. Enter a name of "OpenVPNCustom_ext"
5. Select your newly created log source (OpenVPN) that you created earlier.
6. Click the upload button and select the file "Custom_ext.xml"
7. Click done and proceed to open the DSM menu and select your log source (OpenVPN) that you created earlier.
8. You will need to select Event Mappings tab in the DSM editor and create the manual entries located in the file "Event Mappings.txt"
9. Finally, you will need to create a new log source selecting the custom Log source type we just created.

# Change Log
- 12-15-2018 - Mapped additional events.
- 12-12-2018 - Added additional events for when the VPN service is restarted and when IP addresses are assigned. Additional regex logic was created for the destination IP field for when the server assigns a new IP address to the client. The regex logic for event ID was adjusted to account for the additional events.
- 12-11-2018 - Initial Upload of the source code.
