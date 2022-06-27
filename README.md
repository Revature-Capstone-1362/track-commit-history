# Track Project 1 Commit History

## Project Description
An automation to analyze and generate reports for the number of commits an associate has made to their Project 1 GitHub repositories.

## Technologies Used
- UiPath Studio
- UiPath Orchestrator
- UiPath Assistant
- Microsoft Excel
- Microsoft Word

## Features
- Accepts data input through Excel workbooks
- Generates repository URLs based on standardized GitHub organization and repository names
- Counts commits to main branch and any commits made to auxiliary branches not merged to main
- Generates a PDF report containing the URL of the repository, number of commits separated by branch, and the total number of commits.
- Allows custom input and output directories to be set in config.xlsx
- Sends emails containing reports to trainers and managers, or optionally to one or more override email addresses

### Future Features
- Include option to allow reports to be grouped together, reducing number of emails sent

## Getting Started

### Setting Up Orchestrator and Accounts
1. In Orchestrator, create a queue to contain the transaction items for the automation.
2. Create a GitHub account that will have access to the GitHub organizations containing Project 1 repositories and generate a Personal Access Token for the account.
3. Add the username of the GitHub account and the Personal Access Token as a credential asset in Orchestrator.
4. Add the login details of the email to send reports from as a credential asset in Orchestrator.

### Setting Up Automations
1. Clone project repository using `git clone https://github.com/Revature-Capstone-1362/track-commit-history.git`.
2. Open `project.json` in both CommitTrackerDispatcher and CommitTrackerPerformer folders and publish the projects to Orchestrator.
3. Assign processes to robots.
4. Navigate to package directory on robot machines, usually located in `%userprofile%\.nuget\packages`.
5. Open `config.xlsx` in `1.x.x\lib\net45\Data` directory of dispatcher and set the queue name.
    - Optionally set the path to the directory for input data workbooks. The default directory for input data is the Input folder in this directory.
6. Open `config.xlsx` in `1.x.x\lib\net45\Data` directory of performer and set the queue name, information for the GitHub credential asset, and the information for the email account including the credential asset, server, and port.
    - Optionally set the path to the directory for output report PDFs. The default directory for output reports is the Output folder in this directory.
    - Optionally set override email(s) that reports will be sent to. By default, automation will send emails to the trainer and manager.

### Constraints
- Input data workbooks must contain the following information with the specified column names: `Associate_Name, Trainer_Name, Manager_Name, GitHub_Organization, GitHub_Username`.
- Project 1 repository names must adhere to the following naming scheme: `<Associate First Name>-<Associate Last Name>-P1`. (ex. Warren-Lee-P1)
