# Project: Internal Vulnerability Scanner (Python)

## 1) Project Summary
Build a Python-based internal vulnerability scanner for lab use.

Your team will create a command-line tool that can scan:
- A single target machine (IP or hostname), or
- A small subnet (CIDR notation, for example `192.168.56.0/24`)

The tool must identify security issues on Linux and Windows targets, map detected software/service versions to known CVEs, and generate a report suitable for a technical demo.

## 2) Team and Timeline
- Team Based.
- Implementation style: from scratch (student-built design and code)

## 3) Learning Objectives
By the end of this project, students should be able to:
- Design a practical security scanning workflow in Python.
- Perform host and service enumeration in an internal network setting.
- Detect basic security misconfigurations.
- Correlate technical findings with CVE data.
- Communicate risk, evidence, and remediation clearly.
- Defend implementation decisions during a live demo and Q&A.

## 4) Scope and Rules
### In Scope
- Internal lab environment only.
- Linux and Windows standalone targets.
- Identification and validation of simple misconfigurations.
- CVE mapping for discovered services/software versions.

### Out of Scope
- Destructive testing.
- Privilege escalation, persistence, lateral movement.
- Malware-like behavior.
- Any testing outside authorized lab systems.

## 5) Functional Requirements (Minimum)
Your scanner must support the following minimum capabilities.

### A. Target Input
- Accept one target host (`IP` or hostname), or
- Accept a subnet in CIDR format.
- Validate input and handle invalid targets gracefully.

### B. Discovery and Enumeration
- Detect reachable hosts (for subnet scans).
- Scan TCP ports (at least a configurable common-port set).
- Identify service names on open ports when possible.
- Collect service banner/version info when available.

### C. Security Checks (Required)
Implement checks for at least these conditions:
1. FTP guest/anonymous access allowed.
2. SMB guest/null access exposure (basic check).
3. HTTP exposed without HTTPS (or HTTP-only service risk).
4. Additional at-least-2 simple security checks chosen by the team.

Examples of acceptable additional checks:
- Telnet service enabled.
- RDP exposed to broad subnet.
- Default web server pages exposed.
- Weak or missing security headers on HTTP service.

### D. CVE Correlation
- For detected software/service versions, attempt CVE mapping.
- Each mapped item should include:
  - CVE ID
  - Short description
  - Severity (if available)
  - Reference source
- Handle unknown/unmatched versions cleanly.

### E. Reporting
Generate a report with:
- Scan metadata (time, team name, target scope).
- Findings by host and port/service.
- Misconfiguration findings and evidence.
- CVE matches and severity.
- Risk rating per finding (`Low`, `Medium`, `High`, `Critical`).
- Actionable remediation recommendations.

Output formats:
- Required: terminal summary + machine-readable file (`JSON`).
- Optional bonus: HTML or PDF export.

### F. CLI Argument Parsing
- Implement argument parsing (for example with `argparse`).
- Include a flag to run all checks: `--all`.
- Include flags to run specific checks only, such as:
  - `--ftp` (FTP checks only)
  - `--smb` (SMB checks only)
  - `--http` (HTTP/HTTPS checks only)
- The tool should support extending this pattern for future check modules.

## 6) Non-Functional Requirements
- Code must be modular (not a single large script).
- Clear error handling and logging.
- Readable naming and comments where needed.
- README with setup and usage instructions.
- Reasonable runtime for a small subnet lab scan.
- Structure the project so new modules/checks can be added later with minimal code changes.

## 7) Allowed Libraries

Do not rely on a single external tool to do the entire project logic.
Your Python code must implement core workflow and decision logic.

## 8) Deliverables
Submit:
1. Source code repository.
2. `README.md` with:
   - installation
   - dependencies
   - usage examples
   - assumptions and limitations
3. Sample scan results for:
   - one single-host scan
   - one subnet scan
4. Live demo in front of instructor.

## 9) Grading Rubric (100%)
- Functionality: 10%
- Accuracy and CVE Mapping Quality: 15%
- Code Quality and Engineering Practices: 15%
- Ability to explain code base: 20%
- Presentation + Live Demo + Q&A: 40%

### Rubric Notes
- Functionality: correctness of scanning flow and required checks.
- Accuracy/CVE: relevance of findings, false-positive control, useful mapping.
- Code Quality: structure, readability, reliability, maintainability.
- Presentation/Demo/Q&A: clarity, technical depth, ability to justify design and handle instructor questions.
Limitations and future improvements.

## 10) Success Criteria Checklist
A project is considered complete when it:
- Scans one host and one subnet successfully.
- Works against Linux and Windows targets in lab.
- Detects required misconfigurations.
- Provides CVE mapping where possible.
- Produces usable terminal and JSON reports.
- Is clearly presented and defended in live Q&A.
