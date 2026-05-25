# Lab 03: Configuring Subnets and Public IP in Azure

**Estimated Time:** 30-35 minutes  
**Level:** Beginner  
**Prerequisite:** Lab 02 completed (VNet and VM setup done)

## What We're Doing Here

In the last lab, Azure handled most of the networking automatically. This time we're taking more control. You'll manually create two subnets inside a VNet, deploy a VM without assigning a Public IP during creation, and then create a Public IP address separately and attach it to the VM yourself.

This is actually how it's done in real environments. You rarely want to let Azure auto-assign public IPs without knowing exactly where they're going.

## Step 1: Create a Resource Group

If you deleted the one from Lab 02, create a fresh one. Search for **Resource Groups** in the portal and click **Create**.

- **Subscription:** Free Trial
- **Resource Group Name:** `lab03-rg`
- **Region:** East US

Click **Review + Create** and then **Create**.

## Step 2: Create a Virtual Network with Two Subnets

Search for **Virtual Networks** and click **Create**.

**Basics tab:**

- **Subscription:** Free Trial
- **Resource Group:** `lab03-rg`
- **Name:** `lab03-vnet`
- **Region:** East US

Move to the **IP Addresses** tab. This is where the actual work happens.

You'll see a default address space of `10.0.0.0/16` and one subnet already listed. We're going to keep that and add a second one.

**Editing the first subnet:**

Click on the default subnet to edit it.

- **Subnet name:** `subnet-1`
- **Subnet address range:** `10.0.1.0/24`

Save it.

**Adding the second subnet:**

Click **Add subnet**.

- **Subnet name:** `subnet-2`
- **Subnet address range:** `10.0.2.0/24`

Save it.

You should now see both `subnet-1` and `subnet-2` listed under the address space `10.0.0.0/16`.

Skip through the remaining tabs and click **Review + Create**, then **Create**. Give it a moment to deploy.

## Step 3: Deploy a VM Without a Public IP

Search for **Virtual Machines** and click **Create**, then select **Azure Virtual Machine**.

**Basics tab:**

- **Subscription:** Free Trial
- **Resource Group:** `lab03-rg`
- **Virtual Machine Name:** `lab03-vm`
- **Region:** East US
- **Image:** Ubuntu Server 22.04 LTS
- **Size:** Standard_B1s
- **Authentication type:** SSH public key
- **Username:** `azureuser`
- **SSH public key source:** Generate new key pair

**Networking tab:**

This is the important part for this lab.

- **Virtual Network:** `lab03-vnet`
- **Subnet:** `subnet-1` (we're placing the VM in the first subnet)
- **Public IP:** Click the dropdown and select **None**

That last part is intentional. We're skipping the Public IP for now and will create and attach it manually in the next step.

- **NIC network security group:** Basic
- **Public inbound ports:** Allow SSH (port 22) — keep this on even though there's no public IP yet, you'll need it once the IP is attached

Click **Review + Create**, then **Create**. Download the `.pem` key when prompted and save it. Wait for the deployment to finish.

## Step 4: Create a Public IP Address Separately

Once the VM is deployed, don't connect to it yet. First, let's create the Public IP on its own.

Search for **Public IP addresses** in the portal and click **Create**.

Fill in the following:

- **Subscription:** Free Trial
- **Resource Group:** `lab03-rg`
- **Region:** East US
- **Name:** `lab03-public-ip`
- **IP Version:** IPv4
- **SKU:** Standard
- **Tier:** Regional
- **Assignment:** Static

Using **Static** means the IP won't change even if you stop and restart the VM. Dynamic IPs do change, which can be annoying when you're trying to reconnect.

Click **Review + Create** and then **Create**.

## Step 5: Associate the Public IP with the VM

Now we need to attach this Public IP to the VM's network interface.

Go to your VM `lab03-vm` in the portal. On the left side panel, click **Networking**, then click on the **Network Interface** name (it'll look something like `lab03-vm123`).

Inside the Network Interface settings, click **IP configurations** from the left menu.

You'll see a configuration listed called `ipconfig1`. Click on it.

On the ipconfig1 page:

- Under **Public IP address**, toggle it to **Associate**
- Click the dropdown and select `lab03-public-ip`

Click **Save** at the top.

Give it about 30 seconds. Go back to your VM overview page and you'll now see the Public IP address listed there.

## Step 6: Connect to the VM

Now that the Public IP is attached, copy it from the VM overview page and connect via SSH.

```bash
chmod 400 lab03-key.pem
ssh -i lab03-key.pem azureuser@<your-public-ip>
```

If you land at the `azureuser@lab03-vm:~$` prompt, everything worked.

Run a quick check to confirm network connectivity:

```bash
ping -c 4 google.com
```

## Understanding the Two Subnets

You created two subnets in this lab but only used `subnet-1` for the VM. In practice, here's how subnets are typically used:

- **subnet-1** can hold your application VMs or web servers that face the internet
- **subnet-2** can hold backend resources like databases that should never be publicly accessible

Keeping them separate means you can apply different security rules to each one using Network Security Groups (NSGs), which we'll cover in a later lab.

## If Something Goes Wrong

**Public IP not showing up in the dropdown during association**  
Make sure the Public IP was created in the same region as the VM (East US). IPs from different regions won't appear in the list.

**SSH still not connecting after attaching the IP**  
Go to the VM's Networking tab and confirm that port 22 is listed as an inbound rule in the NSG. If it's missing, add it manually by clicking **Add inbound port rule**.

**ipconfig1 page not showing the associate option**  
Make sure the Public IP SKU matches the VM's NIC SKU. If you created the IP as Standard, the NIC should also be Standard. Basic SKU IPs won't associate cleanly with Standard NICs.

## Cleaning Up

When you're done, go to `lab03-rg` and delete the entire resource group. This removes the VM, VNet, subnets, Public IP, and network interface all at once.

## What's Next

You now know how to separate your network into subnets and manage Public IPs independently. In the next lab, we'll look at Network Security Groups and how to control exactly what traffic is allowed in and out of your resources.

**Lab 04: Network Security Groups (NSG) and Traffic Rules**
