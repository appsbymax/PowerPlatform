# PowerApps – Problem Analysis & CAPA Suite (6W2H · 5 Whys · Ishikawa)

## Quick Overview
A PowerApps solution for **incident intake (6W2H)**, **root-cause analysis** (5 Whys & Ishikawa), and **CAPA action management** with personal task views and automated reminders.  
The tool **significantly improves cross-functional communication and execution** across the organization — it is used continuously not only for analysis but also for **issue escalation** and day-to-day coordination.  
**Adoption:** 100+ unique users.

**Tech used:** PowerApps · Power Automate · SharePoint List · Power BI (optional) · Outlook

---

## Capabilities
- **Capture (6W2H):** structured incident form with evidence.
- **Team setup:** assign analysis team & roles.
- **Root cause:** interactive **5 Whys** and **Ishikawa** (e.g., 6M).
- **Action Plan (CAPA):** containment / corrective / preventive; owners, due dates, status.
- **My Tasks:** personal inbox with filters and quick updates.
- **Notifications:** assignment emails + **automatic reminders** (due in **2 days** and **today**).
- **Escalations:** route overdue or high-priority items to stakeholders.
- **Reporting (optional):** Power BI dashboards (trends, hotspots, downtime).

---

## Impact & Adoption
- **100+ unique users** active across departments.
- Faster alignment between **Production, Quality, Maintenance, Safety**.
- Central source of truth from **incident → analysis → actions → closure**.

---

## Architecture
- **PowerApps (Canvas):** forms (6W2H), RCA (5 Whys, Ishikawa), CAPA, My Tasks.
- **SharePoint Lists:** Incidents, Teams, Actions, RCA_Whys, Ishikawa_Causes (lookups).
- **Power Automate:** on-create/assign notifications; daily reminder jobs (T-2 / T-0).
- **Outlook:** delivery of assignment & reminder emails.
- **Power BI:** KPIs & trend analytics.

---

## Process & Notifications (high level)
1) **Report** incident (6W2H) → 2) **Assemble team** → 3) **Analyze causes** (5 Whys / Ishikawa)  
4) **Plan CAPA** → 5) **Execute & track** (My Tasks) → 6) **Reminders/Escalations** → 7) **Close & report**

> **Reminder logic:** daily check for actions where `Status <> 'Closed'` and `DueDate ∈ {Today+2, Today}`; group by Owner; send a single digest email. Optional escalation for overdue.

---

## How it looks?

### 1) Core App
| Preview | Description |
|---|---|
|<img width="2302" height="1294" alt="MainScreen_baza_analiz" src="https://github.com/user-attachments/assets/b78d88d1-fb1a-459b-b504-0deae50cea45" />| **Main Screen** – entry, navigation, quick links |
| <img width="2861" height="1612" alt="NewForm_baza_analiz" src="https://github.com/user-attachments/assets/72315ddd-54c3-49b2-ac8f-c45046e6daf8" />| **New Request** – 6W2H intake with evidence |
| <img width="1912" height="1072" alt="Gallery_baza_analiz" src="https://github.com/user-attachments/assets/8e002c31-4a3c-457a-b12f-1f68318c3c65" /> | **Analyses Gallery** – each tile represents **one analysis** |
| <img width="2304" height="1292" alt="details_baza_analiz" src="https://github.com/user-attachments/assets/4bd94e19-0bce-408c-8d10-e4be12c206af" /> | **Request Details** – example record with metadata |

### 2) Analysis Views
| Preview | Description |
|---|---|
| <img width="2290" height="1284" alt="6w2h_baza_analiz" src="https://github.com/user-attachments/assets/04d1e656-b428-4eb4-ae25-06810cedc82e" />| **6W2H Review** – structured problem framing |
|<img width="2866" height="1598" alt="Ishikawa_baza_analiz" src="https://github.com/user-attachments/assets/023de385-e316-4607-8ef3-96c4ce6a76cc" />  | **Ishikawa** – category-based cause map (e.g., 6M) |
| <img width="2860" height="1608" alt="5Why_baza_analiz" src="https://github.com/user-attachments/assets/b933f0aa-dbf8-474a-a6d5-fddfadefbf41" />| **5 Whys** – root-cause chain |
|<img width="1112" height="1856" alt="ProcessTree_baza_analiz" src="https://github.com/user-attachments/assets/81edeb2c-ab71-4d17-b7f1-1fe538c3a7ca" /> | **Process Tree** – end-to-end flow perspective |

### 3) Tasking & Notifications
| Preview | Description |
|---|---|
|<img width="2116" height="1072" alt="ListaZadan_baza_analiz" src="https://github.com/user-attachments/assets/7525c0b7-148e-4d00-ae30-3c1e83b16a10" />  | **Tasks Gallery** – filter by **status, owner name, task ID** |
| <img width="891" height="805" alt="mail1_baza_analiz" src="https://github.com/user-attachments/assets/1d692496-5eb2-4a42-bc28-0456105055b3" />| **Assignment Email** – action summary to the owner |
|<img width="1842" height="1005" alt="mail2_reminder_baza_analiz" src="https://github.com/user-attachments/assets/2ed581be-4f96-4dca-a26a-c27b47e95d0a" />| **Overdue Reminder** – automatic T-0 / escalation |

### 4) Reporting (Power BI)
| Preview | Description |
|---|---|
|<img width="3115" height="1750" alt="PowerBI_1_baza_analiz" src="https://github.com/user-attachments/assets/f0703016-260e-4746-a5ba-afeffa9d1267" /> | **Power BI – App Overview** – KPIs, trends |
| <img width="3122" height="1748" alt="PowerBI_2_baza_analiz" src="https://github.com/user-attachments/assets/4ef72f25-d5bf-40d5-bdc9-5b87541fa079" /> | **Power BI – Area Statistics** – hotspots & throughput |
| <img width="3124" height="1757" alt="PowerBI_3_baza_analiz" src="https://github.com/user-attachments/assets/7d709bed-8b81-4e5a-b628-f67c45879d73" /> | **Power BI – Technical Downtime by Area** |

---

##  Data Model (example)
- **Incidents**: Title, 6W2H fields (Who/What/Where/When/Why/How/How much), Area, Severity, Status, Reporter, Date, Attachments  
- **Teams**: IncidentId (lookup), Member, Role  
- **RCA_Whys**: IncidentId, WhyLevel (1–5), Text, ParentId  
- **Ishikawa_Causes**: IncidentId, Category, Cause, Evidence  
- **Actions**: IncidentId, Type (Containment/Corrective/Preventive), Description, Owner, DueDate, Status, Priority

---

##  Why it matters
- **Cross-functional execution**: faster hand-offs and clearer ownership.  
- **Always-on usage** for analysis **and** escalation, not a one-off tool.  
- Traceable lifecycle from **incident → root cause → CAPA → closure**.

---

## My Role
- Designed end-to-end solution architecture (PowerApps, SharePoint, Power Automate)
- Implemented RCA modules (5 Whys, Ishikawa) and full CAPA lifecycle
- Built task inbox, reminder engine (T-2/T-0) and escalation logic
- Provided end-user support, training and functional testing
- Enabled organization-wide adoption across **120+ active users**
- Prepared data model and reporting layer for Power BI analytics

## Business Impact
- Supports **hundreds of incident analyses** and **over a thousand CAPA actions annually**
- Improved cross-functional coordination and ownership transparency
- Reduced manual follow-ups through automated reminders and escalations
- Created a centralized, traceable lifecycle from **incident → root cause → closure**


