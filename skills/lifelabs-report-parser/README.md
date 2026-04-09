# LifeLabs Report Parser Skill

This skill is designed to parse and summarize medical reports from [LifeLabs (MyCareCompass)](https://www.on.mycarecompass.lifelabs.com/reports).

## Features
- **Multi-Report Support**: Designed to handle the "Big PDF" generated when selecting and downloading multiple reports at once from the LifeLabs portal.
- **Date-Based Organization**: Automatically splits the combined PDF into separate markdown sections by their "Date of Service."
- **Data Extraction**: Extracts patient details, ordering doctors, and categorized test results (Hematology, Lipids, etc.).
- **Smart Interpretive Notes**: Uses the specific diagnostic criteria and notes provided *within* your report as the source of truth for result statuses (e.g., A1C risk levels, eGFR stages).

## How to use
1. Go to your [LifeLabs Reports](https://www.on.mycarecompass.lifelabs.com/reports) page.
2. Select multiple reports using the checkboxes.
3. Click on the **Download** button to receive a single, multi-page PDF.
4. Provide this PDF (or its OCR text) to the Gemini CLI and ask to "Parse this LifeLabs report."

## Installation
You can install this skill using the `npx skills` command:

```bash
npx skills add https://github.com/elmhuangyu/skills/tree/main/skills/lifelabs-report-parser
```

## Disclaimer
"LifeLabs" is a registered trademark of LifeLabs LP. This tool is an independent, community-developed skill and is **not** affiliated with, endorsed by, or in any way officially connected to LifeLabs LP or its subsidiaries.
