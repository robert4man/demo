# Admin Access On LEOv3

`LEOv3 uses two tables to manage ACL's.  LEONEW.LEO_GROUP_USERS and LEONEW.LEO_GROUPS`

  

`GROUP_ID 4 = ADMINISTRATORS.  So doing the insert below will give you LEO ADMIN access:`

  

`INSERT INTO LEONEW.LEO_GROUP_USERS SET USER_ID='yourohioid', GROUP_ID='4'`
