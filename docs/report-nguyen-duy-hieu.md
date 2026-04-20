# Day 13 Observability Lab Report - Nguyen Duy Hieu

> Individual split report generated from `docs/blueprint-template.md` for Nguyễn Duy Hiếu.

---

## 1. Team Metadata

- **GROUP_NAME**: Huy-Kha-Hieu-Kien  
- **REPO_URL**: https://github.com/VinUni-AI20k/Lab13-Observability  

- **MEMBERS**:
  - Member A: Trần Đặng Quang Huy | Role: Logging & PII  
  - Member B: Phạm Đan Kha | Role: Tracing & Enrichment  
  - Member C: Nguyễn Duy Hiếu | Role: SLOs & Alerts  
  - Member D: Vũ Đức Kiên | Role: Load Test & Dashboard  

---

## 2. Group Performance (Auto-Verified)

- **VALIDATE_LOGS_FINAL_SCORE**: 100/100  
- **TOTAL_TRACES_COUNT**: 85  
- **PII_LEAKS_FOUND**: 0  

---

## 3. Technical Evidence (Group)

### 3.1 Logging & Tracing

- **EVIDENCE_CORRELATION_ID_SCREENSHOT**: `docs/evidence/correlation-id-log.png`  
- **EVIDENCE_PII_REDACTION_SCREENSHOT**: `docs/evidence/pii-redaction-log.png`  
- **EVIDENCE_TRACE_WATERFALL_SCREENSHOT**: `docs/evidence/trace-waterfall.png`  
- **TRACE_WATERFALL_EXPLANATION**:  
  The slowest span is the retrieval path during `rag_slow`, showing tail latency impact before the answer returns.

---

### 3.2 Dashboard & SLOs

- **DASHBOARD_6_PANELS_SCREENSHOT**: `docs/evidence/dashboard-6-panels.png`

- **SLO_TABLE**:

| SLI           | Target     | Window | Current Value        |
|---------------|------------|--------|----------------------|
| Latency P95   | < 3000ms   | 28d    | 150ms                |
| Error Rate    | < 2%       | 28d    | 0.0%                |
| Cost Budget   | < $2.5/day | 1d     | $0.0018 avg/request |

---

### 3.3 Alerts & Runbook

- **ALERT_RULES_SCREENSHOT**: `docs/evidence/alert-rules.png`  
- **SAMPLE_RUNBOOK_LINK**: `docs/alerts.md#1-high-latency-p95`  

---

## 4. Incident Response (Group)

- **SCENARIO_NAME**: `rag_slow`  

- **SYMPTOMS_OBSERVED**:  
  Latency P95 rises, the dashboard tail-latency panel spikes, and slow requests become obvious in Langfuse.  

- **ROOT_CAUSE_PROVED_BY**:  
  Langfuse Trace ID `473e676cb3070b357fbb120c294b5edc`  
  and related log line `correlation_id=req-2f38c0a0`.  

- **FIX_ACTION**:  
  Disable the injected incident after the demo and rerun clean traffic to show latency recovery.  

- **PREVENTIVE_MEASURE**:  
  Add alerting on tail latency and review retrieval latency in traces before shipping retrieval changes.  

---

## 5. Individual Contributions & Evidence

### Trần Đặng Quang Huy

- **TASKS_COMPLETED**:  
  Implemented logging and PII redaction, including validation and final integration checks.  
- **EVIDENCE_LINK**: Not provided  

---

### Phạm Đan Kha

- **TASKS_COMPLETED**:  
  Implemented tracing, enrichment, and the trace walkthrough evidence.  
- **EVIDENCE_LINK**: Not provided  

---

### Nguyễn Duy Hiếu

- **TASKS_COMPLETED**:  
  Validated SLO targets, alert thresholds, runbook mapping, and incident-response reasoning from metrics to traces to logs.  
- **EVIDENCE_LINK**: Not provided  

---

### Vũ Đức Kiên

- **TASKS_COMPLETED**:  
  Executed load testing, dashboard construction, and evidence capture for performance validation.  
- **EVIDENCE_LINK**: Not provided  

---

## 6. Bonus Items (Optional)

- **BONUS_COST_OPTIMIZATION**:  
  Not claimed in this submission. No before/after cost-optimization experiment was performed.  

- **BONUS_AUDIT_LOGS**:  
  Not claimed in this submission. Audit log pipeline is not implemented.  

- **BONUS_CUSTOM_METRIC**:  
  Claimed. The app exposes `quality_avg` from `app/metrics.py` as a custom heuristic quality metric,  
  and the dashboard shows it as the **"Quality Proxy"** panel.