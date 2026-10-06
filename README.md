# PhiloVista-1620: A Multi-source Benchmark

A multi-source benchmark for philosophical image understanding. Given an image, the task is to select the three philosophical concepts best supported by its visual content, from a fixed vocabulary of 632 concepts.

> Status: the repository currently hosts the **PhiloVista-1620** release (1,620 images). It will be extended to the full PhiloVista-1620 set.

## Directory layout

```
PhiloVista-1620/
├── images/                                          # 1,620 images from 4 sources:
│                                                    #   HAIV (550) · HL (500) · IRFL (420) · MM (150)
├── PhiloVista-1620_labels.csv                       # gold labels: filename, label_1, label_2, label_3
├── PhiloVista-1620_HL.csv                           # HL captions: Scene / Action / Rationale / Object
├── philosophical_image_label_system_formal_632.md   # label system: 632 concepts with Concept IDs (PHC-001 … PHC-632)
├── 主评测_prompt_English.txt                         # main evaluation prompt (English)
└── 主评测_prompt_中文.txt                            # main evaluation prompt (Chinese)
```

## Task format

Each sample asks a model to look at one image and output exactly one JSON object:

```json
{"sample_id": "<id from the user message>", "concept_ids": ["PHC-001", "PHC-002", "PHC-003"]}
```

- The three concept IDs must come from the `Concept ID` column of `philosophical_image_label_system_formal_632.md`, ordered from strongest to weakest visual support.
- Candidate concepts must be grounded in visible objects, people, actions, relationships, spatial structure, scenes, symbols, and legible text.
- See the prompt files for the full evaluation rules (English and Chinese versions are equivalent).
