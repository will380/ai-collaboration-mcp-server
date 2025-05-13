# License Management

This guide covers the license management system for the AI Collaboration MCP Server, including purchasing, verifying, and managing licenses.

## License System Overview

The MCP Server uses a flexible licensing system with options for subscription-based and one-time purchases. Licenses are securely stored and verified using JWT tokens for maximum security.

### License Types

We offer three main license types:

1. **Monthly Subscription** ($9.99/month)
   - Full MCP server access
   - API access
   - Up to 10 projects
   - Email support

2. **Annual Subscription** ($99.99/year)
   - Full MCP server access
   - API access
   - Unlimited projects
   - Priority email support
   - 17% discount compared to monthly

3. **Lifetime License** ($299.99 one-time payment)
   - Full MCP server access
   - API access
   - Unlimited projects
   - Priority support
   - All future updates

## Purchasing a License

### Using NPX Command

The easiest way to purchase a license is using our NPX command:

```bash
npx ai-collaboration-mcp-server buy
```

This will:
1. Display available plans
2. Let you select a plan
3. Open a secure Stripe checkout page in your browser
4. Email you a license key upon successful payment

### Using the API

You can also create a checkout session programmatically:

```javascript
const response = await axios.post('http://your-server-url/license/checkout', {
  planType: 'MONTHLY_SUB',
  successUrl: 'https://your-app.com/success',
  cancelUrl: 'https://your-app.com/cancel'
});

// Redirect the user to the checkout URL
window.location.href = response.data.data.url;
```

## Verifying a License

After purchasing a license, you'll need to set it up:

### Using NPX Command

```bash
npx ai-collaboration-mcp-server setup
```

When prompted, enter your license key. The tool will verify it and save it to your configuration.

### Using the API

```javascript
const response = await axios.post('http://your-server-url/license/verify', {
  licenseKey: 'XXXX-XXXX-XXXX-XXXX'
});

if (response.data.status === 'success' && response.data.data.valid) {
  console.log('License is valid');
  // Store the license in your configuration
} else {
  console.error('License verification failed:', response.data.message);
}
```

## License Verification in Client Code

When connecting to the MCP server from your client, include the license key in the headers:

```javascript
const transport = new HttpClientTransport({
  url: 'http://your-server-url/mcp',
  headers: {
    'x-license-key': 'XXXX-XXXX-XXXX-XXXX'
  }
});

const client = new McpClient();
await client.connect(transport);
```

## Managing Subscriptions

Users with subscription-based licenses can manage their subscriptions through the Stripe Customer Portal:

### Using NPX Command

```bash
npx ai-collaboration-mcp-server status
```

This will display your license information and provide options to manage your subscription if applicable.

### Using the API

```javascript
const response = await axios.post('http://your-server-url/license/portal', {
  licenseKey: 'XXXX-XXXX-XXXX-XXXX'
});

// Redirect to the portal URL
window.location.href = response.data.data.url;
```

## Subscription Lifecycle

### Active Subscription

While a subscription is active, the license is valid and all features are accessible.

### Subscription Cancellation

If a user cancels their subscription:
1. The subscription remains active until the end of the current billing period
2. After the billing period ends, the license status changes to "inactive"

### Subscription Renewal

Subscriptions are automatically renewed at the end of each period. If a renewal payment fails:
1. The system will attempt to collect payment several times
2. The user will receive email notifications about payment issues
3. If payment cannot be collected, the license status will change to "inactive"

## License Security

Our license system uses several security measures:

1. **JWT Tokens**: Licenses are represented as JWT tokens for secure verification
2. **Secure Storage**: License data is stored securely with proper encryption
3. **Regular Verification**: Licenses are verified on server start and periodically during operation
4. **Expiration**: JWT tokens have built-in expiration to prevent unauthorized use

## Troubleshooting License Issues

### Invalid License

If your license is reported as invalid, check:
- Is the license key entered correctly?
- Has the subscription expired or been cancelled?
- Are you using the latest version of the MCP server?

### License Key Recovery

If you've lost your license key, use the email associated with your purchase to recover it:

```bash
npx ai-collaboration-mcp-server recover-license
```

Enter the email address used for purchase, and a recovery link will be sent to your email.

## Enterprise Licensing

For enterprise customers who need custom licensing terms, please contact our sales team at sales@example.com.

Our enterprise licenses offer:
- Custom user limits
- Extended support options
- On-premises deployment
- Custom development and integrations