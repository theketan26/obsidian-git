#### Notes
1. On create, update or renew subscription addons are not checked.
2. Check the daysToAdd in UserSubcriptionService file. Why it is hard coded as 0?

#### Create user subscription API
{
  "id": 0, **null if new subscription else id**
  "trader": 5102, **for trader details**
  "subscriptionPlan": 0, **for subscription plan**
  "activationDate": "string", **anything if id null else instant date**
  "deactivationDate": "string", **instant date**
  "isAutoPayEnabled": true,
  "isTrial": true,
  "trialPeriod": 0,
  "cancellationDate": "string",
  "status": "PAYMENT_INITIATED",
  "isExpired": true,
  "isDeleted": true,
  "dealQtyUnit": "string",
  "dealOrderLimit": 0,
  "dealQtyLimit": 0,
  "deviceLimit": 0,
  "userLimit": "string",
  "freeAdsLimit": 0,
  "isTrustSeal": true,
  "isPreferredUser": true,
  "isTopBanner": true,
  "isFreeTransitInsuranceIncluded": true,
  "isDedicatedRMSupported": true,
  "couponCode": "string",
  "discountAmount": 0,
  "subTotal": 0,
  "sgst": 0,
  "cgst": 0,
  "igst": 0,
  "grandTotal": 0
}