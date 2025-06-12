Flow for subscription and payment through CC Avenue.

## To Dos
1. Create subscriptions API
	Create user subscription in user_subscription table if user buys a new subscription.
2. Upgrade subscription API
	Upgrade user subscription to upgrade the user's current subscription to other one. (to be explored more)
3. Renew subscriptions API
	To renew the user subscription.
4. Create user subscription API
	Create subscription payment but for addons not for subscriptions.
5. Save Success Data Web
	To save success data after successful payment and success response from cc avenue.
6. Save Success Data
	Same as web with different request body.
7. Save Failure Data Web
8. Save Failure Data
9. Update request bodies, current one get unnecessary data from FE.

### Overall Steps:
![[subscriptionFLow.png]]




### GetPaymentRequestData Mutation
![[getPaymentRequestData.png]]


### DTO
##### PAYLOAD
{
	cancelURL: "<Front end/>/api/ccavenue-handle?url=/profile/subscription?payment_status=failed",
	language: "EN",
	payingAmount: Float,
	paymentCurrency: String,
	platform: PLATFORM,
	redirectURL: String,
	userSubscriptionId: String,
	userSubscriptionPaymentId: String,
	userToken: <JWT token/>
}

###### Example request body
{
	cancelURL: "https://web-polystox.techdomeaks.com/api/ccavenue-handle?url=/profile/subscription?payment_status=failed"
	language: "EN"
	payingAmount: 23598.82
	paymentCurrency: "INR"
	platform: "WEB"
	redirectURL: "https://web-polystox.techdomeaks.com/api/ccavenue-handle?url=/profile/subscription?payment_status=success"
	userSubscriptionId: "1259"
	userSubscriptionPaymentId: "289"
	userToken: "eyJhbGciOiJIUzI1NiJ9.eyJzdWIiOiI2MjY0MjU1NTE2IiwiZXhwIjoxNzM5Mjc2OTMwLCJpYXQiOjE3MzkxOTA1MzAsImlkIjo5LCJmaXJzdE5hbWUiOiJOaW1pc2giLCJtaWRkbGVOYW1lIjoiSmkiLCJsYXN0TmFtZSI6IlBvcndhbCIsImVtYWlsIjoibmltaXNoLnBvcndhbEA0N2JpbGxpb24uY29tXyIsInBob25lTnVtYmVyIjoiNjI2NDI1NTUxNiIsImlzRGVsZXRlZCI6ZmFsc2UsImt5Y1N0YXR1cyI6IktZQ19BQ0NFUFRFRCIsIkNBTExJTkcgQ09ERSI6MTAxLCJDQUxMSU5HIENPREUgSUQiOiIrOTEiLCJyb2xlcyI6WyJUUkFERVIiXSwiZ3N0VmVyaWZpZWQiOnRydWUsImFjdGl2ZVN1YnNjcmlwdGlvbklkIjoxMjU5LCJpc0NvbXBhbnlWZXJpZmllZCI6ZmFsc2UsInBsYXRmb3JtIjoiV0VCIiwiZGV2aWNlSWQiOiIxIiwiaW9zVmVyc2lvbiI6IjIuMC4yNSIsImFuZHJvaWRWZXJzaW9uIjoiMi4wLjI0IiwiZm9yY2VVcGRhdGUiOnRydWUsImdzdEluIjoiIiwia3ljSWQiOjksIkJBTk5FUl9GUkVRVUVOQ1kiOjMsInByb2ZpbGVQaWMiOiJodHRwczovL3BvbHlzdG94LXByb2QuczMuYXAtc291dGgtMS5hbWF6b25hd3MuY29tL2ltYWdlcy90cmFkZXJzL3Byb2ZpbGUvaW1hZ2VfcGlja2VyX0JGQzhGQzkzLTc5MDktNDlCNC1CNzhBLUU1OUVEOTg0OEQxQy03MzA2Ni0wMDAwMEJDMzU4NDI4NDc3LmpwZyIsInN0YXR1cyI6IkFDVElWRSJ9.FCn5GLYS0GHD2ywFPYLek0NuEAixT6EjeYBY0qoCXlM"
}