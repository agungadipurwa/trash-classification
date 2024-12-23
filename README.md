# Trash Classification

Connect with me on social media and explore my work:

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-blue?style=flat-square&logo=linkedin)](https://www.linkedin.com/in/agungadipurwa)
[![GitHub](https://img.shields.io/badge/GitHub-Follow-181717?style=flat-square&logo=github)](https://github.com/agungadipurwa)


## About The Project

## Dataset
[Gary Thung - Trashnet](http://www.github.com/garythung/trashnet)

## Getting Started

This will help you better understand how you may be able to give instructions on reproducing projects locally on your own.
Also helps you to automate model development using `Github Action`, model versioning and tracking using `wandb.ai`

## Installation (Local)
Follow these steps to clone this repository and install the required dependencies.
1. Clone the repository:
   ```bash
   git clone https://github.com/yourusername/your-repo.git
   cd your-repo
   ```
2. Create and activate a virtual environment (recommended):
   ```bash
   python -m venv venv
   source venv/bin/activate       # On macOS/Linux
   # or
   venv\Scripts\activate          # On Windows
   ```

3. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

## GitHub Actions Workflow (Automation)
This repository uses a GitHub Actions workflow to automatically run `create_wandb_dataset.ipynb` or `modeling.ipynb` under certain conditions.

### How It Works
1. The workflow definition is in `.github/workflows/autodataset_version.yaml` and `github/workflows/automodeling.yaml`.
2. It is triggered on push events either create_wandb_dataset.ipynb and modeling.ipynb changes.
3. It sets up Python 3.10.11, installs dependencies, and executes modeling.ipynb via nbconvert.
4. The executed notebook is saved as create_wandb_dataset.ipynb and executed_modeling.ipynb (or any name you configure).

   ```
   - name: Export GitHub secret to env
        run: |
          echo "DATA_URL=${{ secrets.DATA_URL }}" >> $GITHUB_ENV
          echo "WANDB_API_KEY=${{ secrets.WANDB_API_KEY }}" >> $GITHUB_ENV
          echo "DATASET_DICT=${{ secrets.DATASET_DICT }}" >> $GITHUB_ENV
   ```
### Result
1. Dataset versioning on wandb.ai
2. Model versioning on wandb.ai

## Additional insights
1. The data contain imbalance label distribution with label trash as the minority. So, need more dataset on that label to make that data pretty good.
2. The data maybe have issue about the trash label that maybe has an image that resembles another image, that can impact the bias with the classification.
