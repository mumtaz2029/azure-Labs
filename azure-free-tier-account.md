
# Lab 01 — Creating an Azure Free Tier Account

**Lab Duration:** 15–20 minutes  
**Difficulty:** Beginner  
**Prerequisites:** A valid email address, a phone number for verification, and a credit/debit card (for identity verification — you will not be charged)

---

## Overview

Before you can start deploying virtual machines, setting up storage, or building cloud infrastructure, you need a place to do it. Microsoft Azure's free tier gives you exactly that — a fully functional cloud account with $200 in credits for the first 30 days, plus 55+ services that remain free for 12 months.

This lab walks you through signing up for an Azure free account step by step. By the end, you'll have access to the Azure Portal and be ready to start your hands-on cloud journey.

---

## What You Get with the Azure Free Tier

| Benefit | Details |
|---|---|
| **$200 credit** | Valid for the first 30 days — use it to explore any Azure service |
| **12 months free** | Popular services like VMs, Blob Storage, and SQL Database at no cost |
| **Always-free services** | 55+ services free forever, including Azure Functions, App Service (F1 tier), and more |
| **No auto-charges** | Your account won't be charged unless you explicitly upgrade to Pay-As-You-Go |

---

## Step-by-Step Instructions

### Step 1 — Go to the Azure Free Account Page

Open your browser and navigate to:

```
https://azure.microsoft.com/en-us/free
```

Click the **"Start free"** button on the homepage.

>  **Tip:** Use a personal email address for this account, not a work or university email — those may already be tied to an existing Azure Active Directory tenant, which can cause issues during signup.

---

### Step 2 — Sign In or Create a Microsoft Account

You'll be prompted to sign in with a Microsoft account.

- **If you already have one** (Outlook, Hotmail, Xbox, etc.) — go ahead and sign in.
- **If you don't have one** — click **"Create one"** and follow the prompts to set up a new Microsoft account. This takes about 2 minutes.

Once signed in, Azure will redirect you to the free account registration form.

---

### Step 3 — Fill In Your Profile Details

Complete the registration form with the following:

- **Country/Region** — Select your country (e.g., India)
- **First and Last Name**
- **Email address** — This will be your account contact email
- **Phone number** — Required for identity verification

Click **"Next"** when done.

---

### Step 4 — Verify Your Identity by Phone

Azure will send a verification code to the phone number you provided.

1. Choose **"Text me"** or **"Call me"** — SMS is usually faster
2. Enter the 6-digit code you receive
3. Click **"Verify code"**

This step confirms you're a real person and not a bot. It's quick and straightforward.

---

### Step 5 — Verify Your Identity by Card

Next, you'll be asked to enter a credit or debit card number.

> ⚠️ **Important:** Microsoft uses this only for identity verification. You will **not** be charged as long as you stay within the free tier limits. Your account is protected from surprise charges — Microsoft requires you to manually upgrade before any billing begins.

Enter your card details and click **"Next"**.

---

### Step 6 — Review the Agreement and Sign Up

Read through the subscription agreement and privacy statement. When ready:

- Check the box to agree to the terms
- Click **"Sign up"**

Azure will take a moment to set up your account. You should see a confirmation screen within 30–60 seconds.

---

### Step 7 — Access the Azure Portal

Once your account is created, click **"Go to Azure Portal"** or navigate directly to:

```
https://portal.azure.com
```

Log in with the Microsoft account you used during registration. You're now inside the Azure Portal — the central dashboard from which you'll manage all your cloud resources.

---

## Verifying Your Setup

Take a moment to confirm everything is in order:

1. In the top-right corner of the portal, click on your profile icon — you should see your name and email
2. In the search bar, type **"Subscriptions"** and press Enter
3. You should see a subscription listed as **"Azure subscription 1"** or **"Free Trial"** with a status of **Active**

If the subscription shows as **Active**, your account is set up correctly and ready to use.

---

## Common Issues and How to Resolve Them

**"This email is already associated with an Azure account"**  
Your email may be tied to an existing Microsoft account or Azure tenant. Try signing up with a different email address.

**Card was declined during verification**  
Some prepaid cards or virtual cards are not accepted. Use a standard credit or debit card. The card is only used for identity verification and won't be charged.

**Verification code not received**  
Check that the phone number was entered correctly with the right country code. If the SMS doesn't arrive within 2 minutes, request a new code or choose the "Call me" option instead.

**Portal loads but shows no subscription**  
Wait a few minutes and refresh the page. Account provisioning sometimes takes 2–5 minutes to complete on the backend.

---

## Key Terms to Know

| Term | What It Means |
|---|---|
| **Azure Portal** | The web-based dashboard at portal.azure.com where you manage all Azure resources |
| **Subscription** | The billing container that groups your Azure resources together |
| **Resource Group** | A logical container used to organize related Azure resources |
| **Free Tier** | A set of services available at no cost, either for 12 months or always-free |
| **$200 Credit** | A one-time credit applied to your account for the first 30 days of your free trial |

---

## Summary

In this lab, you:

- Created a Microsoft account (or used an existing one)
- Signed up for an Azure free tier account
- Verified your identity via phone and card
- Accessed the Azure Portal for the first time
- Confirmed your free trial subscription is active

You now have a live Azure account with $200 in credits and access to over 55 free services. In the next lab, we'll use this account to spin up your first virtual machine on Azure.

---

## Next Lab

**Lab 02 — Creating and Connecting to an Azure Virtual Machine (Ubuntu)**

---

*Lab authored as part of the Azure & DevOps Hands-On Series*
