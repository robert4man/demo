# LEO Cron Jobs

Listed below are all the cronjob in LEO and what they do.

<table class="confluenceTable">
<tbody>
<tr class="header">
<th class="confluenceTh">Name</th>
<th class="confluenceTh">Description</th>
<th class="confluenceTh">Run Time</th>
</tr>
&#10;<tr class="odd">
<td class="confluenceTd">Archive Logs</td>
<td class="confluenceTd">This will take the log files and archive
anything older than a 180 days</td>
<td class="confluenceTd">1st of the month at 1:30 am</td>
</tr>
<tr class="even">
<td class="confluenceTd">Backup MySQL</td>
<td class="confluenceTd">Does a mysqldump on all databases on localhost
for backup</td>
<td class="confluenceTd">Every night at 3:30 am</td>
</tr>
<tr class="odd">
<td class="confluenceTd">Closed Awards</td>
<td class="confluenceTd">Check grant accounting to see if a project has
been closed. If so report to ORSP</td>
<td class="confluenceTd">Every night at 1:00 am</td>
</tr>
<tr class="even">
<td class="confluenceTd">COI Expiration Reminder</td>
<td class="confluenceTd">Check to see if approved COI's are going to
expire. Get 3 total email notices.</td>
<td class="confluenceTd">Every night at 12:05 am except weekends</td>
</tr>
<tr class="odd">
<td class="confluenceTd">COI Reminder</td>
<td class="confluenceTd"><p>Email reminders to chairs and deans
delegates to sign off on faculty COI disclosure.</p>
<p>Only get 3 emails total.</p></td>
<td class="confluenceTd">Every day between 5:00 am and 6:00 pm except
weekends</td>
</tr>
<tr class="even">
<td class="confluenceTd">DMG Reminder</td>
<td class="confluenceTd">Email reminders to chairs and deans delegates
to sign off on DGM request.</td>
<td class="confluenceTd">Every day between 5:00 am and 6:00 pm except
weekends</td>
</tr>
<tr class="odd">
<td class="confluenceTd">Extension Reminder</td>
<td class="confluenceTd">Email reminders to chair and dean delegates to
sign off on extension request</td>
<td class="confluenceTd">Every day between 5:00 am and 6:00 pm except
weekends</td>
</tr>
<tr class="even">
<td class="confluenceTd">HR Data</td>
<td class="confluenceTd">Pull data from Oracle EPROD
OUHR.ORSP_CURRENT_ASSIGNMENTS_V</td>
<td class="confluenceTd">Every night at 2:30 am</td>
</tr>
<tr class="odd">
<td class="confluenceTd">IACUC Annual Report Reminder</td>
<td class="confluenceTd">Email PI that their annual report is due. Only
get 3 reminder emails total.</td>
<td class="confluenceTd">Every night at midnight except weekends</td>
</tr>
<tr class="even">
<td class="confluenceTd">IACUC CITI Training Reminder</td>
<td class="confluenceTd">Remind researchers to upload their CITI
certificate. Total of 3 reminder emails</td>
<td class="confluenceTd">Every night at 5:00 am except weekends</td>
</tr>
<tr class="odd">
<td class="confluenceTd">IACUC Committee Reminders</td>
<td class="confluenceTd">Email all committee members that have not
reviewed assigned protocols prior to 72 hours</td>
<td class="confluenceTd">Every night at midnight except weekends</td>
</tr>
<tr class="even">
<td class="confluenceTd">IACUC Expiration Reminders</td>
<td class="confluenceTd">Email all PI who's protocols are about to
expire. Only 3 notification emails sent</td>
<td class="confluenceTd">Every night at midnight except weekends</td>
</tr>
<tr class="odd">
<td class="confluenceTd">IACUC Faculty Reminders</td>
<td class="confluenceTd">Email faculty who are still pending review of
protocol. Only 3 emails are sent</td>
<td class="confluenceTd">Everyday between 5:00 am and 6:00 pm except
weekends</td>
</tr>
<tr class="even">
<td class="confluenceTd">Innovation Awards</td>
<td class="confluenceTd">Email faculty about their innovation award
approvals. Only 3 total are sent</td>
<td class="confluenceTd">Everyday between 5:00 am and 6:00 pm except
weekends</td>
</tr>
<tr class="odd">
<td class="confluenceTd">IRB Absent Committee</td>
<td class="confluenceTd">Mark committee member as back.</td>
<td class="confluenceTd">Every night at 12:25 am</td>
</tr>
<tr class="even">
<td class="confluenceTd">IRB Awaiting Revision</td>
<td class="confluenceTd">Reminder CI/PI research compliance requested a
revision. Waits 30 days since request</td>
<td class="confluenceTd">Every night at 12:25 am</td>
</tr>
<tr class="odd">
<td class="confluenceTd">IRB CITI Training Reminder</td>
<td class="confluenceTd">Remind IRB researchers their CITI training is
about to expire. 3 emails</td>
<td class="confluenceTd">Every night at 12:25 am</td>
</tr>
<tr class="even">
<td class="confluenceTd">IRB Committee Reminders</td>
<td class="confluenceTd">Email IRB committee members it is their last
day to review assigned protocol</td>
<td class="confluenceTd">Every night at 12:15 am</td>
</tr>
<tr class="odd">
<td class="confluenceTd">IRB Expire</td>
<td class="confluenceTd">Email researchers their IRB has expired.</td>
<td class="confluenceTd">Every night at 12:15 am</td>
</tr>
<tr class="even">
<td class="confluenceTd">IRB Expire Soon</td>
<td class="confluenceTd">Email the researchers that their protocol will
expire soon. 2 month and 1 month warning</td>
<td class="confluenceTd">Every night at 12:20 am</td>
</tr>
<tr class="odd">
<td class="confluenceTd">IRB Reminder</td>
<td class="confluenceTd">Email the faculty researchers pending review. 3
times</td>
<td class="confluenceTd">Everyday between 5:00 am and 6:00 pm except
weekends</td>
</tr>
<tr class="even">
<td class="confluenceTd">LEO Reminders</td>
<td class="confluenceTd">Custom email reminder for ORSP staff.</td>
<td class="confluenceTd">Every night at 1:40 am</td>
</tr>
<tr class="odd">
<td class="confluenceTd">Transmittal Reminders</td>
<td class="confluenceTd">Remind pending faculty to review and approve
transmittal form.</td>
<td class="confluenceTd">Everyday between 5:00 am and 6:00 pm except
weekends</td>
</tr>
</tbody>
</table>
