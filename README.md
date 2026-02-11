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
