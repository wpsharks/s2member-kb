---
title: Integrating ClickBank with s2Member
categories: tutorials
tags: clickbank
author: kristineds
github-issue: https://github.com/websharks/s2member-kb/issues/290
---

[ClickBank](http://www.clickbank.com/) is a secure online retail outlet for more than 10,000 digital product vendors and 100,000 active affiliate marketers. ClickBank is one of the largest online retailers and has over 200 million customers worldwide. They serve more than 200 countries, and are consistently ranked as one of the most highly-visited sites on the web.

If you are planning to use [ClickBank](http://www.clickbank.com/) as your preferred payment gateway with s2Member, you can easily integrate it with s2Member for Direct Payments (_Buy Now_) and Recurring Billing. 

### Enable ClickBank Gateway Inside s2Member
_**Note:** ClickBank integration is only available with s2Member Pro._

1) First, inside s2Member, activate the ClickBank Gateway from the **Other Gateways** option (See: **WordPress Dashboard → s2Member® → Other Gateways**). _This is not enabled by default_.

![ClickBank - Other Gateways](https://cloud.githubusercontent.com/assets/7514953/13260907/a493f81a-da98-11e5-8657-33906f7ed33a.png)

2) Scroll down to the bottom until you find the **ClickBank (w/ Buttons)** and check the box for it. Save changes and refresh the page.

   ![ClickBank - Select Options](https://cloud.githubusercontent.com/assets/7514953/13260998/15e2502a-da99-11e5-8b99-ccfa6dc10c54.png)
------------------
### Configure ClickBank Account Details (required)

1) Sign up for a ClickBank Merchant Account here: https://accounts.clickbank.com/public/#/signup/form/key/ (_if you don't have an existing account yet_) 

![ClickBank - Signup for Account](https://cloud.githubusercontent.com/assets/7514953/13260937/c9620ede-da98-11e5-99b8-808128cacd10.png)

2) Inside your ClickBank account, go to **Settings → My Account**. Scroll down until you see the sections for configuring the Clerk API key and Developer API Key.

![ClickBank - generate API Keys](https://cloud.githubusercontent.com/assets/7514953/13520370/c091fb78-e21a-11e5-8c47-933d6181f37e.png)

- To generate the Clerk/API Key, click the **Edit** button on the top right corner of that box. Click the **Create New Clerk User API Key** button.

![ClickBank - Edit Clerk API Key](https://cloud.githubusercontent.com/assets/7514953/13453065/30c5d264-e088-11e5-8b49-3bba0be0de6c.png)

- In the area that appears, fill in a description (e.g., "s2Member Integration") and tick **all** boxes to each option. Click the **Save** button.

![ClickBank - Generate Clerk API Key](https://cloud.githubusercontent.com/assets/7514953/13453027/f6fa276a-e087-11e5-9816-33ea2168675a.png)

- To generate the Developer/API Key, click the **Edit** button on the top right corner of that box. Click the **Create New Developer Key** button.

![ClickBank - Edit Developer API key](https://cloud.githubusercontent.com/assets/7514953/13453288/c223f6fe-e089-11e5-9fd5-cb2eb7f445b1.png)

- In the area that appears, fill in a description (e.g., "s2Member Integration") and click the **Save** button.

![ClickBank - Generate Developer API Key](https://cloud.githubusercontent.com/assets/7514953/13453192/0212280e-e089-11e5-9e9d-ad3458230646.png)

3) Inside s2Member, go to  **WordPress Dashboard → s2Member → ClickBank Options → ClickBank Account Details**, enter your ClickBank username and generated API keys for both Clerk and Developer. Save changes. 

![ClickBank - username](https://cloud.githubusercontent.com/assets/7514953/13452902/1ff02be8-e087-11e5-9af5-663924731acf.png)

------------------
### Configure ClickBank IPN v2.1 or v6 Integration (required)

To configure the ClickBank IPN v2.1 or v6 integration, it must be set up inside your ClickBank account and s2Member.

1) First, inside your ClickBank account, create a secret key and enter it on the **ClickBank IPN/Secret Key** field found here: **WordPress Dashboard → s2Member → ClickBank Options → ClickBank IPN v2.1 or v6 Integration**.

- To create a secret key inside your ClickBank account, navigate your way to the top right of the page and go to **Settings → My Site**. Scroll down to the bottom until you see the section that says **Advanced Tools**. Click the **Edit** button on the top right corner of that box. Type in a secret key of your choice. (*Note: The secret key must be no more than 16 characters and/or digits, and it must be in ALL CAPS.*)

![ClickBank - Create Secret Key](https://cloud.githubusercontent.com/assets/7514953/13452479/156f0170-e083-11e5-914b-3064b735508c.png)

- Click **Request Access** next to Instant Notification URL. 

![ClickBank - Request IPN URL](https://cloud.githubusercontent.com/assets/7514953/13453405/d482ebe2-e08a-11e5-80c5-5f47e444c59f.png)

- In the area that appears, select **Yes** to each questions. Scroll to the bottom of the Terms of Use area, tick the box and click on the **Save Changes & Request API Access** button. 

![ClickBank - Terms of Use](https://cloud.githubusercontent.com/assets/7514953/13703167/dc5d0ab4-e7ce-11e5-9aa8-c7ed7c65c4a8.png)

2) Once that has been done, go back to your s2Member account and copy the **Instant Payment Notification URL**. See: **WordPress Dashboard → s2Member → ClickBank Options → ClickBank IPN v2.1 or v6 Integration**. You can choose to either use IPN v2.1 URL or IPN v6 URL (You'll choose the version when you configure the URL inside your ClickBank account; we recommend using v6 unless ClickBank says to use v2.1). 

_**Note:** Please do NOT integrate both IPN URLs. Choose one version or the other._

![ClickBank - IPN Integration Secret Key](https://cloud.githubusercontent.com/assets/7514953/13452617/6e3e0b7e-e084-11e5-9206-953bf1fb56bf.png)

3) After copying the **Instant Payment Notification (IPN) URL**, go back to your ClickBank account. Navigate your way to the top right of the page and go to **Settings → My Site**. Scroll down to the bottom until you see the section that says **Advanced Tools**. Click the **Edit** button on the top right corner of that box. 

![ClickBank - Copy IPN](https://cloud.githubusercontent.com/assets/7514953/13705042/f66f245e-e7d9-11e5-864e-b29ae1121187.png)

4) Paste in the IPN URL on the **Instant Notification URL** field and click the **Test Pin** button to verify it. 

![ClickBank - IPN URL](https://cloud.githubusercontent.com/assets/7514953/13453527/d89360e4-e08b-11e5-9d15-3f59914123b2.png)

5) After verifying, click on the **Save Changes** button. That's it! Your ClickBank integration is now complete.

---------------------------

#### Using s2Member-generated ClickBank Buttons

With the ClickBank integration complete, you can now generate ClickBank buttons to provide paid access to the site. See: **WordPress Dashboard → s2Member → ClickBank Buttons**

![ClickBank - Buttons](https://cloud.githubusercontent.com/assets/7514953/13704314/306a74d2-e7d6-11e5-97ca-8a40c3fd90fe.png)