# Announcements App & Resource Diagrams

The announcements app provides functionality so that users can create
announcements to display in their apps. Applications that integrate with
the app must have an "app reference" and "group" saved in the
announcements database. The Grads app is a good point of reference to
see how to set this up if you need to app a group/app ref.

## How to Use

As of the time of this writing, there are a few steps you need to follow
if you need your app to integrate with this service.

1.  A record needs added to the GROUP_TO_APP table in the
    OU_ANNOUNCEMENTS schema.
    1.  Needs: unique ID, IDM group name, and APP_ID reference value
        (this value will be the primary key of an app record created in
        the APP table in the OU_ANNOUNCEMENTS schema).
2.  A record needs added to the APP table in the OU_ANNOUNCEMENTS schema
    defining a new app to be used with this service.
3.  The app integrating the announcement display will need to call
    ${base}/api/announcements/app/{YOUR_REGISTERED_APP_NAME}/announcements/latest
    1.  The return should be a JSON response containing any announcement
        data for the latest announcement.

## Context Diagram

<img src="plugins/servlet/confluence/placeholder/unknown-macro"
class="wysiwyg-unknown-macro" />

  

## Container Diagram

<img src="plugins/servlet/confluence/placeholder/unknown-macro"
class="wysiwyg-unknown-macro" />

## Attachments:

<img src="images/icons/bullet_blue.gif" width="8" height="8" />
[Announcements Resource Architecture
Diagram](attachments/181961344/181961360) (application/gliffy+json)  
<img src="images/icons/bullet_blue.gif" width="8" height="8" />
[Announcements Resource Architecture
Diagram.png](attachments/181961344/181961361.png) (image/png)  
<img src="images/icons/bullet_blue.gif" width="8" height="8" />
[Announcements Resource Architecture
Diagram](attachments/181961344/181961363) (application/gliffy+json)  
<img src="images/icons/bullet_blue.gif" width="8" height="8" />
[Announcements Resource Architecture
Diagram.png](attachments/181961344/181961364.png) (image/png)  
<img src="images/icons/bullet_blue.gif" width="8" height="8" />
[Announcements Resource Architecture
Diagram](attachments/181961344/181961358) (application/gliffy+json)  
<img src="images/icons/bullet_blue.gif" width="8" height="8" />
[Announcements Resource Architecture
Diagram.png](attachments/181961344/181961359.png) (image/png)  
<img src="images/icons/bullet_blue.gif" width="8" height="8" />
[Announcements Container Diagram](attachments/181961344/181961368)
(application/gliffy+json)  
<img src="images/icons/bullet_blue.gif" width="8" height="8" />
[Announcements Container
Diagram.png](attachments/181961344/181961369.png) (image/png)  
