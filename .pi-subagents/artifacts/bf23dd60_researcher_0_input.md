# Task for researcher

Research NEW or community ASR models outside k2-fsa/sherpa-onnx GitHub release tag `asr-models` that are already directly compatible with sherpa-onnx (actual ONNX artifacts/configs, not merely theoretically convertible). Focus Chinese or Chinese-English, China-published, recent 2025-2026, CPU/general, preferably <=200MB. Search GitHub, Hugging Face, ModelScope. For each candidate give exact URL, artifact layout/architecture, size, date, punctuation/hotword/streaming capability, and confidence it loads in sherpa-onnx. Explicitly distinguish already mirrored into upstream asr-models from truly external-only. Return concise findings and top recommendations.

---
Update progress at: /home/xifan/code/vinput-registry/.pi-subagents/artifacts/progress/bf23dd60/progress.md

---
**Output:**
Write your findings to exactly this path: /home/xifan/code/vinput-registry/.pi-subagents/artifacts/outputs/bf23dd60/.pi-subagents/research/external-ready.md
This path is authoritative for this run.
Ignore any other output filename or output path mentioned elsewhere, including output destinations in the base agent prompt, system prompt, or task instructions.

## Acceptance Contract
Acceptance level: attested
Completion is not accepted from prose alone. End with a structured acceptance report.

Criteria:
- criterion-1: Return concrete findings with file paths and severity when applicable

Required evidence: review-findings, residual-risks

Finish with a fenced JSON block tagged `acceptance-report` in this shape:
Use empty arrays when no items apply; array fields contain strings unless object entries are shown.
`criteriaSatisfied[].status` must be exactly one of: satisfied, not-satisfied, not-applicable.
`commandsRun[].result` must be exactly one of: passed, failed, not-run.
`manualNotes` and `notes` are optional strings; an empty string means no note and does not satisfy `manual-notes` evidence.
```acceptance-report
{
  "criteriaSatisfied": [
    {
      "id": "criterion-1",
      "status": "satisfied",
      "evidence": "specific proof"
    }
  ],
  "changedFiles": [
    "src/file.ts"
  ],
  "testsAddedOrUpdated": [
    "test/file.test.ts"
  ],
  "commandsRun": [
    {
      "command": "command",
      "result": "passed",
      "summary": "short result"
    }
  ],
  "validationOutput": [
    "validation output or concise summary"
  ],
  "residualRisks": [
    "none"
  ],
  "noStagedFiles": true,
  "diffSummary": "short description of the diff",
  "reviewFindings": [
    "blocker: file.ts:12 - issue found, or no blockers"
  ],
  "manualNotes": "anything else the parent should know"
}
```