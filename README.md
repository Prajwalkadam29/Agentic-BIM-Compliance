# StructurAI Co-Pilot: Agentic AI for Structural Design Review

![TESSERACT'26](https://img.shields.io/badge/Hackathon-TESSERACT'26-blueviolet)
![Track](https://img.shields.io/badge/Track-Immersive%203D-orange)
![Version](https://img.shields.io/badge/Version-1.0.0--beta-blue)
![License](https://img.shields.io/badge/License-MIT-green)

[cite_start]An autonomous, Agentic AI Co-Pilot designed to automate structural engineering design reviews[cite: 7]. [cite_start]By parsing Industry Foundation Classes (IFC) models against Indian Standard codes (IS 456, IS 1893, IS 800) [cite: 93][cite_start], the system compresses a typical 2-day manual review cycle into just 4 minutes[cite: 135]. 

[cite_start]It provides structural engineers with explainable AI outputs, interactive 3D visualizations, and an automated remediation loop for non-compliant members[cite: 15, 136, 137, 158].

---

## 🏗️ System Architecture

StructurAI Co-Pilot utilizes a highly modular, multi-agent architecture orchestrated by LangGraph. It seamlessly integrates deep IFC parsing, Vision-guided RAG, and an immutable audit trail.

![System Architecture Flowchart](Screenshot 2026-03-27 100323.png)

### The Agentic Pipeline
1. [cite_start]**Input Layer:** Ingests IFC building models alongside structured SP 16 tables and IS/BIS Code PDFs (IS 456, 800, 1893, NBC 2016)[cite: 15, 186, 188].
2. [cite_start]**Parsing & Retrieval:** - `IfcOpenShell` performs deep parsing to extract axis, topology, and PropertySets[cite: 23].
   - **Vision RAG + HyDE** handles complex code clause retrieval using BM25 and GraphRAG for cross-document reasoning.
3. [cite_start]**Agentic Core:** A Supervisor Agent (LangGraph State Machine) acts as the central brain [cite: 38][cite_start], coordinating the IFC parser, code retriever, mathematical calculation engine, and MCP tools[cite: 64].
4. [cite_start]**Output & Visualization:** Renders the model using `xeokit` 3D viewer with BCF fly-to capabilities, color-coded safety bars, and ranked failures[cite: 44, 51].
5. **Auto-Remediation Loop:** Proposes fixes, calculates the embodied carbon delta, and provides a Human-In-The-Loop (HITL) diff view before re-evaluating the model.
6. **Audit & Chat:** All decisions are logged in an immutable audit trail scored by RAGAS, accessible via a conversational Co-Pilot interface.

---

## 🌟 Feature Capabilities & Roadmap

The platform's capabilities are divided into three distinct tiers, ranging from core compliance to advanced AI differentiators.

![Capability Tiers](Screenshot 2026-03-27 100312.png)

### Tier 1: Core Functionality
* [cite_start]**IS 456 Compliance Checks:** Automated evaluation of beams, columns, and slabs (Pu formulas)[cite: 40, 113].
* [cite_start]**xeokit 3D Viewer:** Interactive click-to-query interface with live color overlays for failed members[cite: 44].
* [cite_start]**Explainable AI Output:** Transparent verdicts detailing exact clauses, proposed fixes, and confidence scores.
* **Conversational Interface:** "Why did this fail?" and "How can I fix it?" NLP querying.
* [cite_start]**PDF/DOCX Reports:** Professionally formatted exports with clause provenance and QR code links[cite: 51, 163].

### Tier 2: Differentiators
* [cite_start]**Vision-Guided RAG Chunking:** Preserves complex tabular data and hierarchical clause structures[cite: 30, 126].
* **HyDE + Clause Index:** Hypothetical document embeddings paired with rich metadata for zero-hallucination retrieval.
* [cite_start]**Auto-Remediation Loop:** LangGraph powered state machine that detects a failure, proposes a fix, and re-checks the simulation automatically[cite: 45].
* **HITL Diff View:** Side-by-side comparison of original vs. proposed designs with accept/reject toggles.
* [cite_start]**Golden Dataset Validation:** Real-time dashboard tracking precision, recall, and F1 metrics[cite: 48, 142].

### Tier 3: Production Separators
* [cite_start]**GraphRAG Reasoning:** Advanced cross-document logic to resolve conflicts between multiple codes (e.g., IS 456 vs IS 1893)[cite: 127, 128].
* **Model Context Protocol (MCP) Server:** Allows the LLM to autonomously write and execute its own tool calls against the IFC data.
* **Embodied Carbon Delta:** Calculates the CO2e impact of proposed structural fixes.
* **Docker One-Click Demo:** Fully containerized deployment for seamless, live-hosted presentation to judges.

---
