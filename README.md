---
language:
- en
license: other
task_categories:
- text-generation
pretty_name: CL-bench
size_categories:
- 1K<n<10K
tags:
- context-learning
- long-context
- benchmark
---

# CL-bench: A Benchmark for Context Learning

## Dataset Description

**CL-bench** is a benchmark for evaluating language models' context learning abilities.

Resolving tasks in CL-bench requires models to learn from the provided context, ranging from new domain-specific knowledge, rule systems, and complex procedures to laws derived from empirical data, rather than only relying on pre-trained knowledge.

### Dataset Statistics

- **Total Samples**: 1,899 tasks
- **Format**: JSON (individual task files)
- **Context Categories**: 4 main categories with 22 sub-categories
- **Multi-turn Conversations**: 2-12 turns per task

### Leaderboard

Visit [www.clbench.com](https://www.clbench.com) for the full leaderboard and latest results!

---

## Repository Structure

This repository contains two data organizations:

### 1. `dataset/` - Original CL-bench Structure

The original benchmark data organized by context categories:

```
dataset/
├── Rule_System_Application/           (566 tasks)
│   ├── Game_Mechanics/                (137)
│   ├── Technical_Standards/           (201)
│   ├── Legal_and_Regulatory/          (92)
│   ├── Mathematical_Formalism/        (69)
│   └── Programming_Syntax/            (67)
│
├── Domain_Knowledge_Reasoning/        (663 tasks)
│   ├── Humanities/                    (124)
│   ├── Management/                    (112)
│   ├── Healthcare/                    (105)
│   ├── Finance/                       (101)
│   ├── Science/                       (88)
│   ├── Legal_Advisory/                (76)
│   └── Lifestyle/                     (57)
│
├── Procedural_Task_Execution/         (471 tasks)
│   ├── Workflow_Orchestration/        (229)
│   ├── Operational_Procedures/        (185)
│   └── Instructional_Procedures/      (57)
│
└── Empirical_Discovery_and_Simulation/ (199 tasks)
    ├── Observational_Data/            (95)
    ├── Simulation_Environment/        (59)
    └── Experimental_Data/             (45)
```

### 2. `Turing/` - Reorganized Structure

Tasks reorganized into individual JSON files with refined categorization:

```
Turing/
├── Category_1_Novel_Formal_Systems/              (415 tasks)
│   ├── Games/                                    (137)
│   │   ├── Board_Games/                          (52)
│   │   ├── Other_General/                        (34)
│   │   ├── Sports_Rules/                         (31)
│   │   └── Card_Games/                           (20)
│   ├── Instruction_Manuals/                      (142)
│   │   ├── Product_Manuals/                      (83)
│   │   └── Technical_Documentation/              (59)
│   ├── Math/                                     (69)
│   │   ├── Proof_Property_Reasoning/             (45)
│   │   ├── Complex_Symbolic_Reasoning/           (18)
│   │   └── Novel_Mathematical_Objects/           (6)
│   └── Coding/                                   (67)
│       ├── General_Programming/                  (47)
│       ├── Multi_Agent_Systems/                  (12)
│       ├── Quantum_Computing/                    (5)
│       └── Fictional_DSL/                        (3)
│
├── Category_2_Specialized_Domain_Knowledge/      (814 tasks)
│   ├── Humanities/                               (124)
│   ├── Management/                               (112)
│   ├── Healthcare/                               (105)
│   ├── Finance/                                  (101)
│   ├── Law_Real_World/                           (92)
│   ├── Science/                                  (88)
│   ├── Legal_Advisory/                           (76)
│   ├── Emerging_Tech_Standards/                  (59)
│   └── Lifestyle/                                (57)
│
├── Category_3_Complex_Procedural_Tasks/          (471 tasks)
│   ├── Workflow_Orchestration/                   (229)
│   ├── Operational_Procedures/                   (185)
│   └── Instructional_Procedures/                 (57)
│
└── Category_4_Scientific_Discovery_Simulation/   (199 tasks)
    ├── Observational_Data/                       (95)
    ├── Simulation_Environment/                   (59)
    └── Experimental_Data/                        (45)
```

---

## Task Distribution Summary

| Category | Tasks | Sub-categories |
|----------|-------|----------------|
| Category 1: Novel Formal Systems | 415 | 13 |
| Category 2: Specialized Domain Knowledge | 814 | 9 |
| Category 3: Complex Procedural Tasks | 471 | 3 |
| Category 4: Scientific Discovery Simulation | 199 | 3 |
| **Total** | **1,899** | **28** |

---

## Data Format

### Data Fields

Each task JSON file contains the following fields:

| Field | Type | Description |
|-------|------|-------------|
| `messages` | list | Multi-turn conversation in OpenAI chat format |
| `rubrics` | list | List of evaluation criteria (strings) |
| `metadata` | dict | Contains `task_id`, `context_id`, `context_category`, `sub_category` |

### `messages` Field

The `messages` field follows the standard OpenAI chat format:

```json
[
  {"role": "system", "content": "system prompt"},
  {"role": "user", "content": "context and task"},
  {"role": "assistant", "content": "response"},
  {"role": "user", "content": "follow-up question"}
]
```

### `rubrics` Field

A list of strings, each describing a specific evaluation rubric.

### `metadata` Field

```json
{
  "task_id": "unique identifier for task",
  "context_id": "unique identifier for context",
  "context_category": "Rule System Application",
  "sub_category": "Game Mechanics"
}
```

- **task_id**: Unique identifier for the task
- **context_id**: Unique identifier for the context
- **context_category**: One of the 4 main categories
- **sub_category**: Fine-grained classification

---

## Usage

### Loading Individual Tasks (Turing Structure)

```python
import json
import os

# Load a single task
with open('Turing/Category_1_Novel_Formal_Systems/Games/Board_Games/task_id.json') as f:
    task = json.load(f)

# Access task components
messages = task['messages']
rubrics = task['rubrics']
metadata = task['metadata']
```

### Loading All Tasks from a Category

```python
import json
import os
from pathlib import Path

def load_category(category_path):
    tasks = []
    for json_file in Path(category_path).rglob('*.json'):
        with open(json_file) as f:
            tasks.append(json.load(f))
    return tasks

# Load all Category 1 tasks
cat1_tasks = load_category('Turing/Category_1_Novel_Formal_Systems')
print(f"Loaded {len(cat1_tasks)} tasks")
```

For more details, please see our **GitHub repository**: [github.com/Tencent-Hunyuan/CL-bench](https://github.com/Tencent-Hunyuan/CL-bench)

---

## License

CL-Bench is released under a **custom evaluation-only license**.

Permission is hereby granted, free of charge, to any person obtaining a copy of this dataset and associated documentation files (the "Dataset"), to use, copy, modify, merge, publish, and distribute the Dataset **solely for the purposes of evaluation, testing, and benchmarking of models**.

The Dataset (or any portion thereof) **must not** be used for training, fine-tuning, calibrating, distilling, adapting, or any form of parameter updating.

Please refer to the LICENSE file for the full license text.

---

## Citation

If you find our work useful, please cite it as follows:

```bibtex
@misc{dou2026clbenchbenchmarkcontextlearning,
      title={CL-bench: A Benchmark for Context Learning},
      author={Shihan Dou and Ming Zhang and Zhangyue Yin and Chenhao Huang and Yujiong Shen and Junzhe Wang and Jiayi Chen and Yuchen Ni and Junjie Ye and Cheng Zhang and Huaibing Xie and Jianglu Hu and Shaolei Wang and Weichao Wang and Yanling Xiao and Yiting Liu and Zenan Xu and Zhen Guo and Pluto Zhou and Tao Gui and Zuxuan Wu and Xipeng Qiu and Qi Zhang and Xuanjing Huang and Yu-Gang Jiang and Di Wang and Shunyu Yao},
      year={2026},
      eprint={2602.03587},
      archivePrefix={arXiv},
      primaryClass={cs.CL},
      url={https://arxiv.org/abs/2602.03587},
}
```
