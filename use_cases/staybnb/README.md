# Staybnb

![Cortex Agents](_resources/SnowPrint_header.png)

## Overview
**Staybnb** is a global online marketplace that connects people looking to rent out their homes with those seeking short-term accommodations. Whether it's a cozy apartment in the city, a beachfront villa, or a unique treehouse in the woods, Airbnb offers travelers a wide variety of places to stay in over 220 countries and regions. With a focus on community, trust, and personalized experiences, we enable hosts to earn income while helping guests experience destinations like locals.

## Use Case Deployment
Execute this SQL Query to create and run the notebook in your account which will generate data and required services.
```sql
EXECUTE IMMEDIATE FROM @CORTEX_AGENTS_DEMO.PUBLIC.GITHUB_REPO_CORTEX_AGENTS_DEMO/branches/main/use_cases/staybnb/_internal/setup.sql
  USING (BRANCH => 'main', EXECUTE_NOTEBOOKS => TRUE) DRY_RUN = FALSE;
```

## Structured Data & Use Cases
This repository contains a **fictional dataset** from _Staybnb_. The dataset is split into two core tables that capture information about properties and bookings:

1. **Homes**  
   Contains data about property type and total square meters.

2. **Bookings**  
   Contains information about booking dates, nightly rates and cleaning fees.  

In addition to that we also have image data of properties available. These images are analyzed via a multimodal LLM to extract the room type and the available appliances.
This leads to a third table:  

3. **RENTAL_HOME_ROOMS_STRUCTURED**  
   Contains the rooms and all available appliances per room per home.  

## Unstructured Data & Use Cases
Each property has a description that includes information about the surrounding location, the outdoor area, the host, etc.

## Example Questions
### Selected Services:
Make sure to select the following services for the questions to work:  
- **RENTAL_HOME_DESCRIPTIONS**
- **rental_home_bookings.yaml**

### **Questions for Structured Data**
These queries operate on structured, tabular data sources.

| Question | Data Complexity | Query Complexity |
|----------|----------------|--------|
| Provide an overview per calendar week of how many print jobs are still pending. | Single table, no Search Integration | 🟢 **Easy** |
| Which customers in United Kingdom have the most jobs cancelled? Provide a top 10 list. | 2 tables, 1 Search Integration | 🔴 **Hard** |

### **Questions for Unstructured Data**  
These queries analyze text-based documents.

| Question | Data Complexity | Query Complexity |
|----------|----------------|--------|
| What are the core components of the Prinect Manager CR workflow? | Single text chunk | 🟢 **Easy** |
| What are the basic steps for setting up users and customers? | 2 chunks from one document | 🟡 **Medium** |
| How does the standardized offset print process, including the use of a profile connection space, get operationalized within the Prinect Manager CR workflow during job creation and press calibration? | 4 chunks across two documents | 🔴 **Hard** |