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
 
- Revenue Metrics
  * Monthly Recurring Revenue (MRR)
  * Paying vs non-paying users
  * Plan distribution
  * Revenue concentration
 
- Support Metrics
  * Average resolution time
  * CSAT score
  * SLA compliance
  * Ticket load per account
 
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

Business Value:
  * Immediate reaction to churn
  * Enables customer success outreach
  * Prevents silent revenue leakage

* Low CSAT Escalation

Trigger
When CSAT ≤ 3.

Action:
Sends alert to the responsible team.

Business Value:
  * Fast intervention
  * Protects renewals
  * Escalates unhappy customers before churn

* Onboarding Delay Reminder
Trigger
User has not completed onboarding within the defined timeframe.

Action:
Automated reminder email encouraging completion.

Business Value:
  * Improves activation
  * Reduces early churn
  * Drives time-to-value

Abnormal Usage / Support Spike Alert
Trigger
Unusual increase in account activity or support volume.

Action:
Internal notification.

Business Value:
  * Identifies upsell signals
  * Detects product friction
  * Helps teams respond proactively

## Dashboard (Airtable Interface)
### Executive Dashboard 
* Total Users is 1000
   The platform currently has 1000 registered users.

* Users by Signup Source
  * LinkedIn Ads brings the highest share of users
  * Google Ads and Referral are close behind
  * Organic is slightly lower than paid channels

This means that Paid acquisition is driving a large portion of growth, with LinkedIn performing strongest among them.

* Onboarding Delay
About ~30% of users are delayed, while ~70% completed onboarding.
Most users successfully activate, but nearly one-third failing to complete onboarding is a meaningful risk area.

* Users by Company Size
Distribution is relatively balanced, with the largest share coming from mid-sized to larger companies.
The product is not limited to tiny teams; it is attracting structured organizations as well.

* Users by Plan Type
  * Free has the largest population
  * Starter follows
  * Pro is smaller
  * Enterprise is the smallest segment
The majority of the user base is still at the entry levels, meaning monetization and upgrade opportunities exist.

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

* Users by Feature Events
  * Many users cluster around mid-range usage
  * Fewer users at the very high end
  * Very small numbers at extremely low activity
The product has a healthy base of moderately active users, with a smaller but important group of power users.

* Average Revenue by Users
  * A portion of users generate very little or zero revenue
  * Smaller groups contribute higher amounts
Revenue is unevenly distributed — a minority of users likely contribute a large share of total income.

* Users Growth by Date
The line fluctuates between peaks and dips but stays within a consistent range.
Growth is steady without extreme spikes or collapses.

* Signup Source → Plan Type (Pivot)
  * Free dominates across most channels
  *  LinkedIn Ads and Referral show strong movement into Starter & Pro
  * Enterprise remains small everywhere
Some channels are better at producing paying users, not just traffic.

### Product / Feature Dashboard
* Total Feature Events has 13,000 event_id
This is the total number of tracked product interactions across all users.

Users have performed 13k actions inside the product.

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

### Subscription Dashboard
 * Total Subscribers – 791
There are 791 customers currently holding subscriptions.

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

* Status × Plan Type (Pivot)
  * Active
Pro 138 | Free 299 | Starter 209 | Enterprise 64
  * Cancelled
Pro 29 | Free 0 | Starter 39 | Enterprise 13
Starter and Pro experience more cancellations in absolute numbers, while Free naturally has none.

### Support Dashboard
* Total Tickets
The team handled 800 support tickets.

* Users by Ticket Category
Billing generates the highest number of tickets, while Bug reports are the lowest.

* Users by CSAT
Customer satisfaction is relatively balanced across scores, with no extreme skew.

* Users by Status
Most tickets are Resolved, while a smaller number remain Open.

* Users by Priority
Tickets are almost evenly split between Low, Medium, and High.

* Users by SLA
A large portion of tickets breached SLA, exceeding those resolved within target.

* Ticket Volume Trend
Ticket demand fluctuates monthly, with a strong spike around early 2025.

* Pivot – Status vs Priority
Resolved tickets dominate across all priority levels.
