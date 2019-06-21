# Configure Jenkins

###### Create pipeline

**Steps to configure pipeline**
1. On Jenkins portal, click "New Item" from the left menu, provide a name, and select  **Pipeline** from the options. Then click "OK".
2. Select the created pipeline. Click "Configure" from the left menu,
3. In the **Pipeline** select "This project is parameterized", add below parameters.
    Vault Address:
    ```sh
    Name: VAULT_ADDR
    Value: <vault_address>
    ```
    Vault Token:
    ```sh
    Name: VAULT_TOKEN
    Value: <vault_token>
    ```
    Relese Choice:
    ```sh
    Name: RELEASE_NEW
    Choices: 
    Yes
    No
    ```
    Relese Branch:
    ```sh
    Name: RELEASE_BRANCH
    Choices: <branch_name>

    ```
    Reset Action:
    ```sh
    Name: RESET_ACTION
    Choices: 
    Yes
    No
    ```

4. In the **Pipeline** section below, select "Pipeline script from SCM". All other sections can be left as default or configured according to your project needs.

5. Select "Git" from the "SCM" dropdown and provide the Repository URL and branch where the jenkinsfile is stored. Also select a "Credential" from the dropdown.
6. Change the "Script Path" depending on what pipeline you are creating. Keep all other values as default.<br/>
    ```sh
    Script path: automation/r3-corda/Jenkinsfile
    ```
7. **Save** and your pipeline is configured.
