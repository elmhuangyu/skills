---
name: lifelabs-report-parser
description: Parsing and summarizing LifeLabs medical reports from PDF into organized markdown format by date. Use when you have a LifeLabs blood work or pathology report and need to extract patient, doctor, and test results with reference ranges and diagnostic notes.
---

# LifeLabs Report Parser

This skill provides a structured workflow for converting LifeLabs PDF reports into readable markdown summaries.

## Procedure

1. **Sectioning**: Identify unique "Date of Service" entries. Reports may span multiple pages and different dates. Each unique date should start with a `## Date` header.
2. **Metadata Extraction**:
   - For each section, extract the **Patient** name and the **Ordering Doctor** ("Ordered by").
3. **Result Categorization**:
   - Organize results by their category as listed in the report (e.g., Hematology, Lipids, General Chemistry). Use `### Category` headers.
4. **Formatting Test Results**:
   - Use a nested markdown list format instead of tables.
   - Root item: `- {Test Name}: {Result} {Flag} {Units}`
   - Nested item: `  - Reference: {Reference Range}`
   - Nested item (Conditional): `  - Status: {Status Note}` (Apply this for flagged items like HI/LO or for A1C).
5. **Interpretive Notes as Source of Truth**:
   - LifeLabs reports often include detailed interpretive notes (e.g., for A1C, eGFR, or Lipid thresholds).
   - **DO NOT** use external or hardcoded guidelines.
   - You MUST extract the specific diagnostic criteria or screening notes provided *within the report* and use them to determine the patient's status.
   - For example, if the report provides a multi-level status mapping for A1C, include it in the summary and state the patient's corresponding status.
6. **Final Structure**:
   - Use `assets/report-template.md` as the blueprint for the output.

## Guidelines

- **Conciseness**: Keep values and units clear.
- **Accuracy**: Ensure the flag (HI, LO) is included next to the result value.
- **Reference Ranges**: Always include the reference range provided in the report. If multiple (e.g., fasting vs non-fasting), include both.
