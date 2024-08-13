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
unzip path_to_your_downloaded_file.zip -d data/
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
