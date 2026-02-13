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
