---
date: 2026-06-30 12:00:00
title: From Door Knocks to Data
description: Analysing Deep Canvassing Conversations in the Netherlands
author: Felicity Fan
tags:
  - data science
  - Deep Canvassing
  - Python
image: /images/2026_deep_canvassing_logo.png
---

*This blog post was written by Felicity Fan.*

<b>Partner:</b> [Deep Canvassing Nederland](https://www.deepcanvassing.nl)<br />
<b>Team:</b> 2 Data Enthusiasts, 1 Project Lead<br />
<b>Topic:</b> Analysing deep canvassing survey data<br />
<b>Skills:</b> Python, Streamlit, Pandas, GeoPandas, Git, Data Visualisation, NLP<br />
<b>Project start:</b> January 2026<br />
<b>Project end:</b> July 2026<br />
<b>Place:</b> Remote<br />
<b>Project goals:</b> Evaluate the impact of the deep canvassing campaign on immigration attitudes, understand what drives impact, and build an interactive dashboard to make ongoing insights accessible to the organisation.<br />

## What is Deep Canvassing Nederland?

Deep canvassing is a conversation method where trained volunteers knock on doors and have genuine, empathy-driven conversations with strangers about socially divisive topics. Unlike traditional political canvassing, deep canvassing is not about delivering a message — it is about listening, sharing personal stories, and creating space for people to reflect on their own views. It is one of the few persuasion methods that has been scientifically shown to produce durable attitude change.

[Deep Canvassing Nederland](https://www.deepcanvassing.nl) is a Dutch organisation founded in 2023 with a mission to bring this method to the Netherlands. For the past two years, around a hundred volunteers have been knocking on doors across the country to have 15–20 minute conversations about immigration — one of the most divisive topics in Dutch public life. Every conversation is logged in a custom-built web app, designed with European privacy law in mind so that no single conversation can be traced back to an individual address or volunteer.

## Deep Canvassing Nederland × CorrelAid Netherlands

By early 2026, Deep Canvassing Nederland had built up a rich dataset of thousands of door knocks and conversations — and wanted to understand what it was telling them. That is where CorrelAid Netherlands came in.

Our team of three volunteer data analysts joined forces with the organisation to do three things: evaluate whether the campaign was having a measurable impact on immigration attitudes, understand what factors were associated with the most successful conversations, and build tools that would make these insights available to the organisation on an ongoing basis.

The project ran from January to July 2026, entirely remotely, and resulted in two key deliverables: an interactive Streamlit dashboard and a comprehensive analysis report.

## The Data

Each time a volunteer has a conversation, they record a range of information: where the conversation took place, how many canvassers were present, and crucially — how the participant rated their own attitude on two key statements about immigration, both before and after the conversation, on a scale from 1 to 10.

This before-and-after design is at the heart of what makes deep canvassing measurable. It allows the organisation to go beyond asking "did people seem receptive?" and instead ask: "did attitudes actually shift?"

Over the course of the campaign, volunteers logged activity across eleven regions of the Netherlands, with conversations taking place on every day of the week — though, as you might expect for a volunteer-driven effort, Saturdays were by far the busiest.

<img src="/images/2026_deep_canvassing_activity_dow.png" alt="Bar chart of conversations by day of week, with Saturday by far the busiest, followed by Sunday." style="width:700px;" />

## What We Built

### An Interactive Dashboard

The centrepiece of the project is a multi-page Streamlit dashboard, built entirely in Python and deployed for internal use by the organisation. It gives the Deep Canvassing Nederland team a live view of their data across three main areas:

* **Attitude scores:** How immigration attitudes are shifting before and after conversations, and how this has changed over time
* **Geographic analysis:** Where canvassing is happening across the Netherlands, and how scores vary by region
* **Trends:** How conversation volumes have grown over time, by day of week and by region

The dashboard is designed to be updated as new data comes in, giving the organisation a tool for ongoing monitoring rather than a one-time snapshot.

<img src="/images/2026_deep_canvassing_dashboard.png" alt="Screenshot of the Deep Canvassing Survey Analysis dashboard showing a quick overview of survey rows, postcodes, date range and average migration score." style="width:700px;" />

### An Analysis Report

Alongside the dashboard, we produced a written analysis report covering the full scope of the project: campaign reach, attitude change, geographic patterns, and recommendations for improving data collection and canvassing strategy going forward.

## What the Data Showed

### Conversations are making a difference

The most important finding from the analysis is also the most encouraging: deep canvassing conversations in the Netherlands are associated with a positive shift in immigration attitudes. Among participants who had room to move — that is, those who did not already hold the most positive possible view — a meaningful share increased their score after the conversation. Those who moved downward were a much smaller group.

Put differently: conversations are far more likely to shift someone in a positive direction than a negative one. The effect is modest for most individuals — a point or two on a ten-point scale — but it is consistent, and it is in the right direction.

<img src="/images/2026_deep_canvassing_score_change.png" alt="Histogram of the score change (after minus before), centred on zero with a longer positive than negative tail." style="width:700px;" />

### Geography matters

One of the more analytically interesting findings was the relationship between where canvassing takes place and how effective it tends to be. Using postcode-level data and 2025 election results, we were able to show that immigration attitudes vary meaningfully across Dutch regions — and that this variation has implications for where volunteer effort is likely to have the greatest impact.

<img src="/images/2026_deep_canvassing_postcode_map.png" alt="Map of the Netherlands showing visits and conversations by postcode, with a total of 7,517 visits, 1,864 conversations and a 24.8% conversion rate." style="width:700px;" />

### Activity has grown — with a visible spike

Conversation volumes have grown substantially over the two-year period covered by the dataset. There is a particularly visible spike in activity around the time of the 2025 Dutch elections, reflecting the heightened motivation of volunteers to engage with the public during a politically significant moment.

<img src="/images/2026_deep_canvassing_over_time.png" alt="Chart of conversations per month over time, growing steadily with a pronounced spike around the 2025 Dutch elections." style="width:700px;" />

## Looking Ahead

The dashboard is designed to continue beyond this project, giving the organisation the ability to track their own progress over time without relying on external analysts. We have also shared a set of recommendations for how data collection practices could be improved — covering everything from richer volunteer records to follow-up surveys that could help measure whether attitude changes last beyond the day of the conversation.

## Conclusion

This project showed what is possible when a small team of volunteer data analysts works closely with a motivated civic organisation. Deep Canvassing Nederland has been doing something remarkable for two years — knocking on doors, having difficult conversations, and quietly trying to shift one of the most entrenched social debates in the Netherlands. The data suggests their efforts are working. Our job was to help them see that clearly, and to give them the tools to keep tracking it.

___

_The volunteer team and CorrelAid Netherlands would like to thank Deep Canvassing Nederland for the inspiring collaboration and for their trust in sharing their data with us. It was a privilege to work on a project with such direct social relevance, and we hope the tools and analysis we have delivered will continue to be useful long after this project has wrapped up._

_CorrelAid Netherlands would also like to thank our wonderful volunteers, who dedicate their time and skills to meaningful causes. Thank you for making a difference!_

**Volunteers**: Mehmet Kutluay, Josha van Houdt, Felicity Fan

**Deep Canvassing NL**: Pippi van Ommen

**CorrelAid Netherlands**: Alexis Gillett, Fabian Dablander
