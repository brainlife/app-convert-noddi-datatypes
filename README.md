<h1 align="center">Convert NODDI-deprecated to NODDI datatype</h1>

<p align="center">
  A current <code>neuro/noddi</code> dataset (ndi, odi, isovf) from an old NODDI dataset that uses the icvf/od naming.
</p>

<p align="center">
  <a href="https://github.com/brainlife/abcd-spec"><img src="https://img.shields.io/badge/ABCD_Spec-v1.1-green.svg" alt="ABCD Spec v1.1"></a>
  <a href="https://doi.org/10.25663/brainlife.app.368"><img src="https://img.shields.io/badge/Brainlife-brainlife.app.368-blue.svg" alt="Run on brainlife.io"></a>
  <a href="LICENSE"><img src="https://img.shields.io/badge/License-MIT-lightgrey.svg" alt="MIT license"></a>
</p>

## 🧠 At a glance

<!-- brainlife-app:begin (generated from the App manifest; edit the manifest, not this block) -->

> **Utility that converts a deprecated NODDI dataset to the current NODDI datatype by renaming icvf to ndi and od to odi, and copying isovf and the direction map.**

Copies icvf.nii.gz to ndi.nii.gz, od to odi.nii.gz and isovf unchanged, plus the dir file, into the new noddi datatype. Use it only to make old NODDI outputs usable by Apps that expect the current naming. Utility App; no computation.

| | |
|---|---|
| 📥 **Inputs** | `neuro/noddi-deprecated` |
| 📤 **Outputs** | `neuro/noddi` |
| ⚙️ **Resources** | 1 CPUs · 0.08 h walltime |
| 🔗 **Run it** | [doi.org/10.25663/brainlife.app.368](https://doi.org/10.25663/brainlife.app.368) |

#### 📥 Inputs

| Input | Datatype | Required | Description |
|---|---|---|---|
| `noddi-deprecated` | `neuro/noddi-deprecated` | yes | Deprecated NODDI outputs: icvf, isovf, od and dir maps. |

#### 📤 Outputs

| Output | Datatype | Description |
|---|---|---|
| `noddi` | `neuro/noddi` | NODDI maps renamed to ndi, isovf and odi, with the direction map. |

<!-- brainlife-app:end -->

## 🚀 Running the App

This is a temporary utility App, designed for use within brainlife.io. The main change between the deprecated and the current NODDI datatype is the file naming, which now follows the more commonly used acronyms:

| Deprecated | Current | Map |
|---|---|---|
| `icvf.nii.gz` | `ndi.nii.gz` | neurite density index |
| `od.nii.gz` | `odi.nii.gz` | orientation dispersion index |
| `isovf.nii.gz` | `isovf.nii.gz` | isotropic volume fraction |
| `dir` | `dir` (unchanged) | principal direction map |

The App only copies and renames files; it does not recompute anything.

### ☁️ On brainlife.io

Open the App at [doi.org/10.25663/brainlife.app.368](https://doi.org/10.25663/brainlife.app.368), choose a `neuro/noddi-deprecated` dataset from your project and press **Execute**. The converted `neuro/noddi` dataset is archived to your project and can feed any App that expects the current NODDI naming.

### 💻 Locally

You need `bash`, `cp` and [`jq`](https://jqlang.github.io/jq/); no container is used.

1. Clone this repository.
2. Create `config.json` with the paths to your inputs:

   ```json
   {
       "dir": "/input/noddi/dir.nii.gz",
       "icvf": "/input/noddi/icvf.nii.gz",
       "od": "/input/noddi/od.nii.gz",
       "isovf": "/input/noddi/isovf.nii.gz"
   }
   ```

3. Run the App:

   ```bash
   ./main
   ```

### 🧪 Sample data

Download a NODDI-deprecated dataset from brainlife.io with the [brainlife CLI](https://github.com/brainlife/cli):

```bash
npm install -g brainlife
bl login
mkdir input
bl dataset download <dataset id>
```

## 📦 Outputs

```text
noddi/
├── ndi.nii.gz     neurite density index (was icvf)
├── odi.nii.gz     orientation dispersion index (was od)
├── isovf.nii.gz   isotropic volume fraction
└── dir.nii.gz     direction map, copied with its original name
```

## 🩺 Troubleshooting

- **Missing files in the output**: `main` does not stop on a failed copy; check the job log for `cp` errors, which mean one of the input maps was missing from the deprecated dataset.

## 📚 Citing

> [!TIP]
> If you use this App in your work, please cite the App, the software it builds on and brainlife.io (below). GitHub's **Cite this repository** button gives the App citation in APA and BibTeX.

- Temporary converter app from NODDI-deprecated to NODDI datatype. brainlife.io App. [doi:10.25663/brainlife.app.368](https://doi.org/10.25663/brainlife.app.368)
- Avesani P. et al. The open diffusion data derivatives. Sci Data 6, 69 (2019). [doi:10.1038/s41597-019-0073-y](https://doi.org/10.1038/s41597-019-0073-y)
- Zhang et al. NODDI: Practical in vivo neurite orientation dispersion and density imaging of the human brain. *NeuroImage* 61:1000-1016 (2012). [doi:10.1016/j.neuroimage.2012.03.072](https://doi.org/10.1016/j.neuroimage.2012.03.072)
- Hayashi S, Caron BA, Heinsfeld AS, et al. brainlife.io: a decentralized and open-source cloud platform to support neuroscience research. *Nature Methods* 21:809–813 (2024). [doi:10.1038/s41592-024-02237-2](https://doi.org/10.1038/s41592-024-02237-2)

## 👥 Authors

- Brad Caron

**Contributors:** Soichi Hayashi

## 💰 Funding

[![Wellcome-226486/Z/22/Z](https://img.shields.io/badge/Wellcome-226486%2FZ%2F22%2FZ-purple.svg)](https://wellcome.org/)
[![NIH-NINDS-U24NS140384](https://img.shields.io/badge/NIH_NINDS-U24NS140384-green.svg)](https://reporter.nih.gov/project-details/11261037)
[![NIH-NINDS-UM1NS132207](https://img.shields.io/badge/NIH_NINDS-UM1NS132207-green.svg)](https://reporter.nih.gov/project-details/11411328)
[![NIH-NIBIB-R01EB029272](https://img.shields.io/badge/NIH_NIBIB-R01EB029272-green.svg)](https://reporter.nih.gov/project-details/10262925)
[![NIH-NIBIB-R01EB030896](https://img.shields.io/badge/NIH_NIBIB-R01EB030896-green.svg)](https://reporter.nih.gov/project-details/10428625)
[![NIH-NIMH-R01MH126699](https://img.shields.io/badge/NIH_NIMH-R01MH126699-green.svg)](https://reporter.nih.gov/project-details/10460628)
[![NIH-NIDCD-R01DC020088](https://img.shields.io/badge/NIH_NIDCD-R01DC020088-green.svg)](https://reporter.nih.gov/project-details/11140284)
[![NSF-BCS-1734853](https://img.shields.io/badge/NSF_BCS-1734853-blue.svg)](https://www.nsf.gov/awardsearch/showAward?AWD_ID=1734853)
[![NSF-BCS-2203524](https://img.shields.io/badge/NSF_BCS-2203524-blue.svg)](https://www.nsf.gov/awardsearch/showAward?AWD_ID=2203524)
[![NSF-IIS-1636893](https://img.shields.io/badge/NSF_IIS-1636893-blue.svg)](https://www.nsf.gov/awardsearch/showAward?AWD_ID=1636893)
[![NSF-OAC-2148729](https://img.shields.io/badge/NSF_OAC-2148729-blue.svg)](https://www.nsf.gov/awardsearch/showAward?AWD_ID=2148729)
[![NSF-IIS-1912270](https://img.shields.io/badge/NSF_IIS-1912270-blue.svg)](https://www.nsf.gov/awardsearch/showAward?AWD_ID=1912270)
[![NSF-IIS-2148700](https://img.shields.io/badge/NSF_IIS-2148700-blue.svg)](https://www.nsf.gov/awardsearch/showAward?AWD_ID=2148700)
[![NSF-OAC-1916518](https://img.shields.io/badge/NSF_OAC-1916518-blue.svg)](https://www.nsf.gov/awardsearch/showAward?AWD_ID=1916518)

<sub>brainlife.io is publicly funded, and acknowledging that support helps keep it running. This App was developed with support from Wellcome, the U.S. National Institutes of Health (including the BRAIN Initiative BRAIN CONNECTS program: The Axonal Projectome EXchange, U24NS140384, and the Center for Mesoscale Connectomics, UM1NS132207) and the U.S. National Science Foundation.</sub>

## ⚖️ License

MIT. Copyright (c) 2020 brainlife.io, The University of Texas at Austin and Indiana University.
