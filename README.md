# Generative AI Applications — CVE-Style Description Generation

Udacity AI Mastery Capstone 6 (Project 5). Fine-tunes DistilGPT2 on English CVE descriptions
and evaluates how well it reproduces vulnerability-advisory language, including failure cases
and responsible-use risks. All generated text is fictional and is not a real vulnerability report.

## Deliverables
| File | Description |
|---|---|
| `generative_model.ipynb` | Data loading, preprocessing, model, training, generation, evaluation |
| `module_summary.pdf` | Generative AI Analysis and Ethics Report |
| `requirements.txt` | Environment from `pip freeze` |
| `data/cve_2021_descriptions.csv` | Processed dataset (22,613 records) |
| `data/CVE_TERMS_OF_USE.txt` | CVE Program Terms of Use and MITRE copyright notice |

## Dataset
- Source: CVE List V5 — https://github.com/CVEProject/cvelistV5
- Snapshot used: commit `3cb4c6bfb5fbd74de5b87f5158f97c0c56da8f88`, folder `cves/2021` (CVE-2021-* identifiers)
- License: CVE Program Terms of Use — https://www.cve.org/Legal/TermsOfUse

The processed CSV is included, so the raw data is only needed to rebuild it:

```bash
git clone --filter=blob:none --sparse https://github.com/CVEProject/cvelistV5.git ../_raw/cvelistV5
git -C ../_raw/cvelistV5 checkout --detach 3cb4c6bfb5fbd74de5b87f5158f97c0c56da8f88
git -C ../_raw/cvelistV5 sparse-checkout set cves/2021
```

## Setup and run
Tested on Ubuntu with Python 3.14, PyTorch 2.15 (CUDA), and an NVIDIA RTX A3000 12 GB.

```bash
python3 -m venv .venv && source .venv/bin/activate
pip install -r requirements.txt
jupyter lab generative_model.ipynb
```

Run **Kernel → Restart Kernel and Run All Cells**. The first run downloads DistilGPT2 from Hugging Face.
Model checkpoints are written to `checkpoints/` and are not committed.
