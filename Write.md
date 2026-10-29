# MATACS Associate Software Developer Assessment

**Reference:** MATACS-TH-2026-02

## 1. What should be handled by AI versus deterministic rules?

AI should understand contractor proposals and extract relevant information from uploaded PDFs. The backend will dynamically provide the selected project's category, description, and administrator-configured requirements. AI will extract relevant values, identify missing or unclear information, and return supporting evidence such as quotations and PDF page numbers.

The system will not require a separate industry-specific extraction prompt or fixed set of fields for every category. Relevant information will be retrieved from each proposal's text chunks and evaluated against the selected project's requirements.

Deterministic backend logic will validate extracted results, apply mandatory eligibility checks, calculate weighted scores, compare contractors, and generate rankings. AI will assist with document understanding, but it will not change scoring rules or make the final award decision.

## 2. How will consistency and explainability be maintained?

Each project will store its category, description, requirements, mandatory flags, weights, and supported scoring rules. Each criterion will have a stable ID so extracted findings can be associated with the correct requirement.

AI responses will follow a consistent generic structure containing the proposal ID, criterion ID, status, extracted value, supporting evidence, and page reference. The extracted values can vary by industry: a solar proposal may contain system capacity, while a mechanical proposal may contain equipment and system details.

The backend will validate response structures, data types, and required fields. Results will distinguish between confirmed, not found, failed, and needs review. Missing information will not automatically be treated as proof that a contractor fails a requirement.

The system will retain the evidence, criteria version, and scoring result used for each evaluation so reviewers can understand how decisions were reached.

## 3. How will human oversight and auditability be handled?

Reviewers will see a comparison dashboard containing extracted values, mandatory checks, scores, rankings, and supporting evidence. Important findings will include quotations and PDF page references. Unclear or unsupported findings will be flagged for review.

The original proposals will be preserved, and the system will record evaluation results and reviewer corrections in an audit trail. The system will provide recommendations, but an authorized human will make the final award decision.

Proposal content will be treated as untrusted input. Instructions embedded in a PDF that attempt to influence the evaluation or ranking will be ignored.

## 4. What happens when criteria change after scoring?

Project configurations will be versioned. When an administrator changes a requirement, weight, threshold, or scoring rule, the system will record the new version and identify evaluations that need to be updated.

If only weights or scoring formulas change, the backend can recalculate scores from previously extracted values when those values contain all the necessary information. If a new requirement is added, the system will retrieve relevant chunks from each proposal and extract evidence for that criterion. If the information is unavailable, the result will be marked as not found or needs review.

Each evaluation will record which configuration version produced its results, preventing silent comparisons between scores calculated using different criteria.

## 5. What are the main risks and how will they be mitigated?

- **Incorrect AI extraction:** Require supporting evidence and page references, validate data types, and flag uncertain findings for review.
- **Missing evidence mistaken for failure:** Distinguish between not found, failed, and needs review, and apply configured mandatory rules consistently.
- **Prompt injection:** Treat PDF content as untrusted data and keep evaluation instructions and scoring rules under application control.
- **Inconsistent output:** Use a stable response structure, criterion IDs, validation, and controlled retries or review flags.
- **Unfair comparisons:** Use deterministic scoring formulas, documented normalization rules, and evidence-backed results. Do not allow AI to invent weights or change eligibility requirements.
- **Changing criteria:** Version project configurations and re-extract information when new requirements need evidence that was not previously collected.
- **Privacy and security:** Restrict proposal access, store files securely, and isolate each contractor's chunks and evidence during evaluation.

This architecture uses AI for document understanding while keeping eligibility checks, scoring, rankings, and final decisions transparent, consistent, and auditable.