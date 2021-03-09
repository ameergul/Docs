# Deploy STIG compliant Linux Virtual Machines

This article shows how to use the Azure portal to deploy a STIG compliant Linux Virtual Machine.

> Prerequisites: Azure Gov account, Storage Account (If desired, must be
> in the same resource group/region as the VM, required if you plan to
> store diagnostic log analytics), Log Analytics workspace (required if
> you plan to store diagnostic logs)

## Sign in to Azure

Sign in to the at [Azure Government portal](https://portal.azure.us/).

## Create a STIG compliant virtual machine

1. Select Create a resource
1. Type **Azure STIG Templates for Linux** in the search and press enter
1. Select **Azure STIG Templates for Linux** from the search results and then **Create**
1. In the **Basics** tab, under **Project details**

    a.  Select an existing *Subscription*.

    b.  Create a new *Resource group* or enter an existing resource group

    c.  Select your *Region*

    ![Screenshot of the Project details section showing where you select the Azure subscription and the resource group for the virtual machine](./media/project-details.png)

1. Under **Instance details**, enter all required information

    a.  Enter the *VM name*

    b.  Select the *Linux OS version*

    c.  Select the Instance *Size*

    d.  Enter the Administrator Account *Username*

    e.  Enter the Authentication type

    f.  Enter a *Password or Public Key*

    g.  *Confirm password or Public Key*

    ![Screenshot of the Instance details section where you provide a name for the virtual machine and select its region, image and size](./media/linux-instance-details.png)

1. Under **Disk**

    a.  Select the *OS disk type*

    b.  Select the *Encryption type*

    ![Screenshot of the Disk options section showing where you select the disk and encryption type for the virtual machine](./media/disk-options.png)

1. Under **Networking**

    a.  Select the *Virtual Network*. Either use existing virtual
        network or select *Create new* (note RDP in bound is disallowed)

    b.  Select *Subnet* (using an existing subnet will generate an error and
        require entering a new subnet)

    c. Application security group (optional)

    ![Screenshot of the Network interface section showing where you select the network and subnet for the virtual machine](./media/network-interface.png)

1. Under **Management**

    a.  For Diagnostic settings select *Storage account* (optional, required to
        store diagnostic logs)

    b.  Enter Log Analytics workspace (optional, required to store
        log analytics)

    c. Enter Custom data (optional, not applicable to RHEL 7.2)

    ![Screenshot of the Management section showing where you select the diagnostic settings for the virtual machine](./media/linux-diagnostic-settings.png)

1. Select **Review + create** to review summary of all selections

1. Once the validation check is successful Select ***Create***

1. Once the creation process is started, the
    ***Deployment*** Process page will be displayed

    a.  **Deployment** ***Overview*** tab displays the deployment
        process including any errors that may occur. Once deployment is
        complete this tab provides information on the deployment and
        provides the opportunity to download the deployment details

    b.  ***Inputs*** ***tab*** provides a list of the inputs to the
        deployment

    c.  ***Outputs tab*** provide information on any deployment outputs

    d.  **Template** **tab** provides downloadable access to the json
        scripts used in the template

1. The deployed Virtual machine can be found in the resource group used for the deployment. Since inbound is RDP disallowed, Bastion must be used to connect to the VM.

## Clean up resources

When no longer needed, you can delete the resource group, virtual machine, and all related resources.

Select the resource group for the virtual machine, then select **Delete**. Confirm the name of the resource group to finish deleting the resources.
