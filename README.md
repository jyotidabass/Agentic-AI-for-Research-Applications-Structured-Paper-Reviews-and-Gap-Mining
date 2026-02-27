# Agentic AI for Research Applications: Structured Paper Reviews and Gap Mining

A curated collection of structured reviews and research gap analyses on **Agentic AI benchmarking**, focusing on how large language models (LLMs) perform in real-world agentic scenarios. This repository includes in-depth coverage of two landmark papers in the field.

---

## 📄 Papers Covered

### 1. AGENTIF: Benchmarking Instruction Following of LLMs in Agentic Scenarios
**Authors:** Yunjia Qi, Hao Peng, Xiaozhi Wang, Amy Xin, Youfeng Liu, Bin Xu, Lei Hou, Juanzi Li  
**Institution:** Tsinghua University & ZhipuAI  
**ArXiv:** [2505.19644](https://arxiv.org/abs/2505.19644) | **Code:** [THU-KEG/AgentIF](https://github.com/THU-KEG/AgentIF) | **Dataset:** [HuggingFace](https://huggingface.co/datasets/THU-KEG/AgentIF)

#### Overview
AGENTIF is the **first benchmark specifically designed to evaluate LLM instruction-following ability in agentic scenarios**. Existing benchmarks (e.g., IFEval) use short, synthetically generated instructions averaging ~45 words. AGENTIF addresses a critical gap by using instructions sourced from real-world agentic applications.

#### Key Characteristics
| Property | Details |
|---|---|
| **Instructions** | 707 human-annotated instructions across 50 agentic tasks |
| **Average Length** | 1,723 words per instruction (max: 15,630 words) |
| **Avg Constraints** | 11.9 constraints per instruction |
| **Sources** | Industrial application agents + open-source agentic systems |

#### Constraint Types Evaluated
- **Vanilla** – Basic response constraints
- **Tool Specifications** – Detailed descriptions of available tools
- **Condition Constraints** – Conditional logic within instructions
- **Formatting** – Structural/format requirements
- **Semantic** – Meaning-level requirements
- **Example Constraints** – Few-shot examples embedded in instructions
- **Meta Constraints** – Higher-order constraints that govern other constraints (~25% of instructions)

#### Evaluation Methodology
- **Code-based evaluation** – Automated checks via scripts
- **LLM-based evaluation** – Model-as-judge approach
- **Hybrid Code-LLM evaluation** – Combined pipeline

#### Key Findings
- Current LLMs generally perform **poorly** on agentic instruction following
- Performance degrades significantly with **complex constraint structures** and **tool specifications**
- When instruction length exceeds **6,000 words**, ISR (Instruction Success Rate) approaches **0 for all models**
- ~25% of instructions contain **meta constraints**; models struggle most with *constraint selection* type
- Models tested: o1-mini, GPT-4o, Qwen3-32B, DeepSeek-R1, Claude-3.5, LLaMA-3.1-70B-Instruct

#### Research Gaps Identified
- Post-training data with long, complex instructions is scarce — a major limiting factor
- Meta-constraint compliance (especially conflict resolution between constraints) remains underexplored
- Task decomposition as a mitigation strategy for long-instruction failure needs more investigation
- Manuals (e.g., technical documentation) as a source for post-training data is a promising but unexplored avenue

---

### 2. FieldWorkArena: Agentic AI Benchmark for Real Field Work Tasks
**Authors:** Atsunori Moteki, Shoichi Masui, Fan Yang, Yueqi Song, Yonatan Bisk, Graham Neubig, Ikuo Kusajima, Yasuto Watanabe, Hiroyuki Ishida, Jun Takahashi, Shan Jiang  
**Institutions:** Fujitsu Limited (Japan), Fujitsu Research of America (USA), Carnegie Mellon University (USA)  
**Published:** ACM MM'25 | **Dataset + Code:** [Fujitsu FieldWorkArena](https://en-documents.research.global.fujitsu.com/fieldworkarena/)

#### Overview
FieldWorkArena introduces a benchmark for evaluating agentic AI on **real-world industrial field work tasks** — specifically safety monitoring, manufacturing quality control, and warehouse operations. Existing benchmarks focus on web tasks and are insufficient for the complexity of physical work environments.

#### Dataset Composition
- **Videos and images** captured on-site in factories and warehouses
- **Documents** actually used in industrial operations (manuals, safety protocols)
- **Tasks** created based on interviews with on-site workers and managers

#### Task Structure (3 Groups)
| Group | Stage | Focus Areas |
|---|---|---|
| **Gr1** | Planning | Estimate operations, workflow extraction, incident detection, violation detection |
| **Gr2** | Perception | Spatial cognition, workflow integration, image & video understanding |
| **Gr3** | Action | Action evaluation, system integration |

Tasks also include **Long Horizon Tasks** that span multiple task groups, requiring multi-step reasoning and integration.

#### Example Task
> *"Read the manual and detect the operating procedure from the video to ascertain if safety equipment is being worn. If there is a rule violation related to safety equipment, please issue an alert by email."*

The system must cross-reference a safety manual with live video footage, detect violations, and trigger an automated action — combining document understanding, video perception, and system integration.

#### New Action Space Definition
FieldWorkArena defines a new action space that agentic AI must possess for real-world work environments, extending beyond what previous web-centric benchmarks require.

#### Evaluation Contributions
- Improved evaluation functions over previous methods
- Validated that performance evaluation using Multimodal LLMs (e.g., GPT-4o) is **feasible** for this domain
- Identified both **effectiveness and limitations** of the proposed evaluation method

#### Key Findings
- Existing agentic AI struggles significantly in real-world work environments
- Multimodal reasoning (combining video, image, and document understanding) is a major challenge
- GPT-4o class models can serve as evaluators in this domain

#### Research Gaps Identified
- No existing benchmark adequately covers physical/industrial agentic scenarios
- Safety-critical decision-making under multimodal uncertainty is underexplored
- Long-horizon task performance (multi-stage, multi-modal) remains a major open problem
- Evaluation metrics for real-world agentic tasks are still immature

---

## 🔍 Cross-Paper Research Gap Analysis

| Gap Area | AGENTIF | FieldWorkArena |
|---|---|---|
| Long-instruction handling | ✅ Identified | — |
| Real-world grounding | Partial (real agent prompts) | ✅ Full on-site data |
| Multimodal reasoning | ❌ Text-only | ✅ Video + Image + Doc |
| Physical/industrial tasks | ❌ | ✅ |
| Meta-constraint reasoning | ✅ Identified | — |
| Action space formalization | — | ✅ Defined |
| Post-training data for agents | ✅ Gap highlighted | — |
| Evaluation robustness | Hybrid method | Improved function |

**Synthesis:** Together, these papers reveal that agentic AI evaluation is still in early stages. AGENTIF addresses the *instruction complexity* dimension, while FieldWorkArena addresses the *task realism and modality* dimension. Neither domain is close to solved, and the intersection — complex multimodal instructions in industrial settings — remains entirely open.

---

## 🗂️ Repository Structure

```
├── AGENTIF PAPER.pdf              # Full paper: Benchmarking LLM instruction following in agentic scenarios
├── fieldwork arena paper.pdf      # Full paper: Agentic AI benchmark for real field work tasks
└── README.md                      # This file
```

---

## 🚀 Getting Started

To read the papers:
```bash
# Clone this repository
git clone https://github.com/your-username/Agentic-AI-for-Research-Applications-Structured-Paper-Reviews-and-Gap-Mining.git
cd Agentic-AI-for-Research-Applications-Structured-Paper-Reviews-and-Gap-Mining
```

To access the associated code and datasets for each benchmark:

**AGENTIF:**
```bash
# Code
git clone https://github.com/THU-KEG/AgentIF

# Dataset (HuggingFace)
from datasets import load_dataset
ds = load_dataset("THU-KEG/AgentIF")
```

**FieldWorkArena:**
```bash
# Dataset and evaluation code
# Visit: https://en-documents.research.global.fujitsu.com/fieldworkarena/
```

---

## 📌 Key Takeaways for Practitioners

1. **Don't use short synthetic benchmarks to evaluate agentic LLMs** — they underestimate real-world failure modes.
2. **Instruction length matters critically** — performance collapses beyond ~6,000 words; consider task decomposition.
3. **Tool specification handling is a bottleneck** — most current LLMs struggle with detailed tool descriptions in system prompts.
4. **Multimodal agentic evaluation is nascent** — FieldWorkArena is one of the first to seriously address this.
5. **Meta-constraint compliance is underexplored** — priority and conflict resolution among constraints is a largely unsolved problem.

---

## 📚 Citations

```bibtex
@article{qi2025agentif,
  title={AGENTIF: Benchmarking Instruction Following of Large Language Models in Agentic Scenarios},
  author={Qi, Yunjia and Peng, Hao and Wang, Xiaozhi and Xin, Amy and Liu, Youfeng and Xu, Bin and Hou, Lei and Li, Juanzi},
  journal={arXiv preprint arXiv:2505.19644},
  year={2025}
}

@inproceedings{moteki2025fieldworkarena,
  title={FieldWorkArena: Agentic AI Benchmark for Real Field Work Tasks},
  author={Moteki, Atsunori and Masui, Shoichi and Yang, Fan and Song, Yueqi and Bisk, Yonatan and Neubig, Graham and Kusajima, Ikuo and Watanabe, Yasuto and Ishida, Hiroyuki and Takahashi, Jun and Jiang, Shan},
  booktitle={Proceedings of the 33rd ACM International Conference on Multimedia (MM'25)},
  year={2025}
}
```

---

## 🏷️ Topics

`agentic-ai` `llm-benchmarking` `instruction-following` `multimodal-llm` `research-gap-mining` `paper-review` `field-work` `safety-ai` `evaluation` `nlp`
