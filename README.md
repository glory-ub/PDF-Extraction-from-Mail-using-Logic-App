# PDF-Extraction-from-Mail-using-Logic-App

This repository hosts an Azure Logic App workflow specifically designed to streamline and automate the handling of incoming emails and their attachments. The workflow automatically detects and extracts attachments from new emails, filters PDFs and ignore other file types and securely store them in Azure Blob Storage.

**Prerequisites**

•	Azure subscription

•	Logic App

•	Blob Storage

•	Microsoft 365 or Outlook Account

**Workflow**

**Step 1**: Create a resource group in Azure, which serves as a container for related resources within an Azure solution. It provides a logical boundary for organizing and managing these resources efficiently.

![image](https://github.com/user-attachments/assets/e6dc3289-0b09-479f-b767-08140fd3c048)

 
Once the resource group is created, other resources can be provisioned in the resource group.


**Step 2:** Create Azure storage account: Once the storage account is created, Azure Blob Storage will be used to store the extracted PDF attachments.

**Step 3**: Deploy Azure logic app 

 ![image](https://github.com/user-attachments/assets/1cd632ae-f93c-4876-b3cd-256d7b80b87e)


The Logic App automates the extraction of email attachments and their upload to Azure Blob Storage.

**Step 4**: On the storage account, assign Azure Logic App MSI Storage Blob Data Contributor or Storage Blob Data Owner role.

**Step 5**: Create a new workflow in Logic app
![image](https://github.com/user-attachments/assets/ffebb879-80f8-4e75-b448-dd95f4eeb8d6)

 
**Step 6**: Design the Logic App Workflow

![image](https://github.com/user-attachments/assets/15194b76-c12b-438a-b578-9316480d5dba)


•	When a New Email Arrives
 
![image](https://github.com/user-attachments/assets/8ed99749-de3b-40b8-91f2-2ec648c47be2)


Configure the Logic App to trigger when a new email arrives in a specific email account

 ![image](https://github.com/user-attachments/assets/0fdc770c-8dee-4bd9-aac7-dc44e9e31a67)


•	Action: Get Attachments from Emails 

![image](https://github.com/user-attachments/assets/6c2952c1-aaae-4bbd-8e50-f8ae180ee11e)
 

•	Conditions to filter for PDF Attachments: Ensure only PDF attachments are processed.

	Set the condition to check if the mail has attachment, has attachment is equal to true and the File name ends with pdf
	If the condition is true, proceed to the next step.

![image](https://github.com/user-attachments/assets/0694da74-d4a0-4bb2-838a-39a8ea0fde23)
 
•	Upload Attachment to Azure Blob Storage
	Create a connection to blob by using the authentication type of your choice


![image](https://github.com/user-attachments/assets/82613a45-584d-4f4f-8d1d-7c72c3eb1dea)
 
	Use the connection settings from above, set the folder path for storage of the pdf files.
	Configure the “create blob” action to get the file name and the file content.

 ![image](https://github.com/user-attachments/assets/3ec5b73c-c49a-4f76-9590-414412c2ff7d)


•	Test the Workflow

 ![image](https://github.com/user-attachments/assets/4e8baa91-c11a-4adb-a660-2903d6c387f8)

