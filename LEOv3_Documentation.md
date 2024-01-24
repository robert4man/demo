# LEOv3 Documentation

This is the beginning of the documentation for LEOv3.  Currently this
documentation is incomplete and only applies to LEO development.  This
is a work in progress.

### ACCESS TO LEOv3 DEVELOPMENT ENVIRONMENT

|                 |                                                                                                  |
|-----------------|--------------------------------------------------------------------------------------------------|
| LEO Access / UI | <a href="https://leobeta.research.ohio.edu/"                                                     
                   rel="nofollow">https://leobeta.research.ohio.edu</a>                                              |
| Git Repository  | <a                                                                                               
                   href="https://git.oit.ohio.edu/projects/LEO/repos/leo/browse?at=refs%2Fheads%2FBeta"              
                   rel="nofollow">https://git.oit.ohio.edu/projects/LEO/repos/leo/browse?at=refs%2Fheads%2FBeta</a>  |
| Virtual Server  | ssh://vpr-web-ld001.app.private                                                                  |
| AD Access       | OIT-IDM-AIS-CAD-Devs                                                                             |

### LEOv3 TECHNOLOGIES USED

1.  ModPerl2 https://perl.apache.org/
2.  XML https://www.xml.com/
3.  XSLT https://www.w3.org/TR/2009/PER-xslt20-20090421/
4.  MySQL 5.6: https://www.mysql.com/
5.  Apache 2.2: https://apache.org/

### LEOv3 OUTSIDE DEPENDENCIES

1.  Oracle
2.  Pivot <a href="https://pivot.cos.com/funding_main"
    rel="nofollow">https://pivot.cos.com/funding_main</a>
3.  mailrelay.oit.ohio.edu
4.  Ohio Single Sign On

### LEOv3 SERVICES

LEOv3 relies on two services on the development box in order to run. 
The cad user has complete access to start, stop and restart these
services.  The two services used by LEO are as follows:

-   Apache 2.2 web server

The configuration file for LEO apache is located at
"**/etc/httpd/vhosts.d/25-leo.conf**".  To manage apache service sudo to
the cad service account. 

-   -   **sudo service httpd graceful** to gracefully restart apache.
        (try to always do)
    -   **sudo service httpd restart **to restart the apache server.
    -   **sudo service httpd start** to start the apache server.
    -   **sudo service httpd stop **to stop the apache server.
-   MySQL 5.6 database server

The configuration file for LEO mysql is located at
"**/etc/opt/rh/rh-mysql56/my.cnf"**.  To manage mysql services sudo to
the cad service account.

-   -   **sudo service rh-mysql56-mysqld restart** to restart the mysql
        database server.
    -   **sudo service rh-mysql56-mysqld start **to start the mysql
        database server.
    -   **sudo service rh-mysql56-mysqld stop** to stop the mysql
        database server.

### MySQL Port Forwarding

If you need to talk to the mysql databases on LEO you will need to port
forward from login.oit.ohio.edu to the LEO servers.  You will need to
create ssh keys.

I use the following script to make this happen on the login server:

<table class="confluenceTable">
<tbody>
<tr class="header">
<th class="confluenceTh"><p>#!/usr/bin/bash</p>
<p>nohup ssh -nNT -L 3304:vpr-web-lp001.app.private:3306
ohioID@vpr-web-lp001.app.private &gt; /dev/null 2&gt;&amp;1 &amp;</p>
<p>nohup ssh -nNT -L 3305:vpr-web-ld001.app.private:3306
ohioID@vpr-web-ld001.app.private  &gt; /dev/null 2&gt;&amp;1
&amp;</p></th>
</tr>
&#10;</tbody>
</table>

When you set up your client to talk to LEO mysql servers you would use
host login.oit.ohio.edu **port 3304 to talk to LEO production** and
**port 3305 to talk to LEO development**.

### Single Sign On

This is accomplished in the apache conf file
(/etc/httpd/vhosts.d/25-leo.conf).  You need to install the mod_auth_cas
apache module to use it.

<table class="confluenceTable">
<tbody>
<tr class="header">
<th class="confluenceTh"><p>LoadModule auth_cas_module
modules/mod_auth_cas.so</p>
<p>CASCookiePath /tmp/cas/</p>
<p>CASVersion 2</p>
<p>CASLoginURL https://cas-qa.sso.ohio.edu/login</p>
<p>  CASValidateURL https://cas-qa.sso.ohio.edu/serviceValidate</p>
<p>  CASRootProxiedAs https://leo-qa.research.ohio.edu</p>
<p>  CASTimeout 604800</p>
<p>  CASIdleTimeout 14400</p>
<p><br />
</p>
<p> </p>
<p>    AuthType CAS</p>
<p>    AuthName "CAS"</p>
<p>    require valid-user</p>
<p> </p>
<p>&lt;/VirtualHost&gt;</p></th>
</tr>
&#10;</tbody>
</table>

This will make everything in the
scope <a href="https://leobeta.research.ohio.edu/secure"
rel="nofollow">https://leobeta.research.ohio.edu/secure</a> require CAS
authentication.

### LEOv3 Directory structure

Almost everything you need for LEO is located in **/opt/LEO**.

-   html - where static files go (as defined
    in /etc/httpd/vhosts.d/25-leo.conf)
-   LEO.conf.  This is LEO configuration file.  Store password and
    settings.
-   leo_documents: Where files are stored from old programs
-   lib: Started a newer libraries of LEO.
-   module: (The big chunk of LEO code)
-   schema: Beginning of XSLT schema design of LEO (not implemented)
-   scripts: Some scripts that were designed and used in LEO do fix / do
    things.
-   startup.pl (Import file for LEO mod_perl.  View
    in /etc/httpd/vhosts.d/25-leo.conf)
-   stylesheets: where most of the XSLT stylesheets are.  During LEOv3
    we later changed code so the stylesheets could be next to perl
    files.

### LEOv3 CronJobs

Currently the cronjob for LEO is under the user "hibbard".  Once all the
conversions are made I will move the crontab entry to the cad user.

>     #LEO CRON TAB RAN EVERY 5 MINUTES
>
>     MAILTO=leo.support@ohio.edu
>
>     */5 * * * * perl /opt/LEO/modules/LEO/cron/cronTab.pl

So every 5 minutes the crontab calls cronTab.pl.  When you look at
/opt/LEO/modules/LEO/cron/cronTab.pl you will notice that it will scan
all the files in /opt/LEO/modules/LEO/cron and will try to execute them
with date and time parameters.  If you look at the
/opt/LEO/modules/LEO/cron/TransmittalReminders.pm you will see that it
will not run on the weekends and it only runs between 7am and 6pm.  So
the TransmittalReminders cron tab will run every 5 minutes between those
hours.  Basically this cron task job is to send emails to pending users
to approve or deny a transmittal form.

### MySQL backup

This is another cron job that runs every night at 3:30 am.  The cron
script is /opt/LEO/modules/LEO/cron/backupMySQL.pl.  It dumps the
database to **/srv/backup/mysql/** so when the server is backed up it
has a cold backup copy of the database.

Git Updates

Currently LEO is not setup to use bamboo so we are waiting for Travis to
be implemented then build the CI component to deploy.  Till then you
will just have to do it manually. 

1.  Merge code to BETA branch
2.  SSH to the beta server
3.  cd /opt/LEO
4.  git pull
5.  sudo service httpd graceful

It is important you use *service httpd graceful* in case a user is
uploading a file it will not stop and kill the apache thread.  Graceful
says send a reset when the apache thread is idle.

### How LEOv3 works

Apache uses the file /opt/LEO/startup.pl to setup some environmental
variables as well as do MySQL Persistent database connections. 
Reading /etc/httpd/vhosts.d/25-leo.conf you see the entry:

>     PerlRequire "/opt/LEO/startup.pl"

The next big thing that makes LEO do the rest of the magic is the
LEO::Provider.  Almost everything (when interacting with the website)
goes through the LEO::Provider located at
/opt/LEO/modules/LEO/Provider.pm.  If you look at the LEO apache
configuration file you will see the following entry:

>     CASScope /
>
>     SetHandler perl-script
>
>     PerlResponseHandler LEO::Provider

The above entry says two things.  The /secure, as mentioned above,
enforces CAS single sign on.  Next anything in the URL that matches
/secure/leo/xxx/xxxx.leo URL will go through the LEO::Provider.  Before
the word controller became popular we had providers
<img src="images/icons/emoticons/tongue.svg"
class="emoticon emoticon-cheeky" data-emoticon-name="cheeky"
data-emoji-short-name=":cheeky:" alt="(tongue)" /> .

   

### LEO::Provider

This is a quick break down of what happens in the LEO::Provider.

-   The handler function is called
-   Sometimes there are parameters passed that we will use in the
    Provider or passed to the called page. 
-   Sent up some pipes to dump any kind of warnings into a database
    table.
-   Load LEO settings globally to be used by modules later.
-   Parse the url and extensions.  See what find of content-type should
    be set.
-   Set the users role. 
-   Insert into a database log files who accessed what with complete URL
-   Get all of the groups the user is associated with in LEO.
-   The ability to download files and escape out of the LEO::Provider.
-   Load programs the user might be associated with.  The menu bar in
    LEO will then display them.
-   Load the user preferences.  They might have different font sizes,
    fonts, colors
-   Show any LEO alerts if the user has any
-   Finally LEO will parse the URL and parameters to do special things .
    I will provide some use case scenarios below.
-   Once the module and XML is formed it will be transformed into HTML
    and presented to the end user. (unless you use the passthru=1
    parameter then you will get XML returned)
-   PDF's can be displayed if no CSS3 has been used.  You can just pass
    the parameters pdf=1 to any page

So here are some interesting scenarios to get a grasp of the
LEO::Provider

-   <a href="https://leobeta.research.ohio.edu/secure/leo/core/home.leo"
    rel="nofollow">https://leobeta.research.ohio.edu/secure/leo/core/home.leo</a>: 

This will tell LEO to load **LEO::core::home** module located in
/opt/LEO/modules/**LEO/core/home.pm**.  If you edit this file you will
see 3 functions.

1.  sub new {} . Where parameters are passed from the LEO::Provider. 
    Such objects are the logged in user, groups, parameters and
    settings.
2.  sub check_security{}.  Called from LEO::Provider to see if the user
    can access the page or not.  Returns true or false.  LEO::core::home
    returns true because everyone can access it
3.  sub process {}.  If the user can access the page then execute the
    code in sub process and return the XML or data back.
4.  Once the XML is sent back then the Provider will transform the XML
    into HTML

-   <a
    href="https://leobeta.research.ohio.edu/secure/leo/core/home.leo?passthru=1"
    rel="nofollow">https://leobeta.research.ohio.edu/secure/leo/core/home.leo?passthru=1</a>.
    This will do the same as above however it will return XML and not
    HTML.  Good for debugging.
-   <a
    href="https://leobeta.research.ohio.edu/secure/leo/core/home.leo?pdf=1."
    rel="nofollow">https://leobeta.research.ohio.edu/secure/leo/core/home.leo?pdf=1.</a> 
    This will download the page as a PDF file.

### LEO GROUPS

All of the LEO groups are located in LEONEW.LEO_GROUPS.  All of the
users associated with the LEO GROUPS are in LEONEW.LEO_GROUPS_USERS. 
You can manage these groups inside of LEO by visiting <a
href="https://leobeta.research.ohio.edu/secure/leo/administration/home.leo"
rel="nofollow">https://leobeta.research.ohio.edu/secure/leo/administration/home.leo</a>.

### Setting up a vagrant server for local development.

I will be working on an ansible script to download vmware / vagrant and
setup a LEO environment for localhost development.

  

  

  

  

  

## Attachments:

<img src="images/icons/bullet_blue.gif" width="8" height="8" /> [LEO
Architecture](attachments/169279744/169279752)
(application/gliffy+json)  
<img src="images/icons/bullet_blue.gif" width="8" height="8" /> [LEO
Architecture.png](attachments/169279744/169279753.png) (image/png)  
