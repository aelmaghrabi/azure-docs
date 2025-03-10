---
title: Concepts - Identity and access
description: Learn about the identity and access concepts of Azure VMware Solution
ms.topic: conceptual
ms.date: 07/29/2021
---

# Azure VMware Solution identity concepts

Azure VMware Solution private clouds are provisioned with a vCenter Server and NSX-T Manager. You'll use vCenter to manage virtual machine (VM) workloads and NSX-T Manager to manage and extend the private cloud. The CloudAdmin role is used for vCenter and restricted administrator rights for NSX-T Manager. 

## vCenter access and identity

[!INCLUDE [vcenter-access-identity-description](includes/vcenter-access-identity-description.md)]

> [!IMPORTANT]
> Azure VMware Solution offers custom roles on vCenter but currently doesn't offer them on the Azure VMware Solution portal. For more information, see the [Create custom roles on vCenter](#create-custom-roles-on-vcenter) section later in this article. 

### View the vCenter privileges

You can view the privileges granted to the Azure VMware Solution CloudAdmin role on your Azure VMware Solution private cloud vCenter.

1. Sign in to the vSphere Client and go to **Menu** > **Administration**.

1. Under **Access Control**, select **Roles**.

1. From the list of roles, select **CloudAdmin** and then select **Privileges**. 

   :::image type="content" source="media/concepts/role-based-access-control-cloudadmin-privileges.png" alt-text="Screenshot showing the roles and privileges for CloudAdmin in the vSphere Client.":::

The CloudAdmin role in Azure VMware Solution has the following privileges on vCenter. For more information, see the [VMware product documentation](https://docs.vmware.com/en/VMware-vSphere/7.0/com.vmware.vsphere.security.doc/GUID-ED56F3C4-77D0-49E3-88B6-B99B8B437B62.html).

| Privilege | Description |
| --------- | ----------- |
| **Alarms** | Acknowledge alarm<br />Create alarm<br />Disable alarm action<br />Modify alarm<br />Remove alarm<br />Set alarm status |
| **Content Library** | Add library item<br />Create a subscription for a published library<br />Create local library<br />Create subscribed library<br />Delete library item<br />Delete local library<br />Delete subscribed library<br />Delete subscription of a published library<br />Download files<br />Evict library items<br />Evict subscribed library<br />Import storage<br />Probe subscription information<br />Publish a library item to its subscribers<br />Publish a library to its subscribers<br />Read storage<br />Sync library item<br />Sync subscribed library<br />Type introspection<br />Update configuration settings<br />Update files<br />Update library<br />Update library item<br />Update local library<br />Update subscribed library<br />Update subscription of a published library<br />View configuration settings |
| **Cryptographic operations** | Direct access |
| **Datastore** | Allocate space<br />Browse datastore<br />Configure datastore<br />Low-level file operations<br />Remove files<br />Update virtual machine metadata |
| **Folder** | Create folder<br />Delete folder<br />Move folder<br />Rename folder |
| **Global** | Cancel task<br />Global tag<br />Health<br />Log event<br />Manage custom attributes<br />Service managers<br />Set custom attribute<br />System tag |
| **Host** | vSphere Replication<br />&#160;&#160;&#160;&#160;Manage replication |
| **Network** | Assign network |
| **Permissions** | Modify permissions<br />Modify role |
| **Profile** | Profile driven storage view |
| **Resource** | Apply recommendation<br />Assign vApp to resource pool<br />Assign virtual machine to resource pool<br />Create resource pool<br />Migrate powered off virtual machine<br />Migrate powered on virtual machine<br />Modify resource pool<br />Move resource pool<br />Query vMotion<br />Remove resource pool<br />Rename resource pool |
| **Scheduled task** | Create task<br />Modify task<br />Remove task<br />Run task |
| **Sessions** | Message<br />Validate session |
| **Storage view** | View |
| **vApp** | Add virtual machine<br />Assign resource pool<br />Assign vApp<br />Clone<br />Create<br />Delete<br />Export<br />Import<br />Move<br />Power off<br />Power on<br />Rename<br />Suspend<br />Unregister<br />View OVF environment<br />vApp application configuration<br />vApp instance configuration<br />vApp managedBy configuration<br />vApp resource configuration |
| **Virtual machine** | Change Configuration<br />&#160;&#160;&#160;&#160;Acquire disk lease<br />&#160;&#160;&#160;&#160;Add existing disk<br />&#160;&#160;&#160;&#160;Add new disk<br />&#160;&#160;&#160;&#160;Add or remove device<br />&#160;&#160;&#160;&#160;Advanced configuration<br />&#160;&#160;&#160;&#160;Change CPU count<br />&#160;&#160;&#160;&#160;Change memory<br />&#160;&#160;&#160;&#160;Change settings<br />&#160;&#160;&#160;&#160;Change swapfile placement<br />&#160;&#160;&#160;&#160;Change resource<br />&#160;&#160;&#160;&#160;Configure host USB device<br />&#160;&#160;&#160;&#160;Configure raw device<br />&#160;&#160;&#160;&#160;Configure managedBy<br />&#160;&#160;&#160;&#160;Display connection settings<br />&#160;&#160;&#160;&#160;Extend virtual disk<br />&#160;&#160;&#160;&#160;Modify device settings<br />&#160;&#160;&#160;&#160;Query fault tolerance compatibility<br />&#160;&#160;&#160;&#160;Query unowned files<br />&#160;&#160;&#160;&#160;Reload from paths<br />&#160;&#160;&#160;&#160;Remove disk<br />&#160;&#160;&#160;&#160;Rename<br />&#160;&#160;&#160;&#160;Reset guest information<br />&#160;&#160;&#160;&#160;Set annotation<br />&#160;&#160;&#160;&#160;Toggle disk change tracking<br />&#160;&#160;&#160;&#160;Toggle fork parent<br />&#160;&#160;&#160;&#160;Upgrade virtual machine compatibility<br />Edit inventory<br />&#160;&#160;&#160;&#160;Create from existing<br />&#160;&#160;&#160;&#160;Create new<br />&#160;&#160;&#160;&#160;Move<br />&#160;&#160;&#160;&#160;Register<br />&#160;&#160;&#160;&#160;Remove<br />&#160;&#160;&#160;&#160;Unregister<br />Guest operations<br />&#160;&#160;&#160;&#160;Guest operation alias modification<br />&#160;&#160;&#160;&#160;Guest operation alias query<br />&#160;&#160;&#160;&#160;Guest operation modifications<br />&#160;&#160;&#160;&#160;Guest operation program execution<br />&#160;&#160;&#160;&#160;Guest operation queries<br />Interaction<br />&#160;&#160;&#160;&#160;Answer question<br />&#160;&#160;&#160;&#160;Back up operation on virtual machine<br />&#160;&#160;&#160;&#160;Configure CD media<br />&#160;&#160;&#160;&#160;Configure floppy media<br />&#160;&#160;&#160;&#160;Connect devices<br />&#160;&#160;&#160;&#160;Console interaction<br />&#160;&#160;&#160;&#160;Create screenshot<br />&#160;&#160;&#160;&#160;Defragment all disks<br />&#160;&#160;&#160;&#160;Drag and drop<br />&#160;&#160;&#160;&#160;Guest operating system management by VIX API<br />&#160;&#160;&#160;&#160;Inject USB HID scan codes<br />&#160;&#160;&#160;&#160;Install VMware tools<br />&#160;&#160;&#160;&#160;Pause or Unpause<br />&#160;&#160;&#160;&#160;Wipe or shrink operations<br />&#160;&#160;&#160;&#160;Power off<br />&#160;&#160;&#160;&#160;Power on<br />&#160;&#160;&#160;&#160;Record session on virtual machine<br />&#160;&#160;&#160;&#160;Replay session on virtual machine<br />&#160;&#160;&#160;&#160;Suspend<br />&#160;&#160;&#160;&#160;Suspend fault tolerance<br />&#160;&#160;&#160;&#160;Test failover<br />&#160;&#160;&#160;&#160;Test restart secondary VM<br />&#160;&#160;&#160;&#160;Turn off fault tolerance<br />&#160;&#160;&#160;&#160;Turn on fault tolerance<br />Provisioning<br />&#160;&#160;&#160;&#160;Allow disk access<br />&#160;&#160;&#160;&#160;Allow file access<br />&#160;&#160;&#160;&#160;Allow read-only disk access<br />&#160;&#160;&#160;&#160;Allow virtual machine download<br />&#160;&#160;&#160;&#160;Clone template<br />&#160;&#160;&#160;&#160;Clone virtual machine<br />&#160;&#160;&#160;&#160;Create template from virtual machine<br />&#160;&#160;&#160;&#160;Customize guest<br />&#160;&#160;&#160;&#160;Deploy template<br />&#160;&#160;&#160;&#160;Mark as template<br />&#160;&#160;&#160;&#160;Modify customization specification<br />&#160;&#160;&#160;&#160;Promote disks<br />&#160;&#160;&#160;&#160;Read customization specifications<br />Service configuration<br />&#160;&#160;&#160;&#160;Allow notifications<br />&#160;&#160;&#160;&#160;Allow polling of global event notifications<br />&#160;&#160;&#160;&#160;Manage service configuration<br />&#160;&#160;&#160;&#160;Modify service configuration<br />&#160;&#160;&#160;&#160;Query service configurations<br />&#160;&#160;&#160;&#160;Read service configuration<br />Snapshot management<br />&#160;&#160;&#160;&#160;Create snapshot<br />&#160;&#160;&#160;&#160;Remove snapshot<br />&#160;&#160;&#160;&#160;Rename snapshot<br />&#160;&#160;&#160;&#160;Revert snapshot<br />vSphere Replication<br />&#160;&#160;&#160;&#160;Configure replication<br />&#160;&#160;&#160;&#160;Manage replication<br />&#160;&#160;&#160;&#160;Monitor replication |
| **vService** | Create dependency<br />Destroy dependency<br />Reconfigure dependency configuration<br />Update dependency |
| **vSphere tagging** | Assign and unassign vSphere tag<br />Create vSphere tag<br />Create vSphere tag category<br />Delete vSphere tag<br />Delete vSphere tag category<br />Edit vSphere tag<br />Edit vSphere tag category<br />Modify UsedBy field for category<br />Modify UsedBy field for tag |

### Create custom roles on vCenter

Azure VMware Solution supports the use of custom roles with equal or lesser privileges than the CloudAdmin role. 

You'll use the CloudAdmin role to create, modify, or delete custom roles with privileges lesser than or equal to their current role. You can create roles with privileges greater than CloudAdmin, but you can't assign the role to any users or groups or delete the role.

To prevent creating roles that can't be assigned or deleted, clone the CloudAdmin role as the basis for creating new custom roles.

#### Create a custom role
1. Sign in to vCenter with cloudadmin\@vsphere.local or a user with the CloudAdmin role.

1. Navigate to the **Roles** configuration section and select **Menu** > **Administration** > **Access Control** > **Roles**.

1. Select the **CloudAdmin** role and select the **Clone role action** icon.

   >[!NOTE] 
   >Don't clone the **Administrator** role because you can't use it. Also, the custom role created can't be deleted by cloudadmin\@vsphere.local.

1. Provide the name you want for the cloned role.

1. Add or remove privileges for the role and select **OK**. The cloned role is visible in the **Roles** list.


#### Apply a custom role

1. Navigate to the object that requires the added permission. For example, to apply permission to a folder, navigate to **Menu** > **VMs and Templates** > **Folder Name**.

1. Right-click the object and select **Add Permission**.

1. Select the Identity Source in the **User** drop-down where the group or user can be found.

1. Search for the user or group after selecting the Identity Source under the **User** section. 

1. Select the role that you want to apply to the user or group.

1. Check the **Propagate to children** if needed, and select **OK**. The added permission displays in the **Permissions** section.

## NSX-T Manager access and identity

>[!NOTE]
>NSX-T [!INCLUDE [nsxt-version](includes/nsxt-version.md)] is currently supported for all new private clouds.

Use the *admin* account to access NSX-T Manager. It has full privileges and lets you create and manage Tier-1 (T1) gateways, segments (logical switches), and all services. In addition, the privileges give you access to the NSX-T Tier-0 (T0) gateway. A change to the T0 gateway could result in degraded network performance or no private cloud access. Open a support request in the Azure portal to request any changes to your NSX-T T0 gateway.

 
## Next steps

Now that you've covered Azure VMware Solution access and identity concepts, you may want to learn about:

- [How to configure external identity source for vCenter](configure-identity-source-vcenter.md)

- [How to enable Azure VMware Solution resource](deploy-azure-vmware-solution.md#register-the-microsoftavs-resource-provider)

- [Details of each privilege](https://docs.vmware.com/en/VMware-vSphere/7.0/com.vmware.vsphere.security.doc/GUID-ED56F3C4-77D0-49E3-88B6-B99B8B437B62.html)

- [How Azure VMware Solution monitors and repairs private clouds](./concepts-private-clouds-clusters.md#host-monitoring-and-remediation)



<!-- LINKS - external-->
[VMware product documentation]: https://docs.vmware.com/en/VMware-vSphere/7.0/com.vmware.vsphere.security.doc/GUID-ED56F3C4-77D0-49E3-88B6-B99B8B437B62.html

<!-- LINKS - internal -->
[concepts-upgrades]: ./concepts-private-clouds-clusters#host-maintenance-and-lifecycle-management
