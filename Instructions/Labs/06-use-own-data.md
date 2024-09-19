# Lab 06: Add your data for RAG with Azure OpenAI Service

## Lab scenario
The Azure OpenAI Service enables you to use your own data with the intelligence of the underlying LLM. You can limit the model to only use your data for pertinent topics, or blend it with results from the pre-trained model.

## Lab objectives
In this lab, you will complete the following tasks:
- Task 1 : Deploy a model
- Task 2: Observe normal chat behavior without adding your own data
- Task 3: Connect your data in the chat playground
- Task 4: Chat with a model grounded in your data
- Task 5: Set up an application in Cloud Shell
- Task 6: Configure your application
- Task 7: Run your application

## Estimated time: 60 minutes

### Task 1: Deploy a model

To chat with the Azure OpenAI, you must first deploy a model to use through the **Azure OpenAI Studio**. Once deployed, we will use the model with the playground and use our data to ground its responses.

1. In the **Azure portal**, search for **OpenAI** and select **Azure OpenAI**.

   ![](../media/openai8.png)

2. On **Azure AI Services | Azure OpenAI** blade, select **OpenAI-Lab01-<inject key="DeploymentID	" enableCopy="false"></inject>**

   ![](../media/OpenAI_select.png)

3. To capture the Keys and Endpoints values, on **openai-<inject key="DeploymentID" enableCopy="false"></inject>** blade:
      - Select **Keys and Endpoint (1)** under **Resource Management**.
      - Click on **Show Keys (2)**.
      - Copy **Key 1 (3)** and ensure to paste it in a text editor such as notepad for future reference.
      - Finally copy the **Endpoint (4)** API URL by clicking on copy to clipboard. Paste it in a text editor such as notepad for later use.

        ![](../media/openai-endpoint-new.png "Keys and Endpoints")

4. In the **Overview** pane, click on **Go to Azure OpenAI Studio** it will navaigate to **Azure AI Studio**.

   ![](../media/openai_studio.png)

5. In the Azure OpenAI resource pane, click on **Go to Azure OpenAI Studio** it will navigate to **Azure AI Studio**.

   ![](../media/openai_studio1.png)


6. In the **Deployments (1)** page, click on **+ Deploy model** , Choose **Deploy base Model (2)**.

      ![](../media/deploy-1.jpg "Create a new deployment")
   
7. Search for **GPT-4**, click on **Confirm**

      ![](../media/gpt-4.jpg)
  

8. Within the **Deploy model** pop-up interface, enter the following details:
   
    - **Deployment name**: text-turbo-1 
    - **Model version**: 1106-Preview 
    - **Deployment type**: Standard 
    - Click on **Advanced Settings** 
    - **Tokens per Minute Rate Limit (thousands)**: 10K 
    - **Enable dynamic quota**: Enabled 
    - Click on **Deploy** 
    
    >**Note:** Ensure to set the **Tokens per Minute Rate Limit** to atleast **5K**. Select the Rate Limit scroll bar, and use your keyboard's arrow keys to pinpoint specific token limits.

10. Click on the **Create** button to deploy a model which you will be playing around with as you proceed.

#### Validation

   <validation step="2260bf34-007f-488b-99e5-6138f7cece20" />
   
   > **Congratulations** on completing the task! Now, it's time to validate it. Here are the steps:
   > - Hit the Validate button for the corresponding task. If you receive a success message, you can proceed to the next task. 
   > - If not, carefully read the error message and retry the step, following the instructions in the lab guide.
   > - If you need any assistance, please contact us at labs-support@spektrasystems.com. We are available 24/7 to help you out.


### Task 2: Observe normal chat behavior without adding your own data

Before connecting Azure OpenAI to your data, first observe how the base model responds to queries without any grounding data.

1. In the **Playground** section, select the **Chat** page. The **Chat** playground page consists of three main sections:

     - **Setup** - used to set the context for the model's responses.
    - **Chat session** - used to submit chat messages and view responses.
    - **Deployment** - used to configure settings for the model deployment.

3. In the **Deployment** section, ensure that your model deployment `text-turbo-1 (version:1106-Preview)` is selected.
4. In the **Setup** area, select the default system message template to set the context for the chat session. The default system message is *You are an AI assistant that helps people find information*.
5. In the **Chat session**, submit the following queries, and review the responses:

    ```
    I'd like to take a trip to New York. Where should I stay?
    ```

    ```
    What are some facts about New York?
    ```

    Try similar questions about tourism and places to stay for other locations that will be included in our grounding data, such as London, or San Francisco. You'll likely get complete responses about areas or neighborhoods, and some general facts about the city.


### Task 3: Connect your data in the chat playground

Next, add your data in the chat playground to see how it responds with your data as grounding

1. Copy the URL (https://aka.ms/own-data-brochures) and paste it in the browser. Extract the PDFs in the `.zip` that get downloaded.
   
2. In the **Azure portal**, search for **Storage Account** and select **Storage Account**.

      ![](../media/1.png)

3. On **Storage Account** page, click on **Create**.

      ![](../media/2.png)

4. Create a **Storage Account** resource with the following settings:

    - **Subscription**: Default - Pre-assigned subscription
    - **Resource group**: openai-<inject key="DeploymentID	" enableCopy="false"></inject>
    - **Storage account name**: storage<inject key="DeploymentID	" enableCopy="false"></inject>
    - **Region**: Select <inject key="Region" enableCopy="false" />
    - **Redundancy**: Locally-redundant storage (LRS)

    - Select **Next**
  
      ![](../media/openai-lab06_t4_s4.png "Create storage account")

    - **Allow enable anonymous access on individual containers**: check in the box to enable under advance section. Click on **Review + Create**  and subsequently click on **Create**

      ![](../media/image4.5.png "allow blob access")

5. Wait until the storage account is created before you proceed to the next task. This should take about a minute.

6. On the deployment blade, click **Go to resource**.

      ![](../media/3.png "upload files")

7. On the **Storage Account** blade, from the left navigation, select **Containers (1)**.

8. On **Storage Account | Containers** blade, click on **+ Container (2)**

     ![](../media/storage-container.png "upload files")

9. Create a container with the name "**openaidatasource**" and enable Anonymous access level for container.

      ![](../media/image4.6.png "create container")

10. Select the **openaidatasource** container, and select **Upload**.

11. Upload all the files into the container which are downlaoded and extracted during the first step of Task 4.

      ![](../media/image4.7.png "upload files")

12. In the **Azure portal**, search for **AI search** and select **AI search**.

13.  On **Azure AI services | AI search** blade, click on **+ Create**.

     ![](../media/5.png "upload files")

14. Create an **AI Search** resource with the following settings and click on **Review + create** and subsequenly click on **Create**

    - **Subscription**: Default - Pre-assigned subscription
    - **Resource group**: **openai-<inject key="DeploymentID	" enableCopy="false"></inject>**
    - **Service name**: **cognitive-search-<inject key="DeploymentID	" enableCopy="false"></inject>**
    - **Location**: Select **<inject key="Region" enableCopy="false" />**
    - **Pricing tier**: Basic

      ![](../media/lab06-1.png "Create cognitive search resource")

15. Wait until your search resource has been deployed. Select **Go to resources**.

16. Navigate to the **cognitive-search-<inject key="DeploymentID	" enableCopy="false"></inject>** and in the overview page copy the URL and paste it in a text editor such as notepad for later use.

    ![](../media/x689.png)

17. From the left navigation pane, under **Settings**, click on **Keys** and copy the primary admin key or secondary admin key and paste it in a notepad file for later use.

    ![](../media/keys-cognitive.png)

18. Navigate back to the **Chat playground** in **Azure OpenAI Studio**, select *Add your data* in the setup pane and click on **+ Add a data source**.

    ![](../media/image4.2.png "Add your data in setup pane")
   
19. In the **Add data**, enter the following values for your data source and then click on **Next**.

    - **Select data source (1)**: Azure Blob Storage (preview)
    - **Select Azure Blob storage resouce (2)**: *Choose the storage resource you created*
    - **Select storage container (3)**: openaidatasource
    - **Select Azure AI Search resource (4)**: *Choose the search resource you created*
    - **Enter the index name (5)**: margiestravel
    - **Indexer schedule (6)**: Once

20. Click on **Next (7)** to proceed with "**Data Management**".

    ![](../media/image4.8.png "Add data configurations")
   
21. On the **Data management** page select the **Keyword** search type from the drop-down, and then select **Next**.

    ![](../media/datamanagement.png "Add data")

22. On the **Data Connection** page select the **API key** , and then select **Next**.

    ![](../media/API_key_1.png "Add data")
   
23. On the **Review and finish** page select **Save and close**, which will add your data. This may take a few minutes, during which you need to leave your window open. Once completed, verify if the data source, search resource, and index specified **margiestravel** is present under the **Add your data** tab in **Setup** pane.

#### Validation

   <validation step="3c975bfb-3c4f-421d-aadb-dd85292aad6f" />
      
   > **Congratulations** on completing the task! Now, it's time to validate it. Here are the steps:
   > - Hit the Validate button for the corresponding task. If you receive a success message, you can proceed to the next task. 
   > - If not, carefully read the error message and retry the step, following the instructions in the lab guide.
   > - If you need any assistance, please contact us at labs-support@spektrasystems.com. We are available 24/7 to help you out.

### Task 4: Chat with a model grounded in your data

Now that you've added your data, ask the same questions as you did previously, and see how the response differs.

   ```
   I'd like to take a trip to New York. Where should I stay?
   ```

   ```
   What are some facts about New York?
   ```

You'll notice a very different response this time, with specifics about certain hotels and a mention of Margie's Travel, as well as references to where the information provided came from. If you open the PDF reference listed in the response, you'll see the same hotels as the model provided.

Try asking it about other cities included in the grounding data, which are Dubai, Las Vegas, London, and San Francisco.

> **Note**: **Add your data** is still in preview and might not always behave as expected for this feature, such as giving the incorrect reference for a city not included in the grounding data.

### Task 5: Set up an application in Cloud Shell

To show how to integrate with an Azure OpenAI model, we'll use a short command-line application that runs in Cloud Shell on Azure. Open up a new browser tab to work with Cloud Shell.

1. In the [Azure portal](https://portal.azure.com?azure-portal=true), select the **[>_]** (*Cloud Shell*) button at the top of the page to the right of the search box. A Cloud Shell pane will open at the bottom of the portal.

    ![Screenshot of starting Cloud Shell by clicking on the icon to the right of the top search box.](../media/cloudshell-launch-portal.png)

2. Make sure the type of shell indicated on the top left of the Cloud Shell pane is switched to *Bash*. If it's *PowerShell*, switch to *Bash* by using the drop-down menu.

3. Once the terminal starts, enter the following command to download the sample application and save it to a folder called `azure-openai`.

    ```bash
   rm -r azure-openai -f
   git clone https://github.com/MicrosoftLearning/mslearn-openai azure-openai
    ```
> **NOTE:** if you get Message saying already cloned , please move the next step.

4. The files are downloaded to a folder named **azure-openai**. Navigate to the lab files for this exercise using the following command.

    ```bash
   cd azure-openai/Labfiles/06-use-own-data
    ```

    Applications for both C# and Python have been provided, as well as sample code we'll be using in this lab.

5. Open the built-in code editor, and you can observe the code files we'll be using in `sample-code`. Use the following command to open the lab files in the code editor.

    ```bash
   code .
    ```
   > **NOTE:** If you're prompted to **Switch to Classic Cloud Shell** after running the **code .** command, click on **Confirm**.

   ![](../media/classic-cloudshell-prompt.png) 

### Task 6: Configure your application

For this exercise, you'll complete some key parts of the application to enable using your Azure OpenAI resource.

1. In the code editor, expand the language folder for your preferred language.

2. Open the configuration file for your language.

    - **C#**: `appsettings.json`
    - **Python**: `.env`

3. Navigate to the folder for your preferred language and install the necessary packages.

     **C#**:

    ```
    cd CSharp
    dotnet add package Azure.AI.OpenAI --version 1.0.0-beta.14
    ```

    **Python**:

    ```
    cd Python
    pip install python-dotenv
    pip install openai==1.13.3
    ```

4. In the code editor from the left navigation pane, in the **CSharp** or **Python** folder, open the configuration file for your preferred language

    - **C#**: appsettings.json
    - **Python**: .env

5. Update the configuration values to include:
    - The  **endpoint** and a **key** from the Azure OpenAI resource you created (Which you copied in the previous task alternatively it is available on the **Keys and Endpoint** page for your Azure OpenAI resource in the Azure portal)
    
    - The **deployment name** you specified for your model deployment (available in the **Deployments** page in Azure OpenAI Studio that is **text-turbo-1**).
    
    - The endpoint for your AI search service (Which you copied in the previous task alternatively it is available in the **Url** value on the overview page for your AI search resource in the Azure portal).
    
    - A **key** for your search resource (available in the **Keys** page for your AI search resource in the Azure portal - you can use either of the admin keys)
    - The name of the search index (which should be `margiestravel`).

    - Press **Ctrl + S** on your keyboard to save the file.

      ![](../media/x676.png)

6. Open the code file for your preferred language, and replace the comment ***Configure your data source*** with code to add the Azure OpenAI SDK library:

    **C#**: OwnData.cs

    ```csharp
    // Configure your data source
    AzureSearchChatExtensionConfiguration ownDataConfig = new()
    {
            SearchEndpoint = new Uri(azureSearchEndpoint),
            Authentication = new OnYourDataApiKeyAuthenticationOptions(azureSearchKey),
            IndexName = azureSearchIndex
    };
    ```

    **Python**: ownData.py

    ```python
    # Configure your data source
    extension_config = dict(dataSources = [  
            { 
                "type": "AzureCognitiveSearch", 
                "parameters": { 
                    "endpoint":azure_search_endpoint, 
                    "key": azure_search_key, 
                    "indexName": azure_search_index,
                }
            }]
        )
    ```

7. Review the rest of the code, noting the use of the *extensions* in the request body that is used to provide information about the data source settings.

8. Press **Ctrl + S** on your keyboard to save the file.


## Task 7: Run your application

Now that your app has been configured, run it to send your request to your model and observe the response. You'll notice the only difference between the different options is the content of the prompt, all other parameters (such as token count and temperature) remain the same for each request.

1. In the interactive terminal pane, ensure the folder context is the folder for your preferred language. Then enter the following command to run the application.

    - **C#**: `dotnet run`
    - **Python**: `python ownData.py`

    > **Tip**: You can use the **Maximize panel size** (**^**) icon in the terminal toolbar to see more of the console text.

2. Review the response to the prompt `Tell me about London`, which should include an answer as well as some details of the data used to ground the prompt, which was obtained from your search service.

## Summary

In this lab, you have accomplished the following:
-   Provisioned an Azure OpenAI resource
-   Deployed an OpenAI model within the Azure OpenAI studio
-   Used the power of OpenAI models to generate responses limited to a custom ingested data.

## Proceed with next lab.
