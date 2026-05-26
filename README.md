# QTI Quiz Builder

Turn a spreadsheet of quiz questions into a Canvas-ready import package — no coding, no install, nothing uploaded to a server.

Teachers write their questions in an Excel workbook, open a single HTML page in their browser, and download a `.zip` that imports directly into Canvas as a New Quiz or an Item Bank.

---

## Why this exists

Canvas accepts quiz content in the QTI 1.2 format, but writing QTI by hand means hand-editing XML, and Canvas's importer is picky about it. This tool moves all of that out of the teacher's way: questions are authored in a familiar spreadsheet, and the builder generates correct, importable QTI from it.

It is built so that a teacher who has never seen JSON, XML, or a command line can use it.

---

## What's in this repo

| File | What it is |
|---|---|
| `qti_builder.html` | The builder. A single self-contained web page — open it in a browser and it works. The SheetJS library is bundled inside, so it runs fully offline. |
| `qti_question_workbook_template.xlsx` | The question workbook template, with one worked example per question type. (The builder can also generate this for you.) |
| `qti_workbook_instructions.md` | Instructions for filling out the workbook. Useful as a teacher reference, or to paste into an AI chat so an assistant fills the workbook correctly. |
| `canvas_qti.md` | Technical reference for the QTI 1.2 formats the builder produces — for anyone who wants to understand or extend the output. |

---

## Quick start

1. **Open `qti_builder.html`** in any modern web browser (Chrome, Firefox, Edge, Safari). Double-click the file, or host it and open the link — both work.
2. **Download a workbook template** from Step 2 of the page — choose the version *with examples* if it's your first time.
3. **Fill in your questions** in Excel or Google Sheets. One tab per question type, one row per question.
4. **Upload the finished workbook** back into the page.
5. **Review the preview**, fix anything the page flags, and **download the Canvas package** (`.zip`).
6. **Import into Canvas:**
   - Item Bank: *Item Banks → your bank → Import Content*
   - Quiz: *Settings → Import Course Content → QTI .zip file*

---

## Supported question types

The workbook has a tab for each:

- Multiple Choice
- Multiple Answer
- True / False
- Fill in the Blank
- Numerical
- Essay
- Matching
- Ordering
- Categorization

Each question is tied to a **Category** (a learning objective or topic), which Canvas keeps as the question's label.

---

## Features

- **Single-file, offline, private.** The builder is one HTML file with no dependencies to install. Everything runs in the browser; no question data is ever sent anywhere.
- **Spreadsheet authoring.** Questions are written in Excel/Google Sheets — no JSON, no XML.
- **New Quiz or Item Bank output.** Choose which kind of Canvas package to produce.
- **Per-answer feedback.** Every answer choice — right or wrong — can carry its own explanation.
- **Automatic answer matching for Fill in the Blank.** Teachers type a plain answer; the builder generates the matching rule. Two global options control it: forgive extra spaces, and require exact capitalization.
- **Flexible output.** Build one combined file, one self-contained file per category, or both at once (delivered together in a single download).
- **Question ordering.** Order questions by category (grouping a topic across question types) or by question type.
- **Built-in validation.** The page checks every row and reports problems by tab and row number before you build, so mistakes are easy to find.
- **Forgiving input.** Common spreadsheet mishaps — answer text in place of a letter, a stray pasted row — are handled gracefully rather than failing the whole import.

---

## How it works

The builder reads each tab of the workbook, validates every row, and assembles a QTI 1.2 package: an `imsmanifest.xml` plus the question XML, zipped together exactly as Canvas expects. The QTI formats it produces were verified against real packages exported from Canvas. Technical details are in `canvas_qti.md`.

---

## Requirements

- A modern web browser. That's all.
- Excel, Google Sheets, or any program that can edit and save `.xlsx` files, for writing the questions.

No installation, no account, no internet connection required to run the builder.

---

## Limitations

- Output targets **Canvas LMS** and the **QTI 1.2** format specifically.
- Complex question types (matching, ordering, categorization, and others beyond the basic four) are reconstructed from Canvas exports; verifying the first import of each type is recommended.
- Fill in the Blank supports one accepted answer per blank.
- The example content is written for AP Computer Science A (Java), but the tool itself is subject-agnostic — any subject's questions work.

---

## Contributing

Issues and pull requests are welcome. When reporting an import problem, attaching the workbook (or a small example that reproduces it) makes it much easier to diagnose.

---

## License

See the `LICENSE` file in this repository.
