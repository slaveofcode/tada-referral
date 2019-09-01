---
marp: true
---

# TADA Referral
@engineer_session

+++
# The History of Referral
- Start from a Membership feature (Tambah Member)
- Starting from a simple **Perk** feature
- Referral only on perk using SMS media
---
# And then...
- It's started to be Separated from Membership
- The benefit of thinking BIG from the beginning
- Not related anymore with Membership Whitelist data
---
# Ok, let be more serious Now!
+++
# The FLOW of Referral Program (Origin story)
- Admin setup Reward Program (and Commission) on AVBO
- Make a Perk for it
- Select the Reward Program 
- Publish...
---
# Referral Event Trigger
- Topup (Created... and Used..)
- Make an Order (Created... and abandoned...)
- Customer Registered?
- Made a Subscription?
+++
# Types of Referral (until now... finger-crossed)
- via SMS
- via Membership Landing Page website (membership.usetada.com/wtv)
- via Subdomain Website (demo.tada.st)
- via Subscription ?
---
# Show me the Tables
- Perk(RewardProgramId...)
- RewardPrograms(RewardedCardProgramId, AdvocateCardProgramId, type[membership, referral, referral_subdomain, ...], initiator[perk, subd..])
- RewardWhitelists(phone, isRewarded, ...)
- Commissions
- CommissionCriterias
- RewardCommissions(RewardProgramId, CommissionId)
- RewardCommissionValues
- RewardReferralUsers(GCIUserId, ReferrerId)
- RewardAttachments...
- ReferralSubdomains...
- ReferralCodes...
- RewardUnregisterCommissions ?
- and others...
--- 
# Legacy Referral Code Base
- Placed on `/lib/reward_program` directory
- There are 3 different subdirectory `referral`, `membership`, `attachment`
- `referral` holds all about the referral logic, commission topup and the common referral utils
- `membership` holds all about the membership logic
- `attachment` holds the event emiter for attachment program
- you mastered these code, you're awesome!
---
# Big Parts of Referral Process
1. User Relationship Function
2. Event Trigger Function (transaction, order creation, register customer, etc.)
3. Commission Calculation and Topup
+++
# User Relationship
- Made a relationship through `RewardReferralUsers` using card as identifier
- Then continue to reward program 
- and commission criteria
---
# Event Trigger Function
- Attaching specific function into some transaction event like order, topup, etc.
---
# Commission Calculation
1. Calculator Commission
2. Generator Commission, following the rules & reward from commission criteria.
3. Recording the rewarded commission.
