# AMR-Missing-Risk
A Modeling Approach to Estimating the True Mortality Burden of Antimicrobial Resistance : Quantifying the "Missing Risk"


Quantifying the Attributable Burden of AMR using AI
Project Description
This research initiative aims to quantify the "missing risk" associated with Antimicrobial Resistance (AMR) on patient mortality using a data-driven AI approach. Traditional methods may underestimate the true impact of AMR due to confounding factors. By developing and employing predictive models and counterfactual analysis, this project estimates the proportion of deaths in a synthetic patient population that can be directly attributed to AMR, while accounting for other significant risk factors.

Setup and Installation
This project requires Python and several libraries. It is highly recommended to use a virtual environment to manage dependencies.

Clone this repository:
git clone <repository_url>
cd <repository_name>
(Optional but recommended) Create and activate a virtual environment:
# Using venv
python -m venv venv
source venv/bin/activate  # On Windows, use `venv\Scripts\activate`

# Using conda
conda create -n amr-burden python=3.x
conda activate amr-burden
Install the required dependencies. A requirements.txt file should be available in the repository.
pip install -r requirements.txt
If the requirements.txt file is not present, you can install the dependencies manually:
pip install pandas numpy matplotlib seaborn scikit-learn xgboost joblib
Data
The project uses synthetic patient data for demonstration purposes. The primary data file is synthetic_patient_data.csv, and the processed data is saved as processed_patient_data.csv.

To run the notebook, ensure synthetic_patient_data.csv is in the same directory as the notebook file.

How to Run the Notebook
Make sure you have followed the Setup and Installation steps and have the data file (synthetic_patient_data.csv) in the correct location.
Open the Jupyter Notebook using the following command in your terminal from the project directory:
jupyter notebook
Your web browser should open with the Jupyter Notebook dashboard. Click on the notebook file (e.g., AMR_Mortality_Analysis.ipynb).
Run the cells sequentially from top to bottom. You can use the "Run" button or Shift+Enter. Pay attention to the markdown explanations and code outputs.
Key Findings
The analysis quantifies the comparative mortality burden of different risk factors within the synthetic patient population. Using counterfactual analysis with a trained AI model, the estimated Population Attributable Fraction (PAF) for each factor is determined.

Based on the final analysis (results from Step 5), the estimated PAFs are:

Risk Factor	Population Attributable Fraction (%)
Age (Above 18)	70.3
Comorbidities (Score > 0)	23.0
AMR (Resistant)	17.4
Smoking (Yes)	2.5
Specific Pathogens	-2.7
Interpretation: These results suggest that, in this synthetic dataset, AMR-resistant infections are a significant contributor to patient mortality, with an estimated PAF of 17.4%. While Age and Comorbidities show a higher attributable burden, AMR's impact is substantial and exceeds that of Smoking. The negative PAF for Specific Pathogens might indicate complex interactions or confounding not fully captured, or potentially a protective effect relative to the baseline pathogen mix in the counterfactual.

This analysis highlights the potential magnitude of the "missing risk" of AMR when assessed using a methodology that attempts to account for confounding.

Model Details
The champion model selected for the counterfactual analysis was the Logistic Regression model, which demonstrated the highest AUC-ROC score (0.7714) on the test set after incorporating Inverse Probability of Treatment Weighting (IPTW) during training. IPTW was used to mitigate potential confounding bias by weighting samples based on their propensity score (probability of having an AMR-resistant infection given other characteristics).

License
This project is licensed under the MIT License.

Contact
For questions or feedback, please open an issue on this GitHub repository.

