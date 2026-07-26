<div align="center">

<!-- ============================================================
     HERO
     Regenerate the two custom pieces below (ascii portrait + info
     card) with: python scripts/make_ascii_svg.py / make_info_card.py
     The banner + typing line are external services (capsule-render,
     readme-typing-svg) -- see the note at the bottom of this file.
     ============================================================ -->

<img src="https://capsule-render.vercel.app/api?type=wave&height=180&color=0:020617,50:1e1b4b,100:312e81&section=header&text=Kartik%20Singh&fontSize=46&fontColor=e2e8f0&fontAlignY=42&animation=fadeIn" width="100%" alt="Kartik Singh" />

<a href="https://git.io/typing-svg"><img src="https://readme-typing-svg.demolab.com/?font=JetBrains+Mono&weight=600&size=20&duration=2800&pause=1000&color=A5B4FC&center=true&vCenter=true&width=780&lines=Data+Science+%C2%B7+AI%2FML+Engineer+%C2%B7+Full-Stack+Builder;Grounding+LLMs+in+real+data%2C+not+guesses;90+years+of+market+data+%C2%B7+one+production+ML+pipeline;4+internships+%C2%B7+GM+%26+founder-level+recognition" alt="Typing SVG" /></a>

<br>

</div>

## `whoami`

<table>
<tr>
<td valign="top" width="43%"><img src="./kartik-ascii.svg" width="100%" alt="Kartik Singh — ASCII portrait" /></td>
<td valign="top" width="57%"><img src="./info-card.svg" width="100%" alt="Kartik Singh — experience, stack, highlights" /></td>
</tr>
</table>

Final-year **Data Science** undergraduate (Minor: Finance) at UPES, currently splitting time between an AI product/analytics internship at **Polluxa** and a data science internship at **Gravity Engineering** — on top of two earlier internships at **Maruti Suzuki India Ltd.** Comfortable moving from a SQL query to a Power BI dashboard to a FastAPI backend to an LLM-grounded pipeline, and have had insights reviewed at General Manager and founder level along the way. Looking for full-time or new internship roles in **Data Science, ML/AI Engineering, or Financial Analytics.**

<br>

## Tech Stack

<img src="https://skillicons.dev/icons?i=python,js,ts,react,nextjs,nodejs,fastapi,postgres,mysql,mongodb,docker,aws,git,github,tensorflow" alt="Core stack" />

**AI / ML**
![scikit-learn](https://img.shields.io/badge/scikit--learn-F7931E?style=flat-square&logo=scikitlearn&logoColor=white)
![TensorFlow](https://img.shields.io/badge/TensorFlow-FF6F00?style=flat-square&logo=tensorflow&logoColor=white)
![XGBoost](https://img.shields.io/badge/XGBoost-0B5394?style=flat-square)
![LightGBM](https://img.shields.io/badge/LightGBM-3D8B37?style=flat-square)
![LangChain](https://img.shields.io/badge/LangChain-1C3C3C?style=flat-square)
![Claude API](https://img.shields.io/badge/Claude%20API-D97757?style=flat-square&logo=anthropic&logoColor=white)

**Data / BI**
![Pandas](https://img.shields.io/badge/Pandas-150458?style=flat-square&logo=pandas&logoColor=white)
![NumPy](https://img.shields.io/badge/NumPy-013243?style=flat-square&logo=numpy&logoColor=white)
![Power BI](https://img.shields.io/badge/Power%20BI-F2C811?style=flat-square&logo=powerbi&logoColor=black)
![Tableau](https://img.shields.io/badge/Tableau-E97627?style=flat-square&logo=tableau&logoColor=white)
![Streamlit](https://img.shields.io/badge/Streamlit-FF4B4B?style=flat-square&logo=streamlit&logoColor=white)

**Backend / Cloud**
![GraphQL](https://img.shields.io/badge/GraphQL-E10098?style=flat-square&logo=graphql&logoColor=white)
![AWS](https://img.shields.io/badge/AWS-232F3E?style=flat-square&logo=amazonaws&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)
![Jenkins](https://img.shields.io/badge/Jenkins-D24939?style=flat-square&logo=jenkins&logoColor=white)

<br>

## AI / ML Focus

Two threads run through most of what I build: **grounding LLM output in something verifiable**, and **applying classical ML where the cost of being wrong is real** (markets, business reporting). [Sightline](https://github.com/Kartik281204/sightline-modded) is the first — a 5-step pipeline (permission scope → context retrieval → SQL generation → deterministic validation & execution → explanation with a groundedness check) built specifically so the Claude API never states a number it didn't just get from a real, executed query. The [S&P 500 pipeline](https://github.com/Kartik281204/financemodelling-predictionmodel) is the second — 63 leakage-safe features and a walk-forward CV setup built to survive contact with 90 years of real market data, not just a backtest that looks good once.

<br>

## Featured Projects

<details open>
<summary><b>🔭 Sightline — Grounded AI Analytics Copilot</b></summary>
<br>

`Python` `FastAPI` `PostgreSQL` `Next.js/TypeScript` `Docker` `Anthropic API`

Architected a 5-step grounded AI-query pipeline using FastAPI, PostgreSQL, and the Claude API so the model's plain-English answers are checked against real, executed SQL before they ship — a wrong-but-confident number gets caught and replaced with the raw result instead of going out.

- Permission-scoped semantic layer — role-based access is enforced structurally, not just prompted for
- A deterministic groundedness gate re-checks every number in the generated explanation against the actual query result
- **Identified and patched a real permission-bypass vulnerability during development; shipped with full CI coverage**

```mermaid
flowchart LR
    Q[Question] --> P[Permission scope]
    P --> R[Retrieve context]
    R --> G["Generate SQL<br/>LLM call 1"]
    G --> V{Validate}
    V -- reject --> X[Safe refusal]
    V -- pass --> E[Execute — real rows]
    E --> EX["Explain<br/>LLM call 2"]
    EX --> GC{Groundedness check}
    GC -- fails --> F[Fall back to raw numbers]
    GC -- passes --> OK[Grounded answer]
```

**[→ View Repository](https://github.com/Kartik281204/sightline-modded)**

</details>

<details>
<summary><b>📈 S&P 500 Direction Prediction — Production ML Pipeline</b></summary>
<br>

`Python` `Pandas` `Scikit-learn` `XGBoost` `LightGBM` `NumPy`

Production ML pipeline predicting S&P 500 daily direction on 90 years of market data (1927–2019); benchmarked 5 classifiers via 6-fold expanding-window walk-forward cross-validation — the same discipline a real trading desk would demand before trusting a backtest.

- 63 leakage-safe technical features across price, momentum, volatility, trend, and volume
- Verified zero look-ahead bias via a custom automated test suite, not just a visual sanity check

**[→ View Repository](https://github.com/Kartik281204/financemodelling-predictionmodel)**

</details>

<details>
<summary><b>📧 Bulk Email Verifier — Production API</b></summary>
<br>

`Python` `FastAPI` `asyncio` `aiosmtplib` `dnspython`

Production-grade 3-tier bulk email verifier (Syntax → DNS/MX → SMTP handshake) built with FastAPI and asyncio; semaphore-bounded concurrency handles 20 simultaneous checks without triggering spam filters.

- Catch-all domain detection, plus a Tier 3 fallback for when port 25 is blocked
- Deployed on Render and Railway with a live health-check API

```mermaid
flowchart LR
    A[Email address] --> T1["Tier 1 · Syntax"]
    T1 --> T2["Tier 2 · DNS / MX"]
    T2 --> T3["Tier 3 · SMTP handshake"]
    T3 --> R{Deliverable?}
    R -- port 25 blocked --> FB[Fallback check]
    R -- yes/no --> OUT[Result, 20 concurrent via semaphore]
```

**[→ View Repository](https://github.com/Kartik281204/anti-agenticAI-CRMprotocol)**

</details>

<details>
<summary><b>📊 Employment Tracker Beta — Job Search & Skill Analytics Platform</b></summary>
<br>

`JavaScript` `HTML/CSS` `Electron` `localStorage`

A self-tracking platform computing a weighted employment-likelihood score across DSA progress (156 problems / 12 topics), resume quality, consistency, and applications.

- Shipped as both a browser app and a packaged Electron desktop app
- AI-coach briefings, skill radar charts, and activity heatmaps

**[→ View Repository](https://github.com/Kartik281204/employment-tracker-beta)**

</details>

<br>

## Professional Experience

<table>
<tr><td width="140" valign="top"><b>Jun 2026 – Present</b></td><td>

**AI Product & Business Analyst Intern (Team Lead)** · Polluxa · *Remote, part-time*
Own analytics and CRM workflows across a 3-product portfolio, turning KPI insights into recommendations presented directly to the founder. Automated data collection, preprocessing, and reporting in Python and SQL, cutting manual reporting time ~60% across 5 weekly workflows.

</td></tr>
<tr><td valign="top"><b>Jun 2026 – Present</b></td><td>

**AI Product & Data Scientist Intern** · Gravity Engineering Services · *Remote, part-time*
Backend development and database optimization strengthening performance and reliability across core systems; contributed to Polluxa's core product and engaged directly with clients and board members on project updates.

</td></tr>
<tr><td valign="top"><b>Dec 2025 – May 2026</b></td><td>

**Business Analyst Intern** · Maruti Service Masters — JJ Impex Delhi Ltd. (Maruti Suzuki) · *Delhi*
Six months of business and data analysis for a Maruti Suzuki subsidiary; designed and maintained recurring KPI reports that improved cross-departmental management visibility.

</td></tr>
<tr><td valign="top"><b>Jun 2024 – Nov 2024</b></td><td>

**Data Analyst Intern** · Maruti Sales & Service Delhi — Maruti Suzuki India Ltd. · *Delhi*
Queried and extracted data via SQL across multiple databases; built Power BI dashboards for senior leadership across 3 business units. Recognized by the General Manager for strong analytical performance.

</td></tr>
<tr><td valign="top"><b>Jun 2024 – Aug 2024</b></td><td>

**Web Development & Research Intern** · Laadli Foundation · *Delhi*
Shipped 3 live features across the Foundation's e-commerce and fundraiser platforms; collected and validated 5,000+ field research records supporting impact reports.

</td></tr>
</table>

<br>

## Recognition

- 🏅 Commended **by name by the General Manager**, Maruti Sales & Service Delhi, for analytical performance — documented in a formal completion certificate
- 🏅 Business recommendations and KPI insights presented directly to **founder and board-level stakeholders** at Polluxa and Gravity Engineering
- 🏅 **Zero look-ahead bias**, verified by a custom automated test suite, across 90 years of financial data in the S&P 500 pipeline

<br>

## GitHub Activity

<!-- refreshed daily by .github/workflows/update-profile-art.yml — real data, no third-party API -->
<img src="./contrib-heatmap.svg" width="100%" alt="Kartik's GitHub contribution graph — auto-refreshed daily" />

<img src="https://github-readme-stats.vercel.app/api/top-langs/?username=Kartik281204&layout=compact&theme=tokyonight&hide_border=true&bg_color=0D1117" alt="Top languages" />

<br>
<br>

## Current Focus

`Data Analyst` → `Business Analyst` → `AI Product & Data Scientist` → *(targeting)* `ML / AI Engineer`

- 🔭 Extending **Sightline**'s grounded-query approach — the harder problem now is verification and permission-scoping, not just SQL generation
- 📈 Applying the same walk-forward-validation discipline from the S&P 500 pipeline to new financial ML questions
- 🎓 Finishing my B.Tech in Data Science (Minor: Finance) at UPES, expected June 2027
- 🤝 Open to full-time and internship roles in Data Science, ML/AI Engineering, or Financial Analytics

<br>

## Connect

[![LinkedIn](https://img.shields.io/badge/LinkedIn-kartiksingh28-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/kartiksingh28)
[![LeetCode](https://img.shields.io/badge/LeetCode-KartikSingh281204-FFA116?style=for-the-badge&logo=leetcode&logoColor=white)](https://leetcode.com/u/KartikSingh281204/)
[![GitHub](https://img.shields.io/badge/GitHub-Kartik281204-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/Kartik281204)
[![Email](https://img.shields.io/badge/Email-justkartik9%40gmail.com-D14836?style=for-the-badge&logo=gmail&logoColor=white)](mailto:justkartik9@gmail.com)

<br>

<img src="https://capsule-render.vercel.app/api?type=wave&height=110&color=0:312e81,50:1e1b4b,100:020617&section=footer" width="100%" alt="" />

<sub>Portrait + info card generated from a real photo via a local Python pipeline (background removal, CLAHE contrast, ASCII conversion) — see <code>scripts/</code>. Contribution graph scraped live from github.com, no third-party API. Banner and typing line are external SVG services (capsule-render, readme-typing-svg) and will occasionally have downtime, per their own maintainers.</sub>

</div>
