# Risk and Reliability Analysis: FTA, ETA, and Bayesian Networks

A collection of Jupyter notebooks demonstrating three classical risk and reliability analysis techniques applied to industrial, cyber-physical, and safety-critical case studies:

- **Fault Tree Analysis (FTA)** — top-down, deductive failure analysis
- **Event Tree Analysis (ETA)** — forward-looking accident progression analysis
- **Bayesian Networks (BN)** — probabilistic graphical models for causal reasoning under uncertainty

Each technique is presented at multiple complexity levels (simple, medium, complex) and applied to real-world inspired case studies including chemical plants, smart hospitals, autonomous vehicles, railway signalling, water treatment plants, infusion pumps, oil pipelines, and smart power grids.

## Repository Structure

```
.
├── README.md
├── requirements.txt
│
├── FTA_Simple_Autonomous_Vehicle.ipynb         # FTA - Autonomous Vehicle Emergency Stop Failure
├── FTA_mediumlevel_case_study.ipynb            # FTA - Smart Infusion Pump (medium)
├── FTA_Chemical plant_casestudy.ipynb          # FTA - Chemical Plant (complex)
├── FTA_Library_Autonomous_Vehicle_.ipynb       # FTA using pfta library - AV stopping failure
├── FTA_Library_Chemical_Plant_.ipynb           # FTA using pfta library - Chemical plant cyber-safety
├── FTA_library_Smart_Infusion_Pump.ipynb       # FTA using pfta library - Smart infusion pump
│
├── ETA_Railway_Signal_Failure.ipynb            # ETA - Railway Signal Failure at a Junction
├── ETA_mediumlevel.ipynb                       # ETA - Cyber-Induced Valve Control Failure (Oil Pipeline)
├── ETA_complexlevel.ipynb                      # ETA - Cyber-Induced Failure in Smart Power Grid Substation
│
├── BN_Smart_Hospital.ipynb                     # BN - Smart Hospital Monitoring System
├── BN_Smart_Water_Treatment.ipynb              # BN - Smart Water Treatment Plant Cyber-Safety
└── BNComplexlevel.ipynb                        # BN - Cyber-Physical Risk in Chemical Processing Plant
```

## Notebook Summaries

### Fault Tree Analysis (FTA)

| Notebook | Case Study | Level |
|---|---|---|
| `FTA_Simple_Autonomous_Vehicle.ipynb` | Autonomous vehicle emergency-stop failure | Simple |
| `FTA_mediumlevel_case_study.ipynb` | Smart infusion pump failure | Medium |
| `FTA_Chemical plant_casestudy.ipynb` | Chemical plant top-event failure | Complex |
| `FTA_Library_Autonomous_Vehicle_.ipynb` | Autonomous vehicle stopping failure (uses `pfta` library) | Library-based |
| `FTA_Library_Chemical_Plant_.ipynb` | Chemical plant cybersecurity-safety failure (uses `pfta`) | Library-based |
| `FTA_library_Smart_Infusion_Pump.ipynb` | Smart infusion pump cybersecurity-safety failure (uses `pfta`) | Library-based |

### Event Tree Analysis (ETA)

| Notebook | Case Study | Level |
|---|---|---|
| `ETA_Railway_Signal_Failure.ipynb` | Railway signal failure at a junction | Simple |
| `ETA_mediumlevel.ipynb` | Cyber-induced valve control failure in an oil pipeline pumping station | Medium |
| `ETA_complexlevel.ipynb` | Cyber-induced failure in a smart power grid substation (6 defensive layers) | Complex |

### Bayesian Networks (BN)

| Notebook | Case Study | Level |
|---|---|---|
| `BN_Smart_Hospital.ipynb` | Smart hospital monitoring failure leading to patient risk | Simple |
| `BN_Smart_Water_Treatment.ipynb` | Cyber-safety risk in a smart water treatment plant | Medium |
| `BNComplexlevel.ipynb` | Cyber-physical risk in a chemical processing plant (8 nodes, 10 edges) | Complex |

Each notebook includes the model construction, probability calculations, visual diagrams (event trees, fault trees, or DAGs), inference queries, summary tables, and an interpretation of the results.

## Requirements

- Python 3.9 or newer
- Jupyter Notebook or JupyterLab (or Google Colab)
- The system-level **Graphviz** binary (required by the Python `graphviz` wrapper used to render fault trees and event trees)

Install Graphviz on your system:

- **Windows:** Download the installer from [graphviz.org/download](https://graphviz.org/download/) and add the `bin` folder to your PATH
- **macOS:** `brew install graphviz`
- **Ubuntu / Debian:** `sudo apt-get install graphviz`

Then install the Python dependencies:

```bash
pip install -r requirements.txt
```

## Running the Notebooks

Clone the repository and launch Jupyter:

```bash
git clone https://github.com/<your-username>/<your-repo-name>.git
cd <your-repo-name>
pip install -r requirements.txt
jupyter notebook
```

Then open any of the `.ipynb` files and run the cells top to bottom.

You can also run any notebook directly in **Google Colab** — open the notebook on GitHub and click "Open in Colab", or upload the file at [colab.research.google.com](https://colab.research.google.com).

## Libraries Used

- **pandas** — result tables and data handling
- **matplotlib** — charts, icons, and plots
- **networkx** — graph construction and visualization
- **pgmpy** — Bayesian Network modelling and inference (`DiscreteBayesianNetwork`, `TabularCPD`, `VariableElimination`)
- **graphviz** — Python wrapper for rendering fault tree and event tree diagrams
- **pfta** — fault tree analysis library used in the FTA library-based notebooks
- **ipython** — for displaying images and rich output inside notebooks

## Notes

- The notebooks were originally developed and tested in Google Colab. When running locally, ensure the Graphviz binary is installed and accessible on your PATH, otherwise diagrams will not render.
- Some notebooks include `!pip install ...` cells — these are safe to run in Colab and harmless locally if dependencies are already installed via `requirements.txt`.

## Author

**Aromal**
Email: aromalmanu03@gmail.com

## License

This project is released under the MIT License. Feel free to use, modify, and share with attribution.
