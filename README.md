## Overview
This project addresses a significant challenge in the medical field: the accurate and timely detection of brain tumors from MRI images. Brain tumors can be life-threatening, and early detection is critical for improving patient outcomes and survival rates. However, the manual classification of brain tumors by radiologists is time-consuming and prone to human error, particularly in high-pressure environments. By leveraging convolutional neural networks (CNNs), this project aims to assist medical professionals in accurately identifying and classifying brain tumors into three types—glioma, meningioma, and pituitary tumors—as well as distinguishing these from normal brain tissue.

The utility of this model lies in its potential to serve as a decision-support tool in clinical settings. It can reduce the cognitive load on radiologists, speed up the diagnostic process, and ensure that even subtle indications of tumors are flagged for further examination. By integrating AI into diagnostic workflows, healthcare providers can improve diagnostic accuracy and potentially lower healthcare costs associated with extensive testing. This project is especially important in regions with limited access to specialized medical professionals, where an AI-driven tool could make a significant difference in patient care.


## Data Source
The dataset used in this project is sourced from Kaggle and contains MRI images categorized into four classes: glioma_tumor, meningioma_tumor, pituitary_tumor, and normal. Despite some limitations, such as class imbalance and a relatively small dataset size, the data proved to be effective in developing a binary classification model that can identify tumors with reasonable accuracy. The dataset’s class imbalance—where normal brain images are underrepresented compared to tumor images—posed a challenge for nontumor identification. Additionally the limited data size posed challenges for multiple classification, leading to models that struggled to differentiate between the different tumor types. However, for binary classification (tumor vs. non-tumor), the data was more suitable and enabled the creation of a model that performs well in identifying tumor cases, even if it struggles somewhat with normal cases.


## Stakeholders

**Medical Professionals:** Radiologists, neurologists, and oncologists can use this model as a decision-support tool, helping to identify and classify brain tumors more efficiently. This tool is particularly useful in reducing diagnostic errors and providing a second opinion in ambiguous cases.

**Healthcare Providers:** Hospitals and clinics can integrate this model into their diagnostic workflows to speed up the diagnosis process, potentially reducing costs associated with longer diagnostic procedures and improving patient throughput.

**Researchers:** The project provides a foundation for further research into AI-driven diagnostics, offering insights into the strengths and limitations of current models. Researchers can build on this work to develop more sophisticated models or to explore the application of AI in other areas of medical imaging.

**Patients:** While indirectly, patients benefit from faster, more accurate diagnoses. Early and accurate detection of tumors can lead to timely and effective treatment, which is crucial for improving survival rates and quality of life.


## Summary of Data Science Steps

1. **Binary Classification Preprocessing:**

- Directory Reorganization: The original dataset was organized into four main directories: glioma, meningioma, pituitary tumor, and normal. All images were moved and reorganized into two new directories: 'tumor' and 'nontumor.' This was crucial for setting up the binary classification task.

- Data Cleaning and Normalization: Images were resized and normalized to ensure consistency.

- Data Augmentation: Techniques such as rotation, zoom, and flip were applied to increase the diversity of the training data and help the model generalize better.

- Train-Validation-Test Split: The data was split into training, validation, and test sets, ensuring that each class was proportionally represented in each split.

2. **Binary Model Training and Validation:**

- Multiple CNN architectures were trained and tested, starting with a baseline model and progressively adding more layers, filters, and regularization techniques such as dropout.

3. **Binary Model Evaluation:**

- The best-performing model was evaluated on the holdout test set to confirm its effectiveness. Metrics such as recall, precision, and F1-score were calculated to assess the model’s performance in detecting tumor cases accurately.
  
4. **Multiclass Classification Preprocessing:**

- Directory Reorganization: The dataset was further reorganized into four directories: glioma_tumor, meningioma_tumor, pituitary_tumor, and normal. All images from the previous 'train', 'val', and 'test' directories were sorted into these new directories based on their file names. This reorganization was necessary for setting up the multiclass classification task.
  
- Data Cleaning and Normalization: Similar preprocessing steps were applied, but the focus shifted to preparing the data for distinguishing between three tumor types and normal brain tissue.

5. **Multiclass Model Training and Validation:**

- Multiple CNN models were trained and tested to classify images into four categories. However, the models faced significant challenges due to the dataset’s limitations, leading to lower accuracy and recall for some classes.

6. **Multiclass Model Evaluation:**

- The final multiclass model was evaluated, revealing difficulties in distinguishing between the different tumor types as well as the normal tissue. None of the models achieved sufficient accuracy for deployment, highlighting the need for further development.

  
## Final Model Performance on Evaluation Data
The final binary classification model achieved a test loss of 0.1526 and a test accuracy of 92.26%. It was particularly effective in identifying tumor cases, with a recall of 0.8684 and a precision of 0.8684, making it a reliable tool for assisting in tumor detection. However, the model struggled with non-tumor cases, achieving a recall of only 0.20. These metrics imply that while the model is effective in detecting tumors, it has limitations in distinguishing non-tumor cases from tumors, which could lead to false positives.

The implications of these metrics are significant. The high recall for tumor cases suggests that the model is well-suited for deployment in settings where missing a tumor diagnosis could have severe consequences. However, the lower precision for non-tumor cases indicates that the model may require further refinement to reduce the number of false positives. In practice, this model would be most useful as an initial screening tool, flagging potential tumor cases for further review by a specialist.


## Justification of Metrics and Final Model
Recall was prioritized as the most important metric because, in the context of brain tumor detection, it is crucial to minimize the number of false negatives. Missing a tumor diagnosis could delay treatment and negatively impact patient outcomes. Precision was the second most important metric, as it ensures that when the model predicts a tumor, it is likely correct, reducing unnecessary follow-up procedures.

The final binary CNN model was chosen based on its strong performance in recall and precision, particularly in detecting tumor cases. Its high recall rate makes it a valuable tool for ensuring that most tumors are detected early, which is critical for effective treatment. The model’s utility lies in its ability to assist radiologists by providing a reliable second opinion, especially in ambiguous cases, thereby enhancing the overall diagnostic process. While the model is not perfect, its integration into clinical workflows could significantly improve the speed and accuracy of brain tumor diagnosis.


## Repository Structure

- **data:** Directory containing the dataset and data link
- **notebooks:** Directory containing all reproducibility notebooks
- **.gitignore:** Git ignore file
- **README.md:** Project overview and instructions
- **brain_tumor_identification.ipynb:** Original notebook containing all data science steps
- **requirements.txt:** Python packages required to run the project


## Reproducibility Script

This section provides instructions for reproducing the results from this project. The following steps will guide you through setting up the environment, downloading the necessary data, and running the Jupyter notebooks in the correct order.

### Step 1: Environment Setup

1. **Clone the Repository:**

   Start by cloning the repository to your local machine:
   
   ```bash
   git clone https://github.com/agambino720/tumor_identification_model.git
   cd tumor_identification_model
   ```
2. **Create a Virtual Environment:**

Set up a virtual environment and activate it:

```bash
python -m venv env
source env/bin/activate  # On Windows use: .\env\Scripts\activate
```

Install Required Packages:

Install the necessary Python packages using the requirements.txt file:

```bash
pip install -r requirements.txt
```

### Step 2: Data Download

1. **Download the Dataset:**

Manually download the dataset from Kaggle using this link:

https://www.kaggle.com/datasets/thomasdubail/brain-tumors-256x256/data

2. **Extract the Dataset:**

Once downloaded, extract the dataset into the existing data/ directory in the repository: 

```bash
unzip path_to_your_downloaded_file.zip -d data/   #replace path_to_your_download with actual path
```

After extraction, ensure the dataset directory structure looks like this:

data/
   ├── glioma_tumor/
   ├── meningioma_tumor/
   ├── pituitary_tumor/
   └── normal/
   
### Step 3: Preprocess the Data for Binary Classification

1. **Preprocess the Data for Binary Classification:**

Run the following command to preprocess the data for binary classification:

```bash
jupyter nbconvert --to notebook --execute binary_preprocess_data.ipynb
```

### Step 4: Binary Model Training and Validation

1. **Train and Validate the Binary Classification Model:**

Run the following command to train and validate the binary classification model:

```bash
jupyter nbconvert --to notebook --execute binary_model_train_val.ipynb
```

### Step 5: Binary Model Evaluation

1. **Evaluate the Binary Classification Model:**

Run the following command to evaluate the binary classification model:

```bash
jupyter nbconvert --to notebook --execute binary_model_eval.ipynb
```

### Step 6: Preprocess the Data for Multiclass Classification

1. **Preprocess the Data for Multiclass Classification:**

Run the following command to preprocess the data for multiclass classification:

```bash
jupyter nbconvert --to notebook --execute multiclass_preprocess_data.ipynb
```

### Step 7: Multiclass Model Training and Validation

1. **Train and Validate the Multiclass Classification Model:**

Run the following command to train and validate the multiclass classification model:

```bash
jupyter nbconvert --to notebook --execute multiclass_model_train_val.ipynb
```

### Step 8: Multiclass Model Evaluation

1, **Evaluate the Multiclass Classification Model:**

Run the following command to evaluate the multiclass classification model:

```bash
jupyter nbconvert --to notebook --execute multiclass_model_eval.ipynb
```

## Links

**Data:**

- https://www.kaggle.com/datasets/thomasdubail/brain-tumors-256x256/data

**Presentation**

- https://docs.google.com/presentation/d/10hnycbJEGqjcC5EfjqJc9wBegxfJlWwF0jMu7nQ9ot4/edit?usp=sharing
