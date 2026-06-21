<div align="center">

# CYBERHUNT COMMAND CENTER
### Autonomous Multi-Agent Cybersecurity Operations & Orchestration Hub

---

[![Next.js](https://img.shields.io/badge/Next.js-15-black?style=for-the-badge&logo=next.js)](https://nextjs.org/)
[![React](https://img.shields.io/badge/React-19-blue?style=for-the-badge&logo=react)](https://react.dev/)
[![TypeScript](https://img.shields.io/badge/TypeScript-5-blue?style=for-the-badge&logo=typescript)](https://www.typescriptlang.org/)
[![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-4-38B2AC?style=for-the-badge&logo=tailwind-css)](https://tailwindcss.com/)
[![Socket.io](https://img.shields.io/badge/Socket.io-4-010101?style=for-the-badge&logo=socket.io)](https://socket.io/)
[![Node-PTY](https://img.shields.io/badge/Node--PTY-Terminal_Bridge-green?style=for-the-badge)](https://github.com/microsoft/node-pty)

---

<p align="center">
  CYBERHUNT Command Center is an enterprise-grade cybersecurity operations dashboard that coordinates a mesh network of autonomous, highly specialized security agents directly within your local workspace. Featuring low-latency terminal emulators (xterm.js), dynamic force-directed attack topology graphs (D3.js), live SOC-style threat logging, and an integrated chronological report compiler, the dashboard enables streamlined automated testing and auditing.
</p>

</div>

---

## Core Capabilities

*   **Attack Path Visualization** — Dynamic force-directed network topology mapping that renders active exploit routes, node compromises, and lateral movements in real time.
*   **Low-Latency Terminal PTYs** — Multiple resizable, high-performance terminal consoles (`node-pty`) connected directly to active agent sandboxes over Socket.IO.
*   **Triage Logging Feed** — Real-time event log streaming with threat classification tags mapping adversarial behaviors directly to mitigation rules.
*   **Performance Metrics Dashboard** — Interactive status gauges tracking open security incidents, MITRE ATT&CK coverage percentage, network uptime, and overall workspace risk scores.
*   **Automated Audit Compiler** — Local Markdown reporter that compiles detailed PTES-compliant event records and command execution logs from terminal sessions.

---

## Architectural Topology

<div align="center">
  <p>
    The CYBERHUNT dashboard separates user interaction, state orchestration, and sandbox task execution into distinct, modular tiers connected via real-time WebSocket events.
  </p>
</div>

```mermaid
graph TB
    subgraph Frontend [Next.js Dashboard - Port 3000]
        UI[User Interface / Control panel]
        D3[D3.js Attack Graph]
        XTerm[xterm.js Console Frame]
        Metrics[KPI Metrics & Triage log]
    end

    subgraph Backend [Cyberhunter Bridge - Port 3003]
        Bridge[Socket.IO Gateway]
        PTYMgr[PTY Spawn Manager]
        Compiler[PTES Report Compiler]
        LogWatcher[Session Log Tracker]
    end

    subgraph AgentMesh [Autonomous Agent Mesh Network]
        Audit[Audit Agent]
        SOC[SOC Agent]
        CTI[CTI Agent]
        Pentest[Pentest Agent]
        AutoUse[Auto-Use Agent]
    end

    UI <-->|Socket.IO| Bridge
    XTerm <-->|Real-time stdout/stdin| PTYMgr
    D3 <-->|Telemetry events| LogWatcher
    PTYMgr <-->|node-pty session| AgentMesh
    AgentMesh -->|JSON Session log| LogWatcher
    LogWatcher -->|Parsed findings| Compiler
    Compiler -->|Compiled Markdown report| UI
```

---

## Command & Terminal Signal Lifecycle

<div align="center">
  <p>
    This diagram demonstrates the asynchronous execution pipeline, showcasing how input command data maps to standard streams, and how session logs are stored and dynamically compiled into Markdown.
  </p>
</div>

```mermaid
sequenceDiagram
    autonumber
    actor User as Operator
    participant UI as Dashboard UI
    participant Bridge as Bridge Server
    participant PTY as node-pty Shell
    participant Agent as Autonomous Agent
    participant Storage as Session Log (.json)

    User->>UI: Submit Target (e.g., scan 20.251.144.248)
    UI->>Bridge: socket.emit('terminal:stdin', command)
    Bridge->>PTY: write(command)
    PTY->>Agent: Execute in sandbox
    Agent->>PTY: Return stdout/stderr
    PTY->>Bridge: onData(stream)
    Bridge->>UI: socket.emit('terminal:stdout', stream)
    UI->>User: Render output in xterm.js
    Agent->>Storage: Append step (Thought, Command, Tool Output)
    User->>UI: Click "Generate Report"
    UI->>Bridge: socket.emit('report:generate')
    Bridge->>Storage: Read latest session JSON
    Bridge->>Bridge: Compile chronology and proof-of-concept
    Bridge->>UI: socket.emit('report:update', ready)
    UI->>User: Display completed Markdown report
```

---

## Autonomous Agent Grid

<div align="center">

| Agent | Module Badges | Core Responsibility | Framework Alignment |
| :--- | :--- | :--- | :--- |
| **AUDIT** | ![Audit](https://img.shields.io/badge/Audit_Agent-10b981?style=flat-square&logo=securityscorecard&logoColor=white) | Compliance checks, directory access-control reviews, encryption auditing, and credential leak sweeps. | SOC2 Trust Criteria / ISO 27001 |
| **SOC** | ![SOC](https://img.shields.io/badge/SOC_Agent-3b82f6?style=flat-square&logo=datadog&logoColor=white) | SIEM log monitoring, telemetry correlation, threat ingestion, and endpoint containment. | NIST SP 800-61 Rev 2 |
| **CTI** | ![CTI](https://img.shields.io/badge/CTI_Agent-8b5cf6?style=flat-square&logo=shodan&logoColor=white) | Threat intelligence gathering, OSINT searches, adversary profiling, and TTP mapping. | MITRE ATT&CK Framework |
| **PENTEST** | ![Pentest](https://img.shields.io/badge/Pentest_Agent-ef4444?style=flat-square&logo=target&logoColor=white) | Automated reconnaissance, vulnerability validation, SQL Injection checking, and exploit route execution. | PTES / OWASP Top 10 |
| **AUTO-USE** | ![Auto-Use](https://img.shields.io/badge/Auto--Use_Agent-f59e0b?style=flat-square&logo=google-chrome&logoColor=white) | Desktop GUI task execution, browser automation, and integration of external security tools. | Playwright / PyAutoGUI |

</div>

---

## State Triage & Threat Infection Path

<div align="center">
  <p>
    The lifecycle of a targeted mission propagates through discrete agent threat states before triggering active playbooks and report compilations.
  </p>
</div>

```mermaid
stateDiagram-v2
    [*] --> Initialized: Agent session started
    Initialized --> Scanning: Reconnaissance triggered
    Scanning --> VulnerabilityFound: Finding parsed in console
    VulnerabilityFound --> ExploitPathActive: Trigger lateral movement
    ExploitPathActive --> Compromised: Target node compromised (Root)
    Compromised --> AlertTriggered: Ingest to SOC Threat Feed
    AlertTriggered --> ReportPending: User initiates documentation
    ReportPending --> Compiled: Bridge compiles PoC and stdout logs
    Compiled --> [*]: Remediation plan generated
```

---

## Gemini API Configuration

<div align="center">
  <p>
    The entire cognitive operations engine of the CYBERHUNT agent mesh is powered by the Gemini API Key. This key must be present in the shell configuration files of each agent workspace to enable reasoning, tool selection, and script execution.
  </p>
</div>

### Setting up the API Key

Export your API token locally in the shell scripts of the respective agents:

```bash
# Add to agent startup shell scripts (e.g. xhunter.sh)
export GEMINI_API_KEY="your_gemini_api_key_here"
```

Verify that the key is exported correctly in the following entrypoints:
*   `auditAGENT/xhunter-working/xhunter.sh`
*   `ctiAGENT/xhunter-working/xhunter.sh`
*   `socAGENT/xhunter-working/xhunter.sh`
*   `pentestAGENT/xhunter-working/xhunter.sh`

---

## Automated PTES & Compliance Report Compiler

<p align="center">
  The system bridge backend manages terminal streams and translates them into comprehensive security assessment records. When a report is requested, the compiler parses the session data and writes a standard-compliant report featuring the following key components:
</p>

1.  **System Posture Overview** — Calculations of risk exposure, mitigation state, and node vulnerabilities.
2.  **Attack Chronology** — Step-by-step logs tracking the exact objective, executed shell command, status (Success/Failure), and raw console stdout evidence.
3.  **Remediation Action Plan** — Prioritized checklists for patching vulnerabilities discovered during the run.

---

## Installation & Running

### Prerequisites
*   Node.js 18+
*   npm or bun

### 1. Install Project Dependencies
Run install in both the root dashboard directory and the bridge backend service:
```bash
# Install frontend dashboard package dependencies
npm install

# Install bridge backend dependencies
cd mini-services/cyberhunter-bridge
npm install
cd ../..
```

### 2. Launch Server Services
Run the centralized startup script to initialize the bridge backend and dashboard server:
```bash
chmod +x start-cyberhunter.sh
./start-cyberhunter.sh
```

To re-compile and bundle the production Next.js application, append the build flag:
```bash
./start-cyberhunter.sh --build
```

Open your browser to `http://localhost:3000` to view the active console dashboard.
