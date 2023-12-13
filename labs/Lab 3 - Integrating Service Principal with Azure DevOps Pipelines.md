# Lab 3. Integrating Service Principal with Azure DevOps Pipelines

# 1. Create App Registration

1. Navigate to [https://portal.azure.com/](https://portal.azure.com/).

2. In the search field type `registration` and in the drop-down list select `App registration`.

![lab3-ServicePrincipal1.png](./sparkles/SantaWorkshop-059.png)

3. Click `New registration` on the `App registrations` page.

4. Enter `SantaAppReg` in the `Name` field, keep other fields with predefined values and click `Register`.

![lab3-ServicePrincipal2.png](./sparkles/SantaWorkshop-058.png)

5. Once the app registration is created, navigate to `API permissions` on the left-hand menu.

6. Click `+ Add a permission`.

7. In the pop-up window find and choose `Dynamics CRM`.

![lab3-ServicePrincipal3.png](./sparkles/SantaWorkshop-057.png)

8. Select `user_impersonation` and click `Add permissions`.

![lab3-ServicePrincipal4.png](./sparkles/SantaWorkshop-056.png)

9. Click `Grant admin consent for YOUR COMPANY NAME` and click `Yes` in the pop-up window.

![lab3-ServicePrincipal5.png](./sparkles/SantaWorkshop-054.png)

10. Navigate to `Certificates & secrets`.

11. Click `+ New client secret`.

12. Enter `SantaSecret` in the `Description` field and click `Add`.

![lab3-ServicePrincipal6.png](./sparkles/SantaWorkshop-053.png)

13. Copy secret from the `Value` field and store it somewhere (in Notepad for instance).

:exclamation: _Note:
Once you close this tab or navigate somewhere from this screen, the Secret value won't be available for copy._

![lab3-ServicePrincipal7.png](./sparkles/SantaWorkshop-052.png)

14. Navigate to `Overview` and copy value from fields `Application (client) ID` and `Directory (tenant) ID`.

![lab3-ServicePrincipal8.png](./sparkles/SantaWorkshop-051.png)

***


# 2. Add the Service Principal into Power Platform

1. Navigate to [Power Platform admin center -> Environments](https://admin.powerplatform.microsoft.com/environments).

2. Open `DEV` environment.

3. Click `See all` bellow `Users`.

![lab3-ServicePrincipal9.png](./sparkles/SantaWorkshop-050.png)

4. Click `app users list` in the opened screen.

![lab3-ServicePrincipal10.png](./sparkles/SantaWorkshop-049.png)

5. Click `+ New app user`, and in the pop-up window click `+ Add an app`.

![lab3-ServicePrincipal11.png](./sparkles/SantaWorkshop-048.png)

6. Select `SantaAppReg` and click `Add`.

![lab3-ServicePrincipal12.png](./sparkles/SantaWorkshop-047.png)


7. Select `Business unit`, add either `System Customizer` or `System Administrator` security role, and click `Create`.

![lab3-ServicePrincipal13.png](./sparkles/SantaWorkshop-046.png)


8. Repeat all steps in this section for the `PROD` environment.

*** 


# 3. Create Connection in Azure DevOps using App Registration

1. Navigate to your project in Azure DevOps and open `Pipelines` tab on the left-hand menu.

2. Click on three dots for the pipeline that you created in the previous lab, and click `Edit`.

![lab3-ServicePrincipal14.png](./sparkles/SantaWorkshop-045.png)

3. Go to the step `Power Platform Export Solution` and switch `Authentication type` to `Service Principal/client secret (support MFA)`. After click `Manage` next to `Service connection`.

![lab3-ServicePrincipal15.png](./sparkles/SantaWorkshop-044.png)

4. Click `New service connection`.

5. Select `Power Platform` and click `Next`.

![lab3-ServicePrincipal16.png](./sparkles/SantaWorkshop-043.png)

6. Fill in the form:
- `Authentication method` - `Application Id and client secret`.
- `Server URL` - get this value from Power Apps Maker portal (see bellow).
- `Tenant Id` - `Directory (tenant) ID` that you copied on step 1.
- `Application Id` - `Application (client) ID` that you copied on step 1.
- `Client secret of Application Id` - Secret value that you copied on step 1.
- `Service connection name` - `Dev Service Principal`.

:exclamation: _Note:
To find value for_ `Server URL` _field go to Power Apps maker porta, select environment_ `Dev` -> `Settings` -> `Session details`

![lab3-ServicePrincipal17.png](./sparkles/SantaWorkshop-042.png)

Click `Save`.
Completed form should look as the following:

![lab3-ServicePrincipal18.png](./sparkles/SantaWorkshop-041.png)

7. Go back to your pipeline, refresh `Service connection` field and select `Dev Service Principal`.

8. Go to your solution and update value of the `ElfPalette` environment variable. The new value - `#0AFF3F`.
Run this updated pipeline. 

![lab3-ServicePrincipal19.png](./sparkles/SantaWorkshop-039.png)

***


# 4. Check the result

Once the run will be completed successfully, go to `Repos`, select the folder `NorthPoleCommunicationKit` and check the `History`.

![lab3-ServicePrincipal20.png](./sparkles/SantaWorkshop-038.png)

***


[Go back to the chapter 5](../Chapter5%20-%20Service%20Snowman%20Sanctum.md#third-lab-crafting-our-snowman-for-azure-devops-pipelines)













