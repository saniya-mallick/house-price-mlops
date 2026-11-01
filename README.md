# \# house-price-mlops

# 

# A sample MLOps project that predicts house sale prices from property features. This repository documents the full MLOps lifecycle and the Git branching strategy used to manage it.

# 

# \## Project Overview

# 

# \- \*\*Problem:\*\* Predict the sale price of a house (regression).

# \- \*\*Input features:\*\* Floor area, number of bedrooms, number of bathrooms, age of the house and location.

# \- \*\*Target:\*\* Sale price.

# \- \*\*Planned model:\*\* Random Forest Regressor, compared against a linear regression baseline.

# \- \*\*Planned tools:\*\* scikit-learn, MLflow, FastAPI, Docker, Git/GitHub.

# 

# \## Branching Strategy

# 

# | Branch | Purpose |

# |---|---|

# | `main` | Stable, release-ready code only |

# | `dev` | Integration branch where finished features are combined and tested |

# | `feature/\*` | Short-lived branches for one isolated change |

# 

# Workflow: `feature/\*` -> `dev` -> `main`, using merge commits so the history stays visible.

# 

# \## MLOps Lifecycle

# 

# 1\. \*\*Problem definition:\*\* Estimate house prices to support buyers, sellers and agents. Success is measured by low prediction error (RMSE and MAE) and a high R2 score.

# 2\. \*\*Data collection:\*\* Gather property listings with the features above, for example from a public housing dataset. Store the raw data unchanged.

# 3\. \*\*Data validation:\*\* Check for missing values, duplicates, impossible values (negative area or price) and outliers. Validate the schema before training.

# 4\. \*\*Feature engineering:\*\* Handle missing values, encode location, scale numeric features, and create new features such as price per square foot or house age. Split into train and test sets with a fixed random seed.

# 5\. \*\*Model training:\*\* Train a baseline linear regression and a Random Forest Regressor. Tune hyperparameters and track every run.

# 6\. \*\*Evaluation:\*\* Compare models on the test set using RMSE, MAE and R2. Select the best model and record the results.

# 7\. \*\*Packaging:\*\* Save the trained model and preprocessing steps together, pin dependencies in `requirements.txt`, and describe the runtime in a Dockerfile.

# 8\. \*\*Deployment:\*\* Serve the model through a FastAPI endpoint (`POST /predict`) running inside a Docker container.

# 9\. \*\*Monitoring:\*\* Track request volume, latency, prediction errors and data drift between live data and training data.

# 10\. \*\*Retraining:\*\* Retrain when new data arrives or performance drops. Each change goes through `feature/\*` -> `dev` -> `main` and is compared against the current model before release.

# 

# \## Planned Project Structure

# 

# house-price-mlops/

# \- data/ (raw and processed data)

# \- src/ (training and prediction code)

# \- app.py (FastAPI service)

# \- Dockerfile

# \- requirements.txt

# \- README.md

# 

# \## Reproducibility

# 

# 1\. Clone the repository and create a virtual environment.

# 2\. Install dependencies with `pip install -r requirements.txt`.

# 3\. Run the training script and review the metrics in MLflow.

# 4\. Start the API with `uvicorn app:app --port 8000`.

# 5\. Or build and run the Docker image.

# 

# Note: this repository documents the lifecycle of a sample project. The code files listed above are the planned structure.

