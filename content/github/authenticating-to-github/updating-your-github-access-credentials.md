---
title: Updating your GitHub access credentials
intro: '{% data variables.product.product_name %} credentials include{% if currentVersion != "github-ae@latest" %} not only your password, but also{% endif %} the access tokens, SSH keys, and application API tokens you use to communicate with {% data variables.product.product_name %}. Should you have the need, you can reset all of these access credentials yourself.'
redirect_from:
  - /articles/rolling-your-credentials/
  - /articles/how-can-i-reset-my-password/
  - /articles/updating-your-github-access-credentials
versions:
  free-pro-team: '*'
  enterprise-server: '*'
  github-ae: '*'
---

{% if currentVersion != "github-ae@latest" %}
### Requesting a new password

1. To request a new password, visit {% if currentVersion == "free-pro-team@latest" %}https://{% data variables.product.product_url %}/password_reset{% else %}`https://{% data variables.product.product_url %}/password_reset`{% endif %}.
2. Enter the email address associated with your personal {% data variables.product.product_name %} account, then click **Send password reset email.** The email will be sent to the backup email address if you have one configured.
  ![Password reset email request dialog](/assets/images/help/settings/password-recovery-email-request.png)
3. We'll email you a link that will allow you to reset your password. You must click on this link within 3 hours of receiving the email. If you didn't receive an email from us, make sure to check your spam folder.
4. After clicking on the link in your email, you'll be asked to enter a new password.
  ![Password recovery box](/assets/images/help/settings/password_recovery_page.png)

{% tip %}

To avoid losing your password in the future, we suggest using a secure password manager, like [LastPass](https://lastpass.com/), [1Password](https://1password.com/), or [Keeper](https://keepersecurity.com/).

{% endtip %}

### Changing an existing password

{% data reusables.repositories.blocked-passwords }

1. {% data variables.product.signin_link } to {% data variables.product.product_name %}.
{% data reusables.user_settings.access_settings %}
{% data reusables.user_settings.security %}
4. Under "Change password", type your old password, a strong new password, and confirm your new password. For help creating a strong password, see "[Creating a strong password](/articles/creating-a-strong-password)"
5. Click **Update password**.

{% tip %}

For greater security, enable two-factor authentication in addition to changing your password. See [About two-factor authentication](/articles/about-two-factor-authentication) for more details.

{% endtip %}
{% endif %}
### Updating your access tokens

See "[Reviewing your authorized integrations](/articles/reviewing-your-authorized-integrations)" for instructions on reviewing and deleting access tokens. To generate new access tokens, see "[Creating a personal access token](/github/authenticating-to-github/creating-a-personal-access-token)."

### Updating your SSH keys

See "[Reviewing your SSH keys](/articles/reviewing-your-ssh-keys)" for instructions on reviewing and deleting SSH keys. To generate and add new SSH keys, see "[Generating an SSH key](/articles/generating-an-ssh-key)."

### Resetting API tokens

If you have any applications registered with {% data variables.product.product_name %}, you'll want to reset their OAuth tokens. For more information, see the "[Reset an authorization](/rest/reference/apps#reset-an-authorization)" endpoint.

{% if currentVersion != "github-ae@latest" %}
### Preventing unauthorized access

For more tips on securing your account and preventing unauthorized access, see "[Preventing unauthorized access](/articles/preventing-unauthorized-access)."
{% endif %}
Get Started
Docs
APIs
Tools
Support
PayPal.com
Search
Search
Log in to Dashboard
PAYPAL COMMERCE PLATFORM FOR BUSINESS
Accept Payments
Checkout
Set Up Standard Payments
Advanced Credit and Debit Card Payments
Pay Later Messaging
Integrate
Customize
Customize the Buttons
Customize the Messaging
Best Practices
Advanced Options
Compatibility
Upgrade
Troubleshoot
Analytics
Reference
Commerce Platforms
Make Orders API Calls From Your Server
Set Up Server-Side SDK
Create an Order
Create Order Authorization
Get Order Details
Capture Order
Authorize Order
Capture Order Authorization
Handle Funding Failures
Configure Payments
Alternative Payment Methods
Standalone Payment Buttons
Standard Payments with Single Page Applications
Add Capabilities
Auth and Capture
Buyer Experience
SCA Payment Indicators
Fraud Protection
3D Secure
JavaScript SDK
Orders API
3D Secure Test Scenarios
Reference
Authorization and Honor Period
Style Guide
Browser Support
Supported Alternative Payment Methods
Advanced Credit and Debit Country and Currency Availability
Card Decline Errors
Upgrade Your Integration
Invoicing
Create a QR Code for Invoices
Subscriptions
Capabilities
Pricing Plans
Billing Cycles
Pause or Resume a Subscription
Upgrade or Downgrade a Subscription
Change Subscription Quantity
Start a Subscription on a Future Date
Offer a Trial Period
Charge a Setup Fee
Payment Failures and Recovering Balances
Customize Subscriptions
Make Payments
Payouts
Reference
Currency Conversion
Payouts SDK
PAYMENT METHODS
List of Methods
Pay Later Offers
DEVELOPER RESOURCES
Get Started
Develop
Design Guidelines
REST API URLs
API Idempotency
Currency Codes
Country Codes
State & Province Codes
Locale Codes
JavaScript SDK
JavaScript SDK Script Configuration
JavaScript SDK Complete Reference
JavaScript SDK Performance Optimization
Test and Go Live
Sandbox
API Simulation Tests
Get started
Get started integrating PayPal Commerce Platform by getting your API credentials and sandbox account information.

Get API credentials
Your API credentials are a client ID and secret, which authenticate API requests from your account. While you're developing code, use these credentials when you test API calls in our sandbox environment. You get these credentials from a REST API app in the Developer Dashboard.

To get these credentials:

Log in to the Developer Dashboard with your PayPal account.
Under the DASHBOARD menu, select My Apps & Credentials.
Make sure you're on the Sandbox tab to get the API credentials you'll use while you're developing code. After you test and before you go live, switch to the Live tab to get live credentials.
Under the App Name column, select Default Application, which PayPal creates with a new Developer Dashboard account. Select Create App if you don't see the default app.
Step result
The Default Application page displays your API credentials, including your client ID and secret.

Exchange your API credentials for an access token
Your access token authorizes you to use the PayPal REST API server. To call a REST API in your integration, exchange your client ID and secret for an access token.

You can make the API call in any programming language. The following sections explain how to get your access token using cURL or Postman.

cURL
Copy the following code and modify it.

curl -v POST https://api-m.sandbox.paypal.com/v1/oauth2/token \
  -H "Accept: application/json" \
  -H "Accept-Language: en_US" \
  -u "CLIENT_ID:SECRET" \
  -d "grant_type=client_credentials"
BASHcopy
Change CLIENT_ID to your client ID.
Change SECRET to your secret.
Postman
In the Postman app, complete the following:

Set the verb to POST.
Enter https://api-m.sandbox.paypal.com/v1/oauth2/token as the request URL.
Select the Authorization tab.
From the TYPE list, select Basic Auth.
In the Username field, enter your client ID.
In the Password field, enter your secret.
Select the Body tab.
Select the x-www-form-urlencoded option.
In the KEY field, enter grant_type.
In the VALUE field, enter client_credentials.
Select Send.
Step result
PayPal returns an access token and the number of seconds the access token is valid. When you make calls to a REST API, include the access token in the Authorization header with the designation as Bearer. Reuse the access token until it expires.

When your token expires, call v1/oauth2/token again to request a new token.

Sample response
{
    "scope": "https://uri.paypal.com/services/invoicing https://uri.paypal.com/services/disputes/read-buyer https://uri.paypal.com/services/payments/realtimepayment https://uri.paypal.com/services/disputes/update-seller https://uri.paypal.com/services/payments/payment/authcapture openid https://uri.paypal.com/services/disputes/read-seller https://uri.paypal.com/services/payments/refund https://api-m.paypal.com/v1/vault/credit-card https://api-m.paypal.com/v1/payments/.* https://uri.paypal.com/payments/payouts https://api-m.paypal.com/v1/vault/credit-card/.* https://uri.paypal.com/services/subscriptions https://uri.paypal.com/services/applications/webhooks",
    "access_token": "A21AAFEpH4PsADK7qSS7pSRsgzfENtu-Q1ysgEDVDESseMHBYXVJYE8ovjj68elIDy8nF26AwPhfXTIeWAZHSLIsQkSYz9ifg
    "token_type": "Bearer",
    "app_id": "APP-80W284485P519543T",
    "expires_in": 31668,
    "nonce": "2020-04-03T15:35:36ZaYZlGvEkV4yVSz8g6bAKFoGSEzuy3CQcz3ljhibkOHg"
}
