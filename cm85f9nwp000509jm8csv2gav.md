---
title: "Automating Docker Volume Backups to Azure Blob Storage Also Setting Cron Job"
seoTitle: "Automate Docker Volume Backups to Azure with Cron Jobs | Deepesh Gupta"
seoDescription: "Automate Docker volume backups to Azure Blob Storage using AzCopy, Bash, and cron jobs. A step-by-step guide by Deepesh Gupta. 🚀"
datePublished: Wed Mar 12 2025 04:30:44 GMT+0000 (Coordinated Universal Time)
cuid: cm85f9nwp000509jm8csv2gav
slug: docker-volume-backups-to-azure
tags: docker, azure, devops, backup, cronjob, shell-script, cloud-storage, deepeshmlgupta, azcopy, deepeshgupta

---

### Introduction

When running applications in Docker, persistent data stored in **Docker volumes** is critical. To ensure data safety, regular backups are necessary. This guide walks you through the process of:

* Creating an **Azure Storage Account** and a **Blob Container**.
    
* Generating a **Shared Access Signature (SAS) Token** for secure uploads.
    
* Writing a **Bash script** to back up Docker volumes.
    
* Automating backups using a **cron job** to run daily at 11 AM.
    

---

## Step 1: Create an Azure Blob Storage Account and Container

### 1.1 Create an Azure Storage Account

1. Go to the [Azure Portal](https://portal.azure.com/).
    
2. Search for **Storage Accounts** in the search bar and click **Create**.
    
3. Fill in the required details:
    
    * **Subscription**: Choose your Azure subscription.
        
    * **Resource group**: Create a new one or use an existing one.
        
    * **Storage account name**: Provide a unique name (e.g., `mydockerbackups`).
        
    * **Region**: Select a region close to your deployment.
        
    * **Performance**: Standard.
        
    * **Redundancy**: Locally-redundant storage (LRS) is sufficient.
        
4. Click **Review + Create** and wait for deployment to complete.
    

### 1.2 Create a Blob Storage Container

1. Navigate to the **Storage Account** you just created.
    
2. Click **Containers** &gt; **\+ Container**.
    
3. Name it `terrabackup`.
    
4. Set the **public access level** to `Private (no anonymous access)`.
    
5. Click **Create**.
    

---

## Step 2: Generate a Shared Access Signature (SAS) Token

1. In your **Storage Account**, go to **Security + networking** &gt; **Shared access signature**.
    
2. Select the following permissions:
    
    * **Allowed services**: Blob
        
    * **Allowed resource types**: Container, Object
        
    * **Allowed permissions**: Read, Write, Delete, List
        
3. Set the **Start and Expiry date** (e.g., valid for 1 year).
    
4. Click **Generate SAS and connection string**.
    
5. Copy the **Blob SAS URL** (we’ll use it in the backup script).
    

---

## **Install AzCopy (if not installed)**

Before running the backup script, you need **AzCopy**, a command-line tool used to transfer data to and from Azure Blob Storage.

### **3.1 Install AzCopy on Linux**

Run the following commands in your terminal:

```plaintext
# Download AzCopy  
wget https://aka.ms/downloadazcopy-v10-linux  

# Expand Archive  
tar -xvf downloadazcopy-v10-linux  

# (Optional) Remove existing AzCopy version  
sudo rm /usr/bin/azcopy  

# Move AzCopy to the destination you want to store it  
sudo cp ./azcopy_linux_amd64_*/azcopy /usr/bin/

# Verify installation  
azcopy --version
```

If the installation is successful, you should see the AzCopy version displayed.

## Step 3: Create a Shell Script to Back Up Docker Volume

### 3.1 Write the Backup Script

Create a new shell script file:

```plaintext
nano /home/azureuser/docker_volume_backup.sh
```

Add the following content:

```plaintext
#!/bin/bash

# Variables
VOLUME_NAME="volume_name"
AZURE_STORAGE_URL="https://serverbackuplogs.blob.core.windows.net/terranex"
SAS_TOKEN="your-token"
TIMESTAMP=$(date +"%d-%m-%Y_%H-%M-%S")

# Ensure azcopy is installed
if ! command -v azcopy &> /dev/null
then
    echo "🚧AzCopy is not installed. Please install it first.🚧"
    exit 1
fi

# Create a temporary container and mount the volume, then directly stream to Azure
echo "⌛Copying Docker volume: $VOLUME_NAME directly to Azure Blob Storage⌛..."
docker run --rm -v $VOLUME_NAME:/volume alpine tar -czf - -C /volume . | azcopy copy "https://serverbackuplogs.blob.core.windows.net/uatlogs/$TIMESTAMP.tar.gz?${SAS_TOKEN}" --from-to=PipeBlob

if [ $? -eq 0 ]; then
    echo "Backup successfully uploaded to Azure Blob Storage as $TIMESTAMP.tar.gz."
else
    echo "Upload failed!"
    exit 1
fi

echo "✅Backup process completed.✅"
```

### Explanation of the Script

1. **Define Variables:**
    
    * `VOLUME_NAME`: Specifies the Docker volume to be backed up.
        
    * `AZURE_STORAGE_URL`: The URL of the Azure Blob Storage container.
        
    * `SAS_TOKEN`: The Shared Access Signature for authentication.
        
    * `TIMESTAMP`: Adds a timestamp to the backup file name.
        
2. **Check if AzCopy is Installed:**
    
    * The script checks whether `azcopy` is installed; if not, it exits with an error message.
        
3. **Backup Process:**
    
    * The script runs a **Docker container** with **Alpine Linux**, mounts the specified Docker volume, compresses it (`tar -czf`), and streams the backup directly to Azure Blob Storage using `azcopy`.
        
4. **Upload Verification:**
    
    * If the upload is successful, a success message is displayed; otherwise, the script exits with an error.
        

### 3.2 Give the Script Execute Permission

```plaintext
chmod +x /home/azureuser/docker_volume_backup.sh
```

---

## Step 4: Automate the Backup with a Cron Job

### 4.1 Add a Cron Job

Edit the crontab file:

```plaintext
crontab -e
```

Add the following line at the end to schedule daily backups at 11 AM:

```plaintext
0 11 * * * /home/azureuser/docker_volume_backup.sh >> /var/log/backup.log 2>&1
```

### 4.2 Save and Exit

* If using **nano**, press `CTRL + X`, then `Y`, and press `Enter`.
    
* If using **vim**, press `ESC`, type `:wq`, and press `Enter`.
    

### 4.3 Verify Cron Job

Run the following command to list scheduled cron jobs:

```plaintext
crontab -l
```

It should display the job scheduled to run at 11 AM daily.

---

## Step 5: Set Up Lifecycle Management to Delete Old Backups

Azure doesn’t delete old backups automatically unless you configure **Lifecycle Management**. To retain only the last **6 days** of backups:

1. Go to your **Storage Account**.
    
2. Navigate to **Data management** &gt; **Lifecycle Management**.
    
3. Click **\+ Add a rule**.
    
4. Configure:
    
    * **Rule Name**: `DeleteOldBackups`
        
    * **Scope**: `terrabackup/`
        
    * **Blob type**: `Block blobs`
        
    * **Days since last modification**: `4`
        
    * **Action**: `Delete the blob`
        
5. Click **Save**.
    

---

## Conclusion

By following this guide, you have successfully:

* Created an **Azure Blob Storage Account** and a **container** for backups.
    
* Generated a **SAS token** for secure access.
    
* Written a **shell script** to backup Docker volumes.
    
* Scheduled a **cron job** for daily automation.
    
* Configured **Azure Lifecycle Management** to remove old backups.
    

This ensures that your Docker volume data is safely backed up and efficiently managed. 🚀