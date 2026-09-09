\# ☁️ CloudTask Manager



A cloud-ready REST API built with \*\*Python Flask\*\* and deployed to \*\*Microsoft Azure App Service\*\* using an automated \*\*Azure DevOps CI/CD pipeline\*\*.



The project demonstrates practical DevOps concepts including application development, automated testing, CI/CD, artifact packaging, and cloud deployment.



\---



\## 🚀 Project Overview



\*\*CloudTask Manager\*\* is a lightweight task-management REST API that allows users to:



\* Check application status

\* Check application health

\* Retrieve tasks

\* Create new tasks

\* Validate API input

\* Run automated tests

\* Deploy automatically to Azure App Service



The application is designed as a practical demonstration of how a Python application can move from source code to a cloud-hosted production environment through an automated DevOps pipeline.



\---



\## 🏗️ Architecture



```text

&#x20;                   ┌─────────────────────┐

&#x20;                   │     Developer       │

&#x20;                   │                     │

&#x20;                   │  Python Flask App   │

&#x20;                   └──────────┬──────────┘

&#x20;                              │

&#x20;                              │ Git Push

&#x20;                              ▼

&#x20;                   ┌─────────────────────┐

&#x20;                   │    Azure DevOps     │

&#x20;                   │      Repos          │

&#x20;                   └──────────┬──────────┘

&#x20;                              │

&#x20;                              │ Trigger on main

&#x20;                              ▼

&#x20;                   ┌─────────────────────┐

&#x20;                   │  Azure Pipelines    │

&#x20;                   │                     │

&#x20;                   │  1. Python 3.12     │

&#x20;                   │  2. Install deps    │

&#x20;                   │  3. Run pytest      │

&#x20;                   │  4. Package ZIP     │

&#x20;                   │  5. Deploy          │

&#x20;                   └──────────┬──────────┘

&#x20;                              │

&#x20;                              │ Azure Service Connection

&#x20;                              ▼

&#x20;                   ┌─────────────────────┐

&#x20;                   │   Azure App Service │

&#x20;                   │                     │

&#x20;                   │   Linux Web App     │

&#x20;                   │      + Gunicorn     │

&#x20;                   └──────────┬──────────┘

&#x20;                              │

&#x20;                              ▼

&#x20;                   ┌─────────────────────┐

&#x20;                   │    CloudTask API    │

&#x20;                   │                     │

&#x20;                   │  /                 │

&#x20;                   │  /health           │

&#x20;                   │  /tasks             │

&#x20;                   └─────────────────────┘

```



\---



\## 🛠️ Technologies Used



| Technology        | Purpose                              |

| ----------------- | ------------------------------------ |

| Python            | Application development              |

| Flask             | REST API framework                   |

| Pytest            | Automated testing                    |

| Gunicorn          | Production WSGI server               |

| Microsoft Azure   | Cloud platform                       |

| Azure App Service | Application hosting                  |

| Azure DevOps      | Source control and CI/CD             |

| Azure Pipelines   | Automated build, test and deployment |

| Git               | Version control                      |

| GitHub            | Public project portfolio             |



\---



\## 📡 API Endpoints



\### Home



```http

GET /

```



Returns the application status.



Example response:



```json

{

&#x20; "message": "Welcome to CloudTask Manager",

&#x20; "status": "running"

}

```



\---



\### Health Check



```http

GET /health

```



Used to verify that the application is healthy and responding.



Example:



```json

{

&#x20; "status": "healthy"

}

```



\---



\### Get Tasks



```http

GET /tasks

```



Returns the current task list.



Example:



```json

\[

&#x20; {

&#x20;   "id": 1,

&#x20;   "title": "Learn Azure DevOps",

&#x20;   "completed": false

&#x20; }

]

```



\---



\### Create Task



```http

POST /tasks

```



Creates a new task.



Example request:



```json

{

&#x20; "title": "Deploy application to Azure"

}

```



Example response:



```json

{

&#x20; "id": 2,

&#x20; "title": "Deploy application to Azure",

&#x20; "completed": false

}

```



If the title is missing, the API returns:



```http

400 Bad Request

```



with:



```json

{

&#x20; "error": "Task title is required"

}

```



\---



\## 🔄 CI/CD Pipeline



The project uses \*\*Azure Pipelines\*\* to automate the application delivery process.



The pipeline is triggered whenever changes are pushed to the `main` branch.



\### Pipeline workflow



```text

Git Push

&#x20;  │

&#x20;  ▼

Trigger Azure Pipeline

&#x20;  │

&#x20;  ▼

Install Python 3.12

&#x20;  │

&#x20;  ▼

Install Dependencies

&#x20;  │

&#x20;  ▼

Run Pytest

&#x20;  │

&#x20;  ├── Tests Failed ──► Pipeline Stops

&#x20;  │

&#x20;  ▼

Create ZIP Deployment Package

&#x20;  │

&#x20;  ▼

Deploy to Azure App Service

&#x20;  │

&#x20;  ▼

Application Running in Azure

```



\### Pipeline stages



\#### 1. Configure Python



The pipeline uses Python 3.12.



\#### 2. Install dependencies



Dependencies are installed from:



```text

requirements.txt

```



\#### 3. Run automated tests



The pipeline executes:



```bash

python -m pytest -v

```



This ensures that application changes are tested before deployment.



\#### 4. Create deployment package



The application is packaged into a ZIP artifact.



\#### 5. Deploy to Azure



The `AzureWebApp@1` task deploys the package to Azure App Service using an Azure service connection.



The application is started using Gunicorn:



```bash

gunicorn --bind=0.0.0.0 --timeout 600 app:app

```



\---



\## 🧪 Automated Testing



The project includes automated tests using \*\*Pytest\*\*.



Current tests validate:



\* Home endpoint

\* Health endpoint

\* Tasks endpoint

\* HTTP response status codes

\* JSON response structure



Run the tests locally:



```bash

python -m pytest -v

```



Expected result:



```text

3 passed

```



\---



\## 📁 Project Structure



```text

cloudtask-manager/

│

├── app.py

├── requirements.txt

├── azure-pipelines.yml

├── README.md

├── .gitignore

│

└── tests/

&#x20;   └── test\_app.py

```



\### File description



\*\*`app.py`\*\*



Main Flask application containing the REST API endpoints and task logic.



\*\*`requirements.txt`\*\*



Python dependencies:



```text

Flask

pytest

gunicorn

```



\*\*`tests/test\_app.py`\*\*



Automated API tests.



\*\*`azure-pipelines.yml`\*\*



Azure DevOps CI/CD pipeline configuration.



\*\*`.gitignore`\*\*



Prevents local environments, credentials, environment variables, and unnecessary files from being committed.



\---



\## 🔐 Security Practices



The repository follows basic security practices for a cloud DevOps project.



Sensitive/local files are excluded from source control, including:



```text

.env

.azure/

.venv/

.vscode/

\_\_pycache\_\_/

.pytest\_cache/

```



Azure authentication is handled through an Azure DevOps service connection rather than hard-coding credentials in the application.



\---



\## ☁️ Azure Deployment



The application is hosted on:



\*\*Azure App Service — Linux Web App\*\*



The deployment process is automated through Azure DevOps.



\### Deployment flow



```text

Developer

&#x20;   │

&#x20;   ▼

Git Repository

&#x20;   │

&#x20;   ▼

Azure Pipeline

&#x20;   │

&#x20;   ├── Build

&#x20;   ├── Test

&#x20;   ├── Package

&#x20;   └── Deploy

&#x20;         │

&#x20;         ▼

&#x20;   Azure App Service

```



\---



\## 💻 Run Locally



\### 1. Clone the repository



```bash

git clone https://github.com/SAM517046/CloudTask-manager.git

cd CloudTask-manager

```



\### 2. Create a virtual environment



Windows PowerShell:



```powershell

python -m venv .venv

```



Activate it:



```powershell

.\\.venv\\Scripts\\Activate.ps1

```



\### 3. Install dependencies



```powershell

pip install -r requirements.txt

```



\### 4. Run tests



```powershell

python -m pytest -v

```



\### 5. Start the application



```powershell

python app.py

```



The application runs on:



```text

http://localhost:8000

```



\---



\## 📌 DevOps Skills Demonstrated



This project demonstrates hands-on experience with:



\* Python application deployment

\* REST API development

\* Git version control

\* GitHub repository management

\* Azure DevOps

\* Azure Pipelines

\* CI/CD automation

\* Automated testing

\* Build artifact creation

\* Azure App Service

\* Azure service connections

\* Linux-based cloud hosting

\* Gunicorn

\* Environment and secret management

\* Deployment troubleshooting



\---



\## 🎯 Project Objective



The primary objective of this project was to understand and implement a complete application delivery workflow:



```text

Develop

&#x20;  ↓

Commit

&#x20;  ↓

Push

&#x20;  ↓

Build

&#x20;  ↓

Test

&#x20;  ↓

Package

&#x20;  ↓

Deploy

&#x20;  ↓

Run on Azure

```



This project demonstrates how DevOps practices can automate the journey from source code to a cloud-hosted application.



\---



\## 🔮 Future Improvements



Potential improvements include:



\* Add persistent database storage

\* Add task update and delete operations

\* Add authentication and authorization

\* Add Docker containerization

\* Add Infrastructure as Code using Terraform

\* Add monitoring with Azure Application Insights

\* Add deployment environments such as Dev / Staging / Production

\* Add approval gates for production deployment

\* Add API documentation using Swagger/OpenAPI

\* Add centralized logging

\* Add automated security scanning



\---



\## 👨‍💻 Author



\*\*Mohammad Anees Shaik\*\*



Cloud \& DevOps Engineer



\### GitHub



https://github.com/SAM517046



\---



\## ⭐ Project Highlights



> Flask REST API → Automated Testing → Azure DevOps CI/CD → Azure App Service



This project demonstrates a practical end-to-end cloud deployment workflow using Microsoft Azure and DevOps automation.



