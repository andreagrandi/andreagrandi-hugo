---
title: "It's now possible to use ControlD DNS with Tailscale"
date: 2024-08-13
categories: 
- HowTo
tags:
- controld
- dns
- tailscale
- networking
- tutorial
slug: "using-controld-dns-with-tailscale"
description: "With this tutorial, you will learn how to use ControlD DNS with Tailscale and deliver a secure and ad blocking DNS service to your devices."
image: "cover-controld-tailscale.png"
---

If you are using [**Tailscale**](https://tailscale.com) in some of your devices, you also need to use Tailscale own DNS server to resolve the names of the devices in the network. If you are also a user of [**ControlD**](https://controld.com) DNS, and you want to use it with Tailscale, you can finally do it!

## Configure a new Endpoint on ControlD

First of all, you need to create a new **endpoint** on ControlD. You can do it by logging in to your ControlD account, select **Endpoints** from the left menu, and then click on the plus button.

Scroll down to **Router** section and select **Other** as the device type. In the next screen you need to specify a name, I used `tailscale-global` but you can use any name you want.

Once you have created it, take note of the **Resolver ID**, because you will need it in the next step.

![Configure endpoint on ControlD - screenshot from ControlD docs](configure-endpoint.png)

## Configure the DNS on Tailscale

At this point you need to go to [Tailscale admin console](https://login.tailscale.com/admin/dns), and select the **DNS** tab. Click on the **Add nameserver** menu, and select "Control D" from the list.

![Configure Nameserver - screenshot from ControlD docs](add-controld-tailscale.png)

Once you have selected **ControlD** from the list, you will get this window and you will need to fill the **Endpoint** using the **Resolver ID** you got from the previous step.

![Configure ControlD DNS - screenshot from ControlD docs](add-controld-endpoint.png)

Now you can click on the **Save** button.

## Verify the configuration is working

The configuration is done! If you already have some devices connected to your Tailscale network, you will be able to check if the configuration is working by checking the endpoints visible in the ControlD dashboard: [https://controld.com/dashboard/endpoints](https://controld.com/dashboard/endpoints)

![Check ControlD Endpoints - screenshot from ControlD docs](check-controld-endpoints.png)

If you see a **green dot** next to the router icon, it means the endpoint is in use and the configuration is working.

## References

- [Tailscale Documentation](https://tailscale.com/kb/1403/control-d)
- [ControlD Documentation](https://docs.controld.com/docs/tailscale-integration)
