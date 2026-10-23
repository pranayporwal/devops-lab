\# Exercise 8: Creating a Hello World Jenkins Job



\## Objective

Create a shell script, store it in a Git repository, and configure a Jenkins Freestyle job to execute the script and display its output.



\## Prerequisites

\- Git

\- GitHub account and repository

\- Docker Desktop

\- Jenkins

\- Jenkins Git plugin



\## Project Files

\- `hello-world.sh`: Shell script that prints a greeting.

\- `Exercise-8.1.png`: Jenkins console output screenshot.



\## Procedure



\### Step 1: Create the Shell Script



The `hello-world.sh` script contains a simple command that prints a message to the console.



\### Step 2: Push the Script to GitHub



Initialize the local Git repository, stage the script, commit the changes, connect the remote repository, and push the code to GitHub.



\### Step 3: Access Jenkins



Open the Jenkins dashboard at:



http://localhost:8080



\### Step 4: Create a Freestyle Job



Create a new Jenkins item and select \*\*Freestyle project\*\*.



\### Step 5: Configure Source Code Management



Select Git and provide the URL of the repository containing `hello-world.sh`.



\### Step 6: Configure the Build Step



Add an \*\*Execute shell\*\* build step with the command:



```bash

sh hello-world.sh

```



\### Step 7: Run the Job



Save the job configuration and select \*\*Build Now\*\*.



\### Step 8: Check the Console Output



Open the build in Build History and select \*\*Console Output\*\*.



The script should print:



Hello, Jenkins!



The build should finish successfully if the repository checkout and script execution complete without errors.



\## Expected Results



\- The shell script is stored in GitHub.

\- Jenkins checks out the configured repository.

\- The Jenkins job executes the shell script.

\- The console output displays the greeting.

\- The build completes successfully.



Verify the result by running the Jenkins job.



\## Learning Outcomes



\- Store source code in Git and GitHub.

\- Configure Git as a source code management system in Jenkins.

\- Create and execute a Freestyle job.

\- Inspect Jenkins build logs and console output.

