# Self-Serve-Product-Analytics-Dashboard

Working App --> https://self-serve-dashboard.lovable.app/auth

Problem: Product and Growth teams rely on fragmented reports and manual analysis to measure feature adoption and retention, slowing experimentation and roadmap decisions. Getting a funnel or cohort view means waiting on a data analyst, and different teams calculate metrics like "active user" differently — leading to conflicting numbers.
Goal: Let PMs and Growth stakeholders self-serve answers on adoption, retention, and experiment performance — cutting time-to-insight from days to minutes.
North Star Metric: Weekly Active Insight Generation — number of distinct analyses run by non-analyst users per week.
Key Success Metrics:

Time to insight: 2–3 days → under 10 minutes
Ad-hoc analyst requests: ↓ 60%
Dashboard WAU: 70% of PM/Growth org
Experiments tracked in-platform: 100%

MVP Scope:

Funnel analytics (custom multi-step funnels)
Retention cohorts (D1/D7/D30)
Feature adoption tracking (% of eligible users, segmented)
Experimentation reporting (variant lift, confidence)
Self-serve filtering + saved/shareable views

Out of Scope (later): predictive churn scoring, real-time streaming, full SQL query builder, automated alerting.
Top Priorities (RICE): Funnel Analytics, Retention Cohorts, and Feature Adoption Tracking are P0; Experimentation Reporting, Saved Views, and Metric Glossary are P1.
How It's Built:
Events → ingestion (Kafka/SDK) → warehouse (Postgres/Snowflake) → Python + SQL transformation into funnel/cohort/adoption/experiment tables → a central metrics layer (single definition of "active user," etc.) → FastAPI backend with Redis caching → React + Recharts frontend with filtering and shareable saved views.
Rollout: Event audit & metric alignment (wks 1–2) → MVP pilot with 1–2 teams (wks 3–8) → experimentation + sharing (wks 9–12) → company-wide rollout with RBAC (wks 13–16).
Key Risks: low adoption if UI is too complex, data-trust issues if numbers don't reconcile with existing reports, and performance at scale (mitigated by pre-aggregation and caching).
