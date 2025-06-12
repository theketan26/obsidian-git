# Push
Doing the push notifications first due to existing creds of firebase
*will do later as changes may be required in the current data flow*
   - [ ] On registration complete
   - [ ] KYC Accept
   - [ ] KYC Reject
   - [ ] KYC Re uploaded after rejection
   - [ ] Subscription checkout

# WhatsApp notification
   - [x] On registration complete
   - [ ] KYC Accept
   - [ ] KYC Reject
   - [ ] KYC Re uploaded after rejection

#### Notes
1. Do not have way to accept or reject any KYC document.
2. Do not have
#### WhatsApp token issue
1. Called the create template API, with different different ids
   https://graph.facebook.com/v17.0/<id/>/message_templates
   Result, error, something related to lack of permission, or does not support this operation.
2. Checked permission on, 
   https://developers.facebook.com/tools/debug/accesstoken/?access_token=EAADpi91hNyMBO8ZCm4wy5B4XWs5mDDSXZBm0HhIm2m623j5rJASVWtPK4sCpbflcC4B7DaQTgjbPDwqDTTspXm1U1kGdGIXV0ZBZCQZAajvBxpfsEbi1OruYzMk51s0LaluMMj8LfZAR10v3k1BCbbi8laDIYK3QNVfwda5Y6IRx4gDTSZAOzUQyQZBSSkvCcZC0UWDU2SMzd3wplZCd5E&version=v17.0
   Result, token have the required permission.
3. Called token details fetch API,
   https://graph.facebook.com/v17.0/me
   Result, 
   {
	    "name": "polystox_systemuser",
	    "id": "122265023588011288"
	}
4. Called token details fetch API,
   https://graph.facebook.com/v17.0/me?fields=whatsapp_business_accounts
   Result,
   Tried accessing nonexisting field (whatsapp_business_accounts) on node type (User)
#### Using this for FE firebase notifications
https://medium.com/@munnashisad/fcm-push-notification-in-next-js-app-using-custom-hook-d78494cb9e4f

#### Vapid keys
##### Public Key:
BFFMbpC9v8FoOEuMFTawpNc2Q6kMpVPQkqx2xSIU-9fVIvV8yt2mYM9knOklclIod1i_tT8EloTVritYYNPm0x8
##### Private Key:
AjhJ1gVbxXRsTaailScSVqLBH2gvmm4lBM6bSKIRzno
#### Check the in app notifications
#### Example of Push notification
```
        List<String> fcmTokens = demand.getTrader().getTraderFcmTokens();

        boolean hasFcmTokens = fcmTokens != null && !fcmTokens.isEmpty();

  

        String notificationMsg = messageSource.getMessage("fav_grade_match_msg",

                new Object[]{demand.getTrader().getTraderFullName(), "Demand"},

                defaultLocale);

  

        Notification favGradeNotification = new Notification();

        favGradeNotification.setTraderAction(NotificationMarker.NONE);

        favGradeNotification.setDemand(demand);

        favGradeNotification.setTrader(demand.getTrader());

        favGradeNotification.setFcmTokens(fcmTokens);

        favGradeNotification.setIsSeen(Boolean.FALSE);

        favGradeNotification.setTypeName(NEW_DEMAND);

        favGradeNotification.setTypeId(demand.getId());

        favGradeNotification.setOfferDemandType(demand.getDemandType());

        favGradeNotification.setMessage(notificationMsg);

        logger.info("notification msg {}", notificationMsg);

//                        favGradeNotification.setImage(gradeImage);

        logger.info(" trader id {}", demand.getTrader().getId());

        notificationResolver.save(favGradeNotification);

        if (hasFcmTokens) {

            pushNotificationUtil.sendNotification(

                    messageSource.getMessage("fav_grade_match_subject", new Object[0], Locale.getDefault()),

                    notificationMsg,

                    TYPE_NAME, OFFER,

                    NOTIFICATION_ID, String.valueOf(favGradeNotification.getId()),

                    ID, String.valueOf(demand.getId()),

                    OFFER_DEMAND_TYPE, demand.getDemandType().name(),

                    fcmTokens,

                    null

//                                    gradeImage

            );

        } else {

            String comment = (fcmTokens == null) ? FCM_TOKEN_NULL : FCM_TOKEN_EMPTY;

            favGradeNotification.setComment(comment);

            notificationResolver.save(favGradeNotification);

        }

        notificationPublisher.publish(favGradeNotification, CREATED);

        notificationPublisher.publishAdminUnseenCount();

        notificationPublisher.publishMarker();
```

#### Example of WhatsApp notification
```        
try {

            logger.info("executing trader whatsapp scheduler, current time {}", Instant.now());

            List<Trader> whatsappActiveTraders = traderRepository.findWhatsappActiveTraders();

            logger.info("total whatsapp active traders {}", whatsappActiveTraders.size());

            whatsappActiveTraders.forEach(trader -> {

                try {

                    logger.info("send whatsapp initiative msg to trader {}", trader.getPhone());

                    if ((trader.getPhone() != null && !trader.getPhone().isEmpty()) && (trader.getCallingCodeId() != null && !trader.getCallingCodeId().isEmpty()))

                        sendMessageToUserAfterHelp(trader.getCallingCodeId().concat(trader.getPhone()));

                } catch (IOException e) {

                    throw new RuntimeException(e);

                }

            });

        } catch (Exception e) {

            logger.error("Exception in executeTraderWhatsappScheduler method {}", e.getMessage(), e);

        }

    }
```

#### Temp code in ketan/PSTXD-327/css-unnest branch






