# Product-Led-B2B-Saas-company-Airtable

# Overview
This project simulates a B2B SaaS operating analytics environment built entirely in Airtable.
The system centralizes product usage, subscription revenue, and customer support activity to enable real-time monitoring of business performance.
The objective is to transform raw operational records into:
* Decision-ready KPIs
* Automated workflows
* Executive dashboards
  
The solution demonstrates how a modern SaaS company can run product, revenue, and support intelligence without a traditional data warehouse.

## Data Source
The system is built on four operational datasets.

* SaaS Users
Primary entity representing each customer or account.
Acts as the relational hub connecting product, revenue, and support.

* SaaS Feature Events
Event-level telemetry capturing how users interact with the product.
Tracks:
 - Feature name
 - Event type
 - Device
 - Session
 - Timestamp

* SaaS Subscriptions
Commercial data describing monetization.
Tracks:
 - Plan
 - Monthly recurring revenue
 - Start & end dates
 - Subscription lifecycle

* SaaS Support Tickets
Customer service interactions used to measure satisfaction and operational efficiency.
Tracks:
 - Ticket category
 - Priority
 - Status
 - Resolution metrics
 - CSAT

## Problem Statement

Many growing SaaS companies struggle with fragmented data:

* Product usage lives in event logs
* Revenue information lives in billing systems
* Support data lives in ticketing platforms
* Teams lack a unified customer view

Without integration:
* Leadership cannot see churn risk early
* Upsell opportunities are missed
* Support failures go unnoticed
* Product teams cannot measure adoption

This project solves that by building a single source of truth centered around the user.

## Data Modelling
The base follows a hub-and-spoke model.
Core principle:
* Everything rolls up to the user. All the tables (feature event, ticket and subscription) were linked to users table.

- This enables answering critical cross-functional questions such as:

  * Do high-usage customers churn less?
  * Do certain plans generate more tickets?
  * Does poor CSAT impact expansion?

* Modeling techniques used
  - Linked records
  - Rollups (e.g., last activity date)
  - Counts (e.g., total events, ticket volume)
  - Lookups (plan, pricing)
  - Derived flags (activity, SLA, eligibility)
  
This transforms event data into user-level intelligence.

## Key Fields & Metrics
The project converts raw records into actionable SaaS KPIs.

- Product Metrics
  * Total feature events per user
  * Last activity date
  * Active / inactive behavior
  * Engagement intensity
 <img width="2560" height="1436" alt="user1" src="https://github.com/user-attachments/assets/8326f2e2-6670-4f9c-99d9-47db48d140f4" />

- Revenue Metrics
  * Monthly Recurring Revenue (MRR)
  * Paying vs non-paying users
  * Plan distribution
  * Revenue concentration
 <img width="2558" height="1422" alt="subbbbb" src="https://github.com/user-attachments/assets/66e58a46-7758-46be-935c-8454127d1bc8" />

- Support Metrics
  * Average resolution time
  * CSAT score
  * SLA compliance
  * Ticket load per account
  <img width="2560" height="1419" alt="tick2" src="https://github.com/user-attachments/assets/748e3fcc-bed9-4666-82ff-040181406d7d" />
 
- Growth / Lifecycle Signals
  * Churn risk (inactivity proxy)
  * Upsell eligibility
  * Adoption indicators

 ## Automation Implemented
Beyond reporting, this system activates data into real-time operational workflows. Instead of waiting for manual monitoring, key risk and opportunity signals automatically trigger notifications and actions.
The automations transform Airtable from a database into a SaaS operating engine.

* Subscription Cancellation → Win-Back Workflow
  Trigger
When a subscription record changes to Cancelled.

Action:
Automatically sends a notification / win-back communication.

<img width="2560" height="1412" alt="email auto" src="https://github.com/user-attachments/assets/a4028eb5-4ad5-417b-aaf4-a5d40f37194c" />

Business Value:
  * Immediate reaction to churn
  * Enables customer success outreach
  * Prevents silent revenue leakage

* Low CSAT Escalation

Trigger
When CSAT ≤ 3.

Action:
Sends alert to the responsible team.
<img width="2560" height="1434" alt="csat auto" src="https://github.com/user-attachments/assets/1974ce20-3593-4f9f-8ea0-a1efd5310429" />

Business Value:
  * Fast intervention
  * Protects renewals
  * Escalates unhappy customers before churn

* Onboarding Delay Reminder
Trigger
User has not completed onboarding within the defined timeframe.

Action:
Automated reminder email encouraging completion.
<img width="2558" height="1412" alt="onboard auto" src="https://github.com/user-attachments/assets/2e16d36b-bf06-4337-8dac-457dd63437ba" />

Business Value:
  * Improves activation
  * Reduces early churn
  * Drives time-to-value

Abnormal Usage / Support Spike Alert
Trigger
Unusual increase in account activity or support volume.

Action:
Internal notification.
<img width="2556" height="1452" alt="usage spike" src="https://github.com/user-attachments/assets/c3bb6fb4-700b-4cd3-ad5d-795919876136" />

Business Value:
  * Identifies upsell signals
  * Detects product friction
  * Helps teams respond proactively

## Dashboard (Airtable Interface)
### Executive Dashboard 
* Total Users is 1000
   The platform currently has 1000 registered users.
  
<img width="2553" height="1429" alt="saas ex1" src="https://github.com/user-attachments/assets/ccff851b-f3e1-4710-b936-f79b4a574e0b" />

* Users by Signup Source
  * LinkedIn Ads brings the highest share of users
  * Google Ads and Referral are close behind
  * Organic is slightly lower than paid channels

This means that Paid acquisition is driving a large portion of growth, with LinkedIn performing strongest among them.

* Onboarding Delay
About ~30% of users are delayed, while ~70% completed onboarding.
Most users successfully activate, but nearly one-third failing to complete onboarding is a meaningful risk area.

<img width="2556" height="1254" alt="saas ex2" src="https://github.com/user-attachments/assets/a53287f3-2124-4c15-87cb-5e3392bc0512" />

* Users by Company Size
Distribution is relatively balanced, with the largest share coming from mid-sized to larger companies.
The product is not limited to tiny teams; it is attracting structured organizations as well.

* Users by Plan Type
  * Free has the largest population
  * Starter follows
  * Pro is smaller
  * Enterprise is the smallest segment
The majority of the user base is still at the entry levels, meaning monetization and upgrade opportunities exist.

<img width="2560" height="1218" alt="saas ex3" src="https://github.com/user-attachments/assets/50383c9e-5de8-4330-a8e3-e3825d3932a7" />

* Users by Industry
  * SaaS
  * HealthTech
  * E-commerce
  * FinTech
  * EdTech
SaaS companies appear to lead adoption, but usage is diversified across multiple verticals.

* Users by Country
Users are spread across:
USA, Germany, UK, India, Canada, Nigeria.
No single country dominates heavily.

Customer distribution is international rather than concentrated in one market.

<img width="2554" height="1210" alt="saas ex4" src="https://github.com/user-attachments/assets/44022c76-0733-419e-85ea-f34c7745460a" />

* Users by Feature Events
  * Many users cluster around mid-range usage
  * Fewer users at the very high end
  * Very small numbers at extremely low activity
The product has a healthy base of moderately active users, with a smaller but important group of power users.

* Average Revenue by Users
  * A portion of users generate very little or zero revenue
  * Smaller groups contribute higher amounts
Revenue is unevenly distributed — a minority of users likely contribute a large share of total income.

<img width="2560" height="1407" alt="saas ex5" src="https://github.com/user-attachments/assets/2f005013-8e85-4f16-a0d0-4e35b6dc214b" />

* Users Growth by Date
The line fluctuates between peaks and dips but stays within a consistent range.
Growth is steady without extreme spikes or collapses.

* Signup Source → Plan Type (Pivot)
  * Free dominates across most channels
  *  LinkedIn Ads and Referral show strong movement into Starter & Pro
  * Enterprise remains small everywhere
Some channels are better at producing paying users, not just traffic.

<img width="2560" height="1223" alt="saas ex6" src="https://github.com/user-attachments/assets/87c1bf01-cbd8-4d21-95ed-1d01d444d691" />

### Product / Feature Dashboard
* Total Feature Events has 13,000 event_id
This is the total number of tracked product interactions across all users.
Users have performed 13k actions inside the product.

<img width="2551" height="1426" alt="feat1" src="https://github.com/user-attachments/assets/ba3405bd-21a9-4974-afe2-d503efc6e25f" />

* Users by Feature Name
  * Automation Rule (~2,083) is the most used feature.
  * Dashboard View (~1,947) is the least used.
  * All other features sit very close to ~2k usage.
Feature usage is evenly distributed. No single feature is being ignored or overwhelmingly dominating.

* Users by Event Type
  *Submit ≈ 4,018
  Click ≈ 4,015
  View ≈ 3,967
Users are not only viewing — they are actively clicking and completing actions at almost the same volume.

<img width="2560" height="1208" alt="feat2" src="https://github.com/user-attachments/assets/04ecf926-675b-4a9d-852b-90104e7775e5" />

* Usage by Device Type
  * Desktop ~34%
  * Mobile ~34%
  * Tablet ~32%
Traffic is balanced across devices. The product is not dependent on one platform.

* Event Type × Device (Pivot Table)
Views
  * Desktop 1,367 | Tablet 1,311 | Mobile 1,289
Clicks
  * Desktop 1,380 | Tablet 1,272 | Mobile 1,363
Submits
  * Desktop 1,348 | Tablet 1,280 | Mobile 1,390
Engagement behaviour is consistent regardless of device.
Mobile even leads slightly in completed submissions.

<img width="2560" height="1127" alt="feat3" src="https://github.com/user-attachments/assets/e6b5e6ab-68ed-4c74-a977-58ccfbd17b97" />

### Subscription Dashboard
 * Total Subscribers – 791
There are 791 customers currently holding subscriptions.

<img width="2560" height="1428" alt="sub1" src="https://github.com/user-attachments/assets/a0947db9-2824-461a-9117-913924ff07a1" />

* Total Revenue – 34,716
The subscriptions generate 34,716 in recurring revenue.

* MRR Growth (Monthly Trend)
Revenue increased early in 2024, peaked around mid-year (~57), then fluctuated. There is a sharp dip at the most recent point (value ~4), which likely indicates incomplete data for the month, or a recent drop in renewals.


* Subscriptions by Plan Type
  * Free has the highest number of users (~300).
  * Starter follows (~250).
  * Pro is smaller (~170).
  * Enterprise is the smallest (~80).
Most customers are concentrated in the lower tiers.

<img width="2560" height="1208" alt="sub2" src="https://github.com/user-attachments/assets/ec740673-9b7d-4a02-b94c-1475c77812a5" />

* Subscription by Monthly Price
  * Free (0) → largest share (~38%)
  * $25 → ~31%
  * $79 → ~21%
  * $199 → ~10%
The majority of users are still on low or no-revenue plans.

* Subscription End by Month
Cancellations fluctuate between 1 and 8 per month.
January shows the highest spike (~8).
Recent months appear lower.

<img width="2560" height="1422" alt="sub3" src="https://github.com/user-attachments/assets/537fd560-7bbd-40c4-b257-962b8398f0e2" />

* Subscription by Status
  * Active: 710
  * Cancelled: 81
Most subscriptions remain active, with a smaller churn portion.

* Revenue by Plan Type
  * Enterprise: ~15,323 → highest revenue
  * Pro: ~13,193
  * Starter: ~6,200
  * Free: 0
Even though Enterprise has fewer users, it contributes the most money.

<img width="2560" height="1186" alt="sub4" src="https://github.com/user-attachments/assets/41e45770-6f72-4a43-bc6d-8a88639fd1e0" />

* Status × Plan Type (Pivot)
  * Active
Pro 138 | Free 299 | Starter 209 | Enterprise 64
  * Cancelled
Pro 29 | Free 0 | Starter 39 | Enterprise 13
Starter and Pro experience more cancellations in absolute numbers, while Free naturally has none.

### Support Dashboard
* Total Tickets
The team handled 800 support tickets.

<img width="2560" height="1286" alt="sup1" src="https://github.com/user-attachments/assets/0d028bb8-9020-4cfe-9932-e62238f6414c" />

* Users by Ticket Category
Billing generates the highest number of tickets, while Bug reports are the lowest.

* Users by CSAT
Customer satisfaction is relatively balanced across scores, with no extreme skew.

<img width="2560" height="1227" alt="sup2" src="https://github.com/user-attachments/assets/d52c6c85-be6e-465a-9fe9-6fb2e5a51d25" />

* Users by Status
Most tickets are Resolved, while a smaller number remain Open.

* Users by Priority
Tickets are almost evenly split between Low, Medium, and High.

<img width="2560" height="1218" alt="sup3" src="https://github.com/user-attachments/assets/13a43aea-3b91-40de-8fe2-307bb6cdd45c" />

* Users by SLA
A large portion of tickets breached SLA, exceeding those resolved within target.

* Ticket Volume Trend
Ticket demand fluctuates monthly, with a strong spike around early 2025.

<img width="2560" height="1426" alt="sup4" src="https://github.com/user-attachments/assets/76b73a58-f583-4775-a4dd-59dc632fcf46" />

* Pivot – Status vs Priority
Resolved tickets dominate across all priority levels.


## Key Insights
- Users & Acquisition:
   * LinkedIn Ads and Google Ads drive the highest user acquisition.
   * Organic and referral channels contribute, but at lower volumes.
   * Adoption is strongest among mid-sized and larger companies.
   * The Free plan dominates the user base, while Enterprise remains small.

- Onboarding:
  * Roughly 30% of users experience onboarding delays.
  * This indicates friction in activation and potential early drop-off risk.

- Product Usage:
   * 13,000 total feature events were recorded, showing healthy engagement.
   * Usage is fairly evenly distributed across features, with Automation Rules slightly ahead.
   * Clicks and submits slightly exceed views → users are interacting, not just browsing.
   * Engagement is balanced across desktop, mobile, and tablet.
 
- Revenue & Subscriptions:
  * There are 791 subscribers generating 34,716 in revenue.
  * Most subscriptions sit in Free and Starter.
  * Enterprise and Pro, though smaller in count, generate the majority of revenue.
  * Churn exists mainly in Starter and Pro plans.
  * Recent data shows a drop in MRR in the latest period.
 
  - Support
  * 800 tickets have been created.
  * Billing issues generate the highest support demand.
  * Most tickets are resolved, which is positive.
  * However, SLA breaches are significantly higher than SLA meets.
  * Ticket volume shows periodic spikes, suggesting operational pressure at certain times.
 

## Recommendations
- Acquisition & Growth:
  * Double down on LinkedIn Ads and Google Ads, since they produce the strongest results.
  * Investigate how to improve conversion from Free → Paid, especially into Starter and Pro.
 
- Onboarding Improvement:
  * With ~30% delays, introduce guided setup, onboarding checklists, and automated nudges after inactivity.
  * Monitor completion time as a core activation metric.
 
- Product Strategy:
Since feature usage is evenly spread, no feature is failing.
  * Consider promoting higher-value features that can drive paid upgrades.
  * Look for behaviors that correlate with conversion.
 
- Revenue Expansion
  * Protect Pro and Enterprise customers, they bring most of the money.
  * Analyze why Starter & Pro experience more churn.
  * Introduce upsell prompts based on usage thresholds.
 
- Support & Operations
  * Billing needs root-cause fixes or better documentation.
  * SLA breaches are high → may require more staffing, better routing, or automation.
  * Predict spikes and plan capacity ahead.
