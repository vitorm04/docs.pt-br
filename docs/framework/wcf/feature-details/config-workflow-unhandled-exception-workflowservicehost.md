---
title: "Como configurar um comportamento de exceção não tratado de fluxo de trabalho com o WorkflowServiceHost"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 51b25c86-292c-43e4-8d13-273d2badc8ad
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5b0aa73a1fa96623469e8e3a140e501e7b7a0cfa
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-configure-workflow-unhandled-exception-behavior-with-workflowservicehost"></a><span data-ttu-id="7964e-102">Como configurar um comportamento de exceção não tratado de fluxo de trabalho com o WorkflowServiceHost</span><span class="sxs-lookup"><span data-stu-id="7964e-102">How to: Configure Workflow Unhandled Exception Behavior with WorkflowServiceHost</span></span>
<span data-ttu-id="7964e-103">O <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> é um comportamento que permite que você especifique a ação a ser tomada se uma exceção não tratada ocorrer dentro de um fluxo de trabalho hospedado em <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="7964e-103">The <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> is a behavior that enables you to specify the action to take if an unhandled exception occurs within a workflow hosted in <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span> <span data-ttu-id="7964e-104">Este tópico mostra como configurar esse comportamento em um arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="7964e-104">This topic shows how to configure this behavior in a configuration file.</span></span>  
  
### <a name="to-configure-workflowunhandledexceptionbehavior"></a><span data-ttu-id="7964e-105">Para configurar WorkflowUnhandledExceptionBehavior</span><span class="sxs-lookup"><span data-stu-id="7964e-105">To configure WorkflowUnhandledExceptionBehavior</span></span>  
  
1.  <span data-ttu-id="7964e-106">Adicionar um <`workflowUnhandledException`> elemento em um <`behavior`> elemento dentro de um <`serviceBehaviors`> elemento, usando o `action` atributo para especificar a ação a ser tomada quando uma exceção não tratada ocorre conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="7964e-106">Add a <`workflowUnhandledException`> element in a <`behavior`> element within a <`serviceBehaviors`> element, using the `action` attribute to specify the action to take when an unhandled exception occurs as shown in the following example.</span></span>  
  
    ```xml  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="">  
          <workflowUnhandledException action="abandonAndSuspend"/>   
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="7964e-107">O exemplo de configuração anterior estiver usando a configuração simplificada.</span><span class="sxs-lookup"><span data-stu-id="7964e-107">The preceding configuration sample is using simplified configuration.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="7964e-108">[Simplificado configuração](../../../../docs/framework/wcf/simplified-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="7964e-108"> [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md).</span></span>  
  
     <span data-ttu-id="7964e-109">Esse comportamento pode ser configurado no código, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="7964e-109">This behavior can be configured in code as shown in the following example.</span></span>  
  
    ```csharp  
    host.Description.Behaviors.Add(new WorkflowUnhandledExceptionBehavior { Action = WorkflowUnhandledExceptionAction.AbandonAndSuspend });  
    ```  
  
     <span data-ttu-id="7964e-110">O `action` atributo do <`workflowUnhandledException`> elemento pode ser definido como um dos seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="7964e-110">The `action` attribute of the <`workflowUnhandledException`> element can be set to one of the following values:</span></span>  
  
     <span data-ttu-id="7964e-111">**abandono**</span><span class="sxs-lookup"><span data-stu-id="7964e-111">**abandon**</span></span>  
     <span data-ttu-id="7964e-112">Anula a instância na memória sem tocar o estado da instância persistente (isto é, reverter para o último ponto de persistência).</span><span class="sxs-lookup"><span data-stu-id="7964e-112">Aborts the instance in memory without touching the persisted instance state (that is, roll back to the last persist point).</span></span>  
  
     <span data-ttu-id="7964e-113">**abandonAndSuspend**</span><span class="sxs-lookup"><span data-stu-id="7964e-113">**abandonAndSuspend**</span></span>  
     <span data-ttu-id="7964e-114">Anula a instância na memória e atualiza a instância persistente para ser suspenso.</span><span class="sxs-lookup"><span data-stu-id="7964e-114">Aborts the instance in memory and updates the persisted instance to be suspended.</span></span>  
  
     <span data-ttu-id="7964e-115">**Cancelar**</span><span class="sxs-lookup"><span data-stu-id="7964e-115">**cancel**</span></span>  
     <span data-ttu-id="7964e-116">Chama manipuladores de cancelamento para a instância e, em seguida, conclui a instância na memória, o que também pode removê-lo do repositório de instância</span><span class="sxs-lookup"><span data-stu-id="7964e-116">Calls cancellation handlers for the instance and then completes the instance in memory, which may also remove it from the instance store</span></span>  
  
     <span data-ttu-id="7964e-117">**terminate**</span><span class="sxs-lookup"><span data-stu-id="7964e-117">**terminate**</span></span>  
     <span data-ttu-id="7964e-118">Conclui a instância na memória e a remove do repositório de instância.</span><span class="sxs-lookup"><span data-stu-id="7964e-118">Completes the instance in memory and removes it from the instance store.</span></span>  
  
     [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="7964e-119"><xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>, consulte [extensibilidade de Host do serviço de fluxo de trabalho](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md).</span><span class="sxs-lookup"><span data-stu-id="7964e-119"> <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>, see [Workflow Service Host Extensibility](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7964e-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7964e-120">See Also</span></span>  
 [<span data-ttu-id="7964e-121">Extensibilidade de host de serviço de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="7964e-121">Workflow Service Host Extensibility</span></span>](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)  
 [<span data-ttu-id="7964e-122">Serviços de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="7964e-122">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)
