In this chapter, learn how to configure a Secure File Transfer Protocol (SFTP) adapter using the containerized B2Bi deployment.

## Open the B2Bi dashboard and change password policies

1. In the OpenShift web console, click **Routes** under the **Networking** section in left-hand panel.

![](_attachments/OSOverviewToRoutes.png)

2. Click the **All Projects** pull-down menu and click the **b2bi** project.

![](_attachments/OSRoutesMenu.png)

??? question "BP quiz question"
    Several BP quiz questions will come from the **OpenShift web console**. When taking the BP quiz make sure the ITZ environment is still active and keep this demonstration script open.

3. Notice all the routes that are currently defined in the b2bi Project, there are 15 of them

![](_attachments/OSB2BiAllRoutes.png)

4. To start the setup of the SFTP adapter, launch the IBM Sterling B2Bi dashboard by clicking on the route for the **sterling-fg-b2bi-asi-internal-route-dashboard** route in the **Location** column. Do not click the Route name, rather click the Route link in the **Location** column of the table.

![](_attachments/OSB2BiDashboardRoute.png)

5. If a security risk is received in the browser, accept it. In a production environment certificates would be configured for these web pages.

![](_attachments/FFSecurityRisk1.png)
![](_attachments/FFSecurityRisk2.png)

Note: the images above are from Firefox running on MacOS. They will look different depending on browser and operating system.

!!! hint
    As this is a new install, in this demonstration the default user ids and passwords will be used. To keep things simple in this demonstration, all passwords will be set to **password**. Not secure, but this will be a short lived demonstration environment.

6. Enter **admin** in the **User ID** field and **password** in the **Password** field, and then click **Sign In**.

![](_attachments/B2BiAdminLogin.png)

In the latest {{offering.name}} release, new password policies have been set that require users to change their password the first time they authenticate. 

7. Enter **password** in the **Old Password** field, and then enter **passw0rd!** in both the **New Password** and **Retype Password** fields and click **Sign In**. 

![](_attachments/B2BiAdminChangePassword.png)

For this demonstration environment, change the password policies to simplify the demonstration flow. 

8. Click **Accounts** in left-hand menu and then click **Password Policy**.

![](_attachments/B2BiMainMenu-Accounts.png)

9. Enter **default** in the **Password Policy Name** text entry field and click the **Go!** button in the **Search** section.

![](_attachments/B2BiMainMenu-AccountsSearch.png)

10. Click the **edit** icon for the **Default User Policy**.

![](_attachments/B2BiMainMenu-DefaultPolicy.png)

11. Uncheck the **Password required to contain special characters** and **Required password change on next login attempt** check boxes and then click **Save**.

![](_attachments/B2BiMainMenu-DefaultPolicyChange.png)

12. Click **Finish** on the confirmation screen.

![](_attachments/B2BiMainMenu-DefaultPolicyFinish.png)

!!! important "Important"

    In most cases, clients will typically strengthen the default password policy to match their corporate standards for passwords. Again, they are being reduced here to simplify the demonstration flow.

13. Click **Return** on the completion screen.

![](_attachments/B2BiMainMenu-DefaultPolicyComplete.png)

## Create a SSH Host Identity key

First, a **SSH Host Identity** needs to be created. The Host Identity Key is a Private/Public key pair used to identify the Application SFTP Server to remote clients.  Note, for this demonstration, default values will be used where possible, but production deployments may use other values depending on client requirements.

??? question "BP quiz question"
    Several BP quiz questions will come from the **B2Bi dashboard**. When taking the BP quiz make sure the ITZ environment is still active and keep this demonstration script open.

14. Click the **Deployment** menu item in left-hand menu bar and then click the **SSH Host Identity Key** option.

![](_attachments/B2BiMainMenuToDeployment-2.png)

15. Click the **Go!** button in the **Create: New Host Identity Key** box.

![](_attachments/B2BiHIK-CreatePage.png)

16. Enter **demo** in the **Host Name:** field of the "New Host Identity Key" form and then click the **Next** button.

![](_attachments/B2BiHIK-HostName-2.png)

17. Click **Finish**.

![](_attachments/B2BiHIK-Finish-2.png)

18. Click **Close** on the pop-up dialog.

![](_attachments/B2BiHIK-PopUp.png)

19. Wait until the completed message is received and the click the **Return** button.

![](_attachments/B2BiHIKCreatedCompleted.png)

## Create an SFTP adapter

Next, an SFTP adapter must be created which will utilize the OpenShift service port for B2Bi.

20. Click the **Services** menu item under **Deployment** in the left-hand menu bar.

![](_attachments/B2BiMainMenuDeploymentToServices.png)

21. Click the **Configuration** menu item under **Services**.

![](_attachments/B2BiMainMenuServicesToConfiguration.png)

22. Enter **sftp** in the **Service Name** field and click the **Go!** button in the **Search** box.

![](_attachments/B2BiServicesConfiguratonForm.png)

23. Locate the **SFTP Server Adapter** entry in the table and click the **edit** button.

![](_attachments/B2BiServicesConfigurationSearchResults-2.png)

24. Review the default settings and click **Next**.

![](_attachments/B2BiSFTPAdapterName1.png)

25. Review the settings on the **SFTP Server Adapter: Configuration** form.

![](_attachments/B2BiSFTPDefaultSettings1-2.png)

The default **SFTP Server Listen Port** must be changed to the B2Bi service port configured in OpenShift.

26. Switch back to the OpenShift web console browser window or tab and click **Services** under the **Networking** in the left-hand menu bar.

![](_attachments/OpenShiftRoutesPageToServices.png)

??? question "BP quiz question"
    There is a quiz question related to other B2Bi services. You may want to take note of the other service names or take a screen capture.

27. Find and click the **sterling-fg-b2bi-asi-backend-svc** link.

![](_attachments/OSServicesASI.png)

28. Locate and copy the **Node Port** number for **adapters-1** in the **Service port mapping** table.

![](_attachments/OSServicesASIOverview-NodePort.png)

29. Record the **Node Port** number, it will be used several times during this demonstration.

30. Switch back to the **B2Bi Dashboard** browser window or tab.

??? question "BP quiz question"
    There is a quiz question related to configuring the SFTP adapter. Before clicking **Next** in the following step, look at the alternate **Compression** type available for the SFTP adapter. You may want to record that value.

31. Enter or copy the recorded **Service Port** number into the **SFTP Server Listen Port** entry field and click **Next**.

![](_attachments/B2BiSFTPDefaultSettings2-2.png)

32. Review the default settings on the **SFTP Server Adapter: Configuration: Document Storage** page and click **Next**.

![](_attachments/B2BiSFTPStroage.png)

33. Review the default settings on the **SFTP Server Adapter: Add Policies** page and click **Next**.

![](_attachments/B2BiSFPPolicies.png)

34. Review the default settings on the **SFTP Server Adapter: Configuration** page and click **Next**.

![](_attachments/B2BiSFTPConfigPage.png)

35. Review the default settings on the **SFTP Server Adapter: Extractability** page and click **Next**.

![](_attachments/B2BiSFTPExtractability.png)

36. Review the **SFTP Server Adapter: Confirmation** page and click **Finish**.

![](_attachments/B2BiSFTPFinish.png)

37. Click **Return** after the new SFTP adapter has been created.

![](_attachments/B2BiSFTPConfirmation.png)

38. Click the **checkbox** next to the **SFTP Server Adapter** to start the adapter.

![](_attachments/B2BiSFTPStartAdapter-2.png)

39. Click the ![](_attachments/BangIcon.png) icon next to the **SFTP Server Adapter**.

![](_attachments/B2BiSFTPAdapterEnabled-2.png)

40. Verify the **SFTP Server Adapter** is **Running** and then click the **Close** button.

![](_attachments/B2BiSFTPAdapterStatus-2.png)

41. Click the **Logout** link to log out of the **B2Bi dashboard**.

![](_attachments/B2BiLogout-2.png)

Now that the SFTP adapter is running, it time to move to the next step in the configuration of B2Bi.
