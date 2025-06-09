# EPPC-ALMWS
Repository for the Application Lifecycle Management (ALM) pre-Day workshop at European Power Platform Conference (EPPC)

## Labs
The following describes the labs you will be working on during (or after) the workshop.

### Prerequisites
- Azure DevOps or GitHub Account
- Two Dataverse environments (one for source and one for target)
- App Registration
  - Follow this instruction: https://benediktbergmann.eu/2022/01/04/setup-a-service-principal-in-power-automate/


### Prebuild Pipelines
In the `Pipelines` folder you will find all the pipelines that you will be creating during the workshop.

#### Buid Tools
The pre build pipelines are using the following build tools:

https://marketplace.visualstudio.com/items?itemName=microsoft-IsvExpTools.PowerPlatform-BuildTools

#### Connection
All the pre build pipelines are using App Registrations to connect to the Dataverse environments.
The Pipelines for ADO are using a service connection to connect to the Dataverse environments.
For GH you will need to create environment variables containing the connection information (URL, Client ID, Client Secret, Tenant ID).

#### Folder structure
The pipelines are building on a certain folder structure which is explained in the following link:

https://benediktbergmann.eu/2021/04/27/folder-structure-of-a-dataverse-project/

#### Demo Code
This repo does contain demo code for a Plugin as well as a TypeScript/JavaScript file. For both there are some UnitTests as well.

### Lab 1: Base Pipelines
Create the following pipelines:
- Export Pipeline
- Build Pipeline
- Release Pipeline

You can find the instructions for each pipeline below.

The complete pipelines can be found in the `Pipelines/Base` folder.

#### Export Pipeline
The Export Pipeline will export the solution from the source environment. It should contain the following steps:
- Publish customizations
- Export Solution - Managed
- Export Solution - Unmanaged
- Unpack Solution
- Commit changes

#### Build Pipeline
The Build Pipeline will build the solution. It should contain the following steps:
- Pack Solution
- Publish Artifact

#### Release Pipeline
The Release Pipeline will release the solution to the target environment. It should contain the following steps:
- Download Artifact
- Import Solution

### Lab 2: Advanced Pipelines
Add parameters and conditions to the pipelines.

The complete pipelines can be found in the `Pipelines/Variable-Condition-Loop` folder.

#### SolutionName
The SolutionName should be a variable (in best case in a variable file) that is used in the pipelines.

#### Update or Upgrade
Whether the solution should be updated or upgraded should be a parameter in the Release Pipeline. The parameter should be used in the Import Solution step as a condition.

#### Loop
The Export Pipeline should be able to export multiple solutions. The solutions should be defined in a variable file. The Export Solution step should be in a loop that exports all the solutions.

### Lab 3: Settings
In this lab you should create a settings file that contains the values for Environment Variables and Connection References.

The complete pipelines can be found in the `Pipelines/Settings` folder.

#### Create a settings file
- Download the Solution
- Use PAC CLI to create the settings file

#### Use the settings file
Change the Release Pipeline to use the settings file. This should be done in the Import Solution step.

### Lab 4: Solution Checker
In this lab you should create a pipeline that checks the solution for issues using the Solution checker.

Add a Solution Checker step to the Export Pipeline and use the exported unmanaged solution to check for issues.

The complete pipelines can be found in the `Pipelines/Solution-Checker` folder.

### Lab 5: Mapping
Change both the Eport and Build pipeline to use a mapping file.

Create a mapping file and add it to the unpack and pack steps.

The complete pipelines can be found in the `Pipelines/Mapp` folder.

### Lab 6: Move Data
Change the Release pipeline to import data.

Add a "import data" step at the end of the Relase pipeline.
You could also add an export step in the build pipeline.

The complete pipeline can be found in the `Pipelines/Data` folder