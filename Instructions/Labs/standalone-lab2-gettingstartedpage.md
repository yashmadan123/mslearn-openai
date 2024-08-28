# Develop Generative AI solutions with Azure OpenAI Service Workshop

## Overall Estimated Duration: 1 Hour

## Overview

The purpose of this lab is to enable you to effectively integrate Azure OpenAI Service into your applications, focusing on AI-driven functionalities. Through this lab, you will create and configure an Azure OpenAI resource, deploy and interact with a language model, and build a command-line application in Azure Cloud Shell. Additionally, you will learn to manage conversation history to enhance the contextual relevance of AI responses. This lab offers a professional, hands-on approach to understanding and applying Azure OpenAI capabilities in real-world scenarios.

## Objective

By the end of this lab, you will have:

- **Azure OpenAI Integration**: This hands-on lab will guide you in gaining proficiency in integrating Azure OpenAI Service into your applications to leverage AI-driven functionalities.

- **Create and Configure Azure OpenAI Resources**: This hands-on lab will guide you in setting up and configuring an Azure OpenAI resource to facilitate the deployment of language models.

- **Deploy and Interact with Language Models**: This hands-on lab will guide you in deploying a language model and using a command-line application in Azure Cloud Shell to interact with it, understanding its role in processing natural language.

- **Manage Conversation History**: This hands-on lab will guide you in learning how to manage conversation history to ensure that AI responses remain contextually relevant and meaningful.

- **Develop Practical AI-Powered Applications**: This hands-on lab will guide you in acquiring experience in building AI-powered applications, effectively applying Azure OpenAI capabilities in real-world scenarios.

## Pre-Requisites

You should have a basic understanding of **Azure services**, including **Azure OpenAI** and **Azure Cloud Shell**. Familiarity with **command-line interfaces** and a foundational knowledge of programming concepts are also required.

## Architecture

This diagram outlines the process for setting up and running an AI application. It begins with the creation of a Resource Group, which serves as the container for all related Azure resources. Within this Resource Group, an OpenAI resource is established to support AI model deployment. Following this, a new AI model is deployed to the OpenAI resource. The next step involves setting up a CloudsHell app, which is then configured to meet specific requirements. Finally, the configured app is executed, completing the process. This structured workflow progresses from initial resource creation through model deployment and app configuration, leading to the successful execution of the AI application.

## Architecture Diagram

![](../media/28-08-2024.png "Architecture Diagram")

## Accessing Your Lab Environment
 
Once you're ready to dive in, your virtual machine and lab guide will be right at your fingertips within your web browser.
 
![Access Your VM and Lab Guide](../media/labguide-1.png)

### Virtual Machine & Lab Guide
 
Your virtual machine is your workhorse throughout the workshop. The lab guide is your roadmap to success.
 
## Exploring Your Lab Resources
 
To get a better understanding of your lab resources and credentials, navigate to the **Environment Details** tab.
 
![Explore Lab Resources](../media/env-1.png)
 
## Utilizing the Split Window Feature
 
For convenience, you can open the lab guide in a separate window by selecting the **Split Window** button from the Top right corner.
 
![Use the Split Window Feature](../media/spl.png)
 
## Managing Your Virtual Machine
 
Feel free to start, stop, or restart your virtual machine as needed from the **Resources** tab. Your experience is in your hands!
 
![Manage Your Virtual Machine](../media/res.png)

## Lab Validation

1. After completing the task, hit the **Validate** button under Validation tab integrated within your lab guide. If you receive a success message, you can proceed to the next task, if not, carefully read the error message and retry the step, following the instructions in the lab guide.

   ![Inline Validation](../media/inline-validation.png)

1. You can also validate the task by navigating to the **Lab Validation** tab, from the upper right corner in the lab guide section.

   ![Lab Validation](../media/lab-validation.png)

1. If you need any assistance, please contact us at labs-support@spektrasystems.com.

## **Lab Duration Extension**

1. To extend the duration of the lab, kindly click the **Hourglass** icon in the top right corner of the lab environment. 

    ![Manage Your Virtual Machine](../media/gext.png)

    >**Note:** You will get the **Hourglass** icon when 10 minutes are remaining in the lab.

2. Click **OK** to extend your lab duration.
 
   ![Manage Your Virtual Machine](../media/gext2.png)

3. If you have not extended the duration prior to when the lab is about to end, a pop-up will appear, giving you the option to extend. Click **OK** to proceed. 

## Let's Get Started with Azure Portal
 
1. On your virtual machine, click on the Azure Portal icon as shown below:
 
   ![Launch Azure Portal](../media/sc900-image(1).png)
 
2. You'll see the **Sign into Microsoft Azure** tab. Here, enter your credentials:
 
   - **Email/Username:** <inject key="AzureAdUserEmail"></inject>
 
       ![Enter Your Username](../media/sc900-image-1.png)
 
3. Next, provide your password:
 
   - **Password:** <inject key="AzureAdUserPassword"></inject>
 
       ![Enter Your Password](../media/sc900-image-2.png)
 
4. If prompted to stay signed in, you can click "No."
 
5. If a **Welcome to Microsoft Azure** pop-up window appears, simply click "Maybe Later" to skip the tour.
 
6. Click "Next" from the bottom right corner to embark on your Lab journey!
 
     ![Start Your Azure Journey](../media/sc900-image(3).png)
 
Now you're all set to explore the powerful world of technology. Feel free to reach out if you have any questions along the way. Enjoy your workshop!
