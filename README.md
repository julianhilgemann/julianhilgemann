<div align="center">
<img src="gh_banner.png" alt="Julian Hilgemann — BI & Analytics Engineering" width="100%"/>
</div>

---

**Julian Hilgemann**

Business Intelligence · Analytics Engineering · Advanced Analytics

[LinkedIn](https://linkedin.com/in/julian-hilgemann/) · [Email](mailto:hilgemann.julian@gmail.com) · [Website](https://julianhilgemann.com/?utm_source=github&utm_medium=referral&utm_campaign=github-profile&utm_content=bio-link) · [Hyperadapted](https://hyperadapted.com/?utm_source=github&utm_medium=referral&utm_campaign=github-profile&utm_content=bio-link)

I work on the layer between data infrastructure and business decisions — semantic models, KPI logic, and the reporting interfaces where numbers actually get used. Day to day that means Power BI, DAX, dbt, and SQL, with Python for anything that needs modeling or automation.

My background is in economics and business (B.Sc. Business Administration, graduate work in quantitative economics and time series). Professionally I've spent the last 3 years in fintech, building revenue forecasting models, lead-scoring pipelines, funnel analytics, and investor-grade reporting across a portfolio covering €4bn+ in annual volume.

I'm also genuinely enthusiastic about generative AI and LLM-based workflows — I use agentic tooling daily for prototyping, analysis, and context engineering, and I think the intersection of GenAI, analytics engineering and BI is where a lot of the interesting work is heading.

---

### 🤖 Workflow

<img src="workflow/workflow.png" alt="Workflow: laptop and phone (over Tailscale) prompt Claude Code in VS Code; an Obsidian vault and AGENTS.md and SKILL.md files supply context; agents edit local repositories and reach Jira, databases, dbt, APIs, Azure, Azure DevOps, Fabric, Power BI, TouchDesigner and Blender through MCP servers and CLIs; code is pushed to GitHub and deployed by Actions to live sites" width="100%"/>

I work agent-first, with the language model as my interface. VS Code and Claude Code run side by side over one local workspace that holds all my repositories: some deploy to live sites through GitHub Pages, others are plain code. Every repo carries its own `AGENTS.md` or `CLAUDE.md` and skills, and an Obsidian vault adds the wider context (notes, specs, decisions), so agents start from what I already know. Through MCP servers and CLIs the same agents pick up tickets and to-dos from Jira, query and transform SQL databases with dbt, call APIs, work in Azure, Azure DevOps, Fabric and Power BI, and drive TouchDesigner and Blender, then commit, push and deploy across many repos at once. Away from the desk, my phone reaches the laptop over Tailscale, and Wispr Flow turns voice into prompts.

---

### ⭐ Featured Projects

<table>
<tr>
<td width="55%">

#### [FX Macro Data Platform](https://github.com/julianhilgemann/fx_macro_platform) *(wip)*

Point-in-time data platform for macroeconomic and FX time series. Macro data gets revised, so instead of overwriting values it keeps every vintage: any number traces back to what was knowable when it was published.

**Ingest** — Python clients for FRED, the ECB and the Bundesbank; every response archived verbatim and landed append-only, sha256-indexed  
**Warehouse** — Postgres at a bitemporal grain: the period a value describes and the date it became known  
**Transform** — dbt staging, intermediate and mart layers, each model its own Dagster asset, test results kept by Elementary  
**Serve** — Read-only FastAPI with `as_of` queries, Streamlit analytics, a D3 Germany dashboard and Metabase, plus an OIS-implied ECB rate-probability engine scored against a market-implied feed  

`Python` `Postgres` `dbt` `Dagster` `FastAPI` `Docker`

</td>
<td width="45%">

<img src="https://github.com/julianhilgemann/fx_macro_platform/raw/main/docs/architecture/architecture-card.png" alt="FX Macro Data Platform architecture" width="100%"/>

<sub>One row per series, period and vintage, so an <code>as_of</code> query returns what was knowable on any date</sub>

</td>
</tr>
</table>

<table>
<tr>
<td width="55%">

#### [Vantage Alpin — End-to-End BI Pipeline](https://github.com/julianhilgemann/vantage_alpin_e2e_pipeline)

Full analytics stack for a simulated DACH e-commerce business — from stochastic data generation to a production-grade Power BI reporting layer.

**Data Generation** — NHPP-driven demand simulation with seasonal, trend, and event components  
**Transformation** — dbt with Kimball star schema, marketing cost allocation, currency normalization  
**Semantic Model** — Layered DAX measure taxonomy, calculation groups, field parameters, RLS, TMDL version control  
**Dashboard** — Progressive-disclosure layout with budget variance, time intelligence, and dynamic KPI switching  

`Python` `dbt` `DuckDB` `Power BI` `DAX`

</td>
<td width="45%">

<img src="https://github.com/julianhilgemann/vantage_alpin_e2e_pipeline/raw/main/vantage-rebuild/viz/vantage_dashboard_main.png" alt="Vantage Alpin Dashboard" width="100%"/>

<sub>Star schema with synthetic dim_date (DACH holidays, ISO fiscal periods), no calculated columns</sub>

</td>
</tr>
</table>

<table>
<tr>
<td width="55%">

#### [Datapipe: Audio-reactive Shorts](https://github.com/julianhilgemann/audiovisual-animations)

One command turns a song into a finished 9:16 YouTube Short, with no post-production. The music is measured on a frame-accurate grid, and the measurements drive a neon tunnel rendered headless in Blender, so the picture follows every hit.

**Input** — Six methods, each with its own front end: a loop composed and mastered with DawDreamer, a finished master, master and stems, master, stems and MIDI, stems of anything with no beat assumed, or one complex track measured from every side  
**Analysis** — Onsets per band and per stem, a tempo grid, sections (build, breakdown, drop), loudness, spectral and pitch features; every method writes the same contract, `controls.json` plus `mix.wav`  
**Look** — Per-method mappings decide which sound drives what, swappable styles set the tunnel's shape, and `datapipe tune` opens any run in Blender to tune it live with the sound  
**Delivery** — PyAV encodes 1080×1920 at 60 fps, then automatic gates check length, loudness and true peak, sync, the loop seam and flashes  

`Python` `Blender` `librosa` `DawDreamer` `PyAV` `NumPy`

</td>
<td width="45%">

<img src="https://github.com/julianhilgemann/audiovisual-animations/raw/main/docs/diagrams/pipeline.png" alt="Datapipe architecture: a master, stems, MIDI or a preset and seed go through six front ends that all write one run folder (controls.json, mix.wav, report.png, run.json); headless Blender maps the controls onto a neon tunnel and renders PNG frames; render.py encodes them with the soundtrack to an MP4 and runs automatic checks; datapipe tune opens a run in Blender to tune it by hand" width="100%"/>

<sub>Every input method writes the same run folder, so one Blender back end renders, encodes and checks them all</sub>

</td>
</tr>
</table>

---

### 🌐 Data Apps & Tools

**[Yield Curve Heatmap](https://julianhilgemann.github.io/yield_curve_heatmap_app/)**  
Interactive browser-based visualization of the German government yield curve. Fetches 25+ years of monthly Svensson zero-coupon yields directly from the Bundesbank's SDMX REST API and renders them as a smooth, pixel-interpolated heatmap — 2008, the negative-rate era, and the 2022 hiking cycle all visible at a glance. 26 color palettes, interactive tooltip, configurable date/maturity range, and high-resolution PNG export.  
`React` `D3` `Canvas API` `Bundesbank SDMX API`

**[VaultForge](https://julianhilgemann.github.io/obsidian_claude_vault_forge_app/)**  
Drop a PDF or EPUB, get an Obsidian vault. Parses documents client-side, sends sections to Claude via the Anthropic API, and returns atomic markdown notes with `[[wikilinks]]`, concept tags, and a live D3 knowledge graph — packaged as a ready-to-open `.zip`. Runs entirely in the browser: no backend, no build step, no data leaves your machine.  
`HTML` `D3` `pdf.js` `Claude API`

**[Life in Weeks](https://julianhilgemann.github.io/life_in_weeks_app/)**  
Renders your entire lifespan as a 90×52 grid of weeks. Enter a birthday, pick a palette, label life phases, and export a high-resolution poster (up to 4K / A3 print-ready). Inspired by Tim Urban's *Your Life in Weeks*. Client-side only, mobile-first, dark/light mode.  
`React` `Canvas API`

**[ShaderGradient Playground](https://julianhilgemann.github.io/shader_gradient_app/)**  
Browser-based real-time shader gradient simulator built on Three.js and custom GLSL. Tweak geometry, noise, camera, and lighting live — then export as a looping GIF, WebM, or MP4. Includes 12 built-in presets, a frosted glass overlay tool, and JSX code output for drop-in use with the ShaderGradient React library. Zero build step, single HTML file.  
`Three.js` `GLSL` `Canvas API` `MediaRecorder` `WebCodecs`

**[Lineager](https://julianhilgemann.github.io/lineager/)**  
Interactive family tree you can explore from anyone's point of view. Pan and zoom across generations back to 1400, switch the viewpoint to any person and every relationship label rewrites itself to their perspective, or scrub the timeline to jump generation by generation. Installs to the iPhone or iPad home screen as a full-screen app; edits and photos stay in the browser and are never uploaded. Single HTML file, no build step.  
`HTML` `JavaScript` `PWA`

**[Databites Knowledge Wiki](https://julianhilgemann.github.io/databites_knowledge_vault/)**  
Public reference wiki for the modern data stack, written in Obsidian and published as a static site with Quartz. Covers analytics engineering, DAX and VertiPaq internals, Power BI architecture and governance, Power Query, Fabric, econometrics, Bayesian statistics, and data visualization (IBCS, chart selection). Notes are densely wiki-linked, so the site browses as a knowledge graph, and every push to `main` rebuilds and redeploys it through GitHub Actions.  
`Obsidian` `Quartz` `Markdown` `GitHub Actions`

---

### 📈 Advanced Analytics

**[YouTube Sentiment Snapshot](https://github.com/julianhilgemann/yt_sentiment_scraper)**  
One-shot analyzer of YouTube comment sentiment, themes, and emoji mood. Fetches all comments from a video, scores VADER sentiment, extracts emotional archetypes and surface themes, and renders a single dark-mode dashboard (SVG/PDF/PNG) summarizing audience bias and engagement trends.  
`Python` `VADER` `Pandas` `Matplotlib` `Emoji` `YouTube API`

**[Pipeline Conversion Forecast](https://github.com/julianhilgemann/hybrid_sales_pipeline_forecast)**  
Decision-kernel convolution model for B2B sales forecasting. Estimates daily expected wins from existing pipeline and forecasted arrivals using historical win-probability distributions. Includes walk-forward backtest.  
`Python` `SARIMAX` `Scipy` `Matplotlib`

**[Petition Signature Analysis](https://github.com/julianhilgemann/demographic_analysis)**  
District-level analysis of ~480,000 signatures to a psychotherapy-related German online petition, collected in a 60-hour window. Cleans free-text locations and 57k unique job titles, maps every signature to one of Germany's 400 districts, and joins official open data on 2025 federal election results, socioeconomic deprivation, and university locations. The result: signature density follows political milieu (Spearman ρ = +0.63 with the Green vote share, −0.61 with the AfD share) rather than need, and districts with a university psychology department sign 3.6× more per capita. Delivered as one self-contained HTML report, with raw personal data kept out of the repo. Built end-to-end with Claude in 5 prompts and about two hours.  
`Python` `pandas` `Chart.js` `Open Data` `Claude Code`

---


### 📊 Business Intelligence & Dashboards

**[B2B Energy Trading Dashboard](https://github.com/julianhilgemann/dashboard_gallery/tree/main/energy-trading-dashboard)**  
Decision interface for energy key account managers. Spot market correlations, geospatial demand, dark-mode layout designed in Figma.  
`Power BI` `DAX` `Figma`

### 🔧 Data Pipelines & APIs

**[Agentic Financial Twin](https://github.com/julianhilgemann/e2e_rapid_data_function)**  
End-to-end data pipeline from Excel data contracts to ML forecasting and BI dashboard. Agents that spin up a data stack from a static Excel file, including Prophet-based revenue forecasting.  
`Python` `LLM Agents` `Prophet`

**[Zinskompass API](https://github.com/julianhilgemann/ts_forecast_api)**  
German Bundesbank interest rate forecast API.  
`Python` `FastAPI`

**[German Mortgage Macro Pipeline](https://github.com/julianhilgemann/german_mortgage_macro_pipeline)**  
End-to-end pipeline from the Bundesbank SDMX API to a Power BI semantic model. Pulls 30 macro and lending series (GDP, inflation, ECB rates, yields, household and corporate loan rates and volumes) into DuckDB, transforms them through staging, intermediate and mart layers in dbt, and validates that loan volumes add up across maturity buckets. Housing-loan volumes are forecast 12 months ahead: six candidate models (AutoARIMA, ETS, Theta, CES, MSTL, seasonal naive) compete in expanding-window cross-validation, and the best per series is kept with 90% and 95% prediction intervals. Served through a TMDL semantic model with 20+ DAX measures and a time-intelligence calculation group.  
`Python` `DuckDB` `dbt` `statsforecast` `Power BI` `DAX` `Bundesbank SDMX API`

**[German Macroeconomic API](https://github.com/julianhilgemann/macro_llm_api)** *(wip)*  
LLM-augmented dashboarding API for German macroeconomic data.  
`Python` `FastAPI`

### 🎨 Data Visualization

**[Bundesbank Yield Curve Heatmap](https://github.com/julianhilgemann/buba_yield_curve_viz)**  
Visual exploration of the German yield curve over time.  
`Python` `Matplotlib`

**[TouchDesigner Projects](https://github.com/julianhilgemann/av-td-works)**  
A collection of standalone TouchDesigner projects. The larger ones are pruned to a single COMP whose network is externalized to text files, so git can diff them. Three turn Bundesbank data into sound. *Time Series Wavetable* plays a window of the monthly new-business volume of German housing loans as one cycle of a wavetable synth (detrended, interpolated, waveshaped and band-limited in NumPy) and scans it through the history since 2003, with a GLSL dashboard showing the series, oscilloscope, spectrum, sonogram and a 3D wavetable stack. *Touch the Sonogram* puts the same drone into a camera- and microphone-reactive installation drawn as a point-cloud sonogram, and *Caleidoscopic Sonogram Video* drives that point cloud with an audio track and a modulator video to make square music videos. *FerroScope* draws sound as ferrofluid, a spike lattice raised by a kaleidoscope-folded sonogram, and ships a reusable CRT filter. Smaller sketches cover a live AV set driven by an Elektron Octatrack's MIDI and audio, a music visualizer, an audio-reactive point cloud, a GPU particle swarm and noise-driven instancing studies.  
`TouchDesigner` `Python` `NumPy` `GLSL` `Bundesbank API`

---

### What I work with

| | |
| :--- | :--- |
| **BI & Interface** | Power BI, DAX, Tabular Editor, Figma |
| **Engineering** | SQL (Postgres), dbt, DuckDB, Python, Git |
| **Modeling** | Time series forecasting, econometrics, scikit-learn, Prophet |
| **Languages** | German (native), English (C1), Russian (C1) |

---

### 🧭 Where to find me

<a href="https://julianhilgemann.github.io/ecosystem_graph_app/"><img src="https://github.com/julianhilgemann/ecosystem_graph_app/raw/main/docs/preview.png" alt="Ecosystem graph: this profile as an orange hub, linked to every public repo (blue dots), the live apps and julianhilgemann.com (green diamonds) and LinkedIn, YouTube and email (violet squares); amber and red lines mark links that redirect or are broken" width="100%"/></a>

**[Ecosystem Graph](https://julianhilgemann.github.io/ecosystem_graph_app/)**  
Everything I publish on one interactive map: this profile, every public repo, the apps live on GitHub Pages, my website and my channels, joined by every link between them. Orbit it in 3D, flatten it to 2D or search for a project, and click any node to see what links to it and where it leads. A GitHub Action re-crawls the READMEs and live sites every morning and checks each link, so the same map flags broken links and repos that are reachable only through a rename redirect.  
`JavaScript` `Three.js` `force-graph` `Node.js` `GitHub Actions`
