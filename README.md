# awesome-Tracking-Performance-Drift-in-LLMs-Across-Successive-Version-Updates
> A framework for evaluating and comparing how the accuracy, reliability, consistency, and behavior of large language models change across successive version releases.
## Short Description
 
This repository curates research and resources on **performance drift in large language models (LLMs)** — the phenomenon in which a commercially deployed model's behavior, accuracy, safety posture, or formatting changes across silent version updates, without any change to the code built on top of it. It brings together an original AI-assisted research paper, a citation integrity audit, verified academic references, datasets, monitoring tools, open-source implementations, and learning resources for researchers, engineers, and students working on LLM evaluation, reliability, and monitoring.
 
## Table of Contents
 
- [Topic Overview](#topic-overview)
- [AI-Assisted Research Paper](#ai-assisted-research-paper)
- [Citation Integrity Audit](#citation-integrity-audit)
- [Curated Research Papers](#curated-research-papers)
- [Datasets](#datasets)
- [Tools and Libraries](#tools-and-libraries)
- [GitHub Implementations](#github-implementations)
- [Tutorials and Learning Resources](#tutorials-and-learning-resources)
- [Repository Structure](#repository-structure)
- [Contributing](#contributing)
- [License](#license)
## Topic Overview
 
Large language models accessed through commercial APIs (e.g., OpenAI, Anthropic, Google) are updated continuously — through fine-tuning, RLHF, safety tuning, quantization, and system-prompt changes — often without public disclosure of when or how. Because these updates occur behind a stable model name or endpoint, the "same" model can behave very differently from one week to the next, a phenomenon researchers call **performance drift**. This matters for at least three reasons: production applications built on LLMs can silently break when output format or refusal behavior changes; published evaluations of a named model may not be reproducible after a later update; and apparent performance "improvements" across versions can reflect benchmark contamination rather than genuine capability gains.
 
Key problems in this space include distinguishing genuine capability drift from contamination artifacts, attributing observed behavioral shifts to specific causes (model weights vs. system prompt vs. serving infrastructure), and building monitoring infrastructure that treats a deployed LLM the way software engineering treats a versioned dependency — with changelogs, regression tests, and reproducible longitudinal benchmarks. Major research directions include longitudinal auditing frameworks (e.g., ChatLog), holistic multi-metric evaluation (e.g., HELM), LLM-as-a-judge monitoring pipelines, contamination-aware evaluation design, and standardized, versioned model documentation. This repository organizes the literature and tooling around these directions.
 
## AI-Assisted Research Paper
 
**Title:** *Tracking Performance Drift in Large Language Models Across Successive Version Updates*
 
**Abstract (short):** Large language models deployed as commercial APIs are updated silently and frequently, yet the empirical consequences of these updates for downstream performance remain poorly characterized. This paper synthesizes the emerging literature on performance drift, organized around (1) empirical evidence of drift across capability, safety, and stylistic dimensions; (2) technical mechanisms believed to drive drift (continued fine-tuning, RLHF, quantization, system-prompt changes); (3) current monitoring and evaluation approaches (longitudinal benchmarks, holistic evaluation frameworks, LLM-as-a-judge protocols, contamination-aware evaluation); and (4) methodological challenges and open research gaps, including the lack of causal attribution methods and standardized, versioned model documentation. The paper argues that performance drift is a first-order reliability concern for any organization building production systems atop continuously evolving foundation models.
 
📄 [Read the full paper](./Paper/AI_Assisted_Research_Paper.pdf)
 
## Citation Integrity Audit
 
Every reference cited in the research paper was independently verified against its original source (arXiv abstract pages, publisher DOI records, or conference proceedings) to confirm that authorship, publication year, venue, and persistent identifiers (DOI / arXiv ID) are accurate, and that no fabricated or hallucinated sources were included. No claims in the paper rely on a source that could not be independently located and verified.
 
📄 [Read the full citation integrity audit](./citation-audit/Citation_Integrity_Audit.pdf)
 
## Curated Research Papers
 
### Longitudinal Drift Audits
- Chen, L., Zaharia, M., & Zou, J. (2023/2024). *How is ChatGPT's behavior changing over time?* arXiv:2307.09009 / Harvard Data Science Review, 6(2). https://doi.org/10.1162/99608f92.5317da47
- Tu, S., Li, C., Yu, J., Wang, X., Hou, L., & Li, J. (2024). *ChatLog: Carefully Evaluating the Evolution of ChatGPT Across Time.* arXiv:2304.14106
- Chen, L., Cai, T., Zaharia, M., & Zou, J. (2021). *Did the Model Change? Efficiently Assessing Machine Learning API Shifts.* arXiv:2107.14203
### Evaluation Integrity & Contamination
- Aiyappa, R., An, J., Kwak, H., & Ahn, Y.-Y. (2023). *Can we trust the evaluation on ChatGPT?* TrustNLP 2023. https://doi.org/10.18653/v1/2023.trustnlp-1.5 (arXiv:2303.12767)
### Holistic & Preference-Based Evaluation
- Liang, P., Bommasani, R., et al. (2022). *Holistic Evaluation of Language Models (HELM).* arXiv:2211.09110
- Zheng, L., Chiang, W.-L., Sheng, Y., et al. (2023). *Judging LLM-as-a-Judge with MT-Bench and Chatbot Arena.* NeurIPS 2023. arXiv:2306.05685
- Chiang, W.-L., Zheng, L., Sheng, Y., et al. (2024). *Chatbot Arena: An Open Platform for Evaluating LLMs by Human Preference.* ICML 2024. arXiv:2403.04132
### Classical Concept Drift Foundations
- Gama, J., Žliobaitė, I., Bifet, A., Pechenizkiy, M., & Bouchachia, A. (2014). *A Survey on Concept Drift Adaptation.* ACM Computing Surveys, 46(4). https://doi.org/10.1145/2523813
- Lu, J., Liu, A., Dong, F., Gu, F., Gama, J., & Zhang, G. (2019). *Learning under Concept Drift: A Review.* IEEE TKDE, 31(12). https://doi.org/10.1109/TKDE.2018.2876857
### Model Documentation & Training Foundations
- Mitchell, M., Wu, S., Zaldivar, A., et al. (2019). *Model Cards for Model Reporting.* FAT* '19. https://doi.org/10.1145/3287560.3287596 (arXiv:1810.03993)
- Ouyang, L., Wu, J., Jiang, X., et al. (2022). *Training Language Models to Follow Instructions with Human Feedback.* NeurIPS 2022. arXiv:2203.02155
- OpenAI. (2023). *GPT-4 Technical Report.* arXiv:2303.08774


Full bibliographic details for all sources are in [`references/references.md`](./references/references.md).
 
## Datasets
 
See [`datasets/datasets.md`](./datasets/datasets.md) for the full list, including:
- **ChatLog-Monthly / ChatLog-Daily** — monthly and daily-refreshed ChatGPT response datasets across 21 NLP benchmarks (Tu et al., 2024).
- **MT-Bench & Chatbot Arena conversation logs** — multi-turn evaluation questions and crowdsourced human preference votes (Zheng et al., 2023).
- **HELM scenario data** — benchmark scenarios and raw model completions across a broad set of models (Liang et al., 2022).
## Tools and Libraries
 
See [`tools/tools.md`](./tools/tools.md) for the full list, including:
- **Claude, ChatGPT, and Gemini** — major commercial LLM chat products, relevant both as subjects of performance-drift study and as tools for conducting research.
## GitHub Implementations
 
See [`implementations/github-repositories.md`](./implementations/github-repositories.md) for the full list, including:
- `THU-KEG/ChatLog` — official implementation and dataset repository for ChatLog.
- `stanford-crfm/helm` — official HELM evaluation framework.
- `lm-sys/FastChat` — Chatbot Arena and LLM-as-a-judge implementation.
## Tutorials and Learning Resources
 
See [`tools/tools.md`](./tools/tools.md) and [`references/references.md`](./references/references.md) for links to official documentation, benchmark leaderboards, and lecture material relevant to LLM evaluation and drift monitoring.
 
## Repository Structure
 
```
awesome-llm-performance-drift/
├── README.md
├── paper/
│   └── AI_Assisted_Research_Paper.pdf
├── citation-audit/
│   └── Citation_Integrity_Audit.pdf
├── references/
│   └── references.md
├── datasets/
│   └── datasets.md
├── tools/
│   └── tools.md
├── implementations/
│   └── github-repositories.md
└── LICENSE
```
 
## Contributing
 
Contributions are welcome. Please open an issue or pull request to suggest a paper, dataset, tool, or implementation. Submissions should include full bibliographic information (authors, title, year, venue) and, where available, a DOI, arXiv ID, or other persistent identifier.
 
## License
 
The curation, organization, and original written content in this repository (including the README and the AI-assisted research paper) are released under the [MIT License](./LICENSE), unless otherwise noted. Linked third-party papers, datasets, and tools remain subject to their own original licenses and terms of use.
 
