# Jenkins for Docker Images
**Create and Push docker images to registry**

```
**Assumption**
Details required for registry is updated in respective Jenkinsfile
```

###### Create pipeline

1. On Jenkins portal, click "New Item" from the left menu, provide a name, and select  **Pipeline** from the options. Then click "OK".
2. Select the created pipeline. Click "Configure" from the left menu,
3.  In the **Pipeline** section below, select "Pipeline script from SCM". All other sections can be left as default or configured according to your project needs.
4. Select "Git" from the "SCM" dropdown and provide the Repository URL and branch where the jenkinsfile is stored. Also select a "Credential" from the dropdown.
5. Change the "Script Path" depending on what pipeline you are creating. Keep all other values as default.<br/>
    ```sh
    Script path: automation/r3-corda/Jenkinsfile
    ```
6. **Save** and your pipeline is configured.
