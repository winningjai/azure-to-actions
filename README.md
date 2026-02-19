# Introduction:

This project explains steps to create a sample Azure devops repository and pipelines. Then migrate it to GitHub repository and actions. 

This project has 3 stages namely: - 

    1. Create Azure Devops repository and pipelines.
    2. Migrate Azure repo to github  
    3. Migrate pipelines using github cli and run pipelines as github actions 

## 1, Pipeline creation

Follow the steps below to create azure devops pipeline. 
- Go to [Azure Developer portal](https://dev.azure.com) and create an organization 
- Once done click on new projects
  <img width="1911" height="212" alt="Screenshot from 2026-02-18 15-11-45" src="https://github.com/user-attachments/assets/877720cc-210a-4b98-a938-e71870547c28" />
- Fill project name and description and click create
  <img width="711" height="937" alt="Screenshot from 2026-02-18 15-12-10" src="https://github.com/user-attachments/assets/6c212055-5f20-414c-8bfc-6b4820b317b6" />
- Once project is created, click on + -> create new repository
  <img width="1386" height="320" alt="Screenshot from 2026-02-18 15-12-45" src="https://github.com/user-attachments/assets/57dd02d1-0e1b-4612-8a63-0b264d315157" />
- Click on pipelines -> create new pipeline
  <img width="1418" height="497" alt="Screenshot from 2026-02-18 15-13-28" src="https://github.com/user-attachments/assets/fcc2d7a2-3439-4f39-af97-a90c5585524b" />
- Select Type
- Newly created Repository name
  <img width="1418" height="497" alt="Screenshot from 2026-02-18 15-13-38" src="https://github.com/user-attachments/assets/7402f529-024d-40d1-b0aa-de41d25a686f" /> 
- If we have uploaded the pipeline yaml file to repo, select the branch and file path in next page
  <img width="1902" height="984" alt="Screenshot from 2026-02-18 15-13-56" src="https://github.com/user-attachments/assets/1ae03183-c97c-4068-a478-53f49a067aa5" />
- Review and create pipeline
- Once pipelines are created, go to pipelines and click on run pipeline
- The pipeline run should be look like below
  <img width="1902" height="984" alt="Screenshot from 2026-02-18 15-27-51" src="https://github.com/user-attachments/assets/fa7d1483-f15b-427f-99f3-bcc05d4e7ba6" />

## 2, Migrate repository

Follow the steps below to migrate the Azure devops repository to github. 

- Go to repository and click on clone 
- Copy URL and generate temporary credentials
  <img width="1902" height="984" alt="Screenshot from 2026-02-18 16-42-20" src="https://github.com/user-attachments/assets/20dacb6b-b2e3-42c2-87b4-e7157a402d55" /> 
- Login into github and click import repository
- Fill copied URL and credentials
  <img width="1902" height="1010" alt="Screenshot from 2026-02-18 16-45-10" src="https://github.com/user-attachments/assets/15feaa9e-2af1-4028-8766-b0d3198edc1e" />
- Wait till import completion
  <img width="1902" height="1010" alt="Screenshot from 2026-02-18 16-56-35" src="https://github.com/user-attachments/assets/601fd251-490e-45b7-9fb2-712f5b8717ee" />
  <img width="1902" height="1010" alt="Screenshot from 2026-02-18 16-51-08" src="https://github.com/user-attachments/assets/2426167a-6d4f-4f25-9037-3164db3a9e96" />

## 3, Migrate pipelines 

Follow the steps below to migrate the azure devops pipelines to github actions 

- Install git cli and action-importer extension by following [git cli](https://github.com/cli/cli#installation) and [github action-importer](https://github.com/github/gh-actions-importer?tab=readme-ov-file#installation) 
- Clone repository to local machine 
- Get into repository folder and configure azure and git credentials
  <img width="1902" height="332" alt="Screenshot from 2026-02-18 18-00-00" src="https://github.com/user-attachments/assets/afe31329-dc4c-4754-9c6e-5e6e8e41be91" />
- Update github action-importer 
- Run audit command to generate audit report
  <img width="1902" height="296" alt="Screenshot from 2026-02-18 18-00-23" src="https://github.com/user-attachments/assets/3e18c907-b81c-4be4-8a5e-da3b5f2b7cea" />
- Review generated audit report and noted down the manual tasks to be performed
  <img width="220" height="296" alt="Screenshot from 2026-02-18 18-01-12" src="https://github.com/user-attachments/assets/60ac6af1-fd20-40a3-8dba-09a8444a34be" />
- Run forecast command to generate forecast report 
- Run dry command to generate pipeline yaml files in github actions format. 
- Review generate github actions yaml files
  <img width="1909" height="622" alt="Screenshot from 2026-02-18 18-08-55" src="https://github.com/user-attachments/assets/f75910c0-5c20-4719-8cd8-d48136d0d168" />
- Run actions migrate command
  <img width="241" height="232" alt="Screenshot from 2026-02-18 18-09-36" src="https://github.com/user-attachments/assets/564b2d40-a52e-47d3-838e-7bc80e48d40a" />
- The pull request will be created at github repo
  <img width="1589" height="993" alt="Screenshot from 2026-02-18 18-12-07" src="https://github.com/user-attachments/assets/fbc44ed6-8b2f-4cd5-8c85-0753fde20839" />
- Review pull request and merge it
  <img width="1893" height="993" alt="Screenshot from 2026-02-18 18-17-58" src="https://github.com/user-attachments/assets/e6202271-3f5e-4d3a-9eeb-355ebddad42c" />
- Test github actions by trigger and ran the migrated pipelines.
  <img width="1589" height="993" alt="Screenshot from 2026-02-18 18-12-18" src="https://github.com/user-attachments/assets/3218fa27-82c1-4e06-98d0-00917eb7539e" />

## Sample pipelines: 

The below pipelines are defined in azure-pipelines.yaml file 

### Simple print: 
This pipeline will print statement steps in different shells (bash, powershell,powershell task) in linux runner. 

### Command prompt: 
This pipeline will print statement steps in windows runner. 

### Conditional statement: 
This pipeline will run step based on defined conditions. 

### Dependent jobs: 
This pipeline will run jobs in a defined sequence by defining job dependencies.  

### Azure tasks: 
This pipeline runs a python script using python tasks. 

### Environmental variables: 
This pipeline will read environmental variables and secrets from repo variables. 














