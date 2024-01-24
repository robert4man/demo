# Name Changes

The following schemas / tables / fields will need to be updated when a
user OHIO ID changes.  Not all users will exist in all the tables
however you will need to check each table to see if they do exist.

  

COI.COI_DATA.USER_ID  
  
COMPLIANCE.COMPLIANCE_QUEUE.COI_USER_ID  
COMPLIANCE.COMPLIANCE_QUEUE.CITI_USER_ID  
  
DGM.DGM_DATA.MAINPI  
  
EXTENSIONS.EXTENSION_DATA.MAINPI  
  
LEONEW.IACUC_CITI_TRAINING.USER_ID  
LEONEW.IACUC_FACULTY.USER_ID  
LEONEW.IACUC_FORM.CREATED_BY  
  
LEONEW.IRB_CITI_TRAINING.USER_ID  
LEONEW.IRB_CITI_TRANING_HIPAA.USER_ID  
LEONEW.IRB_FACULTY.USER_ID  
LEONEW.IRB_FORM.CREATED_BY  
LEONEW.IRB_PROTOCOL.PROTOCOL_MANAGER  
LEONEW.IRB_PROTOCOL.PROTOCOL_ADMIN  
  
LEONEW.FACULTY.USER_ID  
LEONEW.TRANSMITTAL_LINK_FACULTY.USER_ID  
  
TRANSMITTAL.TRANSMITTAL_DATA.USER_ID  
TRANSMITTAL.TRANSMITTAL_LINK_FACULTY.USER_ID  
  
Only one in LEOv4 .. I was smarter with it:  
LEOv4.users_profile.username

  

Simply replace their old OHIO ID with their new OHIO ID in the above
schemas / tables / fields.  Might make a good student project to get
this scripted?Database Update Query (Replace usernew and userold with
respective values): 

UPDATE COI.COI_DATA  
SET USER_ID = 'usernew'  
WHERE USER_ID = 'userold';

UPDATE COMPLIANCE.COMPLIANCE_QUEUE  
SET COI_USER_ID = 'usernew', CITI_USER_ID = 'usernew'  
WHERE COI_USER_ID = 'userold';

UPDATE DGM.DGM_DATA  
SET MAINPI = 'usernew'  
WHERE MAINPI = 'userold';

UPDATE EXTENSIONS.EXTENSION_DATA  
SET MAINPI = 'usernew'  
WHERE MAINPI = 'userold';

UPDATE LEONEW.IACUC_CITI_TRAINING  
SET USER_ID = 'usernew'  
WHERE USER_ID = 'userold';

UPDATE LEONEW.IACUC_FACULTY  
SET USER_ID = 'usernew'  
WHERE USER_ID = 'userold';

UPDATE LEONEW.IACUC_FORMS  
SET CREATED_BY = 'usernew'  
WHERE CREATED_BY = 'userold';

UPDATE LEONEW.IRB_CITI_TRAINING  
SET USER_ID = 'usernew'  
WHERE USER_ID = 'userold';

UPDATE LEONEW.IRB_CITI_TRAINING_HIPAA  
SET USER_ID = 'usernew'  
WHERE USER_ID = 'userold';

UPDATE LEONEW.IRB_FACULTY  
SET USER_ID = 'usernew'  
WHERE USER_ID = 'userold';

UPDATE LEONEW.IRB_FORM  
SET CREATED_BY = 'usernew'  
WHERE CREATED_BY = 'userold';

UPDATE LEONEW.IRB_PROTOCOL  
SET PROTOCOL_MANAGER = 'usernew', PROTOCOL_ADMIN = 'usernew'  
WHERE PROTOCOL_MANAGER = 'userold';

UPDATE LEONEW.FACULTY  
SET USER_ID = 'usernew'  
WHERE USER_ID = 'userold';

UPDATE LEONEW.TRANSACTION_LINK_FACULTY  
SET USER_ID = 'usernew'  
WHERE USER_ID = 'userold';

UPDATE TRANSMITTAL.TRANSMITTAL_DATA  
SET USER_ID = 'usernew'  
WHERE USER_ID = 'userold';

UPDATE TRANSMITTAL.TRANSMITTAL_LINK_FACULTY  
SET USER_ID = 'usernew'  
WHERE USER_ID = 'userold';

UPDATE LEOv4.users_profile  
SET username = 'usernew'  
WHERE username = 'userold';

  

  
