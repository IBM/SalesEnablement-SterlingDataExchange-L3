Create Partner community

Return to the OpenShift web console and click on the route link to the IBM Sterling File Gateway user interface (UI): **sterling-fg-b2bi-asi-internal-route-filegateway portal

OSRoutesFileGateway.png

At the IBM Sterling File Gateway

Enter **fg_sysadmin** in the User ID field, **password** in the Password field, and then click the **Sign In** button.

FG_login.png

Click the **Participants** pull-down menu item on top menu bar.

FG_Participants.png

Click **Communities** in the **Participants** menu.

FG_CommunitiesMenu.png

In the **Communities** pop-up window, click the **add** link.

FG_CommunitiesAddLink.png

Enter **sftp_community** in the **Community Name** entry field and click **Next**.

FG_CommunitiesName.png

Select both the **Partner Initiates Protocol Connections to Mailbox** and the **Partner Listens for Protocol Connections** check boxes.

FG_CommunitiesProtocol-1.png

Select the **SSH/SFTP** checkbox and click **Next**.

FG_CommunitiesProtocol-2.png

Click **Next** on the **Add Community: Notifications** form.

FG_CommunitiesNotifications.png

Click **Finish** to confirm the creation of the new community.

FG_CommunitiesFinish.png

Click **Return** on the community confirmation screen.

FG_CommunitiesComplete.png

Next, add 2 partners to the newly created **sftp_community**.

Click the **edit** link for the **sftp_community** on the **Communities** listing pop-up window.

FG_CommunitiesEdit.png

Under **Partner**, click the **Add** link.

FG_CommunitiesDetails.png

Enter **partner1** in the **Partner Name** field, 10 digits in the **Phone** field and **partner1@localhost.com** in the **Email Address** field, and then click **Next**.

FG_CommunitiesPartner1.png

Enter **partner1** in the **User Name** field, **password** in the **Password** field, **password** in the **Confirm Passwod** field, **Partner** in the **Given Name** field, and **Surname** field, and then click **Next**.

FG_CommunitiesPartner1Password.png

Click **partner1 is a Producer of Data** and then click **Next**.

FG_CommunitiesPartner1Role.png

Review the default settings on the **Initiate Connections Settings** screen and then click **Next**.

FG_CommunitiesPartner1ICS.png

Review the default settings on the **PGP Settings** screen and then click **Next**.

FG_CommunitiesPartner1PGP.png

Review the settings for **partner1** and click **Finish**.

FG_CommunitiesPartner1Confirm.png


Click **Return** on the **Added Partner Successful** screen.

FG_CommunitiesPartner1Success.png

Repeat the last 8 steps to create a second partner named **partner2** using the same settings.

FG_CommunitiesPartner2.png

Click **Return** on the **Edit Community: sftp_community** screen after creating both partners.

FG_CommunitiesReturn.png

Close the **Communities** pop-up window.

FS_CommunitiesClose.png

Click **Partners** under the **Participants** menu.

FG_ParticipantsPartnersMenu.png

Click the **Refresh** button if **partner1** and **partner2** do not appear in the **Partners** table.

FG_PartnersTable.png

## Create routing template

Click **Templates** under the **Routes** menu.

FG_RoutesMenuTemplates.png

Click the **Create** button at the bottom of the **Routing Channel Templates** page.

FG_Templates.png

Enter **Passthrough** in the **Template Name** field and then click **Next>>**.

FG_TemplateCreateName.png

Review the **Special Characters** settings and then click **Next>>**.

FG_TemplateCreateSpecialChars.png

Add **All Partners** to both the **Producer Groups** and **Consumer Groups** tables.

FG_TemplateCreateSpecialGroups1.png

Click **Next>>** after adding **All Partners** to both groups.

FG_TemplateCreateSpecialGroups2.png

Review the **Provisioning Facts** page and then click **Next>>**.

FG_TemplateCreateProvisioningFacts.png

Review the **File Operation** page and then click **Next>>**.

FG_TemplateCreateFileOperation.png

Click the **Add** button on the **Producer** page.

FG_TemplateCreateProducerAdd.png

Click the **Producer File Type** pull-down menu and select **Unknown**.

FG_TemplateCreateProducerUnknownMenuSelect.png

Enter **.+** in the **File name pattern as regular expression** field and then click **Save**.

FG_TemplateCreateProducerUnknownPattern.png

Setting the file pattern to the regular express **.+** allows for file names of one or more characters.

Click **Next>>** on the **Producer**  page.

FG_TemplateCreateProducerNext.png

Click the **Add** button on the **Consumer** page.

FG_TemplateCreateConsumerAdd.png

Click the **Add** button on the **New Delivery Channel** pop-up window.

FG_TemplateCreateConsumerNewDeliveryChannel.png

Click **Unknown** in the **Consumer File Type** pull-down menu.

FG_TemplateCreateConsumerNewDeliveryChannelFileTypeMenu.png

Enter **${ProducerFileName}** in the **File name format*** field.

```
${ProducerFileName}
```

Review the help information regarding file name formats by overing over the **File name format** entry field and then click **Save**.

FG_TemplateCreateConsumerNewDeliveryChannelFileTypeFormat.png

Click **Save** on the **New Delivery Channel** pop-up window.

FG_TemplateCreateConsumerNewDeliveryChannelSave.png

Click **Save** on the **Consumer** page.

FG_TemplateCreateConsumerSave.png

Click **OK** on the **Routing Channel Template successfully created.** pop-up message.

FS_TemplateCreated.png

Review the settings for the new **Passthrough** routing channel template.

FS_TemplateSummary.png

Click the **Channels** option under the **Routes** menu.

FG_RoutesChannelsMenu.png

Click the **Create** button at bottom right to create a new **Channel**.

FG_ChannelCreate.png

Select **Passthrough** for the **Routing Channel Template**, **partner1** for the **Producer**, and **partner2**  for the **Consumer**, and then click **Save** to create the new channel.

FG-ChannelCreateP1toP2.png

Click **OK** on the **Success** pop-up window.

FG_ChannelCreateP1toP2Success.png

Repeat the last 3 steps to create a channel from partner2 to partner 1.

FG-ChannelCreateP2toP1

Click **Sign Out**.

FG-SignOut.png

In the next chapter, the fun begins as the partners start to securely exchange files.
