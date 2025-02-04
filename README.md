# Sports and Women’s Sports: Gender Bias in Text Generation with Olympic Data
Author: [Laura Biester](https://www.laurabiester.com/) (Middlebury College)
Contact: lbiester@middlebury.edu

---

This repository includes the prompts and annotations for the paper "Sports and Women’s Sports: Gender Bias in Text Generation with Olympic Data", published at NAACL 2025. The organization of the repository is explained in detail below.

## Prompts
The prompts are available in the `prompts` directory. The underspecifid prompts are in the `Prompt` column of `underspecified.tsv`; other columns include `Discipline`, `Season`, `Year`, and `Event`. The specified prompts are in the `Prompt` column of `specified.tsv`; in addition to the columns that are also present in `underspecified.tsv`, this file includes a `Gender` column. These are the raw prompts, before adding special tokens for instruction-tuned models.

## Results
The generated text and corresponding annotated medalists are available in the `results` directory. There are two sub-directories: `specified` and `underspecified`. Each filename indicates the model used to generate the text in the `text` column. The columns `Discipline`, `Season`, `Year`, `Event`, and `Gender` (optionally, for the specified prompts) can be used to link these results to the prompts in the `prompts` directory. Additional columns include the results of events as followed:

* For _specified_ prompts:
  * `real_g`, `real_s`, `real_b`: The NOC codes corresponding to the real medal winners (g/s/b = gold/silver/bronze)
  * `gen_g`, `gen_s`, `gen_b`: The NOC codes corresponding to the generated winners
* For _underspecified_ prompts:
  * `real_f_g`, `real_f_s`, `real_f_b`: The NOC codes corresponding to the real female winners
  * `real_m_g`, `real_m_s`, `real_m_b`: The NOC codes corresponding to the real male winners
  * `gen_u_g`, `gen_u_s`, `gen_u_b`: The NOC codes corresponding to the generated winners _whose gender could not be explicitly determined from the text_
  * `gen_f_g`, `gen_f_s`, `gen_f_b`: The NOC codes corresponding to the generated female winners _whose gender was mentioned explicitly in the text_
  * `gen_m_g`, `gen_m_s`, `gen_m_b`: The NOC codes corresponding to the generated male winners _whose gender was mentioned explicitly in the text_

A final column, `status` is used to indicate the reliability of the annotations:

* `accepted` (OK) was selected in most instances, when neither of the situations below applied.
* `unsure` (Ambiguity or Inconsistency in Text) was selected when the model stated that the event did not exist, gave results for a different event, or stated that results changed after the fact due to doping or other policy violations.
* `rejected` (Cannot Annotate) was selected when an instance could not be annotated appropriately due to limitations in the annotation interface, because it required labeling a span with multiple labels. These instances were manually labeled in the final data files by the author.

When the generated text indicates that a tie occurred, NOC codes are separated by `,`.


## Annotations
The annotations are available in `annotations` directory. These should not be needed to reproduce the results in the paper, as the processed versions in `results` represent the same data in a format that is simpler to use and has the original nationalities in the text mapped to NOC does. However, they are presented for completeness, and could in theory be used for sequence tagging. The annotations are in CONLL format with IOB tags. The annotations for each model's generated text are split into multiple files, which is how they were originally given to annotators.

---

The original Olympic results used in this work were obtained through a data request to the [Olympic Studies Center](https://olympics.com/ioc/olympic-studies-centre).
