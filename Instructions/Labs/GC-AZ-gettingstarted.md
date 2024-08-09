# Develop Generative AI solutions with Azure OpenAI Service
### Overall Estimated Duration: 8 Hours
### Overview

This hands-on labs, you'll use Azure OpenAI Service models to simplify and explain complex code, help understand code functionality, and suggest improvements. These models are capable of generating code, fixing bugs, and providing helpful comments using natural language prompts, enhancing the coding experience by allowing developers to describe their intentions in plain language. Additionally, the Azure OpenAI Service includes the DALL-E model, which can generate original images from natural language descriptions, further expanding your creative capabilities.

## Objective 

This lab aims to give learners hands-on experience with Azure OpenAI Service models, allowing them to deploy and explore these models using the Completions and Chat playgrounds. Participants will experiment with natural language prompts, adjust parameters, and engage in code generation, bug fixing, and code explanation. Additionally, learners will explore the DALL-E model for generating images from text descriptions, further enhancing their understanding of Azure OpenAI resources.

Participants will learn:

**Generate and Improve Code with Azure OpenAI Service**: This hands-on exercise aims to teach participants how to effectively generate and enhance code using Azure OpenAI Service tools. Participants will learn to leverage natural language prompts to create, refine, and debug code, improving their coding skills with the help of AI-driven models.

**Generate Images with the DALL-E Model**: In this activity, participants will learn to create and modify images using the DALL-E model. By crafting and adjusting natural language prompts, they will explore how to generate specific visual outcomes, enhancing their ability to use AI for creative purposes.

### Prerequisites
Participants should have:

1. **Development Skills**: Basic programming knowledge and experience with APIs and SDKs.
2. **AI Concepts**: Understanding prompt engineering, code development, and image generation using models such as DALL-E.
3. **Content Management**: Understanding data integration for RAG and content filtering techniques.
   
### Architecture

This lab provides robust functionalities for leveraging AI within Azure. Azure OpenAI integrates your data with large language models, enabling customized and secure interactions tailored to your needs. Azure OpenAI Models offer pre-trained and customizable models for various applications, such as text generation and language translation. Azure CloudShell provides an online, browser-based shell for managing Azure resources and running scripts, streamlining cloud management. DALL-E generates images from textual descriptions using advanced AI technology, enhancing creative capabilities. Finally, prompt engineering refines input prompts to optimize AI model responses, ensuring accuracy and relevance in outputs.

### Architecture Diagram

![](../media/blank_diagram_1.JPG "Lab Environment")

### Explanation of Components

- **Azure OpenAI**: Integrates your data with massive language models, allowing for personalized and secure interactions.Allows for fine-tuning of AI models with your own datasets, resulting in specialized and relevant outputs for your business needs.
- **Azure OpenAI Models**: Provides pre-trained and customisable big language models for a variety of AI applications, including text generation, sentiment analysis, and language translation, with the option to tailor models to specific use cases.
- **Azure CloudShell**: Offers an online, browser-based shell for managing Azure resources and running scripts.Allows you to deploy, manage, and automate Azure services directly from your web browser, eliminating the need for local installations.
- **DALL-E**: DALL-E uses artificial intelligence technology to generate visuals from written descriptions.Enhances creativity by translating word inputs into distinct and coherent pictures.
- **Prompt Engineering**: Prompt engineering fine-tunes input prompts to improve AI model replies, ensuring accurate and relevant outputs by optimizing how prompts are produced and delivered to AI models.
- **AI chat**: AI chat also known as an AI chatbot or conversational AI, is a technology that uses artificial intelligence to facilitate automated, human-like conversations between machines and users. These systems are designed to understand and interpret natural language inputs, enabling them to respond in a way that simulates a real conversation.

## Getting Started with Lab

1. Once the environment is provisioned, a virtual machine (JumpVM) and lab guide will get loaded in your browser. Use this virtual machine throughout the workshop to perform the lab. You can see the number on the lab guide bottom area to switch to different exercises of the lab guide.

   ![](../media/getting-started1.png "Lab Environment")
   
1. To get the lab environment details, you can select the **Environment Details** tab. Additionally, the credentials will also be emailed to your email address provided during registration. You can start, stop, and restart virtual machines from the **Resources** tab.

   ![](../media/envdetails.png "Lab Environment")

## Login to Azure Portal
1. In the JumpVM, click on Azure portal shortcut of Microsoft Edge browser which is created on desktop.

   ![](../media/azureportal_icon1.png "Lab Environment")
   
1. On **Sign into Microsoft Azure** tab you will see login screen, in that enter following email/username and then click on **Next**. 
   * Email/Username: <inject key="AzureAdUserEmail"></inject>
   
     ![](../media/image7.png "Enter Email")
     
1. Now enter the following password and click on **Sign in**.
   * Password: <inject key="AzureAdUserPassword"></inject>
   
     ![](../media/image8.png "Enter Password")
     
1. If you see the pop-up **Action Required**, click **Ask Later**.

     ![](../media/asklater.png "Action required window")
     
    > If you are getting popup **save password**, then select **Save & Turn on** option.
       
1. If you see the pop-up **Stay Signed in?**, click **No**.

1. If you see the pop-up **You have free Azure Advisor recommendations!**, close the window to continue the lab.

1. If a **Welcome to Microsoft Azure** popup window appears, click **Maybe Later** to skip the tour.

1. Now you will see Azure Portal Dashboard, click on **Resource groups** from the Navigate panel to see the resource groups.

     ![](../media/select-rg.png "Resource groups")

1. Confirm you have a resource group **openai-<inject key="Deployment-id" enableCopy="false"/>** present as shown in the below screenshot. You need to use the **openai-<inject key="Deployment-id" enableCopy="false"/>** resource group throughout the entire process of lab execution.

     ![](../media/rg.png "Resource groups")
   
1. Use **Next** button from lower right corner to move on to the next page.

   ![](../media/next1.png "Resource groups")


This hands-on lab empowers participants to master Azure OpenAI Service by guiding them through setup, SDK integration, and prompt engineering. It also covers code generation, image creation with DALL-E, RAG data integration, and content filtering for comprehensive learning.

### Support Contact
 
The CloudLabs support team is available 24/7, 365 days a year, via email and live chat to ensure seamless assistance at any time. We offer dedicated support channels tailored specifically for both learners and instructors, ensuring that all your needs are promptly and efficiently addressed.

Learner Support Contacts:

- Email Support: labs-support@spektrasystems.com
- Live Chat Support: https://cloudlabs.ai/labs-support

### Happy learning !
