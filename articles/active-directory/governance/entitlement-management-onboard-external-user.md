---
title: Tutorial - Onboard external users to Azure AD through an approval process - Azure Active Directory
description: Step-by-step tutorial for how to create an access package for external users requiring approvals in Azure Active Directory entitlement management.
services: active-directory
documentationCenter: ''
author: sama
ms.service: active-directory
ms.workload: identity
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: tutorial
ms.subservice: compliance
ms.date: 08/18/2021
ms.author: sama
ms.collection: M365-identity-device-management


#Customer intent: As a IT admin, I want step-by-step instructions for creating an access package for managing external users through approvals.

---
# Tutorial - Onboard external users to Azure AD through an approval process

You can use entitlement management as a way of onboarding external users. This feature allows external users to request access to a set of resources and where you can set up approvals before they gain access to your directory. For external users onboarded through entitlement, you can manage their lifecycle through access packages. When their last access package expires, they'll be removed from your directory.

In this tutorial, you work for WoodGrove Bank as an IT administrator. You’ve been asked to create an access package to onboard partners from an outside organization that your business group is working with. They will need access to a Teams group called **External collaboration**. 
Approval is needed by an by internal sponsor for collaborating organizations. Also, you've been informed that the partner's access needs to expire after 60 days.
To use Azure AD entitlement management, you must have one of the following licenses:

- Azure AD Premium P2
- Enterprise Mobility + Security (EMS) E5 license

For more information, see [License requirements](entitlement-management-overview.md#license-requirements).

## Step 1: Configure basics

**Prerequisite role:** Global administrator, Identity Governance administrator, User administrator, Catalog owner, or Access package manager

1. In the Azure portal, in the left navigation, click **Azure Active Directory**.

2. In the left menu, click **Identity Governance**.

3. In the left menu, click **Access packages**. If you see Access denied, ensure that an Azure AD Premium P2 license is present in your directory.

4. Click **New access package**.

5. On the **Basics** tab, enter the name **External user package** and description **Access for external users pending approval**.

6. You can leave the **Catalog** drop-down list set to **General**.

## Step 2: Configure resources

1. Click **Next** to open the **Resource roles** tab.
 
   On this tab, you select the resources and the resource role to include in the access package.

2. Click on **Groups and Teams** and search for your group **External collaboration**.

## Step 3: Configure requests

1. Click **Next** to open the **Requests** tab.

   On this tab, you create a request policy. A *policy* defines the rules or guardrails to access an access package. You create a policy that allows a specific user in the resource directory to request this access package.

2. In the **Users who can request access** section, click **For users not in your directory** and then click **All users (All connected organizations + any new external users)**.

3. Ensure that **Require approval** is set to **Yes**.

4. The following settings allow you to configure how your approvals work for your external users:

5. For **Require requestor justification**, leave this as **Yes**.

6. For **How many stages** leave this as **1**.

7. For **Approver** scenario select **Internal sponsor**. This option comes from a configured [Connected Org](entitlement-management-organization.md) where you can sponsors for specific organizations you're working with. This allows you to set someone specified in the Connected Org from within your organization to be the approver. 

8. For **Decision must be made in how many days?** leave this as **14**.

9. For **Require approver justification** leave this as **Yes**.

10. Set **Enable new requests and assignments** to **Yes** to enable this access package to be requested as soon as it's created.

## Step 4: Configure requestor information

1. Click **Next** to open the **Requestor information** tab

2. On this screen, you can ask additional questions to collect more information from your requestor. These questions are shown on their request form and can be set to required or optional. For now you can leave these as empty.

## Step 5: Configure lifecycle

1. Click **Next** to open the **Lifecycle** tab

2. In the **Expiration** section, set **Access package assignment expire** to **Number of days**.

3. Set **Assignment expire after** to **60** days. This field determines when your guest users will have to renew their access.

4. You can also configure **Access Reviews** which allows periodic checks of whether the guest still needs access to the access package. A review can be a self-review or you can set specific reviews for this task. For more information, see [Access Reviews](entitlement-management-access-reviews-create.md).

## Step 6: Review and create your access package

1. Click **Next** to open the **Review + Create** tab.

2. On this screen, you can review the configuration for your access package before creating. If there are any issues, you can use the tabs to navigate to a specific point in the create experience to make edits.

3. When you're happy with your selections, click on **Create**. After a few moments, you should see a notification that the access package was successfully created.

4. Once created, you’ll be brought to the **Overview** page for your access package. You can find the **My Access portal link** and copy the value here. Share this link with your external users and they can go to request this package to start collaborating.

## Step 7: Clean up resources

In this step, you can delete the **External user package** access package. 

**Prerequisite role:** Global administrator, Identity Governance administrator or Access package manager

1. In the **Azure portal**, in the left navigation, click **Azure Active Directory**.

2. In the left menu, click **Identity Governance**.

3. In the left menu, click **Access Packages**. 

4. Open the **External user package** access package. 

5. Click **Resource Roles**.

6. Select the **External collaboration** group you added to this access package, and in the **Details** pane, select **Remove resource role**. In the message that appears, select **Yes**.

7. Open the list of access packages.

8. For **External user package**, select the ellipsis (...) and then select **Delete**. In the message that appears, select **Yes**.

## Next steps

Learn about creating access packages to manage access to other types of resources such as applications, and sites. [Tutorial: Manage access to resources in Azure AD entitlement management](/active-directory/governance/entitlement-management-access-package-first.md)
