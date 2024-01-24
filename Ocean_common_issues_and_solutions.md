# Ocean common issues and solutions

  

# Ocean 2

  

**A new employee A will replace the role of the current employee B but
it does not work?**

          Usually the new employee A's start date is still in the
future. The IDM job sync every 12 hours, we usually just need to wait. 

**How can we change contact of a document? **

          Depends on the status of the contact of the document. If
contact is active employee, it's best to have contact change it. They
just need to go to the work list and find the document box on the left
document list window. The admin can do the same thing. 

          However, if the contact is no longer with the university and
the document is not in the review process, software engineer team will
need to reassign it manually. 

**Customer claims the data is not saved in the text/comment box.**

**           **Usually two cases for this situation. 1. session time
out, it took them more than 30 minutes to type and data get lost when
their session expire. 2. value too long, the max we can accept is 4k
words. The UI did not provide nice validation on max length.

**Customer claims they can not create a document for a course. **

**           **Search existing document list and see if there is already
one create. We do not allow multiple document for same course at certain
time unless one of them is in published status. 

**Customer does not get email. **

          There could be many issues related to email but Ocean has been
sending emails to thousands of people in the past 5 years. The common
cause was customer disabled email in their comment settings. Some
blocked our email address or set as unsafe etc. To debug if we actually
send email, we have to ask mail rely people which takes forever. 

**Add/Remove people from roles.**

         We ask department admin and ocean admin to do this rather than
IT. 

**Document has been submitted but I want to edit something now**

         Once document is in approval chain, there is no way to edit it
unless ask the current approver to deny and return it to the contact. 

**Error on saving/submitting/publishing a document**

         Directly send it to SE team, there are usually course setting
issues in ocean or people soft that block the operation

  

# Ocean 1

**Customer wants to delete an existing program. **

         There is no way to do this in the app, the request has to be
route to software engineer team 

**Can I replace a role with another user **

         This can be done by shadowing in as the person who has the
authority of managing certain roles. There is a hierarchy of roles and
the one level above can manage the roles in the level below. This kind
of request should go to UCC office since IT does not know the structure
of approval hierarchy. If customer sees whole page load to an error
message page, then forward to SE team. 

**Can not save document since my program component returns "can not save
orphan component"**

**          **This issue can usually resolved by customer themselves.
They need to click on edit of the document, go to the component setting
page and remove all components marked red. In rare case, there might be
issues of deleting them on code side, route to SE team. 

**Can not find a program in the search box**

         This issue is not common, usually caused by conflict of program
names or error on the database side, this issue has to be route to
SE/Registrar 

  

  

  
