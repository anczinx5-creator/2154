# Business Model - Pricing & Payments

## Overview
The platform implements a subscription-based business model where institutions and employers pay for access, while students use the platform for free.

## Pricing Structure

### Institution Plans
1. **Basic Plan** - $99.99/month
   - 100 credentials per month
   - Email support
   - Analytics dashboard

2. **Pro Plan** - $299.99/month
   - 500 credentials per month
   - Priority support
   - Analytics dashboard
   - Custom branding

3. **Enterprise Plan** - $999.99/month
   - Unlimited credentials
   - 24/7 support
   - Analytics dashboard
   - Custom branding
   - API access

### Employer Plans
1. **Basic Plan** - $49.99/month
   - 50 verifications per month
   - Email support

2. **Pro Plan** - $149.99/month
   - 200 verifications per month
   - Priority support
   - Bulk verification

### Student Access
- **FREE** - Students have unlimited access to:
  - Store credentials
  - Share credentials
  - View credential history
  - 3D credential showcase

## TRINETRA Promo Code
For the current phase, use the promo code **TRINETRA** to get 100% discount on all plans.

### How to Use:
1. Select a plan (Institution or Employer)
2. Enter "TRINETRA" in the promo code field
3. Click "Apply"
4. Complete the payment (final amount will be $0.00)
5. Get instant access for 1 year

## Features

### Payment System
- Subscription-based access control
- Promo code system with:
  - Percentage or fixed discounts
  - Expiration dates
  - Usage limits
  - User type restrictions
- Transaction history tracking
- Automatic subscription management

### Access Control
- **Institutions**: Must have active subscription to issue credentials
- **Employers**: Free tier (3 verifications), then subscription required
- **Students**: Always free, no restrictions
- Real-time subscription status checking

### Database Tables
1. `pricing_plans` - Stores available subscription plans
2. `payment_transactions` - Records all payment transactions
3. `promo_codes` - Manages promotional codes
4. `user_subscriptions` - Tracks active user subscriptions

## Implementation Details

### Subscription Checking
```typescript
import { checkUserSubscription } from './utils/subscriptions';

const { hasAccess, subscription } = await checkUserSubscription(
  walletAddress,
  'institution' // or 'employer'
);
```

### Payment Flow
1. User selects a plan
2. Optionally applies promo code
3. System calculates final amount
4. Transaction is recorded in database
5. Subscription is activated if payment is $0 (promo code)
6. Access is granted immediately

### Free Tier for Employers
- First 3 verifications are free
- After that, subscription required
- Counter tracked in component state
- Persistent across page reloads possible with localStorage

## Future Enhancements
- Stripe/PayPal integration for real payments
- Automatic recurring billing
- Usage analytics per plan
- Plan upgrade/downgrade functionality
- Email notifications for subscription events
- Invoice generation
- Multi-currency support
