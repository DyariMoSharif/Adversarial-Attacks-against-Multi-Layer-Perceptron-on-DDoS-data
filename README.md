**Author:** Dyari Mohammed Sharif
> Google Scholar Profile: https://scholar.google.com/citations?user=tfdtpGEAAAAJ&hl=en&oi=ao

# Adversarial Attacks against Multi-Layer Perceptron on DDoS data
> This repository contains the implementation and experimental notebooks for the published paper **“Adversarial Attacks against Multi-Layer Perceptron on DDoS data”**.
The paper studies the robustness of a high-performing Multi-Layer Perceptron (MLP) model for DDoS detection under adversarial perturbations. Rather than relying on gradient-based attacks or requiring access to model internals, the work shows that a simple and protocol-compliant perturbation of a single feature (`Flow IAT Mean`) can severely degrade classification performance. The experiments demonstrate that a baseline model with very high accuracy on benign test conditions can become highly unreliable under targeted perturbations, including cases where accuracy collapses under combined attacks. The paper also evaluates adversarial retraining, showing that retraining improves robustness substantially, but does not eliminate the vulnerability entirely.
This repository is organized to mirror the experimental structure of the paper, including:- baseline replication of the selected MLP study on CICIDS2017,- adversarial perturbation scenarios,- randomization analysis,- feature set expansion,- feature selection justification through cardinality-based comparison,- cross-set evaluation on CICDDoS2019,- imbalance evaluation using a balanced Syn dataset,- adversarial learning / adversarial retraining.
**Author:** Dyari Mohammed Sharif  

Link to the Paper:
https://rdcu.be/feXe3

---
## Repository Structure
### Main notebooks
#### `01_Selected_Study_CICIDS2017.ipynb`This notebook is the main implementation of the paper’s core experiment on the **CICIDS2017 Wednesday** dataset using the **selected 6 features**. It replicates the selected MLP-based DDoS detection study and serves as the foundation for the central results reported in the paper.
This notebook corresponds to:- **Section: Experiments and Results**- **Subsection: Adversarial Perturbation Scenarios**- **Subsection: Adversarial Learning**
It includes:- data loading, scaling, and train-test split,- replication of the selected MLP configuration,- baseline performance before perturbation,- perturbation of malicious samples only,- perturbation of benign samples only,- perturbation of both benign and malicious samples,- adversarial retraining / adversarial learning.
---
#### `02_Full_Feature_CICIDS2017.ipynb`This notebook extends the selected-study experiment from 6 features to the **full CICIDS2017 feature set**. It is used to assess whether the observed adversarial weakness is tied only to the minimal feature subset or persists when the full feature space is used.
This notebook corresponds to:- **Subsection: Feature Set Expansion**
It includes:- loading the CICIDS2017 data with the full feature set,- handling NaN and infinite values,- scaling and label encoding,- baseline performance with full features,- adversarial perturbation using the expanded feature configuration.
---
#### `03_Cross_Set_CICDDoS2019.ipynb`This notebook evaluates the generalization of the approach on **CICDDoS2019**, specifically the **UDPLag** dataset.
This notebook corresponds to:- **Subsection: Cross-Set Evaluation**
It includes:- loading the `UDPLag` dataset,- selected-feature preprocessing,- baseline MLP evaluation,- adversarial perturbation on both benign and malicious samples,- analysis of generalization beyond the CICIDS2017 setting.
---
#### `04_Balanced_CICDDoS2019.ipynb`This notebook investigates the effect of **class imbalance** by using a balanced version of the **Syn** dataset from CICDDoS2019.
This notebook corresponds to:- **Subsection: Evaluation of Imbalance**
It includes:- loading the CICDDoS2019 Syn data,- balancing the dataset,- preprocessing and train-test splitting,- baseline MLP evaluation,- perturbation-based robustness analysis under balanced conditions.
---
#### `05_Lowest-cardinality_Selected_Study_CICIDS2017.ipynb`This notebook supports the paper’s analysis of **feature selection justification** by comparing perturbations on lower-cardinality features against the main perturbation feature used in the paper.
This notebook corresponds to:- **Subsection: Feature Selection Justification**
It includes:- selected-study CICIDS2017 setup,- perturbation experiments on lower-cardinality features,- comparison against the stronger perturbation effect observed for `Flow IAT Mean`.
---
## Randomization experiments
The repository includes separate folders for experiments that vary randomization settings, such as train-test splitting, MLP initialization, and seed behavior. These folders support the paper’s discussion of robustness under different random conditions.
### `01_Effect of Randomization/`Randomization experiments for the **selected 6-feature CICIDS2017 setup**.
This folder corresponds to the randomization analysis discussed under:- **Subsection: Adversarial Perturbation Scenarios**
Files:- `Enabled_onData_First Run.ipynb`- `Enabled_onData_Second Run.ipynb`- `Enabled_onData_Third Run.ipynb`- `Enabled_onMLP_First Run.ipynb`- `Enabled_onMLP_Second Run.ipynb`- `Enabled_onMLP_Third Run.ipynb`
These notebooks evaluate how the adversarial outcomes change when randomness is enabled in the data split and/or the MLP.
---
### `02_Effect of Randomization/`Randomization experiments for the **full-feature CICIDS2017 setup**.
This folder corresponds to:- **Subsection: Feature Set Expansion**  with additional randomization analysis.
Files:- `Full_feature_CICIDS2017_FirstRun.ipynb`- `Full_feature_CICIDS2017_SecondRun.ipynb`- `Full_feature_CICIDS2017_ThirdRun.ipynb`
---
### `03_Effect of Randomization/`Randomization experiments for the **cross-set UDPLag evaluation** on CICDDoS2019.
This folder corresponds to:- **Subsection: Cross-Set Evaluation**  with additional randomization analysis.
Files:- `UDPLag_CICDDoS2019_First Run.ipynb`- `UDPLag_CICDDoS2019_Second Run.ipynb`- `UDPLag_CICDDoS2019_Third Run.ipynb`
---
### `04_Effect of Randomization/`Randomization experiments for the **balanced Syn evaluation** on CICDDoS2019.
This folder corresponds to:- **Subsection: Evaluation of Imbalance**  with additional randomization analysis.
Files:- `Syn_CICDDoS2019_First_Run.ipynb`- `Syn_CICDDoS2019_Second_Run.ipynb`- `Syn_CICDDoS2019_Third_Run.ipynb`
---
## Datasets
### `Datasets/`This folder contains the compressed datasets used across the experiments in the paper.
Included files:- `CICIDS2017_Wednesday_Paper.csv.gz`- `UDPLag.csv.gz`- `CICDDoS2019_Syn_part1.csv.gz`- `CICDDoS2019_Syn_part2.csv.gz`- `CICDDoS2019_Syn_part3.csv.gz`- `CICDDoS2019_Syn_part4.csv.gz`
These datasets support:- the selected-study CICIDS2017 experiments,- the full-feature CICIDS2017 experiments,- the cross-set evaluation on UDPLag,- the balanced-data evaluation on Syn.
---
## Paper-to-code mapping
### Section: Experiments and Results- Core baseline and perturbation experiments: `01_Selected_Study_CICIDS2017.ipynb`
### Subsection: Adversarial Perturbation Scenarios- Main implementation: `01_Selected_Study_CICIDS2017.ipynb`- Randomization analysis: `01_Effect of Randomization/`
### Subsection: Feature Set Expansion- Main implementation: `02_Full_Feature_CICIDS2017.ipynb`- Randomization analysis: `02_Effect of Randomization/`
### Subsection: Feature Selection Justification- Main implementation: `05_Lowest-cardinality_Selected_Study_CICIDS2017.ipynb`
### Subsection: Cross-Set Evaluation- Main implementation: `03_Cross_Set_CICDDoS2019.ipynb`- Randomization analysis: `03_Effect of Randomization/`
### Subsection: Evaluation of Imbalance- Main implementation: `04_Balanced_CICDDoS2019.ipynb`- Randomization analysis: `04_Effect of Randomization/`
### Subsection: Adversarial Learning- Main implementation: `01_Selected_Study_CICIDS2017.ipynb`
---
## Notes- The notebooks are organized by experiment rather than by paper section titles, so this README provides a direct bridge between the published paper and the implementation.- The core selected-study notebook replicates the referenced MLP setup using a small feature set and then extends it with adversarial perturbation and adversarial retraining experiments.- The additional folders capture repeated runs and seed-dependent behavior for reproducibility analysis.
