# Cover Letter — eBioMedicine Submission

**To the Editors of eBioMedicine**

We submit for your consideration the manuscript entitled **"Benchmarking Large Language Models for Zero-Shot Risk of Bias Assessment in Randomised Controlled Trials: A Systematic Comparison Across Eight Frontier Models"** for publication as a Research Article.

---

## 1. Why eBioMedicine

eBioMedicine occupies a distinctive position at the interface of translational biomedical research and clinical practice. Our study evaluates whether contemporary large language models (LLMs) can reliably assist in Risk of Bias (RoB) assessment — a quality-appraisal step that is both a methodological cornerstone of systematic reviews and a direct determinant of which evidence informs clinical guidelines and patient care. The question is not purely technical: errors in RoB assessment propagate into meta-analyses, potentially inflating pooled effect estimates (when high-risk studies are leniently classified) or excluding credible evidence (when low-risk studies are unnecessarily flagged). We believe eBioMedicine's readership — clinicians, clinical researchers, and evidence synthesists — is precisely the audience for whom these findings are most consequential.

---

## 2. Literature Context and Knowledge Gap

Automated RoB assessment has been explored since early rule-based and supervised machine-learning approaches, but the advent of instruction-following LLMs opened the possibility of a fundamentally different paradigm: zero-shot, prompt-driven assessment that mimics the expert reviewer workflow without task-specific training data. A recent preregistered evaluation (Nyrhi et al., 2026) applied four models to 100 RCTs from 10 Cochrane reviews and reported interobserver κ of 0.27–0.39, concluding that no model reached the reliability threshold for autonomous use. While valuable, that study could not determine whether the reliability shortfall is uniform across the RoB 1.0 structure or whether specific domains and intervention types are already tractable — a distinction with direct implications for how LLMs can be deployed in practice. Our study addresses this gap.

---

## 3. Main Findings

We evaluated eight state-of-the-art LLMs (Gemini 2.5 Pro, Gemini 2.5 Flash, DeepSeek v4-Flash, GPT-5.4, Claude Haiku 4.5, Qwen 3.7-Plus, GLM-5, and Grok 4.3) on a common benchmark of 227 RCTs drawn from 127 Cochrane systematic reviews published in 2024, covering 24 clinical specialties and yielding 1,589 annotated cells across seven RoB 1.0 domains.

Our principal findings are:

- **Aggregate performance is approximately stable across frontier models**, with accuracy ranging narrowly from 57.6% to 62.5%. This convergence shifts the central question from *which model* to *which domains and intervention types* support reliable assistance.
- **Macro-F1 and Gwet's AC1 are more informative metrics than accuracy** for this task, because models with the highest accuracy partially achieve it by over-predicting majority-class labels — a strategy that suppresses detection of High Risk and Unclear Risk, the categories most consequential for evidence appraisal.
- *Unclear Risk* was the most consistently under-detected class (recall below 0.20 in three of seven domains), reflecting the epistemic nature of the category.
- **Sequence generation (D1) and allocation concealment (D2)** were reliably assessed across all models and represent plausible near-term targets for assisted screening.
- **Blinding of participants/personnel (D4)** displayed the most systematic leniency bias and the highest consensus failure rate (22.0% of cells correct by no model), concentrated in trials where blinding is structurally impossible (surgical, physiological, and device interventions).
- **Other bias (D7)** showed the greatest inter-model divergence and was the most difficult domain, with accuracy ranging from 24.2% to 55.5%.
- Pairwise complementarity analysis confirmed that the eight models make substantially non-redundant errors (7.4%–17.4% of cells are correctable by substituting any one model for another), suggesting that ensemble or hybrid strategies warrant further investigation.
- A comparison of per-domain versus single-call inference found no meaningful performance advantage for either approach; the primary difference is computational (single-call reduces inference calls by 7×).

---

## 4. Human Health Relevance

Systematic reviews and meta-analyses are the primary evidence base for clinical practice guidelines, health technology assessments, and regulatory submissions. The validity of these documents depends on rigorous RoB appraisal: a meta-analysis that pools trials with uncontrolled confounding inherits and can amplify those flaws, ultimately reaching patients through guidelines derived from misleading pooled estimates.

Our results directly inform how LLM-assisted RoB tools should be designed and where their current limits lie. The leniency bias documented for D4 — where models fail to recognise that blinding is physically infeasible in many trial designs — corresponds to a clinically meaningful blind spot: High Risk trials incorrectly classified as acceptable may be uncritically included in meta-analyses, while unnecessarily flagging Low Risk trials risks excluding credible evidence from an already small evidence pool. By quantifying both error directions and their domain specificity, our study provides actionable guidance for developers of systematic-review automation tools, for journal editors evaluating AI-assisted methodological checklists, and for clinical trialists considering how automated quality screening will treat their work.

---

## 5. Translational Insights

Three concrete, actionable conclusions emerge from our benchmark:

1. **A blinding-sensitive prompt rule targeting D4** — distinguishing trials where blinding is physically feasible (pharmacological, placebo-controlled) from those where it is not (surgical, physiotherapy, device) — is the single modification most likely to reduce the systematic leniency bias documented here. This rule targets the domain with the most directionally consistent errors across all eight models.

2. **A domain-stratified deployment strategy** may be preferable to monolithic LLM-based RoB screening: D1 and D2 are candidates for near-term semi-automated assistance, while D4, D5, and D7 require human oversight under the current design.

3. **The cell-level concordance partition** (all-correct, all-wrong-same-label, mixed, all-wrong-different-labels) provides a practical triage framework: cells where all models converge on the *same wrong* answer are the highest-priority targets for prompt refinement or annotation review, because architectural diversity makes model-idiosyncratic explanation implausible, pointing instead to shared training priors or genuine ground-truth noise.

---

## 6. Data and Code Availability

All analysis code (data processing, model querying, statistical analysis, and figure generation) is available in a public GitHub repository. Model predictions (per-cell judgements and free-text justifications) are not publicly deposited at this time: the full-text PDFs used as input are not all open-access, and the underlying study corpus is under independent expert medical review for a forthcoming benchmark publication; public release is deferred to that work. The benchmark ground-truth annotations derive from published Cochrane review reports and are reproducible from the Cochrane Library.

---

## 7. Prior Submission History

This manuscript has not been submitted to, published in, or posted on a preprint server prior to this submission. No portion of this work has been published or is under simultaneous consideration elsewhere.

---

We confirm that all authors have approved the final manuscript, that the work is original, and that there are no conflicts of interest to declare. We look forward to your consideration.

Sincerely,

Luiz Felipe Teixeira  
[Institution, Department]  
luiz.felipe.teixeira@usp.br

*On behalf of all co-authors*
