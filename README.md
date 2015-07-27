This is a simple web soft-phone that uses WebRTC and Jingle to dial free iNums telephone numbers. It uses the following components to achieve this.

 * Customized version of [http://phono.com Phono SDK] for webrtc only that connects to the Voxeo SIP cloud and handles the Jingle signalling and WebRTC media. Flash support has completely been removed. *It only works with Chrome ver 23+ for now. Firefox support will come later*

 * Openfire Server with [http://code.google.com/p/openfire-websockets websockets] and [http://code.google.com/p/redfire redfire] plugins to lookup iNums and map to Phono SIP addresses using XMPP Presence for anonymous users.

 * Candybar and DialPad GUI components from [https://github.com/att-innovate AT&T Foundry and &Yet]
 
 * [http://www.addthis.com/labs/social-sign-in AddThis social sign] on service for Facebook, Google and Twitter

Live demo is running at https://webrtc.free-solutions.org:8443/webrtc-phone

==Outgoing Calls==

Just type in 9 digit iNum and press enter or or use the dialpad and click on call button to make the call. The application will add the 883510 prefix and the inum.net domain to create the full SIP URI sip:883510xxxxxxxxx@inum.net before placing the call via Phono.

===Other Features===
||Feature||Description||Example||
||Direct Link||Use webrtc-phone directly from a web page link to make a call. <br>Just add the destination parameter. The example will dial the echo test service on inum.net||https://webrtc.free-solutions.org:8443/webrtc-phone/?destination=000000091||
||Dial other free SIP numbers||You can dial other free SIP telephone numbers on other domains by using the domain parameter. the example will dial the HD Voice test service at zipdx.com||https://webrtc.free-solutions.org:8443/webrtc-phone/?destination=3366&domain=login.zipdx.com||
||Short Codes||You can use a prefix to limit the digits dialed to an extension. The example provided will initially dial Softmart using US Toll free number 2436292 and any subsequent seven digit tool free number using the service at egiga.com||https://webrtc.free-solutions.org:8443/webrtc-phone/?prefix=sip:*8501800&domain=ekiga.net&destination=2436292||
||Toll Free numbers||The previous example could also be done by requesting Phono to dial a telephone number. Use the tel: prefix.||https://webrtc.free-solutions.org:8443/webrtc-phone/?prefix=tel:&destination=+18002436292||

http://webrtc-phone.googlecode.com/files/webrtc-phone2.jpg

==Incoming Calls==
In order to receive incoming calls, you must provide a personal iNum which will be temporarly mapped to your Phono SIP address. You do this by providing the inum parameter with your inum that should be re-mapped. 

*PLEASE NOTE that the remapping is only for other users in the same webrtc-phone service.*.

If your iNum is dialed from a regular phone, the call will end up on whatever device you have forwarded it to. It is only when the number is dialed from webrtc-phone that it will be re-mapped to your active Phono session. This is achieved by creating a user session on an Openfire server for every active webrtc-phone user and using XMPP presence to broadcast the Phono SIP session Id to every user session. The session Id is cached and used instead of the sip:883510xxxxxxxxx@inut.net address when the iNum is dialed.

You can set your social identity to Facebook, Twitter or Google. Provided you give webrtc-phone permissions, your photo/avatar and name will appear on the incoming call details. 

Click on the appropriate social icon button to do this. 

http://webrtc-phone.googlecode.com/files/webrtc-phone.jpg

==How to Use==
Grab the download file and unzip into your Openfire OPENFIRE_HOME/resources/spank folder and install the [http://code.google.com/p/openfire-websockets openfire-websockets] and [http://code.google.com/p/redfire redfire] plugins.

Point your browser at http://your_server:7070/webrtc-phone.

For more information and support for Openfire and the redfire/websockets plugins, visit http://www.igniterealtime.org

For more information about Phono SDK visit www.phono.com

For more information about iNum, vist www.inum.net
