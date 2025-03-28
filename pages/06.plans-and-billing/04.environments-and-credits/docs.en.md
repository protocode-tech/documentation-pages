---
title: 'Credit Consumption for Environments'
taxonomy:
    category:
        - docs
media_order: 'billing_consumption_FR.png,billing_consumption_EN.png'
---

Open environments consume credits. The number of credits consumed per hour depends on the allocated resources. By default, environments are set to the minimum profile ("Small"), which consumes one credit per hour. Depending on project needs, the minimum may not be sufficient, in which case it is possible to [increase allocated resources](/project-configuration/resource-allocation). The available profiles are as follows:

| Name    | CPU       | RAM    | Credits / h    | Default |
|---------|----------|--------|---------------|---------|
| Small   | 2 cores  | 4 GB   | 1 credit / h  | Yes     |
| Medium  | 4 cores  | 8 GB   | 2 credits / h | No      |
| Large   | 8 cores  | 16 GB  | 4 credits / h | No      |
| XLarge  | 16 cores | 32 GB  | 8 credits / h | No      |
| XXLarge | 32 cores | 64 GB  | 16 credits / h| No      |

!!! Example: A "Medium" environment open for 7 hours will consume 14 credits.

Subscription plans provide a monthly credit allowance (currently ranging from 50 to 350 credits per month). Environment credit consumption is continuously deducted from this balance. You can check your current usage at any time by navigating to "Billing" and viewing the "Current Consumption" section:

![billing_consumption_EN](billing_consumption_EN.png?style=max-width:25rem;)

Credits granted by subscription plans do not roll over if unused. At the start of each new billing cycle, the available credit balance is reset.