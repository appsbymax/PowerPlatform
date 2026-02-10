PowerApps – Near Miss Reporting App

##  Quick Overview
A PowerApps solution that enables **every employee** to report a **Near Miss** (“close call”) in seconds.  
Submissions are instantly routed to the right people. The app supports **classification/area filtering, risk assessment, root-cause analysis (5 Whys)**, and **action assignment** (containment/corrective/preventive).

**Tech used:** PowerApps · Power Automate · SharePoint List · Power BI (optional) · Outlook

---

##  Capabilities
- Fast reporting with attachments (photo/video)
- Instant notifications to safety/area owners (Power Automate + Outlook)
- Browsing & filtering by classification, area, date, status
- Risk assessment (severity × likelihood, auto score)
- Root cause via interactive **5 Whys**
- CAPA actions (containment/corrective/preventive) with owners & due dates
- Status, SLA & follow-ups; optional Power BI dashboards

---

##  Architecture
- **PowerApps (Canvas)**: forms, galleries, RCA, actions
- **SharePoint List(s)**: reports, actions, classifications
- **Power Automate**: routing, notifications, escalations
- **Outlook**: email delivery
- **Power BI**: trends & KPIs

**Process Diagram**  
![Process Diagram]( <img width="3268" height="411" alt="near_miss_process" src="https://github.com/user-attachments/assets/6be4c4c4-df6c-4e9f-a7f2-86f9542a8f1c" />)

---

##  Screenshots
| Preview | Description |
|---|---|
| <img width="1432" height="805" alt="Main_screen_NM" src="https://github.com/user-attachments/assets/65b0bd42-d79e-4938-8bc7-20147a08f6f8" /> | **Main Screen** – entry & navigation |
| <img width="1303" height="740" alt="form_screen_NM" src="https://github.com/user-attachments/assets/836c4062-0630-42f1-b73e-d952d8fa467c" /> | **Formularz** – new Near Miss form (attachments) |
| <img width="1396" height="740" alt="gallery_screen_NM" src="https://github.com/user-attachments/assets/b456e6fd-07f3-4400-9c8d-dc1c60d89d4f" /> | **Galleria** – list of reports with filters |
| <img width="1389" height="738" alt="details1_screen_NM" src="https://github.com/user-attachments/assets/a6d7fc88-af7f-42fd-b759-110a9bccaf79" /> | **Szczegóły zgłoszenia** – full report details |
| <img width="1391" height="739" alt="Ocenaryzyka1_screen_NM" src="https://github.com/user-attachments/assets/990f56e9-a4c7-48bb-b423-8b6917988259" /> | **Ocena ryzyka** – severity × likelihood, score |
| <img width="1390" height="674" alt="5why_screen_NM" src="https://github.com/user-attachments/assets/92648494-042c-48ab-aac4-471a32f4357b" /> | **5 Why** – root cause tree |
| <img width="1391" height="449" alt="akcje_koryg_screen_NM" src="https://github.com/user-attachments/assets/6e0525f0-f435-4f0c-a693-b95ee637b6e8" /> | **Akcje korygujące** – CAPA with owners & due dates |
| <img width="508" height="648" alt="flow_NMpng" src="https://github.com/user-attachments/assets/bfaecd51-71d8-4d90-a939-d5ea1c1ba865" /> | **Flow (Power Automate)** – routing/escalation |
| <img width="587" height="342" alt="mail_NMpng" src="https://github.com/user-attachments/assets/aba654fa-6c7a-423f-a629-311cc88f50d8" /> | **Mail powiadomienia** – auto email to stakeholders |


---

##  Data Model
- **NearMiss**: Title, Description, Area, Classification, Severity, Likelihood, **RiskScore**, Reporter, Date, Attachments, Status
- **Actions**: Type (Containment/Corrective/Preventive), Description, Owner, DueDate, Status, **NearMissId**
- **RCA**: 5 Whys nodes linked to **NearMissId**

---

## ✅ Why it matters
- Faster reporting and fewer missed “almost incidents”
- Structured RCA with accountable actions
- Stronger safety culture through transparency and feedback
