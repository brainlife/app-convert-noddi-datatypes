[![Abcdspec-compliant](https://img.shields.io/badge/ABCD_Spec-v1.1-green.svg)](https://github.com/brain-life/abcd-spec)
[![Run on Brainlife.io](https://img.shields.io/badge/Brainlife-brainlife.app.368-blue.svg)](https://doi.org/https://doi.org/10.25663/brainlife.app.368)

# Temporary converter app from NODDI-deprecated to NODDI datatype

<!-- brainlife-app:begin (generated from the App manifest; edit the manifest, not this block) -->

**Utility that converts a deprecated NODDI dataset to the current NODDI datatype by renaming icvf to ndi and od to odi, and copying isovf and the direction map.**

Copies icvf.nii.gz to ndi.nii.gz, od to odi.nii.gz and isovf unchanged, plus the dir file, into the new noddi datatype. Use it only to make old NODDI outputs usable by Apps that expect the current naming. Utility App; no computation.

Run it on brainlife.io: [https://doi.org/10.25663/brainlife.app.368](https://doi.org/10.25663/brainlife.app.368)

| Input | Datatype | Required | Description |
|---|---|---|---|
| `noddi-deprecated` | `neuro/noddi-deprecated` | yes | Deprecated NODDI outputs: icvf, isovf, od and dir maps. |

| Output | Datatype | Description |
|---|---|---|
| `noddi` | `neuro/noddi` | NODDI maps renamed to ndi, isovf and odi, with the direction map. |

Runtime: 1 CPUs; 0.08 h walltime.

Please cite:
- Avesani P. et al. The open diffusion data derivatives. Sci Data 6, 69 (2019). [doi:10.1038/s41597-019-0073-y](https://doi.org/10.1038/s41597-019-0073-y)

<!-- brainlife-app:end -->

This app will This app is purely designed for use within brainlife as it converts a deprecated NODDI datatype to the newer version. Specifically, the biggest change between the two datatypes is the naming schema employed with icvf => ndi and od => odi, to match the more commonly used acronyms

### Authors

- Brad Caron (bacaron@utexas.edu)

### Contributors

- Soichi Hayashi (shayashi@iu.edu)

### Funding Acknowledgement

brainlife.io is publicly funded and for the sustainability of the project it is helpful to Acknowledge the use of the platform. We kindly ask that you acknowledge the funding below in your publications and code reusing this code.

[![NSF-BCS-1734853](https://img.shields.io/badge/NSF_BCS-1734853-blue.svg)](https://nsf.gov/awardsearch/showAward?AWD_ID=1734853)
[![NSF-BCS-1636893](https://img.shields.io/badge/NSF_BCS-1636893-blue.svg)](https://nsf.gov/awardsearch/showAward?AWD_ID=1636893)
[![NSF-ACI-1916518](https://img.shields.io/badge/NSF_ACI-1916518-blue.svg)](https://nsf.gov/awardsearch/showAward?AWD_ID=1916518)
[![NSF-IIS-1912270](https://img.shields.io/badge/NSF_IIS-1912270-blue.svg)](https://nsf.gov/awardsearch/showAward?AWD_ID=1912270)
[![NIH-NIBIB-R01EB029272](https://img.shields.io/badge/NIH_NIBIB-R01EB029272-green.svg)](https://grantome.com/grant/NIH/R01-EB029272-01)

### Citations

We kindly ask that you cite the following articles when publishing papers and code using this code.

1. Avesani, P., McPherson, B., Hayashi, S. et al. The open diffusion data derivatives, brain data upcycling via integrated publishing of derivatives and reproducible open cloud services. Sci Data 6, 69 (2019). https://doi.org/10.1038/s41597-019-0073-y

#### MIT Copyright (c) 2020 brainlife.io The University of Texas at Austin and Indiana University

## Running the App

### On Brainlife.io

You can submit this App online at [https://doi.org/https://doi.org/10.25663/brainlife.app.368](https://doi.org/https://doi.org/10.25663/brainlife.app.368) via the 'Execute' tab.

### Running Locally (on your machine)

1. git clone this repo

2. Inside the cloned directory, create `config.json` with something like the following content with paths to your input files.

```json
{
	"dir": "/input/noddi/dir.nii.gz",
	"icvf": "/input/noddi/icvf.nii.gz",
	"od": "/input/noddi/od.nii.gz",
	"isovf": "/input/noddi/isovf.nii.gz"
}
```

### Sample Datasets

You can download sample datasets from Brainlife using [Brainlife CLI](https://github.com/brain-life/cli). 

```
npm install -g brainlife
bl login
mkdir input
bl dataset download
```

3. Launch the App by executing 'main'

```bash
./main
```

## Output

The main output of this App is a noddi datatype, containing the neurite density index (ndi), orientation dispersion index (odi), and isotropic volume fraction (isovf) data.

#### Product.json

The secondary output of this app is `product.json`. This file allows web interfaces, DB and API calls on the results of the processing.

### Dependencies

This App only requires [singularity](https://www.sylabs.io/singularity/) to run. If you don't have singularity, you just need a terminal with a "cp" command.

#### MIT Copyright (c) 2020 brainlife.io The University of Texas at Austin and Indiana University
