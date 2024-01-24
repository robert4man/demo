# Common auth user can not login/activate issue

It's not uncommon to see a few requests of not being able to activate
accounts through auth user system starting from summer when students
getting their bill for next year. It's not hard to resolve this. 

  

1.  Go into the database and check the status of the request, if user
    was created with status 'I', that means the activation step failed. 
2.  Communicate to the user that you are about to fix this, disregard
    system generated mail 
3.  Shadow login as student and resend the activation
4.  At this point, you will be able to find the email content sent to
    the user in the email audit table 
5.  get the activation link and activate it with a random password, this
    password does not need to be kept but need to align with IDM
    requirement 
6.  Send the user this link and ask the user to reset password: <a
    href="https://webapps.ohio.edu/authorized-user-resource/password/reset"
    rel="nofollow"
    style="">https://webapps.ohio.edu/authorized-user-resource/password/reset</a>
7.  Remind the user to use good password for the account

  

Since the process involves many entities student, system, parent and
external email box. There could be problem anywhere in the chain. The
most common issues we had was user sending invalid password or account
was already created but user forgot the password. The most efficient way
is to force the user to do a password reset. 

In summary,

if user already exist in IDM (you will get activation failure), send
password reset link directly 

if user is new (99% of the case), activate the account on behalf of user
and send reset link 

  
