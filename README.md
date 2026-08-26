# Search reproducibility materials

This folder accompanies the systematic review and holds the files from each stage of the selection process, organized according to the PRISMA stages.

Studies were identified through **two arms**, each following the same three-stage structure (`1-Identification` → `2-Screening` → `3-Included`):

- **`1-via_databases/`** — searching in Scopus and PubMed · run on **27 May 2026**
- **`2-via_citation_tracking/`** — citation tracking (backward + forward) · run on **1 July 2026**

```
.
├── 1-via_databases/
│   ├── 1-Identification/
│   │   ├── scopus_raw.ris
│   │   └── pubmed_raw.txt
│   ├── 2-Screening/
│   │   ├── dedup_screened_5149.bib
│   │   ├── INCLUDED.zip
│   │   └── MAYBE.zip
│   └── 3-Included/
│       ├── reviewer_1/
│       │   ├── 57_excluded_DB.zip
│       │   └── 88_included_DB.zip
│       ├── reviewer_2/
│       │   ├── 59_excluded_DB.zip
│       │   └── 86_included_DB.zip
│       ├── reviewer_3/
│       │   └── Full_text_agreements.xlsx
│       └── 86_included.zip
│
└── 2-via_citation_tracking/
    ├── 1-Identification/
    │   ├── 1-input_86_viaDB.ris
    │   ├── 2-references_backward.ris
    │   ├── 3-citations_forward.ris
    │   └── 4-combined-pool_1945.bib
    ├── 2-Screening/
    │   ├── 5-survivors_to_screen1533.bib
    │   └── 14_included.zip
    └── 3-Included/
        ├── reviewer_1/
        │   ├── 7_excluded_CT.zip
        │   └── 7_included_CT.zip
        ├── reviewer_2/
        │   ├── 7_excluded_CT.zip
        │   └── 7_included_CT.zip
        ├── reviewer_3/
        │   └── Full_text_agreements_CT.xlsx
        └── 7_included_CT.zip
```

---

## 1 · `via_databases/` — Database searching (27 May 2026)

### 1-Identification/
Records exactly as downloaded from each database, unprocessed.

- **`scopus_raw.ris`** — Raw **Scopus** export: 5,091 records. Each one carries the field `Export Date: 27 May 2026`, the stamp with which Scopus itself dates the export.
- **`pubmed_raw.txt`** — Raw **PubMed** export in MEDLINE format: 1,876 records.

### 2-Screening/
Deduplication of both sources and title/abstract screening (carried out in **Rayyan**).

- **`dedup_screened_5149.bib`** — Deduplicated set that entered screening: 5,149 references (1,818 duplicates removed from the 6,967 identified). This is the starting point of screening.
- **`INCLUDED.zip`** — Rayyan export with the records marked **Included** at title/abstract. Contains `customizations_log.csv` with the decision for each record.
- **`MAYBE.zip`** — The same for records marked **Maybe**.

Together, the **Included** and **Maybe** records make up the **145 reports sought for retrieval** at full text. (The flow diagram reports only this combined figure; the individual Included/Maybe counts are recoverable from the two Rayyan `customizations_log.csv` files.)

### 3-Included/
Independent full-text screening by two reviewers, third-reviewer adjudication, and the final included set. This set is also the **seed** from which citation tracking (Arm 2) was launched (extracted as `1-input_86_viaDB.ris`).

- **`reviewer_1/`** — reviewer 1's independent full-text decisions: `88_included_DB.zip` and `57_excluded_DB.zip`.
- **`reviewer_2/`** — reviewer 2's independent full-text decisions: `86_included_DB.zip` and `59_excluded_DB.zip`.
- **`reviewer_3/Full_text_agreements.xlsx`** — third-reviewer adjudication: every disagreement between reviewers 1 and 2 and how it was resolved.
- **`86_included.zip`** — Final studies included via databases (86), after consensus and adjudication (48 of the 134 assessed were excluded: 39 out of scope, 7 wrong publication type, 1 retracted, 1 duplicate).

Each reviewer's include/exclude zips together cover all 145 reports sought for retrieval (reviewer 1: 88 include / 57 exclude; reviewer 2: 86 / 59); the 11 reports that could not be retrieved sit among the excluded records, even though only the 134 retrievable reports were read in full. Inter-rater agreement (Cohen's κ = 0.77) was computed on those 134 reports.

---

## 2 · `via_citation_tracking/` — Citation tracking (1 July 2026)

Backward and forward searching from the Arm 1 included set, using **`citationchaser`** (R package) over **Lens.org**. Seeded from the 86 studies retained from the database search; of these, 83 carried a DOI resolvable in Lens.org and were used as seeds (the remaining three were CEUR-WS workshop contributions without a resolvable DOI).

### 1-Identification/
Raw yield of the citation search.

- **`1-input_86_viaDB.ris`** — Input seed set (the Arm 1 included studies whose citations are searched).
- **`2-references_backward.ris`** — **Backward** search: the 1,415 unique references cited by the seed articles.
- **`3-citations_forward.ris`** — **Forward** search: the 665 unique articles that cite the seed.
- **`4-combined-pool_1945.bib`** — Backward and forward **combined and deduplicated**: 1,945 unique references (2,080 raw hits minus the 135 records retrieved in both directions).

### 2-Screening/
Title/abstract screening (in **Rayyan**).

- **`5-survivors_to_screen1533.bib`** — Set that entered screening: 1,533 references (after removing the 412 already present in the deduplicated database corpus).
- **`14_included.zip`** — Rayyan export with the records marked **Included** at title/abstract (14). Contains `customizations_log.csv` with the decision for each record.

### 3-Included/
Same structure as Arm 1: independent screening by two reviewers, third-reviewer adjudication, and the final included set.

- **`reviewer_1/`** — reviewer 1's independent full-text decisions: `7_included_CT.zip` and `7_excluded_CT.zip`.
- **`reviewer_2/`** — reviewer 2's independent full-text decisions: `7_included_CT.zip` and `7_excluded_CT.zip`.
- **`reviewer_3/Full_text_agreements_CT.xlsx`** — third-reviewer adjudication of any disagreements.
- **`7_included_CT.zip`** — Final studies included via citation tracking (7). All 14 reports were retrieved and assessed; 7 were excluded with reasons (6 out of scope, 1 non-English), leaving 7.

Each reviewer independently classified the 14 reports assessed at full text (7 include / 7 exclude).

---