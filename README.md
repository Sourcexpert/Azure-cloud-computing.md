### **Steps that I use to Create Azure Virtual Desktop (AVD) on Azure Using the Portal**  

### ✅ **Step 1: I Set Up the Virtual Network (VNet)**    
1. Create a **Virtual Network (VNet)** for AVD.  
 
![Screenshot 2025-03-18 085848](https://github.com/user-attachments/assets/fe93b396-dbc1-4325-91fb-854896e836cd)

![Screenshot 2025-03-18 085952](https://github.com/user-attachments/assets/c1129799-5bc0-4937-afcd-5399b789d285)

### ✅ **Step 2: Create a Host Pool**  
1. I go to **[Azure Portal](https://portal.azure.com/)**.  
2. Search for **Azure Virtual Desktop** and select it.  
3. Click **Host Pools > + Create a Host Pool**.  
4. Fill in details:  
   - **Subscription & Resource Group**  
   - **Host Pool Name**  
   - **Location**  
   - **Host Pool Type** (Personal/Shared)  
5. Click **Next: Virtual Machines**.  

![Screenshot 2025-03-18 090958](https://github.com/user-attachments/assets/c9ac01b5-94ac-4f47-83c8-841df0ff9a79)


### ✅ **Step 3: Configure Virtual Machines (VMs)**  
1. **Enable or Disable VM Creation** (Choose “Yes” to add VMs).  
2. **Select Image Type** (e.g., Windows 11 Multi-session). I used Operating system
:
Windows (Windows 11 Enterprise multi-session)
Size
:
Standard D2as v5 (2 vcpus, 8 GiB memory)
 .  
3. Choose **VM size**, number of VMs, and naming convention.  
4. Configure **Network & Security** settings.  
5. Click **Next: Workspace**.  


### ✅ **Step 4: Assign a Workspace**  
1. Select **No** to register the host pool with a workspace and I create it seperately after deployment of the AVD.   
2. Click **Next: Review + Create**.  
![Screenshot 2025-03-24 125726](https://github.com/user-attachments/assets/06dd0374-dfef-4f23-919a-c529768df780)


### ✅ **Step 5: Review & Deploy**  
1. Review all configurations.  
2. Click **Create** to deploy the AVD environment.  
3. Wait for the deployment to complete.  
![Screenshot 2025-03-18 092604](https://github.com/user-attachments/assets/1c0e41c0-57c6-4b3d-aac8-19d5714cd5d0)

![Screenshot 2025-03-24 125054](https://github.com/user-attachments/assets/bd7dc5af-3d23-4285-b3e7-067e552a97a2)

### ✅ **Step 6: Assign Users to the AVD Host Pool**  
1. Go to **Azure Virtual Desktop > Application Groups**.  
2. Select the **Default Desktop Application Group**.  
3. Click **Assignments > Add Users**.  
4. Select users from **Azure AD** and save.  


### ✅ **Step 7: Access Azure Virtual Desktop**  
1. Provide users with the AVD access link:  
   - **Web Client:** [https://rdweb.wvd.microsoft.com/arm/webclient](https://rdweb.wvd.microsoft.com/arm/webclient)  
   - **AVD Client:** Install Remote Desktop Client and log in.  
2. Users can sign in with their **Azure AD credentials** to access their virtual desktop.  

---![Screenshot 2025-03-24 131701](https://github.com/user-attachments/assets/e50ffc17-db1c-4445-8689-37fd23dbb84e)

![Screenshot 2025-03-24 131701](https://github.com/user-attachments/assets/324f8a81-d944-4190-b2ea-b0348001df82)

🎯 **Done! Your Azure Virtual Desktop (AVD) is now set up and ready for users!** 🚀



### Problems encountered

On my first through fifth attempts to provision the AVD, I ran into several errors. After thorough troubleshooting, I pinpointed the issue to a lack of sufficient role permissions for AVD provisioning. Eventually, I was granted User Administrator rights, which resolved the problem
![Screenshot 2025-03-18 093838](https://github.com/user-attachments/assets/fb3f93b3-b0a3-4031-ba20-eee051d49565)
