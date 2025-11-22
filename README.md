Vehicle Insurance MLOps Pipeline

This repository demonstrates a complete MLOps workflow for managing and deploying a machine learning pipeline on vehicle insurance data. It showcases end-to-end processes including data ingestion, validation, transformation, model training, cloud storage, deployment, and CI/CD automation.

Project Setup and Structure
1. Project Template

Run the template.py file to generate the initial project structure with all required folders and placeholder modules.

2. Package Management

Configure local package imports using:

setup.py

pyproject.toml

(Refer to crashcourse.txt for explanations.)

3. Virtual Environment and Dependencies
conda create -n vehicle python=3.10 -y
conda activate vehicle
pip install -r requirements.txt


Verify installed packages:

pip list

MongoDB Setup and Data Management
4. MongoDB Atlas Configuration

Create a new project on MongoDB Atlas.

Set up a free M0 cluster.

Create a database user and allow access from 0.0.0.0/0.

Copy the connection string for Python (replace <password>).

5. Uploading Data to MongoDB

Add dataset inside a folder named notebook.

Create mongoDB_demo.ipynb.

Use the notebook to insert data into MongoDB.

Verify uploaded data under Database → Browse Collections.

Logging, Exception Handling, and EDA
6. Logging and Exception Handling

Create logging and custom exception modules and test them using demo.py.

7. Exploratory Data Analysis and Feature Engineering

Perform EDA and feature engineering in dedicated notebooks before integrating the logic into the pipeline.

Data Ingestion Pipeline
8. Data Ingestion

Define MongoDB connection functions in configuration/mongo_db_connections.py.

Implement ingestion logic in:

data_access

components/data_ingestion.py

Update configuration files:

entity/config_entity.py

entity/artifact_entity.py

Run demo.py to test ingestion.

Set MongoDB environment variable:

Bash:

export MONGODB_URL="mongodb+srv://<username>:<password>..."


PowerShell:

$env:MONGODB_URL="mongodb+srv://<username>:<password>..."

Data Validation, Transformation, and Model Training
9. Data Validation

Define schema in config/schema.yaml.

Implement validation utilities in utils/main_utils.py.

10. Data Transformation

Implement transformation logic in components/data_transformation.py.

Add estimator utilities in entity/estimator.py.

11. Model Training

Write the training pipeline in components/model_trainer.py.

Reuse logic from estimator utilities.

AWS Setup for Model Storage and Deployment
12. AWS Configuration

Create an IAM user with AdministratorAccess.

Configure AWS credentials as environment variables:

export AWS_ACCESS_KEY_ID="YOUR_KEY"
export AWS_SECRET_ACCESS_KEY="YOUR_SECRET"


Update S3 bucket details in constants/__init__.py.

13. S3 Model Storage

Create an S3 bucket named my-model-mlopsproj in region us-east-1.

Create functions to upload and download models in:

src/aws_storage

entity/s3_estimator.py

Model Evaluation, Deployment, and API Pipeline
14. Model Evaluation and Pusher

Implement model evaluation.

Build model pusher to deploy the trained model.

Create the prediction pipeline.

Integrate the API using app.py.

15. Static and Template Directory

Add static and template folders for hosting the frontend interface.

CI/CD Pipeline with Docker, GitHub Actions, and AWS
16. Docker and GitHub Actions

Create:

Dockerfile

.dockerignore

Set GitHub Secrets:

AWS_ACCESS_KEY_ID

AWS_SECRET_ACCESS_KEY

AWS_DEFAULT_REGION

ECR_REPO

17. AWS EC2 and ECR

Launch an EC2 instance.

Install Docker on the instance.

Register the EC2 machine as a GitHub self-hosted runner.

18. Deployment

Expose port 5080 on EC2.

Access the deployed application using:

http://<public_ip>:5080

Additional Resources

Crash course for setup.py and pyproject.toml in crashcourse.txt

GitHub Secrets documentation for secure CI/CD integration

Project Workflow Summary

Data Ingestion
Data Validation
Data Transformation
Model Training
Model Evaluation
Model Deployment
CI/CD automation with Docker, GitHub Actions, AWS EC2, and Amazon ECR
