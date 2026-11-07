# 🚀 AI Agent · Fintech · 3D Engine · Air-Gap

[![Typing SVG](https://readme-typing-svg.herokuapp.com?size=24&duration=3000&color=36BCF7&lines=Financial+AI+Agents;Browser+3D+Engines;Air-Gap+GPU+Research;Autonomous+AI+Ops)](https://git.io/typing-svg)

### **Financial AI agents, browser 3D engines, air-gapped GPU research platforms, and autonomous AI Ops**

Domain AI that can run as a cloud service, a self-contained browser runtime, or a disconnected on-prem lab. The same patterns — agents, local inference, containers, and reproducible delivery — show up in fintech, spatial engines, air-gap GPU platforms, and a fully automated AI Ops loop that ships [www.edumgt.co.kr](https://www.edumgt.co.kr/) through S3 and CloudFront.

---

## 🌐 Solution Map

```mermaid
flowchart TB
    subgraph FIN["AI Fintech"]
        DRL["domain-rag-lab"] -->|"backtest specs"| LUM["lumina-invest"]
        LUM -->|"Open API orders"| SCT["stock-coin-trade"]
        DRL -.-> SKP["stock-kms-portal"]
    end
    subgraph ENG["Web 3D Engines"]
        HAN["Hanok simulator<br/>dimetric studio"]
        KART["Siamese Cat KartRider<br/>Three.js + Rapier"]
    end
    subgraph AIR["Air-Gap GPU Research"]
        HAR["harbor-lab<br/>offline registry"]
        K8S["k8s-jupyter-lab<br/>OVA + K8s + local LLM"]
        HAR -.->|"image mirror"| K8S
    end
    subgraph OPS["Autonomous AI Ops"]
        HERMES["Agent harness<br/>Hermes style"] --> CREW["Multi-agent crew<br/>CrewAI style"]
        CREW --> SITE["edumgt-site<br/>S3 + CloudFront<br/>www.edumgt.co.kr"]
        SITE -.->|"monitoring feedback"| HERMES
    end
```

- **Fintech**: independently deployed services, separate databases, REST only (API key auth).
- **3D**: browser engines with no required backend — a procedural dimetric studio and a WebGL physics sim.
- **Air-gap**: VMware OVA delivery into a network with no public internet. Harbor, Nexus, and GitLab mirror images and packages; GPU workers run local LLM, agents, and JupyterHub.
- **AI Ops**: an always-on agent harness (Hermes style) receives events, a role-based crew (CrewAI style) plans, builds, reviews, and deploys, and monitoring feeds back into the loop. Reference target: the static site behind www.edumgt.co.kr on Amazon S3 and CloudFront.

---

## 📈 AI Fintech

Four repositories form a pipeline for financial AI, quant analysis, RAG-based knowledge search, paper trading, and brokerage Open API auto-trading.

```mermaid
flowchart LR
    DRL["domain-rag-lab<br/>(finance RAG & LEAN backtests)"] -->|"backtest results / strategy specs (HTTP API)"| LUM["lumina-invest<br/>(robo-advisor & quant signals)"]
    LUM -->|"order / balance Open API (API key)"| SCT["stock-coin-trade<br/>(paper trading & Open API broker)"]
    DRL -.->|"fork & frontend integration"| SKP["stock-kms-portal<br/>(learning, charts, KMS, Lex/RAG portal)"]
```

- **Integration principle**: `domain-rag-lab`, `lumina-invest`, and `stock-coin-trade` are deployed independently with separate databases and communicate only via REST APIs (API key auth).
- **Portal**: `stock-kms-portal` consolidates `domain-rag-lab` and the investment-analysis web app into a single entry point (port 80).

---

## 📦 Featured Projects

### 1. [stock-kms-portal](https://github.com/edumgt/stock-kms-portal)
Integrated Korean financial learning and investment-analysis KMS portal. `FastAPI` `Vanilla JS` `ApexCharts` `Qdrant` `pgvector` `AWS Lex` `LEAN`
*   **Market charts**: Query domestic and global stock/index prices (Yahoo Finance-based API) with candlestick charts
*   **Financial learning**: 10 learning units, with Mermaid.js diagrams
*   **LEAN backtesting**: Built-in local Docker runner for the QuantConnect LEAN engine
*   **Hybrid chat & RAG**: AWS Lex v2 chatbot combined with Qdrant document RAG
*   **Origin**: Forked from the `domain-rag-lab` structure, with frontends migrated to a single origin

### 2. [stock-coin-trade](https://github.com/edumgt/stock-coin-trade)
Paper-trading platform for stocks (KRX), crypto, and alternative assets, plus brokerage Open API practice. `FastAPI` `AWS SAM` `MariaDB` `PostgreSQL` `Vanilla JS` `Nginx`
*   **Open API**: Virtual account issuing and order execution (`/api/v1/orders`, etc.) for external systems such as `lumina-invest`
*   **Data**: MariaDB for members/trades, PostgreSQL (`pg-stock`) for OHLCV minute/daily bars
*   **Broker integrations**: Korea Investment & Securities (KIS) API/paper trading, KB Securities Open API, Alpaca Paper Trading, TradingView Pine Script
*   **Tooling**: KIS MCP (Model Context Protocol) server with VS Code/Codex integration
*   **Frontend**: Vanilla JavaScript (ES Modules) served by Nginx

### 3. [lumina-invest](https://github.com/edumgt/lumina-invest)
Robo-advisor and quant-signal orchestrator for automated trading. `FastAPI` `Celery` `PostgreSQL` `Redis` `LangChain` `LangGraph` `Qdrant` `Neo4j` `LightGBM`
*   **Auto-trading engine**: Celery Beat runs the `quant.auto_trade_cycle` task every 10 minutes
*   **Orchestration**: Receives strategy specs backtested in `domain-rag-lab`, computes risk limits, and sends orders to `stock-coin-trade` via Open API
*   **AI & ML**: LangChain/LangGraph agents, Scikit-learn and LightGBM models
*   **AWS**: SageMaker training-result lookup and AWS Comprehend sentiment analysis
*   **Storage**: PostgreSQL 16 (SQLAlchemy, asyncpg, Alembic), Redis (sessions, Celery broker/backend)

### 4. [domain-rag-lab](https://github.com/edumgt/domain-rag-lab)
RAG for financial products and asset allocation, with QuantConnect LEAN backtest workflows. `FastAPI` `Streamlit` `Qdrant` `pgvector` `Redis` `Docker`
*   **Hybrid search**: Qdrant vector search and PostgreSQL keyword search fused with Reciprocal Rank Fusion (RRF)
*   **Multi-turn orchestrator**: Session short-term memory and `pgvector`-based long-term memory
*   **Ingestion**: PDF/TXT document ingestion and chunking pipeline
*   **LEAN backtesting**: Local Docker-based QuantConnect LEAN engine
*   **Infrastructure**: Docker Compose, Caddy (TLS reverse proxy), AWS EC2 deployment

### Comparison

| Repository | Domain | Databases | Role |
|---|---|---|---|
| `domain-rag-lab` | Finance RAG & LEAN backtests | PostgreSQL (`pgvector`), Qdrant | Streamlit UI + FastAPI, backtest results |
| `lumina-invest` | Quant signals & robo-advisor | PostgreSQL, Redis, Neo4j, Qdrant | Periodic signals, order triggers |
| `stock-coin-trade` | Stock/crypto/alt-asset paper trading | MariaDB, PostgreSQL (`pg-stock`) | Paper order Open API, KIS/KB/Alpaca |
| `stock-kms-portal` | Learning, charts, KMS portal | PostgreSQL (`pgvector`), Qdrant | Unified UI, AWS Lex + RAG chatbot, LEAN |

---

## 🎮 Web 3D Engines

Browser-native spatial runtimes. Scenes render on the client: a dimetric town studio drawn on Canvas 2D, and a WebGL time-trial with a physics step. Neither needs a game server to place a building or run a lap.

### 5. [A-web-based-Hanok-simulator-game](https://github.com/edumgt/A-web-based-Hanok-simulator-game)
Joseon village studio — a 2:1 dimetric town builder for composing a hanok village and exporting a pixel-perfect snapshot. `React` `Vite` `TypeScript` `Canvas 2D`
*   **World**: 16×16 diamond grid (256 cells), painter’s-algorithm depth sort, nearest-neighbor pixel art
*   **Procedural architecture**: runtime isometric hanok — *gidan*, timber columns, *changhomun*, *giwa* / *choga*, *jangdokdae*, *ondol* chimneys — 56 buildings inside a 256-tile palette
*   **Scene tools**: 90° rotation, day/night lighting, looping mill and water animation, five village presets, undo
*   **Export**: 2,176×1,216 PNG snapshot with preview, download, and clipboard copy
*   **Runtime**: no server and no project file; the map lives in memory until export

### 6. [Siamese-Cat-KartRider](https://github.com/edumgt/Siamese-Cat-KartRider)
Browser 3D time-trial — a 1:87 HO-scale kart on a night-time desk coaster. `Three.js` `Rapier` `WebGL2` `Vite` `Web Audio`
*   **Engine**: single WebGL loop (ACES, bloom, depth-of-field, FXAA) with a Rapier static world and a spline vehicle step
*   **Track**: six-sector banked coaster, drift sparks, apex boost, guardrail penalty, F1-style start lights
*   **Ghost & cameras**: best-lap hologram recorded at 30 Hz (`localStorage`), chase / cockpit / desk orbit / drone cameras, autopilot
*   **Diorama**: millimeter-scale desk and bedroom; GLB props with procedural-mesh fallback
*   **Delivery**: `vite build` bundles models so a race can run from the production dist without a live asset host

---

## 🔒 Air-Gap GPU Research

On-prem platforms for teams that cannot send models, code, or research data to a public cloud. Images, packages, and weights are staged online, then imported from media into a disconnected VMware lab.

```mermaid
flowchart LR
    subgraph BUILD["Online build"]
        PACKER["Packer + Ansible"] --> OVA["OVA x8"]
        PACKER --> BUNDLE["Offline bundle"]
    end
    OVA --> MEDIA["USB / HDD"]
    BUNDLE --> MEDIA
    subgraph AIRGAP["Customer air-gap"]
        INFRA["Harbor · Nexus · GitLab · NAS"]
        K8S["Kubernetes<br/>control plane + GPU workers"]
        GPU["Ollama · vLLM · TGI<br/>JupyterHub · agents"]
        INFRA --> K8S --> GPU
    end
    MEDIA --> INFRA
    MEDIA --> K8S
```

### 7. [k8s-jupyter-lab](https://github.com/edumgt/k8s-jupyter-lab)
Air-gap AI agent platform delivered as VMware OVAs — GPU local LLM, JupyterHub, and Kubernetes for an internal research network. `VMware OVA` `Kubernetes` `NVIDIA GPU` `Ollama` `vLLM` `JupyterHub` `Harbor`
*   **Delivery**: Packer/Ansible builds eight OVAs (control plane, three GPU workers, Harbor, Nexus, GitLab, NAS) plus an offline bundle of images, manifests, apt packages, and model files
*   **GPU path**: physical NVIDIA GPU via PCIe passthrough or vGPU, `nvidia-container-runtime` on containerd, CUDA inside the pod
*   **Research stack**: Ollama, vLLM, and TGI for local inference; JupyterHub for notebooks; LangGraph and AutoGen agents; Chroma and Milvus for RAG
*   **Offline coding**: preloaded Ollama models with Codex CLI or Claude Code pointed at the local runtime — no public API required to edit, explain, or draft tests
*   **Install**: `phase1` build online → `phase2` rehearse after boot → `phase3` import and apply inside the air-gap

### 8. [harbor-lab](https://github.com/edumgt/harbor-lab)
Hands-on lab for running Harbor the way an air-gapped network would: internal registry, CA trust, robot accounts, and image import without Docker Hub. `Harbor` `Docker` `kind` `WSL2`
*   **Air-gap flow**: save/load/tar import, proxy-cache concepts, and a preflight that checks images in Harbor before a model deploy
*   **Cluster pull**: kind pulls a Harbor HTTPS image using an image-pull secret and the internal CA
*   **Inference images**: vLLM image skeleton and Kubernetes deploy templates (probes, `imagePullSecret`, NodePort) as the registry side of a GPU research stack

| Repository | Domain | Runtime | Role |
|---|---|---|---|
| `A-web-based-Hanok-simulator-game` | Procedural dimetric studio | Canvas 2D, in-browser | Hanok village composer and PNG export |
| `Siamese-Cat-KartRider` | WebGL 3D engine | Three.js, Rapier, WebGL2 | Desk-scale kart sim, ghost lap, diorama |
| `k8s-jupyter-lab` | Air-gap GPU research platform | VMware OVA, Kubernetes, NVIDIA | Local LLM, JupyterHub, agents, offline bundle |
| `harbor-lab` | Air-gap registry operations | Harbor, Docker, kind | Image mirror, CA trust, offline import |

---

## 🤖 Autonomous AI Ops

A fully automated operations loop for a production site. An always-on agent harness in the style of [Hermes Agent](https://github.com/NousResearch/hermes-agent) owns the tool-call loop, skills, long-term memory, sessions, and guardrails. It delegates work to a role-based crew in the style of [CrewAI](https://github.com/crewAIInc/crewAI), and the crew ships the result to the live site. The reference target is [www.edumgt.co.kr](https://www.edumgt.co.kr/), a static site built from [edumgt-site](https://github.com/edumgt/edumgt-site) and served from Amazon S3 through CloudFront. The same model is shown as an interactive 3D architecture on the site ([04 · Autonomous AI Ops](https://www.edumgt.co.kr/en.html#exam-3d)).

```mermaid
flowchart LR
    subgraph HARNESS["Agent harness · Hermes style"]
        EV["Events & triggers<br/>Git push · alerts · cron · chat"] --> HM["Agent Harness<br/>tool loop · skills · memory · sessions"]
        HM --> GD["Policy & guardrails<br/>secrets · limits · approval"]
    end
    subgraph CREW["Multi-agent crew · CrewAI style"]
        PL["Planner Agent<br/>tasks · acceptance criteria"] --> BD["Builder Agent<br/>code · content · build_site.py"]
        BD --> RV["Reviewer · QA Agent<br/>tests · links · a11y · security"]
        RV -.->|"below the bar"| BD
    end
    subgraph AWS["AWS delivery & operations · www.edumgt.co.kr"]
        GH["GitHub<br/>edumgt-site commits / PRs"] --> DP["Deploy Agent<br/>aws s3 sync · invalidation"]
        DP --> S3["Amazon S3<br/>static origin · versioning · OAC"]
        S3 --> CF["Amazon CloudFront<br/>HTTPS · edge cache"]
        CF --> WEB["www.edumgt.co.kr<br/>Route 53 · ACM"]
        CF --> MON["Monitoring<br/>CloudWatch · access logs · health checks"]
    end
    HM --> PL
    GD --> DP
    RV --> GH
    MON -.->|"feedback · self-healing"| EV
```

- **Harness (Hermes style)**: one long-running agent process receives Git webhooks, monitoring alerts, scheduled jobs, and human chat through a single gateway, keeps long-term memory and a skill library, and decides what to delegate.
- **Crew (CrewAI style)**: Planner, Builder, Reviewer/QA, and Deploy agents with explicit roles and acceptance criteria. Work that fails review loops back to the Builder instead of reaching production.
- **Guardrails**: secrets stay outside the model context, execution limits bound each run, and production changes outside the approved scope escalate to a human.
- **Delivery**: verified changes are committed to `edumgt-site`, the built `index.html` / `en.html` are synced to the S3 origin bucket (reads allowed only from CloudFront via OAC), and a CloudFront invalidation publishes the new version at www.edumgt.co.kr.
- **Feedback**: CloudWatch metrics, access logs, and availability checks flow back into the harness, so a detected failure starts a fix run automatically.

| Layer | Role | Reference components |
|---|---|---|
| Agent harness | Always-on event intake, tool loop, memory, guardrails | Hermes Agent style harness, webhooks, cron, chat gateway |
| Multi-agent crew | Plan → build → review → deploy with role agents | CrewAI style crew, `build_site.py`, tests and security checks |
| Delivery & operations | Static site hosting and feedback loop | GitHub, Amazon S3, CloudFront, Route 53, ACM, CloudWatch |

---

## 🧠 Tech Stack

![Python](https://img.shields.io/badge/Python-3776AB?logo=python&logoColor=white)
![FastAPI](https://img.shields.io/badge/FastAPI-009688?logo=fastapi&logoColor=white)
![Java](https://img.shields.io/badge/Java-Spring%20Boot-6DB33F?logo=springboot&logoColor=white)
![Three.js](https://img.shields.io/badge/Three.js-000000?logo=threedotjs&logoColor=white)
![WebGL](https://img.shields.io/badge/WebGL-990000?logo=webgl&logoColor=white)
![Qdrant](https://img.shields.io/badge/Qdrant-VectorDB-DC244C)
![PostgreSQL](https://img.shields.io/badge/pgvector-PostgreSQL-4169E1?logo=postgresql&logoColor=white)
![Ollama](https://img.shields.io/badge/Ollama-LLM-black)
![NVIDIA](https://img.shields.io/badge/NVIDIA_GPU-76B900?logo=nvidia&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?logo=docker&logoColor=white)
![Kubernetes](https://img.shields.io/badge/Kubernetes-326CE5?logo=kubernetes&logoColor=white)
![VMware](https://img.shields.io/badge/VMware-607078?logo=vmware&logoColor=white)
![Harbor](https://img.shields.io/badge/Harbor-60B932?logo=goharbor&logoColor=white)
![AWS](https://img.shields.io/badge/AWS-FF9900?logo=amazonaws&logoColor=white)
![Amazon S3](https://img.shields.io/badge/Amazon_S3-569A31?logo=amazons3&logoColor=white)
![CloudFront](https://img.shields.io/badge/CloudFront-8C4FFF?logo=amazonaws&logoColor=white)
![CrewAI](https://img.shields.io/badge/CrewAI-multi--agent-FF5A50)
![Hermes Agent](https://img.shields.io/badge/Hermes_Agent-harness-1F2937)
