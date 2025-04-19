# H1B Visa Approval Prediction Web Application

Welcome to the **H1B Visa Approval Prediction** project! This repository contains a Streamlit-based web application that predicts the probability of approval for H1B visa applications using a pre-trained Random Forest classifier model. The app provides an interactive interface for users to input relevant visa application details and receive an approval likelihood prediction.

---

## Table of Contents

- [Project Overview](#project-overview)  
- [Features](#features)  
- [Installation](#installation)  
- [Usage](#usage)  
- [File Structure](#file-structure)  
- [Technical Details](#technical-details)  
- [Contributing](#contributing)  
- [License](#license)  

---

## Project Overview

The H1B visa application process can be complex and uncertain. This project aims to assist applicants and employers by providing a data-driven prediction of visa approval chances based on historical application data. The core of the application is a machine learning model trained on past H1B visa data, which is integrated into a user-friendly Streamlit web app.

---

## Features

- **Interactive User Interface:**  
  Users can select company name, SOC name, job title, state, city, and input salary to get predictions.

- **Dynamic Dropdowns:**  
  City options dynamically update based on the selected state to ensure relevant choices.

- **Probability Output:**  
  The app displays the probability of visa approval or rejection, helping users understand the likelihood of success.

- **Background Image:**  
  The app includes a visually appealing background image for enhanced user experience.

---

## Installation

1. **Clone the repository:**

   ```bash
   git clone https://github.com/pratikkanade/ML_project_h1b_visa_approval_predictions.git
   cd ML_project_h1b_visa_approval_predictions
   ```

2. **Create and activate a virtual environment (optional but recommended):**

   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. **Install required packages:**

   ```bash
   pip install -r requirements.txt
   ```

4. **Ensure the following files are present in the root directory:**

   - `visapred.py` (Streamlit app script)  
   - `h1b_prediction_model_rf2.pk` (Pre-trained Random Forest model)  
   - `step1_tab.csv` (Historical H1B visa application data)  

---

## Usage

Run the Streamlit app with the following command:

```bash
streamlit run visapred.py
```

This will open the web application in your default browser. Follow the on-screen instructions:

1. Select the **Company Name**, **SOC Name**, and **Job Title** from dropdown menus.
2. Select the **State**; the **City** dropdown will update accordingly.
3. Enter the **Salary** as a numeric input.
4. Click the **Predict** button to see the visa approval probability.

---

## File Structure

- `visapred.py` — Main Streamlit application script implementing the UI and prediction logic.  
- `h1b_prediction_model_rf2.pk` — Serialized Random Forest classifier model used for predictions.  
- `step1_tab.csv` — Dataset containing historical H1B visa application records used for categorical encoding and dropdown population.  
- `Notebook.ipynb` — Jupyter notebook (optional) containing exploratory data analysis and model training steps.

---

## Technical Details

### Model Loading

- The app loads a pre-trained Random Forest classifier from `h1b_prediction_model_rf2.pk` using Python's `pickle` module.
- This model predicts visa approval based on encoded categorical inputs and salary.

### Data Preparation

- Reads `step1_tab.csv` to extract categorical columns: `EMPLOYER_NAME`, `SOC_NAME`, `JOB_TITLE`, `STATE`, and `CITY`.
- Converts these columns to pandas categorical types.
- Creates dictionaries mapping category indices to category names for encoding user inputs and populating dropdown menus.

### Prediction Functions

- `predict_note_authentication(company_name, soc_name, job_title, salary, city, state)`:  
  Returns the predicted class label (approved or rejected) based on encoded inputs.

- `predict_probability(company_name, soc_name, job_title, salary, city, state)`:  
  Returns the probability scores for each class, enabling display of approval likelihood.

### Streamlit User Interface

- The app title is set to **"H1B Visa Prediction"**.
- A background image is embedded using base64 encoding for enhanced aesthetics.
- The layout consists of two columns:
  - **Column 1:** Dropdowns for Company Name, SOC Name, and Job Title.
  - **Column 2:** Dropdown for State, dynamically filtered City dropdown, and numeric input for Salary.
- The **Predict** button triggers the prediction process and displays results.

### Output Display

- Upon prediction, the app shows the probability of visa approval or rejection as a success message.
- The model outputs a binary classification with associated probabilities, helping users gauge their application's chances.

---

## Contributing

Contributions are welcome! Please fork the repository and submit pull requests for improvements or bug fixes. For major changes, open an issue first to discuss your ideas.

---

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

---

Thank you for exploring the H1B Visa Approval Prediction app! We hope it provides valuable insights into your visa application process. For questions or support, please open an issue in the repository.