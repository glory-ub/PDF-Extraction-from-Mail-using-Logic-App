**The following content is AI generated and might contain incorrect information. Before you use this content, make sure to review for inaccuracies.**    
# Summary    
The purpose of this workflow is to listen for new emails with attachments in the Inbox folder and extract PDF attachments. It then creates a blob in Azure Blob Storage for each PDF attachment.    
||Workflow Properties|Value|    
|-----|-----|-----|    
|1|Connector type - In App|2|    
|2|Connector type - Shared|3|    
|3|Connector type - Custom|0|    
|4|API Connections|2|    
    
# Workflow Steps  
## How the workflow starts (Triggers)  
- **When_a_new_email_arrives_(V3)**  
  - **Type:** Shared  
  - **Description:** This trigger is activated when a new email arrives in the specified folder.  
  - **Trigger Input:** The input for this trigger is the email settings and metadata, such as the importance, attachments, and folderPath.  
  - **Trigger Output:** The trigger does not have any outputs.  
  
## How the workflow continues (Actions)  
- **For_each**  
  - **Type:** In App  
  - **Description:** This action allows us to iterate over each attachment in the email.  
  - **Action Output:** The output of this action is the collection of attachments.  
  
  - Actions:  
    - **Get_Attachment_(V2)**  
      - **Type:** Shared  
      - **Description:** This action is used to get the content of each attachment.  
      - **Action Input:** The input for this action is the attachment details, such as the host connection, method (GET), and path (the ID of the email and the ID of the specific attachment).  
      - **Action Output:** The output of this action is the content of the attachment.  
  
    - **Condition**  
      - **Type:** In App  
      - **Description:** This action checks if the attachment is not empty.  
      - **Action Output:** The output of this action is the condition result.  
  
      - Actions:  
        - **Create_blob_(V2)**  
          - **Type:** Shared  
          - **Description:** This action creates a blob in Azure Blob Storage for each non-empty attachment.  
          - **Action Input:** The input for this action is the blob details, such as the host connection, method (POST), body (the binary content of the attachment), headers, path (the path of the destination folder in Azure Blob Storage), and queries (the name of the attachment and the query parameters).  
          - **Action Output:** The output of this action is the created blob in Azure Blob Storage.