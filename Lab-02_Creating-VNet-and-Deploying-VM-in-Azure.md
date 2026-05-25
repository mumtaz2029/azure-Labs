# Lab 02: How to Create a Virtual Network (VNet) and Deploy a Virtual Machine (VM) in Azure

**Estimated Time:** 25-30 minutes  
**Level:** Beginner  
**Prerequisite:** Lab 01 completed (Azure free account ready)

## What We're Doing Here

Before deploying a virtual machine, you need a network for it to live in. In Azure, that's called a Virtual Network or VNet. Think of it like setting up the electrical wiring in a house before you move in the furniture. The VM is the furniture, the VNet is the wiring.

This lab walks you through creating a VNet first, then deploying a Linux VM inside it.

## Step 1: Create a Resource Group

Everything in Azure lives inside a Resource Group. It's basically a folder that keeps related resources together so you can manage and delete them easily.

Log into [portal.azure.com](https://portal.azure.com), search for **Resource Groups** in the top search bar, and click **Create**.

Fill in the following:

- **Subscription:** Your free trial subscription
- **Resource Group Name:** something like `lab-rg` or `devops-lab-rg`
- **Region:** Choose the one closest to you. For India, go with **Central India** or **South India**

Click **Review + Create** and then **Create**. Done in under a minute.

## Step 2: Create a Virtual Network

Search for **Virtual Networks** in the portal and click **Create**.

On the Basics tab, fill in:

- **Subscription:** Free Trial
- **Resource Group:** Select the one you just created
- **Name:** something like `lab-vnet`
- **Region:** Same region you picked for the resource group

Move to the **IP Addresses** tab. By default Azure gives you a `10.0.0.0/16` address space with a subnet already created. That's fine for now, leave it as is.

Skip through the remaining tabs and click **Review + Create**, then **Create**. The VNet will be ready in about 30 seconds.

## Step 3: Deploy a Virtual Machine

Now for the main part. Search for **Virtual Machines** in the portal and click **Create**, then select **Azure Virtual Machine**.

**Basics tab:**

- **Subscription:** Free Trial
- **Resource Group:** Same one you've been using
- **Virtual Machine Name:** give it something simple like `lab-vm`
- **Region:** Same region as your VNet
- **Image:** Ubuntu Server 22.04 LTS (this is free tier eligible)
- **Size:** Click "See all sizes" and pick **Standard_B1s** as it falls under the free tier
- **Authentication type:** SSH public key
- **Username:** `azureuser` (keep this, it's the default)
- **SSH public key source:** Generate new key pair (Azure will create one for you)

**Networking tab:**

This is where you connect the VM to the VNet you created.

- **Virtual Network:** Select `lab-vnet`
- **Subnet:** The default subnet should already be selected
- **Public IP:** Leave it on so you can connect to the VM from outside
- **NIC network security group:** Basic
- **Public inbound ports:** Allow SSH (port 22)

Leave everything else as default and click **Review + Create**.

Azure will validate the configuration. Once it passes, click **Create**.

A popup will appear asking you to download the SSH private key. Click **Download private key and create resource**. Save the `.pem` file somewhere safe on your computer. You'll need it to connect to the VM.

Deployment usually takes 2-3 minutes.

## Step 4: Connect to the VM

Once deployment is complete, click **Go to resource**.

On the VM overview page, copy the **Public IP address**.

Open your terminal (or MobaXterm if you're on Windows) and run:

```bash
chmod 400 your-key-name.pem
ssh -i your-key-name.pem azureuser@<your-public-ip>
```

Replace `your-key-name.pem` with the actual file name you downloaded, and `<your-public-ip>` with the IP you just copied.

If everything is set up correctly, you'll see the Ubuntu welcome message and a prompt like this:

```
azureuser@lab-vm:~$
```

You're in. You now have a live Linux VM running in Azure.

## Quick Verification

Run a couple of commands to confirm the VM is working properly:

```bash
# Check the OS version
cat /etc/os-release

# Check network connectivity
ping -c 4 google.com

# Check your current user
whoami
```

All three should return clean output without any errors.

## If Something Goes Wrong

**SSH connection times out**  
Go back to your VM in the portal, click **Networking** on the left side, and check that port 22 is listed as an inbound rule. If it's missing, add it manually.

**Wrong key file error**  
Make sure you're pointing to the correct `.pem` file path and that you ran `chmod 400` on it first. On Windows using MobaXterm, load the key through the session settings under Advanced SSH settings.

**VM size not available in your region**  
Try switching the region to East US or West Europe. Not all VM sizes are available in every region.

**Deployment failed**  
Check the error message in the deployment details. It's usually either a quota issue (free accounts have limits) or a name conflict. Rename the VM or try a different region.

## Cleaning Up

If you're done experimenting and want to avoid using up your free credits, go to your Resource Group and click **Delete resource group**. This removes the VM, VNet, and everything else inside it in one go.

## What's Next

You've got a VNet set up and a VM running inside it. In the next lab, we'll go further 
