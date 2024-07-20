---
title: "Buy or Rent? RaspberryPi vs VPS"
date: 2024-07-20
categories: 
- Opinion
tags: 
- raspberrypi
- vps
- hosting
- hardware
- cloud
- tailscale
- buy
- rent
- server
slug: "buy-or-rent-raspberrypi-vs-vps"
description: "Recently I was planning to self host a service I'm using and I was immediately stuck on a decision: should I just buy a Raspberry Pi 5 or rent a VPS?"
image: "cover-raspberrypi-vs-vps.png"
---

Recently I was planning to self host a service I'm using and I was immediately stuck on a decision: **should I just buy a Raspberry Pi 5 or rent a VPS?**

## Requirements 

Let's starts from the basic question: **what specs do I need to run this service?** Reading around, it seems that something with 4GB of RAM and 20-30 GB of disk could be enough for my needs. Good. 

## Costs

A **[Raspberry Pi 5](https://www.raspberrypi.com/products/raspberry-pi-5/) would cost me around 100€** (including accessories) plus the cost of energy, while **renting a VPS** with similar characteristics, **would cost me around 4,50€/month** (I used [Hetzner VPS prices](https://www.hetzner.com/cloud/) as reference).

To compensate costs of purchasing a Raspberry Pi, **I should keep running my service for at least a couple of years**. After that time, having purchased a Raspberry Pi would come cheaper (if you consider the total cost per month) then keep paying Hetzner.

## Complexity 

Honestly, both solutions are quite **challenging** (if you want to do things in the right way) and similar in terms of administration, the main difference would be that in case of a Raspberry Pi, I would have to also include the setup of something like [Tailscale Funnel](https://tailscale.com/kb/1223/funnel), to be able to expose my device on the public Internet (my provider, Fastweb, doesn't give public IP addresses to every user and most of them are behind a NAT).

In addition to this, I would also have to do the initial **installation of the operating system** and the **network configuration**, but it's surely not the most difficult part.

Everything else (installing a web server, a database, configuring them, installing and running the service etc...) would be exactly the same.

## The solution 

Both solutions are valid and both have pros and cons. So, what should one do? The best approach is evaluate both of them and pick the one that suits our needs.

## Raspberry Pi (buy)

Let's analyse the case we buy a **Raspberry Pi**.

### Pros

- You physically own the hardware
- It can be more fun to own an electronic device
- After a couple of years you basically run your service for free (apart from the electricity)
- Your data is definitely private 

### Cons

- Home connection is less reliable than a VPS network 
- If the device breaks after two years, you have to buy it from scratch 
- A bit more complexity for the initial setup
- If you don't need the service anymore after a couple of months, you are left with an expensive device collecting dust
- Physical hardware gets old: the same Raspberry Pi is unlikely to serve you for many years and you will need to buy a new one every few years

## VPS (rent)

What if we rent a **Virtual Private server**?

### Pros

- Your service is always up (even when your local ISP fails)
- You don't have an high initial cost
- If you decide to give up after a couple of months, you have only wasted less than 10€
- Easier initial setup

### Cons

- Your data won't be private
- If you keep running the service after 2 years (or the equivalent considering the cost of the Raspberry Pi) you also keep paying

## Conclusion

As you can see, **there is no right or wrong solution**. Depending on our own priorities and preferences, we may choose to buy something or to rent.

What did I end up choosing for my specific case? Well... in the end **I found a third solution** which has some of the benefits of both, it was much easier to configure (I got it up and running in less than 1 hour) and most importantly **costed me 0€**!

But I will talk about it in another post 😉
