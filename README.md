#Simple Android Instant Messaging Application#

Simple because it is not a kind of application for end users. It is for people who want to learn somethings about Android or test some applications on Android also in order to be honest , this software was prepared to be admitted to PhD at NEU :), however I didn't succeed :( so this software may be considered as useless for me, but it may be useful for some beginners and I am willing to share all information I have for free so you can contact me by email below

Then let me describe the software, this is a simple IM application runs on Android, application makes http request to a server, implemented in php and mysql, to authenticate, to register and to get the other friends' status and data, then it communicates with other applications in other devices by socket interface.

###New Project: Butterfly TV - Live Stream Messaging###

It lets you broadcast live your important moments to your contacts. 
https://play.google.com/store/apps/details?id=com.butterfly'> http://www.mekya.com/wp-content/uploads/2014/11/icon-butterflyTV-150x150.png' width='52' /> https://play.google.com/store/apps/details?id=com.butterfly'> https://developer.android.com/images/brand/en_generic_rgb_wo_60.png' />

##Features##

User registration
User authentication
Adding a new friend by username
Approving a friend
Messaging with a friend in list (Of course)
Shows online and offline users
Runs a background service in order to get messages even when the application is closed.
Uses notification area when a new message is received.
Quiting the application(kills the background service)

##How to make it run##

There is a folder whose name is Server, copy all files under Server folder to a folder in your web server directory, for instance android_im that can be accessed by http://192.168.7.5/android_im/ (192.168.7.5 is the IP address of computer which runs apache and mysql, use local network IP address instead of using localhost or 127.0.0.1) Open the index.php and enter database connectivity parameters such as host, username, password etc. write error_reporting(0) in top of index.php Create the tables in mysql database ``` CREATE TABLE friends ( Id int(10) unsigned NOT NULL auto_increment, providerId int(10) unsigned NOT NULL default '0', requestId int(10) unsigned NOT NULL default '0', status binary(1) NOT NULL default '0', PRIMARY KEY (Id), UNIQUE KEY Index_3 (providerId,requestId), KEY Index_2 (providerId,requestId,status) ) ENGINE=InnoDB DEFAULT CHARSET=latin1 COMMENT='providerId is the Id of the users who wish to be friend with';

CREATE TABLE users ( Id int(10) unsigned NOT NULL auto_increment, username varchar(45) NOT NULL default '', password varchar(32) NOT NULL default '', email varchar(45) NOT NULL default '', date datetime NOT NULL default '0000-00-00 00:00:00', status tinyint(3) unsigned NOT NULL default '0', authenticationTime datetime NOT NULL default '0000-00-00 00:00:00', userKey varchar(32) NOT NULL default '', IP varchar(45) NOT NULL default '', port int(10) unsigned NOT NULL default '0', PRIMARY KEY (Id), UNIQUE KEY Index_2 (username), KEY Index_3 (authenticationTime) ) ENGINE=InnoDB DEFAULT CHARSET=utf8; ```

set AUTHENTICATION_SERVER_ADDRESS in http://code.google.com/p/simple-android-instant-messaging-application/source/browse/trunk/src/com/mekya/communication/SocketOperator.java'>socketOperator, it must be the address where server folder are located, for our example it is http://192.168.7.5/android_im/ (don't use localhost)

Then run your application in Eclipse with ADT plugin.

it can be learned http://developer.android.com/sdk/1.5_r1/installing.html'>how to install Android SDK and ADT plugin

Every application opens a random port(more than 10000) to listen, http://developer.android.com/guide/developing/tools/adb.html#forwardports'>port forwarding is needed to communicate applications. It can be learned what the port numbers are that applications open in "users" table.

if it is wanted to run applications on same computer, remove the slashes at the line of //IP=10.0.2.2 in sendmessage function in http://code.google.com/p/simple-android-instant-messaging-application/source/browse/trunk/src/com/mekya/services/IMService.java'>imService . Then you need to port forwarding. let me give me an example for instance user1 logins the emulator-5554 with port number 12345 and user2 logins the emulator-5556 with port number 54321

then issue these commands

adb -s emulator-5554 forward tcp:12345 tcp:12345

adb -s emulator-5556 forward tcp:54321 tcp:54321

##Demo Video##

You can http://simple-android-instant-messaging-application.googlecode.com/files/simple_android_im_application_demo.avi'>download and watch video(26 MB) from Downloads section.

##Screenshots##

| http://farm4.static.flickr.com/3586/3518346905_4134236be9.jpg?v=0 | http://farm4.static.flickr.com/3323/3518423107_ae3a218274.jpg?v=0 | |:------------------------------------------------------------------|:------------------------------------------------------------------| | http://farm3.static.flickr.com/2064/3543194582_3e7d1cd0a0.jpg?v=0 | http://farm4.static.flickr.com/3368/3518464413_eaac2c65ac.jpg?v=0 |

##Support##

There is no support given anymore for this project.

##Author##

Ahmet Oguz Mermerkaya (mekya) www.mekya.com
