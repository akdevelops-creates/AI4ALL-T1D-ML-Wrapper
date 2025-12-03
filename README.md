# Tackling the "Taboo": An ML Solution for Foods That Break Standard T1D Therapy

### *A Predictive "Safety Net" for Type 1 Diabetes Management*

**Author:** Anthony Kerr  
**Program:** AI4ALL Ignite Accelerator (Portfolio Project)  
**Status:** Phase 1 Complete (Proof of Concept)

-----

## 📌 Project Overview

Standard Type 1 Diabetes (T1D) dosing fails on complex meals because it myopically focuses on carbohydrates. This project shifts the paradigm by training a machine learning **"wrapper"** to analyze the critical, overlooked impact of **fat, protein, and fiber**.

By accurately classifying "taboo" foods (like pizza, plantains, or rich pastas) as **High-Risk** before insulin delivery, this model serves as a predictive safety net for stable blood sugar where current treatments—whether manual injections or automated pumps—consistently fall short.

### The Core Problem

  * **Standard Therapy:** Relies on "Carb Counting," which assumes digestion is linear and predictable.
  * **The Reality:** High-fat and high-protein meals delay gastric emptying, causing a "delayed spike" 3–5 hours post-meal—long after standard insulin has peaked.
  * **The Result:** A dangerous glucose "rollercoaster" and immense mental burden ("Diabetes Distress") for patients.

-----

## 🧠 The Solution: Machine Learning "Wrapper"

Think of standard therapy as a car (it makes the moves). This model is the **GPS Navigator**.

It uses a **Random Forest Classification** algorithm to analyze the *full* nutritional context of a meal. It predicts whether a specific combination of macros will cause a delayed spike that standard math misses, outputting a simple, actionable signal:

  * 🟢 **Low Risk:** Proceed with standard dosing.
  * 🔴 **High Risk:** Intervention required (e.g., split bolus, extended delivery).

-----

## 📊 Data Source & Attribution

This project utilizes real-world longitudinal data from the **University of Manchester**.

  * **Dataset:** [T1D-UOM – A Longitudinal Multimodal Dataset of Type 1 Diabetes (V1.0.1)](https://zenodo.org/records/15169264)
  * **Repository:** [ManchesterCSCoordinatedDiabetesStudy](https://github.com/sharpic/ManchesterCSCoordinatedDiabetesStudy)
  * **Scope:** 16 individuals, data collected Oct 2023 – Aug 2024.
  * **Key Features Used:**
      * **Nutritional:** Carbohydrates, Fat, Protein, Fiber.
      * **Physiological:** Continuous Glucose Monitor (CGM) readings, Insulin (Bolus/Basal).

> **Attribution:** I gratefully acknowledge the creators of the T1D-UOM dataset for providing the granular nutritional data necessary to train this model.

-----

## ⚙️ Methodology

### 1\. Feature Engineering

We engineered specific features to capture the physiological complexity of digestion:

  * **Fat-to-Carb Ratio (FCR):** A key indicator of the "Pizza Effect" (delayed absorption).
  * **Protein-to-Carb Ratio (PCR):** Indicator of sustained glucose rise.
  * **Insulin On Board (IOB):** Calculated active insulin to prevent stacking errors.
  * **Glucose Rate of Change (RoC):** The dynamic trend of blood sugar pre-meal.

### 2\. Model Architecture

  * **Type:** Supervised Learning (Binary Classification)
  * **Algorithm:** **Random Forest Classifier**
  * **Why Random Forest?** It efficiently handles the non-linear, complex interactions between fat/protein and digestion significantly better than linear regression models. It is also robust against noise in self-reported food logs.

-----

## ⚠️ Ethical Considerations & Limitations (Responsible AI)

As part of the AI4ALL Responsible AI framework, explicitly acknowledging bias is critical:

1.  **Evaluation Bias (Population):** The model was trained on a small cohort of 16 individuals in Manchester, UK. The training data heavily favors Western diets.
2.  **Cultural Agnosticism vs. Reality:** While the *approach* (using macronutrients) is culturally agnostic, the *model* may underperform on culturally significant non-Western foods (e.g., high-fiber African or Caribbean dishes) if those specific macro-combinations were absent from the UK training set.
3.  **Proof of Concept:** This tool is currently a **Proof of Concept**. It is **not** a medical device and should not be used for active treatment decisions without retraining on a larger, more diverse dataset.

-----

## 🚀 Usage

### Prerequisites

  * Python 3.x
  * Jupyter Notebook
  * Libraries: `pandas`, `numpy`, `scikit-learn`, `matplotlib`, `seaborn`

### Installation

1.  Clone the repo:
    ```bash
    git clone https://github.com/YourUsername/AI4ALL-T1D-ML-Wrapper.git
    ```
2.  Install requirements:
    ```bash
    pip install -r requirements.txt
    ```
3.  Run the analysis notebook:
      * Open `T1D_ML_Wrapper_Analysis.ipynb` in Jupyter.

-----

## 🔮 Next Steps

  * **Phase 2 (March 2026):** Retrain model on diverse, international data to mitigate Evaluation Bias.
  * **Phase 3 (May 2026):** Develop a web-based MVP tool for user testing.
  * **Long-term:** Integrate with open-source artificial pancreas systems (like AndroidAPS/Loop) as a plugin "safety layer."

-----

*This project was created for the AI4ALL Ignite Accelerator.*
