---
author: karlerickson
ms.author: v-shilichen
ms.service: azure-spring-apps
ms.topic: include
ms.date: 10/18/2023
---

<!-- 
To reuse the Spring Apps instance creation steps in other articles, a separate markdown file is used to describe how to provision Spring Apps instance for RESTful API app.

[!INCLUDE [provision-enterprise-azure-spring-apps](provision-enterprise-azure-spring-apps.md)]

-->

Use the following steps to create the service instance:

1. Select **Create a resource** in the corner of the Azure portal.

1. Select **Compute** > **Azure Spring Apps**.

   :::image type="content" source="../../media/quickstart-deploy-web-app/create-azure-spring-apps.png" alt-text="Screenshot of the Azure portal that shows Azure Spring Apps in the list of compute resources." lightbox="../../media/quickstart-deploy-web-app/create-azure-spring-apps.png":::

1. Fill out the **Basics** form with the following information:

   | Setting                   | Suggested value                   | Description                                                                                                                                                                                                                                                                                        |
   |---------------------------|-----------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   | **Subscription**          | Your subscription name.           | The  Azure subscription that you want to use for your server. If you have multiple subscriptions, choose the subscription in which you'd like to be billed for the resource.                                                                                                                       |
   | **Resource group**        | **myresourcegroup**                 | A new resource group name or an existing one from your subscription.                                                                                                                                                                                                                               |
   | **Name**                  | **myasa**                           | A unique name that identifies your Azure Spring Apps service. The name must be between 4 and 32 characters long and can contain only lowercase letters, numbers, and hyphens. The first character of the service name must be a letter and the last character must be either a letter or a number. |
   | **Plan**                  | **Enterprise**                    | The pricing plan that determines the resource and cost associated with your instance.                                                                                                                                                                                                              |
   | **Region**                | The region closest to your users. | The location that is closest to your users.                                                                                                                                                                                                                                                        |
   | **Zone Redundant**        | Unselected                        | The option to create your Azure Spring Apps service in an Azure availability zone. This feature isn't currently supported in all regions.                                                                                                                                                          |
   | **Software IP plan**      | Pay-as-You-Go                     | Pay as you go with Azure Spring Apps.                                                                                                                                                                                                                                                              |
   | **Terms**                 | Selected                          | The agreement checkbox associated with [Marketplace offering](https://aka.ms/ascmpoffer). You're required to select this checkbox.                                                                                                                                                                 |
   | **Deploy sample project** | Unselected                        | The option to use the built-in sample application.                                                                                                                                                                                                                                                 |

   :::image type="content" source="../../media/quickstart-deploy-web-app/create-enterprise-basics.png" alt-text="Screenshot of the Azure portal that shows the Create Azure Spring Apps page." lightbox="../../media/quickstart-deploy-web-app/create-enterprise-basics.png":::

1. Select **Review and Create** to review your selections. Then, select **Create** to provision the Azure Spring Apps instance.

1. On the toolbar, select the **Notifications** icon (a bell) to monitor the deployment process. After the deployment finishes, you can select **Pin to dashboard**, which creates a tile for this service on your Azure portal dashboard as a shortcut to the service's **Overview** page.

   :::image type="content" source="../../media/quickstart-deploy-web-app/notifications.png" alt-text="Screenshot of the Azure portal that shows the Notifications pane for Azure Spring Apps creation." lightbox="../../media/quickstart-deploy-web-app/notifications.png":::

1. Select **Go to resource** to go to the **Azure Spring Apps Overview** page.
