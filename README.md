<h1>🏷️ Project Title</h1>
<p><b>RFQ → CRM Automation & Integration Platform</b></p>

<div class="section">
<h2>🧾 Executive Summary</h2>
<p>
This system is a production-grade, AI-powered Request-For-Quotation automation platform built for <b>Alrouf Lighting</b>.  
It replaces manual email-based RFQ handling with an intelligent, event-driven pipeline that:
</p>
<ul>
<li>Reads incoming RFQ emails via IMAP</li>
<li>Uses Gemini LLM to extract structured business data</li>
<li>Persists logs into Google Sheets</li>
<li>Archives attachments to Google Drive</li>
<li>Creates CRM opportunities (mock)</li>
<li>Sends customer acknowledgements</li>
<li>Alerts sales teams in Slack</li>
</ul>
<p>
This platform demonstrates how modern AI + orchestration replaces entire back-office teams with deterministic, auditable automation.
</p>
</div>

<div class="section">
<h2>📑 Table of Contents</h2>
<ul>
<li>🏷️ Project Title</li>
<li>🧾 Executive Summary</li>
<li>📑 Table of Contents</li>
<li>🧩 Project Overview</li>
<li>🎯 Objectives & Goals</li>
<li>✅ Acceptance Criteria</li>
<li>💻 Prerequisites</li>
<li>⚙️ Installation & Setup</li>
<li>🔗 API Documentation</li>
<li>🖥️ UI / Frontend</li>
<li>🔢 Status Codes</li>
<li>🚀 Features</li>
<li>🧱 Tech Stack & Architecture</li>
<li>🛠️ Workflow & Implementation</li>
<li>🧪 Testing & Validation</li>
<li>🔍 Validation Summary</li>
<li>🧰 Verification Testing Tools</li>
<li>🧯 Troubleshooting & Debugging</li>
<li>🔒 Security & Secrets</li>
<li>☁️ Deployment</li>
<li>⚡ Quick-Start Cheat Sheet</li>
<li>🧾 Usage Notes</li>
<li>🧠 Performance & Optimization</li>
<li>🌟 Enhancements & Features</li>
<li>🧩 Maintenance & Future Work</li>
<li>🏆 Key Achievements</li>
<li>🧮 High-Level Architecture</li>
<li>🗂️ Project Structure</li>
<li>🧭 How to Demonstrate Live</li>
<li>💡 Summary, Closure & Compliance</li>
</ul>
</div>

<div class="section">
<h2>🧩 Project Overview</h2>
<p>
The RFQ Automation Platform is built on n8n as a distributed workflow engine.  
Incoming emails are treated as real-time business events.  
The workflow stored in <b>RFQ_to_CRM_Workflow.json</b> contains 20 interconnected nodes orchestrating data extraction, validation, CRM simulation, storage, and communication.
</p>
</div>

<div class="section">
<h2>🎯 Objectives & Goals</h2>
<table>
<tr><th>Goal</th><th>Implementation</th></tr>
<tr><td>Zero manual RFQ handling</td><td>IMAP trigger + Gemini extraction</td></tr>
<tr><td>Traceability</td><td>Google Sheets Master Log</td></tr>
<tr><td>Instant response</td><td>Gmail Auto-Reply Node</td></tr>
<tr><td>Sales visibility</td><td>Slack alerts with parsed RFQ data</td></tr>
<tr><td>Scalable CRM readiness</td><td>Mock CRM simulating Salesforce/Odoo</td></tr>
</table>
</div>

<div class="section">
<h2>✅ Acceptance Criteria</h2>
<ul>
<li>Every RFQ email must generate a CRM ID</li>
<li>No duplicate emails may be processed</li>
<li>All attachments must be archived</li>
<li>Slack notification must include RFQ value, company, and email</li>
<li>All failures must be written to Error_Log.json</li>
</ul>
</div>

<div class="section">
<h2>💻 Prerequisites</h2>
<ul>
<li>n8n v1.x</li>
<li>Google Workspace API access</li>
<li>Slack Bot Token</li>
<li>Gemini API Key</li>
<li>Gmail IMAP Enabled</li>
</ul>
</div>

<div class="section">
<h2>⚙️ Installation & Setup</h2>
<ol>
<li>Install n8n (local or cloud)</li>
<li>Import RFQ_to_CRM_Workflow.json</li>
<li>Connect Google, Slack, Gmail credentials</li>
<li>Verify Google Sheet IDs</li>
<li>Enable workflow</li>
</ol>
</div>

<h2>🔗 API Documentation</h2>
<p>This platform exposes its integration surface via <b>n8n service connectors</b> and <b>internal REST-style webhooks</b>.</p>
<table>
<tr><th>Component</th><th>Endpoint / Node</th><th>Purpose</th></tr>
<tr><td>IMAP Trigger</td><td>imap.gmail.com</td><td>Reads RFQ emails</td></tr>
<tr><td>Gemini LLM</td><td>POST /v1/models/gemini:generateContent</td><td>Extracts RFQ fields</td></tr>
<tr><td>Google Sheets</td><td>AppendRow API</td><td>Stores RFQ logs</td></tr>
<tr><td>Google Drive</td><td>Files.upload</td><td>Stores RFQ attachments</td></tr>
<tr><td>Slack</td><td>chat.postMessage</td><td>Sends sales alerts</td></tr>
<tr><td>Gmail</td><td>messages.send</td><td>Sends acknowledgements</td></tr>
</table>
</div>

<h2>🖥️ UI / Frontend</h2>
<p>This system is backend-driven and operates via n8n’s orchestration UI.</p>
<ul>
<li><b>Dashboard:</b> n8n workflow canvas showing node execution states</li>
<li><b>Input:</b> Gmail inbox receiving RFQs</li>
<li><b>Data Views:</b> Google Sheets (RFQ_Master_Log, RFQ_Parsed_Data)</li>
<li><b>Sales UI:</b> Slack channel notifications</li>
<li><b>File UI:</b> Google Drive RFQ_Attachments folder</li>
</ul>
</div>


<h2>🔢 Status Codes</h2>
<table>
<tr><th>Code</th><th>Meaning</th></tr>
<tr><td>200</td><td>RFQ processed successfully</td></tr>
<tr><td>202</td><td>RFQ queued for processing</td></tr>
<tr><td>409</td><td>Duplicate RFQ detected</td></tr>
<tr><td>422</td><td>LLM extraction failed</td></tr>
<tr><td>500</td><td>Workflow execution error</td></tr>
</table>
</div>

<div class="section">
<h2>🚀 Features</h2>
<ul>
<li>LLM-based email understanding</li>
<li>Multi-sheet data persistence</li>
<li>Drive-based attachment archival</li>
<li>CRM simulation engine</li>
<li>Bilingual auto-reply support</li>
<li>Duplicate prevention via Message-ID hashing</li>
<li>Structured error logging</li>
</ul>
</div>

<div class="section">
<h2>🧱 Tech Stack & Architecture</h2>
<pre>
Email → IMAP → n8n → Gemini AI → Sheets → CRM → Drive → Gmail → Slack
</pre>
</div>

<div class="section">
<h2>🛠️ Workflow & Implementation</h2>
<ol>
<li>IMAP detects new RFQ email</li>
<li>Message-ID checked against Google Sheets</li>
<li>Email text sent to Gemini for extraction</li>
<li>JSON output normalized</li>
<li>Raw email stored</li>
<li>Parsed fields stored</li>
<li>CRM ID generated</li>
<li>Files uploaded</li>
<li>Auto-reply sent</li>
<li>Slack notified</li>
</ol>
</div>

<!-- ===================== 🧪 Testing & Validation ===================== -->
<section>
<h2>🧪 Testing & Validation</h2>
<table>
<tr><th>ID</th><th>Area</th><th>Test</th><th>Expected</th><th>Explanation</th></tr>
<tr><td>T01</td><td>Email</td><td>Send RFQ email</td><td>Workflow triggers</td><td>IMAP picks new mail</td></tr>
<tr><td>T02</td><td>LLM</td><td>Unstructured RFQ</td><td>JSON extracted</td><td>Gemini parsing</td></tr>
<tr><td>T03</td><td>CRM</td><td>Mock insert</td><td>CRM ID generated</td><td>Function node</td></tr>
<tr><td>T04</td><td>Slack</td><td>Notify</td><td>Message delivered</td><td>Sales alert</td></tr>
</table>
</section>

<!-- ===================== 🔍 Validation Summary ===================== -->
<section>
<h2>🔍 Validation Summary</h2>
<ul>
<li>100% of RFQs processed in test runs</li>
<li>No duplicates passed deduplication</li>
<li>All attachments archived</li>
<li>CRM IDs generated for each RFQ</li>
</ul>
</section>

<!-- ===================== 🧰 Verification Testing Tools ===================== -->
<section>
<h2>🧰 Verification Testing Tools</h2>
<ul>
<li>n8n Execution Logs</li>
<li>Google Sheets audit trail</li>
<li>Slack message history</li>
<li>CRM_Mock_Log.json</li>
<li>Error_Log.json</li>
</ul>
</section>

<!-- ===================== 🧯 Troubleshooting & Debugging ===================== -->
<section>
<h2>🧯 Troubleshooting & Debugging</h2>
<table>
<tr><th>Issue</th><th>Cause</th><th>Resolution</th></tr>
<tr><td>No email trigger</td><td>IMAP misconfigured</td><td>Re-auth Gmail</td></tr>
<tr><td>LLM failure</td><td>API quota</td><td>Rotate Gemini key</td></tr>
<tr><td>Sheet not updated</td><td>Permission error</td><td>Re-share sheet</td></tr>
<tr><td>Slack not posting</td><td>Token revoked</td><td>Generate new token</td></tr>
</table>
</section>

<!-- ===================== 🔒 Security & Secrets ===================== -->
<section>
<h2>🔒 Security & Secrets</h2>
<ul>
<li>OAuth2 for Google APIs</li>
<li>Slack Bot Token stored in n8n credentials</li>
<li>Gemini API keys stored in .env</li>
<li>All secrets excluded via .gitignore</li>
</ul>
</section>

<!-- ===================== ☁️ Deployment ===================== -->
<section>
<h2>☁️ Deployment</h2>
<ul>
<li>n8n Cloud or VPS-based Docker deployment</li>
<li>Google APIs enabled on production account</li>
<li>Dedicated Gmail inbox for RFQs</li>
<li>Slack workspace configured</li>
</ul>
</section>

<!-- ===================== ⚡ Quick-Start Cheat Sheet ===================== -->
<section>
<h2>⚡ Quick-Start Cheat Sheet</h2>
<ol>
<li>Import workflow JSON</li>
<li>Connect credentials</li>
<li>Send RFQ email</li>
<li>Check Sheets, Drive, Slack</li>
</ol>
</section>

<!-- ===================== 🧾 Usage Notes ===================== -->
<section>
<h2>🧾 Usage Notes</h2>
<ul>
<li>One inbox per company</li>
<li>Arabic & English RFQs supported</li>
<li>Attachments auto-archived</li>
<li>CRM mock replaceable with Salesforce</li>
</ul>
</section>

<!-- ===================== 🧠 Performance & Optimization ===================== -->
<section>
<h2>🧠 Performance & Optimization</h2>
<ul>
<li>Parallel CRM + Drive processing</li>
<li>Deduplication via Message-ID hash</li>
<li>LLM token optimization</li>
<li>Batch Google Sheet writes</li>
</ul>
</section>

<!-- ===================== 🌟 Enhancements & Features ===================== -->
<section>
<h2>🌟 Enhancements & Features</h2>
<ul>
<li>Salesforce integration</li>
<li>Odoo CRM sync</li>
<li>OCR on attachments</li>
<li>Analytics dashboard</li>
</ul>
</section>

<!-- ===================== 🧩 Maintenance & Future Work ===================== -->
<section>
<h2>🧩 Maintenance & Future Work</h2>
<ul>
<li>Credential rotation</li>
<li>LLM model upgrades</li>
<li>Scaling Sheets → BigQuery</li>
<li>Queue-based retry engine</li>
</ul>
</section>

<!-- ===================== 🏆 Key Achievements ===================== -->
<section>
<h2>🏆 Key Achievements</h2>
<ul>
<li>100% automation of RFQ flow</li>
<li>Zero manual CRM entry</li>
<li>Instant client acknowledgement</li>
<li>Sales-ready alerts in seconds</li>
</ul>
</section>

<!-- ===================== 🧮 High-Level Architecture ===================== -->
<section>
<h2>🧮 High-Level Architecture</h2>
<pre>
Client → Gmail → IMAP → n8n → Gemini AI → Sheets → CRM → Drive → Gmail → Slack
</pre>
</section>

<div class="section">
<h2>🗂️ Project Structure</h2>
<pre>
RFQ_to_CRM_Automation/
├── Workflow_JSON/
│   ├── RFQ_to_CRM_Workflow.json
│   ├── CRM_Mock_Log.json
│   ├── Error_Log.json
│   ├── Example_Input_Email.json
│   └── Sample_Output_Data.json
├── Documentation/
├── Screenshots/
├── Auto_Reply_Sample.txt
├── Sample_Raw_Email.eml
└── Master_README.md
</pre>
</div>

<div class="section">
<h2>💡 Summary, Closure & Compliance</h2>
<p>
This platform is enterprise-grade, auditable, AI-driven automation designed to replace manual sales operations.  
It follows data-logging, traceability, and modular design principles required for ISO-aligned enterprise workflows.
</p>
</div>

</body>
</html>
