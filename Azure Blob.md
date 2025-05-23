
# **Setting Up Azure Blob Storage for Power Apps**  
I recently configured **Azure Blob Storage** for a Power Apps application, and I documented the steps to make it easier for future setups. Here’s my process:

## **Step 1: Creating the Azure Blob Storage Account**  
1. I logged into the [Azure Portal](https://portal.azure.com).  
2. Clicked **Create a resource** > **Storage account**.  
3. Selected **Storage account – blob, file, table, queue**.  
4. Configured the following:  
   - **Subscription**: Picked my Azure subscription.  
   - **Resource group**: Created a new one for better organization.  
   - **Storage account name**: Chose a unique name for easy identification.  
   - **Region**: Selected the most optimal location.  
   - **Performance**: Opted for **Standard** since high-speed access wasn’t a priority.  
   - **Replication**: Used **Locally-redundant storage (LRS)** for cost efficiency.  
5. Clicked **Review + Create**, then **Create** to deploy the storage account.  

## **Step 2: Creating a Blob Container**  
1. Navigated to the **Storage Account** I just created.  
2. Opened the **Containers** section.  
3. Clicked **+ Container**, entered a container name, and set the **Public access level** (initially private).  
4. Clicked **Create** to finalize the setup.
![Screenshot 2025-05-23 113256](https://github.com/user-attachments/assets/e13e7032-2254-4e6f-ae67-b7febcd83916)

![Screenshot 2025-05-23 113359](https://github.com/user-attachments/assets/b3608d9a-75e8-4a53-a6a5-2b5be6790339)

## **Step 3: Retrieving Access Keys**  
1. Went to **Security + networking** > **Access keys**.  
2. Copied the **Storage account name** and **Key**, which were needed for Power Apps integration.

![Screenshot 2025-05-23 114937](https://github.com/user-attachments/assets/4e736e87-f8cf-4676-91aa-05555a78d411)


![Screenshot 2025-05-23 114040](https://github.com/user-attachments/assets/3d4b5ccf-69e2-440c-bb5f-c0b7e5fecbd6)

## **Step 4: Connecting Blob Storage to Power Apps**  
1. Opened **Power Apps** and went to **Data** > **Connections**.  
2. Clicked **New connection** > **Azure Blob Storage**.  
3. Entered the **Storage account name** and **Access key** from the previous step.  
4. Clicked **Create**, successfully integrating Azure Blob Storage into Power Apps.  

---

## **Challenges I Faced & How I Fixed Them**  
Initially, after creating the blob container and sharing the **key, client ID, and necessary credentials** with the Power Apps team, it didn’t work. After troubleshooting with my colleague and consulting with my mentor, we discovered that:  
- The **Power Apps tenant** was different from the **Azure tenant**, causing authentication failures.  
- My blob container was set to **private**, blocking external access.  

### **Solution:**  
To resolve the issue, I changed the container’s **access settings from private to anonymous**, allowing **public access**. This enabled the Power Apps team to successfully retrieve data without authentication conflicts.

---

## **Step 5: What the Power Apps Team Did**  
Once the connection was set up, the Power Apps team implemented Blob Storage in their application:

1. **Created a Canvas App** in Power Apps.  
2. **Added the Azure Blob Storage connector** to retrieve files.  
3. Used a **Gallery** to display stored files with:  
   ```  
   AzureBlobStorage.ListRootFolderV2().value  
   ```  
4. Added an **Upload Button** to enable file uploads:  
   ```  
   AzureBlobStorage.CreateFile("ContainerName", TextInput.Text, AddMediaButton.Media)  
   ```  
5. **Tested the setup**, verifying that Power Apps could interact with stored blobs correctly.  

---

## **Key Takeaways & Best Practices**  
While switching to **anonymous access** fixed the issue, it **exposes storage publicly**, which can be a security risk. A better approach is:  
1. **Grant specific user permissions** via **Azure Role-Based Access Control (RBAC)**.  
2. **Use Shared Access Signatures (SAS)** instead of full access keys.  
3. **Ensure tenant alignment** between Azure and Power Apps to avoid authentication failures.  

I’ll apply these secure access methods in future projects to ensure data protection. If you’re working on something similar and need assistance, feel free to reach out! 🚀  

---
