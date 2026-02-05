# Source-Control-with-Power-BI-and-Fabric

prerequisites
git
azure devops or github
power bi desktop
fabric 

1
create a new repo for your project in Github or azure repos

step 2 

create your pbi report in pbi desktop using your own data or the free dataset in this example

3 clone your repo locally

step 4 

save the file as .pbip o power bi project in your local 

Power BI Desktop introduces a new way to author, collaborate, and save your projects. When you save your work as a Power BI Project (PBIP), report and semantic model item definitions are saved as individual plain text files in a simple, intuitive folder structure.

Saving your work as a project has the following benefits:

Text editor support - PBIP files are formatted text files containing semantic model and report metadata. These files are publicly documented and human readable. While project files support simple text editing tools like Notepad, it's better to use a code editor like Visual Studio Code (VS Code), which provides a rich editing experience including intellisense, validation, and Git integration.

Folder structure transparency - Separate folders for the semantic model and report, enabling powerful yet simple tasks like copying semantic model tables between projects or reusing report pages. A great choice for creating and reusing development templates.

Source control ready - Open text files, designed for seamless integration with Git, enabling version history and team collaboration. To learn more, see Version control in Git.

Continuous Integration and Continuous Delivery (CI/CD) support - Apply CI/CD practices on top of your existing source control systems using PBIP files, incorporating quality gates and automating deployment to production environments. To learn more about CI/CD in Fabric, see Fabric CI/CD workflows.

Programmatic generation and editing item definitions - You can programmatically generate and modify item definition text files, enabling batch operations such as updating all report pages visuals or adding a set of measures to each table. For semantic models, you can use the Tabular Object Model (TOM) client library to deserialize the semantic model metadata, make programmatic modifications, and serialize it back to the files.

5 push your models and reports to your remote repo 

6 on fabric create for this example a Dev and a Prod workspace 
7 in the workspace setting go to git integration and select either Azure DevOps or Github and make your connection

use a dev branch for the dev workspace and the same for prod 

8 once done i will sync with your remote repo and the models and report will be in your fabric workspace 

importing the data your the reports is beyond this guide 

9 test the integration

1 make new reports locally 

2 save it as your next version and pbip

3 use git to push the chances to the remote 

4 see the source control automatically syncing your chances to fabric

this also works the other way around form fabric to the repo to your local by using the same Git technology


Operationalizing this

example

image your team has a fabric capcity for development and one for production 

you can have all your PBI developers creating their models ans reports and then creating pull requests to your development branch which will be approve only by a tester who ensure the report is good enough to eventually pass to the prod capacity using this integrations 



