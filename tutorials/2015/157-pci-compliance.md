---
title: PCI Compliance
categories: tutorials
tags: pci-compliance
author: jaswsinc
github-issue: https://github.com/websharks/s2member-kb/issues/157
---

### What does it mean to become PCI Compliant?

[![](https://c674753.ssl.cf2.rackcdn.com/security-8805-header-gray.gif){.alignright}](http://secure.trust-guard.com/certificates/8805)

#### The Short Version (Simplified)

It means you’ve paid a security scanning company (such as [McAfee® Secure](http://www.mcafeesecure.com) or [TrustGuard](http://s2member.com/r/trustguard/)) to scan your server routinely, and that you address any security vulnerabilities that your security scans reveal. It also means that you are filing PCI Compliance Reports (normally with assistance provided by these companies) after your scans are all green.

#### Additional Details (Security Standards Council)

[![](//cdn.websharks-inc.com/s2member/uploads/pci-compliant.png){.alignright}](https://www.pcisecuritystandards.org/)

The Payment Card Industry (PCI) Data Security Standard (PCI DSS) is a set of requirements designed to ensure that _all_ companies that process, store, or transmit credit card information maintain a secure environment. Essentially, any merchant that has a Merchant ID (MID) with a credit card company.

The Payment Card Industry [Security Standards Council](https://www.pcisecuritystandards.org/) (PCI SSC) was launched on September 7, 2006 to manage the ongoing evolution of the Payment Card Industry (PCI) security standards with a focus on improving payment account security throughout the transaction process. The PCI DSS is administered and managed by the PCI SSC ([www.pcisecuritystandards.org](http://www.pcisecuritystandards.org)), an independent body that was created by the major payment card brands (Visa, MasterCard, American Express, Discover and JCB.). 

**It is important to note:** The payment brands and acquirers (i.e., the credit card companies) are responsible for enforcing compliance (should they choose to do so)—_not_ the PCI council.

### How do I Become PCI Compliant?

#### **Step 1.** Determine whether or not you need to become PCI compliant.

If your site (on _your_ domain name) provides a form for a customer to enter a credit card number, you _must_ become PCI Compliant. It’s that simple. This means that all site owners running s2Member Pro Forms _must_ become PCI compliant. This also means that site owners running only Payment Buttons do _not_ need to become PCI Compliant, because Payment Buttons lead customers to an offsite location where the credit card number is entered at the merchant gateway domain—_not_ on their domain name.

#### **Step 2.** Find a company to scan your server routinely.

You will need to pay a company to run PCI Compliance scans against your server. We recommend [TrustGuard](http://s2member.com/r/trustguard/) for the best rates. However, there are many other companies to choose from. A Google search will return a long list of companies ready to take your money for this service.

#### **Step 3.** Read the PCI compliance scan provided by [TrustGuard](http://s2member.com/r/trustguard/).

Your website developer (or perhaps your hosting company) will need to fix any issues that [TrustGuard](http://s2member.com/r/trustguard/) warns you about. Your server (and the software that you run on it) _must_ pass a PCI Compliance scan. You will need to resolve any issues that may prevent you from obtaining PCI Compliance. See additional notes below regarding this step.

#### **Step 4.** File your PCI compliance reports.

Ask your PCI Compliance scanning company (e.g., [TrustGuard](http://s2member.com/r/trustguard/)) to help you file your PCI Compliance Reports. Most PCI scanning services will have a section in your account where you can fill out online forms for this. So that makes this easy enough to deal with. Please consult with your server scanning company.

---

**That’s it!** You're now PCI Compliant, and you will remain PCI Compliant as long as you keep monitoring the scans they perform, you fix any issues they report, and you continue to file your PCI Compliance Reports regularly.

---

### Regarding Step 3 (Resolving Issues)

Now, step 3 is where the work is. Most site owners will get a long list of techy mumbo jumbo they have no clue how to deal with. So at this point, you'll be looking at your web host and saying “Why am I not PCI Compliant on this server? I need to have this list of issues reported by [TrustGuard](http://s2member.com/r/trustguard/) fixed please. Can you help?” **If your hosting provider is one of these, you may _not_ like their response.**

-  BlueHost does not help; as far as we know.
- MediaTemple (gs) does not help; as far as we know.
- Rackspace Cloud Sites does not help; as far as we know.
- Or, any other cloud-based solution (for the most part).

These companies are serving the masses at cheap/affordable rates. They care about compatibility and flexibility, and while they also care about security, they don’t care what [TrustGuard](http://s2member.com/r/trustguard/) or any other scanning service thinks of their configuration. Nor will they work toward cleaning up a report produced by a scanning company for you. In most cases they will simply tell you they can't offer you PCI Compliance. _You may need to change hosting companies!_

**If you're running a dedicated server**, or you're on a VPS, the hosting company will usually _not_ help you in this case either, because it’s all _yours_ to deal with. If changes/updates need to occur, you are the one to handle that—_not_ the hosting company. So for instance, these hosting companies will _not_ help you with PCI Compliance—not unless you pay them extra and they agree to help.

- VPS.net does not help; as far as we know.
- Amazon EC2 does not help; as far as we know.
- Rackspace Cloud Servers does not help; as far as we know.
- MediaTemple (DV, XE, Nitro, etc) does not help; as far as we know.
- DigitalOcean Droplets; these are dedicated containers—no help as far as we know.
- Or, any other dedicated server or VPS (for the most part).

### Choosing the Right Hosting Company

**Companies that are known to maintain their servers for PCI Compliance**, and where we have confirmed this to be the case by contacting the hosting company to verify they will assist site owners.

<div class="li-margins"></div>

- #### [HostGator](http://s2member.com/r/hostgator/) (best for novice site owners)

  If you’re a novice, and you don’t want to deal with PCI Compliance updates/fixes by yourself, go with [HostGator](http://s2member.com/r/hostgator/). It’s cheap, and they claim to support PCI Compliance scans and to help you correct any issues that you have with these scanners. We confirmed this with [HostGator](http://s2member.com/r/hostgator/) about 6 months ago in live chat. You can choose any [HostGator](http://s2member.com/r/hostgator/) plan, they are all maintained for PCI Compliance (that’s what we were told).

- #### [FireHost](http://s2member.com/r/firehost/) (best for serious site owners w/ money)

  This is the company that we use @ s2Member.com. [FireHost](http://s2member.com/r/firehost/) is all about security and support. Plus they will help with anything/everything—you pay for that. _Of course there are others out there, but these are the ones that we commonly recommend._

### Is the s2Member software PCI compliant?

Yes. When PCI Compliance Reports are filed, you might be asked questions like:

-   Do you store passwords? If so, do you use one-way encryption?
-   Do you store credit card numbers? If so, are these encrypted?

These questions need to be answered properly of course. And, this is where we can say “Yes, the s2Member software is PCI Compliant”; because we take the steps necessary to ensure the software is designed in a way that leaves you able to answer these questions properly.

#### Do you store passwords? If so, do you use one-way encryption?

This comes back to WordPress itself, because s2Member works with existing functionality provided by WordPress when it comes to password encryption and database storage. The answer to this question is, “Yes, passwords are stored by WordPress with one-way encryption”.

#### Do you store credit card numbers? If so, are these encrypted?

No, we do _not_ store credit card numbers. All financial details, including, but not limited to: credit card numbers, expiration dates, billing addresses; are _all_ stored securely, inside your Stripe, PayPal, Authorize.Net, ClickBank, and/or Google Checkout accounts; and _not_ within WordPress.

s2Member only uses approved API connections provided by your payment gateway. s2Member does _not_ store any financial information, it only stores a Paid Subscr. ID (aka: Transaction ID or Recurring Profile ID) inside your WordPress database. This is an easy way for s2Member to reference information obtained through future API calls related to a particular customer’s account. This also makes PCI Compliance and privacy concerns much easier for you to deal with. Again, s2Member stores all financial information securely within your payment gateway account, and _not_ locally within WordPress.

_**Note:** This article is for educational purposes only. Please do your own research on this subject. Thanks!_
