# Model Deployment 1

## Phase - ( 1 Making a model available through an API Endpoint using fastapi )

### (Given commands are for linux, find the correct command for your Operating System)

### 1. Create and activate a virtual environment

    python -m venv .venv
    source .venv/bin/activate

### 2. Create a project directory and move into it

    mkdir mlops-first-pipeline
    cd mlops-first-pipeline

### 3. Install Packages

    pip install -r requirements.txt

### 4. Implement a simple machine learning model

### 5. Train and save the model

    python train.py

### 6. Implement FastAPI and create endpoints

### 7. Start the server

    uvicorn main:app --reload

## Phase - 2 ( Virualization with Docker )

### Docker Commands

    docker ps
    docker ps -a

    docker build -t mlops-iris-image-cs .
    -t = tag name = name of the image

    docker run -d -p 8000:8000 --name mlops-cs-container mlops-iris-image-cs

## Phase - 3 ( Automated Testing and CI/CD with Github actions )

### Our Goal

Whenever we push our code to github, the system should automatically run the tests and build the Docker image. Later we will extend the same pipeline to publish the image and deploy it.

1. Developer pushes the code.
2. Github Actions starts the workflow.
3. Triggered by a push or pull request.
4. Run tests and validate the model API behaviour.
5. Build Image and verify Docker packaging.

### Part - 1: What are CI/CD ?

CI - Continous Integration - Automatically validates the code changes through tests and build checks.

CD - Continous Delivery - Keep changes ready to release, with production release potentially requiring approval

CD - Continous Deployment - Automatically releases changes to production when all required checks pass.

CD - Continous Development

### Automation Testing

Required Tools -

1. pytest
2. FastAPI TestClient
3. Github Actions

-- mlops
------ tests
---------- test_api.py
------ .github
---------- workflows
-------------- ci.yaml

Install 2 dependencies:

- pytest - It discovers and runs automated tests, report failures

- httpx - FastAPI TestClient uses HTTPX to simulate HTTP Requests to your application without requiring you to separate web server (It needs no real ports on the machine ?)

        pip install pytest httpx
        (Also add these in requirements.txt)

python -m pytest -v
