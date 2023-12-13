# Lab 5. Crafting Your First Release in Azure DevOps: Build


# 1. Create Build pipeline

1. Navigate to `Pipeline` and click `New pipeline`.

![lab5-Build1.png](./sparkles/SantaWorkshop-026.png)

2. As we proceed during the creation of the first pipeline, select `Use the classic editor` -> click `Continue` -> `Empty job`.

3. Rename pipeline with `Santa Workshop-Build`

4. Uncheck `Shallow fetch` in `Get source`.

5. Add the following tasks to `Agent job 1`:

- `Power Platform Tool Installer`
- `Power Platform Pack Solution`
- `Copy Files to:`
- `Publish Artifacts: drop`

![lab5-Build3.png](./sparkles/SantaWorkshop-025.png)

***

# 3. Configure pipeline tasks

## 3-1 Power Platform Pack Solution

### Field: Source Folder of Solution to Pack

Click on three dots and select the folder `NorthPoleCommunicationKit`.

![lab5-Build4.png](./sparkles/SantaWorkshop-024.png)

### Field: Solution Output File

Copy to this field the following value:
`$(Build.ArtifactStagingDirectory)\$(PowerPlatform.SolutionName)_managed.zip`

### Field: Type of Solution

Select `Managed`

![lab5-Build5.png](./sparkles/SantaWorkshop-023.png)

## 3-2 Copy Files to:

### Field: Source Folder

Click on three dots and select the folder `Settings`.

![lab5-Build6.png](./sparkles/SantaWorkshop-022.png)

### Field: Contents

Keep `**`.

### Field: Target Folder

Copy to this field the following value:
`$(Build.ArtifactStagingDirectory)`

![lab5-Build7.png](./sparkles/SantaWorkshop-021.png)

## 3-3 Publish Artifact: drop

Keep fields with predefined values.

![lab5-Build8.png](./sparkles/SantaWorkshop-020.png)

***


# 4. Set up pipeline variable

1. Go to Variables.

2. Click + Add button.

3. Provide the variable name `PowerPlatform.SolutionName` and its value `NorthPoleCommunicationKit`.

![lab5-Build9.png](./sparkles/SantaWorkshop-019.png)

***


# 5. Run pipeline

1. Click `Save & queue`, and click `Save & queue` in the drop-down list.

2. In the Run pipeline pop-up window click `Save and run`.

Once the pipeline will be completed successfully go to the last run and select `1 published; 1 consumed`:

![lab5-Build10.png](./sparkles/SantaWorkshop-018.png)

The Artifact will be available:

![lab5-Build10.png](./sparkles/SantaWorkshop-017.png)

***


[Go back to the chapter 7](../Chapter7%20-%20Deployment%20Deck-The-Halls%20Dock.md#fifth-lab-crafting-your-first-release-in-azure-devops---build)