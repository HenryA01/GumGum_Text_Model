# GumGum Multi-Label Text Classification Model

## Project Overview

This project is a multi-label text classification model developed for GumGum, aimed at categorizing text transcripts based on specific content guidelines. Given two datasets, `prod_silver.csv` for training and `bbkpi_gold.csv` for testing, this project includes data cleaning, label correction using the GPT API, and model retraining for accurate classification performance.

### Objectives and Goals

The main objective of this project is to create an efficient and accurate model to classify text into specific content categories such as profanity, hate speech, adult content, and more. This classification helps improve content safety by identifying and filtering sensitive content in textual data. The project aims to achieve high performance on important metrics like F1 Micro and F1 Macro scores.

### Methodology

- **Data Collection and Preprocessing**: The initial training data (`prod_silver.csv`) required cleaning due to inaccurate labels. A GPT-based script was used to fill and correct labels in this dataset.
- **Model Training**: A transformer-based model was retrained using the cleaned data. The testing dataset (`bbkpi_gold.csv`) with verified human labels was used to evaluate the model’s performance.
- **Tools and Libraries**: Key libraries include Hugging Face Transformers, scikit-learn, and pandas for data manipulation, model training, and evaluation.

### Results and Key Findings

After data cleaning and model retraining, we observed significant improvements in key metrics:

- **F1 Micro** improved by approximately 39.67%.
- **F1 Macro** improved by approximately 38.88%.
- **Accuracy** showed a slight decrease of approximately 5.79%.

These results indicate that cleaning the training data had a substantial positive impact on the model's classification performance for specific metrics, enhancing its ability to detect sensitive content.

### Potential Next Steps

Future improvements could include:

- **Hyperparameter Tuning**: Further adjustments to improve accuracy and F1 scores.
- **Experimentation with Different Models**: Trying other transformer architectures.
- **Deployment**: Deploying the model as an API for real-time content moderation applications.
- **Further Data Augmentation**: Expanding training data with more accurate labels.

---

## Table of Contents

1. [Project Overview](#project-overview)
2. [Data Description](#data-description)
3. [Cleaning the Data](#cleaning-the-data)
4. [Using the Model](#using-the-model)
5. [Performance Metrics](#performance-metrics)
6. [Performance Improvement](#performance-improvement)
7. [Installation and Usage](#installation-and-usage)

---

## Data Description

- `prod_silver.csv`: This CSV file is the training data. It includes potentially incorrect labels that need to be cleaned and verified.
- `bbkpi_gold.csv`: This CSV file is the testing data, containing verified human labels.

The data contains the following columns:

- **Column 1**: Text transcript (the content to classify)
- **Column 2**: "Obscenity and Profanity, including language, gestures, and explicitly gory, graphic or repulsive content intended to shock and disgust"
- **Column 3**: "Safe"
- **Column 4**: "Death, Injury or Military Conflict"
- **Column 5**: "Arms and Ammunition"
- **Column 6**: "Debated Sensitive Social Issues"
- **Column 7**: "Hate Speech & Acts of aggression"
- **Column 8**: "Adult & Explicit Sexual Content"
- **Column 9**: "Crime & Harmful acts to individuals and Society and Human Right Violation"
- **Column 10**: "Illegal Drugs/Tobacco/e-cigarettes/Vaping/Alcohol"

## Cleaning the Data

To ensure accurate labels in the training data, the file `prod_silver.csv` needs to be cleaned. A script utilizing the GPT API (`GPT_Filling_Empty_Labels.ipynb` in the `Scripts_Used` folder) automates this process by generating labels based on the text content.

## Using the Model

After data cleaning, retrain the model with the new labels by following these steps:

1. Download the repository.
2. Review `Final_Cleaned_Data.xlsx` and perform any additional cleaning if needed.
3. Use `GPT_Filling_Empty_Labels.ipynb` to automatically fill missing labels based on the `Empty_Labels_Data.xlsx` file.
4. Use `GumGum_Latest_Model.ipynb` to train the model on the cleaned data, specifying:

   - `prod_silver_df`: the newly cleaned data.
   - `bbkpi_df`: the test data in `bbkpi_gold.csv`.

5. Adjust hyperparameters and select the desired transformer model in `GumGum_Latest_Model.ipynb`.

## Performance Metrics

The model outputs the following metrics:

- Training Loss
- Validation Loss
- **F1 Micro**: Important for evaluating overall classification performance.
- **F1 Macro**: Evaluates performance across classes.
- **Accuracy**: Measures overall prediction correctness.

Focus on F1 Micro, F1 Macro, and Accuracy to assess model performance.

## Performance Improvement

The data cleaning process significantly improved the model's performance, as shown below:

1. **F1 Micro**:

   - Original: 0.238849
   - Cleaned: 0.333725
   - Percentage Improvement: ~39.67%

2. **F1 Macro**:

   - Original: 0.201026
   - Cleaned: 0.279202
   - Percentage Improvement: ~38.88%

3. **Accuracy**:
   - Original: 0.623134
   - Cleaned: 0.587065
   - Percentage Decrease: ~5.79%

### Summary

- F1 Micro improved by approximately 39.67%.
- F1 Macro improved by approximately 38.88%.
- Accuracy decreased by approximately 5.79%.

---

## Installation and Usage

1. **Clone the Repository**:

   ```bash
   git clone https://github.com/fulati/GumGum_Text_Classification_Model.git
   ```

2. **Install Dependencies**:

   ```bash
   pip install -r requirements.txt
   ```

3. Inspect `Final_Cleaned_Data.xlsx` and clean as necessary.

4. **Run the Data Cleaning Script**:

   - Execute `GPT_Filling_Empty_Labels.ipynb` in `Scripts_Used` to clean and fill missing labels.

5. **Train the Model**:

   - Open `GumGum_Latest_Model.ipynb`, adjust data paths for cleaned and test data, and run the notebook to train and evaluate the model.

6. **Evaluate the Performance**:
   - Review metrics and visualizations to assess model effectiveness.

---

## Contributing

Contributions are welcome! To contribute:

1. Fork this repository.
2. Create a new branch (`git checkout -b feature-branch`).
3. Commit your changes (`git commit -m 'Add new feature'`).
4. Push to the branch (`git push origin feature-branch`).
5. Open a pull request.

Please follow the coding guidelines and ensure your code is tested.

## License

This project is licensed under the Apache License 2.0 - see the [LICENSE](LICENSE) file for details.

## Credits and Acknowledgments

- **Developed by**: Fulati Aizihaer
- **Special Thanks**: To GumGum for providing the datasets and support.
- **Libraries Used**: Hugging Face Transformers, scikit-learn, pandas.

---

This should cover everything needed to get started with the project. Happy coding!
