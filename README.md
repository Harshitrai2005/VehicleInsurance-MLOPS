 # ********** MLOPS PROJECT OVERVIEW **********

This project is built to demonstrate a complete and production-ready MLOps pipeline for handling vehicle insurance data. My goal here is to present a structured workflow that recruiters and visitors can easily follow. The project covers everything from setting up the environment, processing data, building the ML pipeline, deploying the model, and automating the backend using CI/CD.

 # ********** PROJECT SETUP AND STRUCTURE **********

Step 1: Project Template
I begin by running the template.py file, which creates the initial project layout and all required folders.

Step 2: Local Package Setup
The setup.py and pyproject.toml files are configured so that local modules can be imported smoothly. The crashcourse.txt file contains supporting notes for these.

Step 3: Virtual Environment and Dependencies
I create a dedicated environment and install required packages using requirements.txt:

conda create -n vehicle python=3.10 -y
conda activate vehicle
pip install -r requirements.txt

I verify the installations using:
pip list

# ********** MONGODB SETUP AND DATA MANAGEMENT **********

Step 4: MongoDB Atlas Setup
I register on MongoDB Atlas, create a project, and set up a free M0 cluster. After creating the username and password and allowing access from any IP (0.0.0.0/0), I copy the Python connection string (replacing <password> with my actual password).

Step 5: Uploading Data to MongoDB
Inside a folder named notebook, I place the dataset and create a notebook file called mongoDB_demo.ipynb. Using this notebook, I insert data into MongoDB and verify it through the Browse Collections section in Atlas.

********** LOGGING, EXCEPTION HANDLING, AND EDA **********

Step 6: Logging and Exception Modules
I build custom logging and exception handling modules and test them using a simple demo.py file.

Step 7: EDA and Feature Engineering
I perform feature analysis and engineering in the EDA & Feature Engineering notebook to prepare the data for ingestion and transformation.

# ********** DATA INGESTION PIPELINE **********

Step 8: Building Data Ingestion
I define MongoDB connection functions inside configuration.mongo_db_connections.py.
The ingestion components are developed inside:

data_access

components.data_ingestion.py

I also update the ingestion configuration details in:

entity/config_entity.py

entity/artifact_entity.py

After setting the MongoDB environment variable, I run demo.py to verify ingestion.

Setting MongoDB URL as environment variable:

For Bash:
export MONGODB_URL="mongodb+srv://<username>:<password>...."

For PowerShell:
$env:MONGODB_URL = "mongodb+srv://<username>:<password>...."

On Windows, these can also be set using system environment variable settings.

# ********** DATA VALIDATION, TRANSFORMATION, AND MODEL TRAINING **********

Step 9: Data Validation
I define the validation schema in config.schema.yaml and write the validation utilities inside utils.main_utils.py.

Step 10: Data Transformation
The transformation logic is implemented in components.data_transformation.py.
An estimator.py file is added under the entity folder.

Step 11: Model Training
Using the estimator logic, I build the actual training workflow inside components.model_trainer.py.

********** AWS SETUP FOR MODEL STORAGE AND DEPLOYMENT **********

Step 12: AWS Configuration
I log in to AWS, create an IAM user with AdministratorAccess, and set the AWS keys as environment variables.

For Bash:
export AWS_ACCESS_KEY_ID="YOUR_AWS_ACCESS_KEY_ID"
export AWS_SECRET_ACCESS_KEY="YOUR_AWS_SECRET_ACCESS_KEY"

I prepare an S3 bucket by adding access details in constants.init.py.

Step 13: Model Evaluation and S3 Storage
I create an S3 bucket named my-model-mlopsproj in the us-east-1 region.
Then I write code inside src.aws_storage and entity/s3_estimator.py to handle model uploads and downloads.

# ********** MODEL EVALUATION, PUSHER, AND PREDICTION PIPELINE **********

Step 14: Deployment Pipeline Components
I build the evaluation and pusher components, and then develop the prediction pipeline.
The app.py file is set up to expose model predictions through an API.

Step 15: Static and Template Folders
I add the static and template directories for the web interface.

# ********** CICD SETUP USING DOCKER, GITHUB ACTIONS, AND AWS **********

Step 16: Docker and GitHub Actions
I write the Dockerfile and .dockerignore.
GitHub Actions are configured using secrets for:

AWS_ACCESS_KEY_ID

AWS_SECRET_ACCESS_KEY

AWS_DEFAULT_REGION

ECR_REPO

Step 17: EC2 and ECR Setup
I launch an EC2 instance and install Docker on it.
This EC2 machine is added as a self-hosted runner for GitHub Actions.

Step 18: Deploying the Final Application
I open port 5080 on the EC2 instance.
The application becomes accessible at:
http://<public_ip>:5080

# ********** ADDITIONAL NOTES **********


crashcourse.txt contains a short guide on setup.py and pyproject.toml.

GitHub Secrets ensure secure storage of AWS authentication details.

# ********** COMPLETE WORKFLOW SUMMARY **********

Data Ingestion ,
Data Validation ,
Data Transformation, 
Model Training ,
Model Evaluation ,
Model Deployment ,
CI/CD using GitHub Actions, Docker, AWS EC2, and ECR
