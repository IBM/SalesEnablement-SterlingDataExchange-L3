In this chapter, learn how to create a B2Bi partner community, add partners to the community, create a routing template, and create routing channels.

## Create a partner community

1. Return to the OpenShift web console and click on the route link to the IBM Sterling File Gateway user interface (UI): **sterling-fg-b2bi-asi-internal-route-filegateway**.

![](_attachments/OSRoutesFileGateway.png)

2. Enter **fg_sysadmin** in the User ID field, **password** in the Password field, and then click the **Sign In** button.

![](_attachments/FG_login.png)

3. Click the **Participants** pull-down menu item on top menu bar.

![](_attachments/FG_Participants.png)

4. Click **Communities** in the **Participants** menu.

![](_attachments/FG_CommunitiesMenu.png)

5. In the **Communities** pop-up window, click the **add** link.

![](_attachments/FG_CommunitiesAddLink.png)

6. Enter **sftp_community** in the **Community Name** entry field and click **Next**.

![](_attachments/FG_CommunitiesName-2.png)

7. Select both the **Partner Initiates Protocol Connections to Mailbox** and the **Partner Listens for Protocol Connections**.

![](_attachments/FG_CommunitiesProtocol-1-2.png)

8. Select the **SSH/SFTP** checkbox and click **Next**.

![](_attachments/FG_CommunitiesProtocol-2-2.png)

9. Click **Next** on the **Add Community: Notifications** form.

![](_attachments/FG_CommunitiesNotifications.png)

10. Click **Finish** to confirm the creation of the new community.

![](_attachments/FG_CommunitiesFinish-2.png)

11. Click **Return** on the community confirmation screen.

![](_attachments/FG_CommunitiesComplete.png)

## Add partners to the partner community

Next, add 2 partners to the newly created **sftp_community**.

12. Click the **edit** link for the **sftp_community** on the **Communities** pop-up window.

![](_attachments/FG_CommunitiesEdit.png)

13. Under **Partner**, click the **Add** link.

![](_attachments/FG_CommunitiesDetails-2.png)

14. Enter **partner1** in the **Partner Name** field, 10 digits in the **Phone** field, **partner1@localhost.com** in the **Email Address** field, and then click **Next**.

![](_attachments/FG_CommunitiesPartner1.png)

15. Enter **partner1** in the **User Name** field, **password** in the **Password** field, **password** in the **Confirm Password** field, **Partner** in the **Given Name** field, **One** in **Surname** field, and then click **Next**.

![](_attachments/FG_CommunitiesPartner1Password.png)

16. Click **partner1 is a Producer of Data** and then click **Next**.

![](_attachments/FG_CommunitiesPartner1Role.png)

17. Review the default settings on the **Initiate Connections Settings** screen and then click **Next**.

![](_attachments/FG_CommunitiesPartner1ICS.png)

18. Review the default settings on the **PGP Settings** screen and then click **Next**.

![](_attachments/FG_CommunitiesPartner1PGP.png)

19. Review the settings for **partner1** and click **Finish**.

![](_attachments/FG_CommunitiesPartner1Confirm.png)

20. Click **Return** on the **Added Partner Successful** screen.

![](_attachments/FG_CommunitiesPartner1Success.png)

21. Repeat the Steps 13 through 20 to create a second partner named **partner2** using the same settings.

![](_attachments/FG_CommunitiesPartner2.png)

22. Click **Return** on the **Edit Community: sftp_community** screen after creating both partners.

![](_attachments/FG_CommunitiesReturn-2.png)

23. Close the **Communities** pop-up window.

![](_attachments/FS_CommunitiesClose.png)

24. Click **Partners** under the **Participants** menu.

![](_attachments/FG_ParticipantsPartnersMenu.png)

25. Click the **Refresh** button if **partner1** and **partner2** do not appear in the **Partners** table.

![](_attachments/FG_PartnersTable.png)

## Create a routing template

26. Click **Templates** under the **Routes** menu.

![](_attachments/FG_RoutesMenuTemplates.png)

27. Click the **Create** button at the bottom of the **Routing Channel Templates** page.

![](_attachments/FG_Templates.png)

28. Enter **Passthrough** in the **Template Name** field and then click **Next>>**.

![](_attachments/FG_TemplateCreateName.png)

29. Review the **Special Characters** settings and then click **Next>>**.

![](_attachments/FG_TemplateCreateSpecialChars.png)

30. Add **All Partners** to both the **Producer Groups** and **Consumer Groups** tables.

![](_attachments/FG_TemplateCreateGroups1.png)

31. Click **Next>>** after adding **All Partners** to both groups.

![](_attachments/FG_TemplateCreateGroups2.png)

32. Review the **Provisioning Facts** page and then click **Next>>**.

![](_attachments/FG_TemplateCreateProvisioningFacts.png)

33. Review the **File Operation** page and then click **Next>>**.

![](_attachments/FG_TemplateCreateFileOperation.png)

34. Click the **Add** button on the **Producer** page.

![](_attachments/FG_TemplateCreateProducerAdd.png)

35. Click the **Producer File Type** pull-down menu and select **Unknown**.

![](_attachments/FG_TemplateCreateProducerUnknownMenuSelect.png)

36. Enter **.+** in the **File name pattern as regular expression** field and then click **Save**.

![](_attachments/FG_TemplateCreateProducerUnknownPattern.png)

Setting the file pattern to the regular expression **.+** allows for file names of one or more characters.

37. Click **Next>>** on the **Producer** page.

![](_attachments/FG_TemplateCreateProducerNext.png)

38. Click the **Add** button on the **Consumer** page.

![](_attachments/FG_TemplateCreateConsumerAdd.png)

39. Click the **Add** button on the **New Delivery Channel** pop-up window.

![](_attachments/FG_TemplateCreateConsumerNewDeliveryChannel.png)

40. Click **Unknown** in the **Consumer File Type** pull-down menu.

![](_attachments/FG_TemplateCreateConsumerNewDeliveryChannelFileTypeMenu.png)

41. Enter **${ProducerFileName}** in the **File name format*** field.

```
${ProducerFileName}
```

42. Review the help information regarding file name formats by hovering over the **File name format** entry field and then click **Save**.

![](_attachments/FG_TemplateCreateConsumerNewDeliveryChannelFileTypeFormat.png)

43. Click **Save** on the **New Delivery Channel** pop-up window.

![](_attachments/FG_TemplateCreateConsumerNewDeliveryChannelSave.png)

44. Click **Save** on the **Consumer** page.

![](_attachments/FG_TemplateCreateConsumerSave.png)

45. Click **OK** on the **Routing Channel Template successfully created.** pop-up message.

![](_attachments/FS_TemplateCreated.png)

46. Review the settings for the new **Passthrough** routing channel template.

![](_attachments/FS_TemplateSummary.png)

## Create routing channels

47. Click the **Channels** option under the **Routes** menu.

![](_attachments/FG_RoutesChannelsMenu.png)

48. Click the **Create** button at bottom right to create a new **Channel**.

![](_attachments/FG_ChannelCreate.png)

49. Select **Passthrough** for the **Routing Channel Template**, **partner1** for the **Producer**, and **partner2** for the **Consumer**, and then click **Save** to create the new channel.

![](_attachments/FG-ChannelCreateP1toP2.png)

50. Click **OK** on the **Success** pop-up window.

![](_attachments/FG_ChannelCreateP1toP2Success.png)

51. Repeat the steps 48 through 50 to create a channel from partner2 to partner1.

![](_attachments/FG-ChannelCreateP2toP1.png)

52. Click **Sign Out**.

![](_attachments/FG-SignOut.png)

In the next chapter, the fun begins as the partners start to securely exchange files.
