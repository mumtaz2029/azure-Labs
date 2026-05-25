# Lab 01: Setting Up Your Azure Free Account

**Estimated Time:** 15-20 minutes  
**Level:** Beginner

## Before You Start

You'll need three things: an email address, a phone number, and a debit or credit card. The card is just for identity verification. Microsoft won't charge you unless you manually upgrade your account later, so keep that in mind if that's been stopping you from signing up.

## Why Free Tier?

When you're just getting started with Azure, you don't want to worry about costs every time you spin up a resource. The free account gives you $200 in credits for the first 30 days, which is more than enough to get through beginner labs without touching your wallet. After 30 days, a bunch of services stay free for 12 months like Linux VMs (limited hours), Blob Storage, and Azure SQL Database.

The account doesn't auto-charge you once the trial ends. You'd have to actively upgrade it, so there's no surprise bill waiting for you.

## Creating the Account

Head over to [azure.microsoft.com/free](https://azure.microsoft.com/en-us/free) and hit **Start free**.

You'll be asked to sign in with a Microsoft account. If you already have one (Outlook, Hotmail, anything from Microsoft) just use that. If not, create a new one right there. It takes two minutes.

> One thing worth noting: if you're using a college or work email, it might already be linked to an existing Azure tenant. That can cause issues during signup. A personal email works best here.

## Filling Out the Registration Form

Once you're signed in, Azure takes you to the actual signup form. Fill in your name, country, and contact email. When you hit the phone verification step, go with **Text me** as it's faster than the call option. Enter the code you receive and move on.

The card step comes right after. Enter your card details and Azure runs a small verification check. Nothing gets charged at this point.

Agree to the terms and click **Sign up**. The account usually activates within a minute.

## Getting Into the Portal

Once it's done, click **Go to Azure Portal** or just open [portal.azure.com](https://portal.azure.com) directly.

To confirm everything's working, type **Subscriptions** in the search bar at the top. You should see something like *Azure subscription 1* or *Free Trial* with a status of **Active**. If you see that, you're good to go.

## If Something Goes Wrong

**The email is already in use**  
This usually means it's tied to an existing Microsoft or Azure account. Try a different email.

**Card declined**  
Prepaid and some virtual cards don't go through. Use a regular debit or credit card.

**Didn't receive the SMS code**  
Double-check the country code and number. If it still doesn't come through, request a new one or use the call option.

**Subscription not showing after signup**  
Give it a couple of minutes and refresh. The backend sometimes takes a bit to finish provisioning.

## What's Next

Your Azure account is live. In the next lab, we'll use it to create a Linux virtual machine, connect to it over SSH, and run a few basic commands. That's where things start to get interesting.

**Lab 02: Creating and Connecting to an Azure Virtual Machine**
