# AZ104-ComputeandIdentityManagement
This project involves deploying a virtual machine, securing it using RBAC, applying Azure Policies for resource governance, encrypting sensitive data, and monitoring costs. It teaches foundational concepts for managing Azure identities, governance, and compute resources.
**Scenario**

A company wants to deploy a virtual machine for their web application, secure it with role-based access control, enforce a policy for naming conventions, encrypt sensitive data, and monitor the cost of the deployed resources.

**Steps**

1. **Create a Virtual Machine**
    - Go to **Azure Portal** > **Virtual Machines** > **Create**.
    - Select subscription, resource group, region, VM size, and OS (Windows/Linux).
    - Configure an admin username/password or SSH key.
    - Add a **data disk** during creation.
    - Configure **Networking**:
    - Review and create the VM.
    - Download private key.
2. **Configure Role-Based Access Control (RBAC)**
    - Now create a key vault and store the private key, note you’ll need to assign yourself the permissions (least privilege principle)
    - Navigate to the VM > **Access Control (IAM)** > **Add Role Assignment**.
    - Assign the **"Virtual Machine Contributor"** or a custom role to a user or group.
    - Verify permissions:
        - Go to Entra > Manage > Groups > All groups > your group name
3. **Log into the VM**
    - Go to VM > your vm > connect > SSH using Azure CLI > Configure
    - Test IP in the browser to see that it’s only accessible via SSH not HTTPS due to NSG
4. **Apply Azure Policy**
    - Navigate to **Azure Policy** > Authoring > **Definitions > Initiative definition > Name > Category > Next**
    - **Add policy definition(s) > Search tag > Select a few “Inherit a tag from resource group…” and “Inherit a tag from subscription_name” > Search allow > Select Allowed > Select “Allowed resource types” > Review + Create > Next**
    - Create group > Tags > Save > Previous > Select tag policies > Add to a group > Select Tags > Save
    - Select Initiative parameters > Create initiative parameter > Name > DisplayName > Allowed Values > Save
    - **For Reference ID’s Inherit a tag from resource group… and Inherit a tag from subscription_name select Value Type as Use Initiative Parameter and Value(s) as Name, Allowed resource types as “virtualMachines” > Review and create > Create**
    - Now assign the initiative to the subscription and test
5. **Monitor and Manage Costs**
    - Navigate to **Cost Management + Billing** > **Billing scope > Cost management > Budgets** > Add:
    - Review **Cost Analysis** to identify trends and optimize spending.
    - Review Advisor recommendations to see cost recommendations.
