# Lab 5. Crafting Your First Release in Azure DevOps: Release

# 1. Create Release

1. Navigate to `Releases`.

2. Select `New pipeline`.

![lab5-Release1.png](./sparkles/SantaWorkshop-016.png)

3. Select `Empty job`.

![lab5-Release2.png](./sparkles/SantaWorkshop-015.png)

4. Close information pane.

![lab5-Release3.png](./sparkles/SantaWorkshop-014.png)

5. Click `+ Add an artifact`

![lab5-Release4.png](./sparkles/SantaWorkshop-013.png)

6. Fill in the following fields:
- `Source (build pipeline)` - select `Santa Workshop-Build` (the name of the Build pipeline).
- `Source alias` - `drop`.

![lab5-Release5.png](./sparkles/SantaWorkshop-012.png)

7. Click `Add`.

8. Click `1 job, 0 task`.

![lab5-Release6.png](./sparkles/SantaWorkshop-011.png)

9. Add the following tasks:
- `Power Platform Tool Installer`
- `Power Platform Import Solution`

![lab5-Release7.png](./sparkles/SantaWorkshop-010.png)

***


# 2. Configure task Power Platform Import Solution

### Filed: Authentication type

Select `Service Principal/client secret (support MFA)`

### Field: Service connection

Select `PROD`

### Field: Solution Input File

Click on three dots, select `NorthPoleCommunicationKit_managed.zip` and click `OK`.

![lab5-Release8.png](./sparkles/SantaWorkshop-009.png)

### Field: Use deployment settings file

Ensure that you check this field.

### Field: Deployment Settings File

Click on three dots, select `SantaWorkshop.json` and click `OK`.

![lab5-Release9.png](./sparkles/SantaWorkshop-008.png)

### Section: Advanced

Check `Import as a Managed solution`.

![lab5-Release10.png](./sparkles/SantaWorkshop-007.png)

***


# 3. Save and create Release

1. Click `Save`, then click `OK`.

![lab5-Release11.png](./sparkles/SantaWorkshop-006.png)

2. Click `Create release, then click `Create`.

![lab5-Release11.png](./sparkles/SantaWorkshop-005.png)

***

# 4. Check PROD environment

1. Go to `PROD` environment.

2. Open the solution `North Pole Communication Kit`.

3. Open the environment variable `ElfPalette` and check that the `Current Value` is `#FFFF00` (as we defined in the Settings file).

![lab5-Release15.png](./sparkles/SantaWorkshop-003.png)

4. Share the app with your account and Play it. 

![lab5-Release16.png](./sparkles/SantaWorkshop-002.png)

You should see the app with yellow header:

![lab5-Release16.png](./sparkles/SantaWorkshop-001.png)

***

[Go back to the chapter 7](../Chapter7%20-%20Deployment%20Deck-The-Halls%20Dock.md#sixth-lab-crafting-your-first-release-in-azure-devops---release)







