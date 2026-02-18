# Category Mapping: Requested vs Existing Repository Structure

This document maps the requested benchmark categories to the existing repository categories in CL-bench.

---

## Overview

| Requested Category | Existing Repo Category | Match Level |
|-------------------|----------------------|-------------|
| Novel Formal Systems | Rule_System_Application | ✅ Strong Match |
| Specialized Domain Knowledge | Domain_Knowledge_Reasoning | ✅ Strong Match |
| Complex Procedural Tasks | Procedural_Task_Execution | ✅ Strong Match |
| Scientific Discovery Simulation | Empirical_Discovery_and_Simulation | ✅ Strong Match |

---

## Detailed Category Mapping

### Category 1: Novel Formal Systems → Rule_System_Application

**Requested (400 tasks):**
| Sub-category | Tasks | Description |
|-------------|-------|-------------|
| Games | 100 | Board games, card games, sports rule following |
| Math | 100 | Mathematical theorem proving and application |
| Coding | 100 | Programming language syntax and semantics |
| Instruction Manuals | 100 | Following device/equipment instructions |

**Existing Repo (5 sub-categories):**
| Sub-category | Description | Sample Task Types |
|-------------|-------------|-------------------|
| Game_Mechanics | Board game rules, strategy games | Chess variants, Candyland rule interpretation |
| Mathematical_Formalism | Mathematical proofs, formal systems | Z-modular arithmetic, symbolic logic |
| Programming_Syntax | Code interpretation, language rules | DSL execution, code prediction |
| Legal_and_Regulatory | Compliance rules, regulatory frameworks | Rule-based legal reasoning |
| Technical_Standards | Standards compliance, specifications | Technical rule following |

**Mapping:**
- `Games` → `Game_Mechanics` (Direct match)
- `Math` → `Mathematical_Formalism` (Direct match)
- `Coding` → `Programming_Syntax` (Direct match)
- `Instruction Manuals` → `Technical_Standards` + `Legal_and_Regulatory` (Partial overlap)

---

### Category 2: Specialized Domain Knowledge → Domain_Knowledge_Reasoning

**Requested (350 tasks):**
| Sub-category | Tasks | Description |
|-------------|-------|-------------|
| Fictional Law/Constitution | 50 | Reasoning with made-up legal systems |
| Constructed Languages | 50 | Klingon, Esperanto, fictional languages |
| Emerging Tech | 50 | Cutting-edge technology understanding |
| Finance | 50 | Financial domain knowledge |
| Law | 50 | Legal domain knowledge |
| Niche Language Translation | 50 | Domain-specific translation |
| Semantic Drift Analysis | 50 | Language evolution understanding |

**Existing Repo (7 sub-categories):**
| Sub-category | Description | Sample Task Types |
|-------------|-------------|-------------------|
| Finance | Financial analysis, trading, accounting | Market analysis, financial calculations |
| Healthcare | Medical knowledge, clinical reasoning | Diagnosis, treatment protocols |
| Humanities | History, philosophy, cultural studies | Historical analysis, ethical reasoning |
| Legal_Advisory | Legal advice, case analysis | Contract review, legal interpretation |
| Lifestyle | Daily life, consumer decisions | Product recommendations, life advice |
| Management | Business operations, leadership | Strategy, team management |
| Science | Scientific knowledge, research | Research analysis, scientific reasoning |

**Mapping:**
- `Finance` → `Finance` (Direct match)
- `Law` → `Legal_Advisory` (Direct match)
- `Fictional Law/Constitution` → `Legal_Advisory` (Needs extension for fictional systems)
- `Emerging Tech` → `Science` + `Management` (Partial overlap)
- `Constructed Languages` → **NEW** (Not in existing repo)
- `Niche Language Translation` → **NEW** (Not in existing repo)
- `Semantic Drift Analysis` → **NEW** (Not in existing repo)

---

### Category 3: Complex Procedural Tasks → Procedural_Task_Execution

**Requested (150 tasks):**
| Sub-category | Tasks | Description |
|-------------|-------|-------------|
| With Tools (Pattern A) | 50 | Multi-step procedures using tools |
| With Tools (Pattern B) | 50 | Alternative tool-based workflows |
| Without Tools | 50 | Pure reasoning procedural tasks |

**Existing Repo (3 sub-categories):**
| Sub-category | Description | Sample Task Types |
|-------------|-------------|-------------------|
| Instructional_Procedures | Step-by-step instructions | Following tutorials, guides |
| Operational_Procedures | Business operations, workflows | B2B Sales (Winning by Design), CRM operations |
| Workflow_Orchestration | Complex multi-step processes | Multi-agent coordination, process management |

**Mapping:**
- `With Tools (Pattern A/B)` → `Workflow_Orchestration` + `Operational_Procedures` (Existing tasks include tool usage patterns)
- `Without Tools` → `Instructional_Procedures` (Direct match)

**Note:** Existing repo tasks include multi-turn conversations with system prompts defining operational contexts (e.g., B2B Sales Assistant with Winning by Design methodology).

---

### Category 4: Scientific Discovery Simulation → Empirical_Discovery_and_Simulation

**Requested (100 tasks):**
| Sub-category | Tasks | Description |
|-------------|-------|-------------|
| Sandbox Simulation | 50 | Simulated environments for experimentation |
| Law Discovery | 50 | Discovering scientific laws from data |

**Existing Repo (3 sub-categories):**
| Sub-category | Description | Sample Task Types |
|-------------|-------------|-------------------|
| Experimental_Data | Analyzing experimental results | Centrifugal pump experiments, hydraulic calculations |
| Observational_Data | Analyzing observational studies | Pattern recognition, data interpretation |
| Simulation_Environment | Complex simulation scenarios | MERLIN safety system (volatile materials refinery) |

**Mapping:**
- `Sandbox Simulation` → `Simulation_Environment` (Direct match - includes complex safety system simulations)
- `Law Discovery` → `Experimental_Data` + `Observational_Data` (Combined coverage)

**Note:** Existing tasks include sophisticated simulations like MERLIN safety protocol with component monitoring, fault detection, and rule-based reasoning in industrial settings.

---

## Task Count Comparison

| Category | Requested Tasks | Existing Tasks | Gap |
|----------|----------------|----------------|-----|
| Novel Formal Systems / Rule_System_Application | 400 | ~475* | -75 |
| Specialized Domain Knowledge / Domain_Knowledge_Reasoning | 350 | ~665* | -315 |
| Complex Procedural Tasks / Procedural_Task_Execution | 150 | ~285* | -135 |
| Scientific Discovery / Empirical_Discovery_and_Simulation | 100 | ~474* | -374 |
| **Total** | **1,000** | **~1,899** | **-899** |

*Approximate counts based on repository exploration

---

## Gaps and New Sub-categories Needed

The following sub-categories from the requested structure are **not present** in the existing repository:

1. **Constructed Languages** (50 tasks)
   - Klingon, Esperanto, Elvish, and other artificial languages
   - Translation, grammar interpretation, vocabulary usage

2. **Niche Language Translation** (50 tasks)
   - Domain-specific terminology translation
   - Technical jargon across languages

3. **Semantic Drift Analysis** (50 tasks)
   - Historical word meaning changes
   - Language evolution patterns

---

## Recommended Actions

1. **Direct Reuse**: Most existing sub-categories align well with requested structure
2. **Naming Standardization**: Consider aligning naming conventions between the two structures
3. **Gap Filling**: Create new tasks for Constructed Languages, Niche Translation, and Semantic Drift
4. **Task Redistribution**: Existing repo has 899 more tasks than requested - may need pruning or redistribution

---

## File Structure Reference

```
CL-bench/
├── Domain_Knowledge_Reasoning/
│   ├── Finance/
│   ├── Healthcare/
│   ├── Humanities/
│   ├── Legal_Advisory/
│   ├── Lifestyle/
│   ├── Management/
│   └── Science/
├── Empirical_Discovery_and_Simulation/
│   ├── Experimental_Data/
│   ├── Observational_Data/
│   └── Simulation_Environment/
├── Procedural_Task_Execution/
│   ├── Instructional_Procedures/
│   ├── Operational_Procedures/
│   └── Workflow_Orchestration/
└── Rule_System_Application/
    ├── Game_Mechanics/
    ├── Legal_and_Regulatory/
    ├── Mathematical_Formalism/
    ├── Programming_Syntax/
    └── Technical_Standards/
```
