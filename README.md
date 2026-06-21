# ██████╗██╗   ██╗██████╗ ███████╗██████╗ ██╗  ██╗██╗   ██╗███╗   ██╗████████╗███████╗██████╗ 
# ██╔════╝╚██╗ ██╔╝██╔══██╗██╔════╝██╔══██╗██║  ██║██║   ██║████╗  ██║╚══██╔══╝██╔════╝██╔══██╗
# ██║      ╚████╔╝ ██████╔╝█████╗  ██████╔╝███████║██║   ██║██╔██╗ ██║   ██║   █████╗  ██████╔╝
# ██║       ╚██╔╝  ██╔══██╗██╔══╝  ██╔══██╗██╔══██║██║   ██║██║╚██╗██║   ██║   ██╔══╝  ██╔══██╗
# ╚██████╗   ██║   ██████╔╝███████╗██║  ██║██║  ██║╚██████╔╝██║ ╚████║   ██║   ███████╗██║  ██║
#  ╚═════╝   ╚═╝   ╚═════╝ ╚══════╝╚═╝  ╚═╝╚═╝  ╚═╝ ╚═════╝ ╚═╝  ╚═══╝   ╚═╝   ╚══════╝╚═╝  ╚═╝
# 
#               🤖 MULTI-AGENT CYBERSECURITY COMMAND & OPERATIONS CENTER 🤖

[![Next.js](https://img.shields.io/badge/Next.js-15-black?style=for-the-badge&logo=next.js)](https://nextjs.org/)
[![React](https://img.shields.io/badge/React-19-blue?style=for-the-badge&logo=react)](https://react.dev/)
[![TypeScript](https://img.shields.io/badge/TypeScript-5-blue?style=for-the-badge&logo=typescript)](https://www.typescriptlang.org/)
[![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-4-38B2AC?style=for-the-badge&logo=tailwind-css)](https://tailwindcss.com/)
[![Socket.io](https://img.shields.io/badge/Socket.io-4-010101?style=for-the-badge&logo=socket.io)](https://socket.io/)
[![Node-PTY](https://img.shields.io/badge/Node--PTY-Terminal_Bridge-green?style=for-the-badge)](https://github.com/microsoft/node-pty)

**CYBERHUNTER Command Center** is an ultramodern, premium-designed cybersecurity multi-agent operations hub. It orchestrates a mesh network of autonomous, highly specialized AI security agents directly in your workspace. Equipped with real-time terminal rendering (xterm.js), dynamic D3.js force-directed attack graphs, live threat logs, and a dynamic forensic report compiler, it represents the next generation of automated defense and offensive validation.

---

## 🌌 Core Features

*   **📈 Real-Time D3.js Attack Graph** — Dynamic, interactive topology visualization. Simulates exploit path propagation, network infection vectors, and exfiltration targets in real-time.
*   **💻 Autonomous PTY Console Frame** — Multiple resizable, low-latency terminals running native command-line shells (`node-pty`) driven by autonomous security agents.
*   **🚨 Live Threat Feed** — Chronological SOC-style event log with classification tags mapping out attack tactics (Recon, Lateral Movement, Privilege Escalation).
*   **🛡️ Dynamic Security KPI Metrics** — Animated risk gauges, MITRE ATT&CK coverage tracking, network uptime levels, and SOC compliance score tracking.
*   **📄 Forensic Report Compiler** — Auto-compiles chronological security reports directly from terminal socket activity and agent session history.

---

## 🧩 The Agent Mesh & Core Personas

The system coordinates 5 distinct AI agent operations, each aligned to a specific cybersecurity discipline:

| Agent | Console Accent | Role & Responsibility | Frameworks / Focus |
| :--- | :--- | :--- | :--- |
| **🛡️ AUDIT** | Emerald | Compliance checks, IAM role review, encryption audit, and credential harvesting sweeps. | SOC2 Trust Criteria, ISO 27001 Annex A |
| **🚨 SOC** | Blue | Live log monitoring, host event analysis, network triage, and incident containment. | NIST SP 800-61 Rev 2 |
| **🧠 CTI** | Violet | Threat intelligence, OSINT gathering, adversary profiling, and TTP mapping. | MITRE ATT&CK Matrix |
| **🎯 PENTEST** | Red | Active target scanning, vulnerability discovery, SQL Injection testing, and exploit mapping. | PTES Framework, OWASP Top 10 |
| **🤖 AUTO-USE** | Amber | Desktop GUI automation, browser-based target interaction, and tool orchestration. | Playwright, Python PyAutoGUI |

> [!NOTE]
> **CTI Agent Identity Alignment:** The Cyber Threat Intelligence (CTI) Agent has been explicitly configured to function as a professional CTI analyst and principal threat investigator. All default AI self-identifications (like Google Gemini) are overridden to maintain operations-grade immersion.

---

## ⚡ The Key of Power (Gemini API Configuration)

The lifeblood of the CYBERHUNTER multi-agent system is the **Gemini API Key**—referred to as the **Key of Power**. This key must be configured correctly across all agent workspaces to enable autonomous decision-making, tool execution, and reasoning.

### 🔑 Setting up the API Key

Create or update the configuration inside each agent's execution shell (`xhunter.sh`) or save it globally in your environment variables:

```bash
# Export the API Key to power the autonomous engines
export GEMINI_API_KEY="your_gemini_api_key_here"
```

You can verify the configuration directly in each agent directory:
*   `auditAGENT/xhunter-working/xhunter.sh`
*   `ctiAGENT/xhunter-working/xhunter.sh`
*   `socAGENT/xhunter-working/xhunter.sh`
*   `pentestAGENT/xhunter-working/xhunter.sh`

---

## 📄 Chronological PTES & OWASP Report Compiler

The backend incorporates a dynamic **Security Assessment Report Compiler** inside `/mini-services/cyberhunter-bridge`. When clicking **"Generate Report"**, the backend parses the active Socket.IO terminal buffer or workspace session history to build a highly detailed markdown file containing:

1.  **Executive Summary & Security Posture** — Dynamic risk scores and uptime metrics based on node status.
2.  **Methodology & Scope** — Standard-compliant validation testing phases.
3.  **Chronological Attack Path & Chronology** — Lists every single command run, its objective, execution status (✅/❌), and the raw console `stdout` evidence.
4.  **Action Gaps & Prioritized Action Plans** — Tailor-made remediation steps based on target results.

---

## 🛠️ Architecture Overview

```
┌────────────────────────────────────────────────────────┐
│               CYBERHUNTER NEXT.JS DASHBOARD            │
│                  (Next.js on Port :3000)               │
│                                                        │
│   ┌────────────┐     ┌──────────────┐     ┌────────┐   │
│   │ Sidebar    │     │ Attack Graph │     │ Threat │   │
│   │ Controls   │     │   (D3.js)    │     │  Feed  │   │
│   └────────────┘     └──────────────┘     └────────┘   │
│                                                        │
│   ┌────────────────────────────────────────────────┐   │
│   │          xterm.js Terminals (Socket.IO)         │   │
│   │    [AUDIT]  [SOC]  [CTI]  [PENTEST]  [AUTO]    │   │
│   └────────────────────────────────────────────────┘   │
└───────────────────────────┬────────────────────────────┘
                            │ Socket.IO
┌───────────────────────────┴────────────────────────────┐
│               CYBERHUNTER BRIDGE BACKEND               │
│                  (Node.js on Port :3003)               │
│                                                        │
│  • Manages terminal PTY processes (node-pty)           │
│  • Synchronizes real-time metrics and alerts           │
│  • Compiles chronological session logs into Markdown   │
└────────────────────────────────────────────────────────┘
```

---

## 🚀 Quick Start & Installation

### Prerequisites
*   Node.js 18+
*   npm or bun

### 1. Install Dependencies
Install all package configurations in the main folder and bridge service:
```bash
# Install frontend dashboard dependencies
npm install

# Install bridge backend dependencies
cd mini-services/cyberhunter-bridge
npm install
cd ../..
```

### 2. Start CYBERHUNTER Command Center
Run the centralized startup daemon script to launch both the Socket.IO bridge and the Next.js dashboard:
```bash
chmod +x start-cyberhunter.sh
./start-cyberhunter.sh
```

To force a fresh Next.js production build, run the script with the `--build` flag:
```bash
./start-cyberhunter.sh --build
```

Access the dashboard at `http://localhost:3000` in your web browser.

---

## 🔒 Security Standards Mapped

*   **PTES** (Penetration Testing Execution Standard)
*   **OWASP Top 10** (Vulnerability & Exploit Triage)
*   **SOC 2 Type II** (Compliance controls check CC6.1 - CC7.2)
*   **NIST SP 800-61 Rev 2** (Computer Security Incident Handling Guidelines)
*   **MITRE ATT&CK Matrix** (Tactics and adversarial TTP identification)
