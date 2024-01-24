# Admin Access to LEOv4

LEOv4 uses django, which uses LEOv4.users_profiles and
LEOv4.users_profiles_groups.  You will first have to insert yourself in
the the users_profile table.  Once you exist in the users_profile table
get your "id" . Using that id then insert yourself into the
users_profile_groups table.  Look at the SQL below to help.

  

    INSERT INTO  
        LEOv4.users_profile  
    SET 
        username='YOUR_OHIO_ID', 
        first_name='YOUR_FIRST_NAME', 
        last_name='YOUR_LAST_NAME'
        is_staff=1, 
        is_active=1,
        is_superuser=1  

    INSERT INTO 
        LEOv4.users_profile_groups 
    SET 
        profile_id='above_auto_generated_id',
        group_id=1
