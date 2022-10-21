In this chapter, learn how to configure the Secure File Transfer Protocol (SFTP) adapter using the containerized B2Bi deployment.

1. In the OpenShift web console, click **Routes** under the **Network** section in left-hand panel.

![](_attachments/OSOverviewToRoutes.png)

2. Click the **All Projects** pull-down menu and click the **b2bi** project.

![](_attachments/OSRoutesMenu.png)

3. Notice all the routes that are currently defined in the b2bi Project, there are 15 of them

![](_attachments/OSB2BiAllRoutes.png)

4. To start the setup of the test partner accounts, launch the IBM Sterling B2Bi dashboard by clicking on the route for the sterling-fg-b2bi-asi-internal-route-dashboard route in the **Location** column. Do not click the Route name... click the Route link in the **Location** column of the table.

![](_attachments/OSB2BiDashboardRoute.png)

5. If a security risk is received in the browser, accept it. In a production environment certificates would be configured for these web pages.

![](_attachments/FFSecurityRisk1.png)
![](_attachments/FFSecurityRisk2.png)

Note: the images above are from Firefox running on MacOS. They will look different depending on browser and operating system.

!!! hint
    As this is a new install, in this demonstration the default user ids and passwords will be used. To keep things simple in this demonstration, all passwords will be set to **password**.  Not secure, but this will be a short lived demonstration environment.

6. Enter **admin** in the **User ID** field and **password** in the **Password** field, and then click **Sign In**.

![](_attachments/B2BiAdminLogin.png)

First, a **SSH Host Identity** needs to be created. The Host Identity Key is a Private/Public key pair used to identify the Application SFTP Server to remote clients.  Note, for this demonstration, default values will be used where possible, but production deployments may use other values depending on client requirements.

7. Click the **Deployment** menu item in left-hand menu bar.

![](_attachments/B2BiMainMenuToDeployment.png)

8. Click the **SSH Host Identity Key** menu item in the left-hand menu bar.

![](_attachments/B2BiMainMenuDeploymentToHIK.png)

9. Click the **Go!** button in the **Create: New Host Identity Key** box.

![](_attachments/B2BiHIK-CreatePage.png)

10. Enter **demo** in the **Host Name:** field of the "New Host Identity Key" form and then click the **Next** button.

![](_attachments/B2BiHIK-HostName.png)

11. Click **Finish**.

![](_attachments/B2BiHIK-Finish.png)

12. Click **OK**

![](_attachments/B2BiHIKCreated.png)

13. Wait until the completed message is received and the click the **Return** button.

![](_attachments/B2BiHIKCreatedCompleted.png)

Next, an SFTP adapter must be created which will utilize the OpenShift service port for B2Bi.

14. Click the **Services** menu item under **Deployment** in the left-hand menu bar.

![](_attachments/B2BiMainMenuDeploymentToServices.png)

15. Click the **Configuration** menu item under **Services**.

![](_attachments/B2BiMainMenuServicesToConfiguration.png)

16. Enter **sftp** in the **Service Name** field and click the **Go!** button in the **Search** box.

![](_attachments/B2BiServicesConfiguratonForm.png)

17. Locate the **SFTP Server Adapter** entry in the table and click the **edit** button.

![](_attachments/B2BiServicesConfigurationSearchResults.png)

18. Review the default settings and click **Next**.

![](_attachments/B2BiSFTPAdapterName1.png)

19. Review the settings on the **SFTP Server Adapter: Configuration** form.

![](_attachments/B2BiSFTPDefaultSettings1.png)

The default **SFTP Server Listen Port** must be changed to the B2Bi service port configured in OpenShift.

20. Switch back to the OpenShift web console browser window or tab and click the **Services** under the **Networking** in the left-hand menu bar.

![](_attachments/OpenShiftRoutesPageToServices.png)

21. Find and click the **sterling-fg-b2bi-asi-backend-svc** link.

![](_attachments/OSServicesASI.png)

22. Locate and copy the **Service Port** number for **adapters-1** in the **Service port mapping** table.

![](_attachments/OSServicesASIOverview.png)

23. Record this **Service Port** number, it will be used several times during this demonstration.

24. Switch back to the **B2Bi Dashboard** browser window or tab.

![](_attachments/B2BiSFTPDefaultSettings1.png)

25. Enter or copy the recorded **Service Port** number into the **SFTP Server Listen Port** entry field and click **Next**.

![](_attachments/B2BiSFTPDefaultSettings2.png)

26. Click **Next** on the **SFTP Server Adapter: Configuration: Document Storage** page.

![](_attachments/B2BiSFTPStroage.png)

27. Review the default settings on the **SFTP Server Adapter: Add Policies** page and click **Next**.

![](_attachments/B2BiSFPPolicies.png)

28. Review the default settings on the **SFTP Server Adapter: Configuration** page and click **Next**.

![](_attachments/B2BiSFTPConfigPage.png)

29. Review the default settings on the **SFTP Server Adapter: Extractability** page and click **Next**.

![](_attachments/B2BiSFTPExtractability.png)

30. Review the **SFTP Server Adapter: Confirmation** page and click **Finish**.

![](_attachments/B2BiSFTPFinish.png)

31. Click **Return** after the new SFTP adapter has been created.

![](_attachments/B2BiSFTPConfirmation.png)

32. Click the **checkbox** next to the **SFTP Server Adapter** to start the adapter.

![](_attachments/B2BiSFTPStartAdapter.png)

33. Click the ![](_attachments/BangIcon.png) next to the **SFTP Server Adapter**.

![](_attachments/B2BiSFTPAdapterEnabled.png)

34. Verify the **SFTP Server Adapter** is **Running**.

![](_attachments/B2BiSFTPAdapterStatus.png)

35. Close the **Adapter Information** pop-up window.

![](_attachments/B2BiSFTPAdapterStatus2.png)

36. Click the **Logout** link to log out of the **B2Bi dashboard**.

![](_attachments/B2BiLogout.png)

Now that the SFTP adapter is running, it time to move to the next step in the configuration of B2Bi.
