---
title: 'Como: configurar um comportamento de exceção sem tratamento de fluxo de trabalho com WorkflowServiceHost'
ms.date: 03/30/2017
ms.assetid: 51b25c86-292c-43e4-8d13-273d2badc8ad
ms.openlocfilehash: 8f7fe203a4198aa98e8aee1be3a12e4d72a066f8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59175403"
---
# <a name="how-to-configure-workflow-unhandled-exception-behavior-with-workflowservicehost"></a><span data-ttu-id="3a82f-102">Como: configurar um comportamento de exceção sem tratamento de fluxo de trabalho com WorkflowServiceHost</span><span class="sxs-lookup"><span data-stu-id="3a82f-102">How to: Configure Workflow Unhandled Exception Behavior with WorkflowServiceHost</span></span>
<span data-ttu-id="3a82f-103">O <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> é um comportamento que permite que você especifique a ação a ser tomada se uma exceção sem tratamento ocorrer dentro de um fluxo de trabalho hospedado no <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="3a82f-103">The <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> is a behavior that enables you to specify the action to take if an unhandled exception occurs within a workflow hosted in <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span> <span data-ttu-id="3a82f-104">Este tópico mostra como configurar esse comportamento em um arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="3a82f-104">This topic shows how to configure this behavior in a configuration file.</span></span>  
  
### <a name="to-configure-workflowunhandledexceptionbehavior"></a><span data-ttu-id="3a82f-105">Para configurar WorkflowUnhandledExceptionBehavior</span><span class="sxs-lookup"><span data-stu-id="3a82f-105">To configure WorkflowUnhandledExceptionBehavior</span></span>  
  
1.  <span data-ttu-id="3a82f-106">Adicione um <`workflowUnhandledException`> elemento em um <`behavior`> elemento dentro de um <`serviceBehaviors`> elemento, usando o `action` atributo para especificar a ação a ser tomada quando uma exceção sem tratamento ocorre conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="3a82f-106">Add a <`workflowUnhandledException`> element in a <`behavior`> element within a <`serviceBehaviors`> element, using the `action` attribute to specify the action to take when an unhandled exception occurs as shown in the following example.</span></span>  
  
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
    >  <span data-ttu-id="3a82f-107">O exemplo de configuração anterior está usando a configuração simplificada.</span><span class="sxs-lookup"><span data-stu-id="3a82f-107">The preceding configuration sample is using simplified configuration.</span></span> <span data-ttu-id="3a82f-108">Para obter mais informações, consulte [simplificado configuração](../../../../docs/framework/wcf/simplified-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="3a82f-108">For more information, see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md).</span></span>  
  
     <span data-ttu-id="3a82f-109">Esse comportamento pode ser configurado no código, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="3a82f-109">This behavior can be configured in code as shown in the following example.</span></span>  
  
    ```csharp  
    host.Description.Behaviors.Add(new WorkflowUnhandledExceptionBehavior { Action = WorkflowUnhandledExceptionAction.AbandonAndSuspend });  
    ```  
  
     <span data-ttu-id="3a82f-110">O `action` atributo da <`workflowUnhandledException`> elemento pode ser definido como um dos seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="3a82f-110">The `action` attribute of the <`workflowUnhandledException`> element can be set to one of the following values:</span></span>  
  
     **<span data-ttu-id="3a82f-111">abandonar</span><span class="sxs-lookup"><span data-stu-id="3a82f-111">abandon</span></span>**  
     <span data-ttu-id="3a82f-112">Anula a instância na memória sem tocar o estado da instância persistentes (isto é, reverter para o último ponto de persistência).</span><span class="sxs-lookup"><span data-stu-id="3a82f-112">Aborts the instance in memory without touching the persisted instance state (that is, roll back to the last persist point).</span></span>  
  
     **<span data-ttu-id="3a82f-113">abandonAndSuspend</span><span class="sxs-lookup"><span data-stu-id="3a82f-113">abandonAndSuspend</span></span>**  
     <span data-ttu-id="3a82f-114">Anula a instância na memória e atualiza a instância persistida deve ser suspensa.</span><span class="sxs-lookup"><span data-stu-id="3a82f-114">Aborts the instance in memory and updates the persisted instance to be suspended.</span></span>  
  
     **<span data-ttu-id="3a82f-115">cancelar</span><span class="sxs-lookup"><span data-stu-id="3a82f-115">cancel</span></span>**  
     <span data-ttu-id="3a82f-116">Chama os manipuladores de cancelamento para a instância e, em seguida, conclui a instância na memória, que também pode removê-lo do repositório de instância</span><span class="sxs-lookup"><span data-stu-id="3a82f-116">Calls cancellation handlers for the instance and then completes the instance in memory, which may also remove it from the instance store</span></span>  
  
     **<span data-ttu-id="3a82f-117">terminate</span><span class="sxs-lookup"><span data-stu-id="3a82f-117">terminate</span></span>**  
     <span data-ttu-id="3a82f-118">Conclui a instância na memória e o remove do armazenamento de instância.</span><span class="sxs-lookup"><span data-stu-id="3a82f-118">Completes the instance in memory and removes it from the instance store.</span></span>  
  
     <span data-ttu-id="3a82f-119">Para obter mais informações sobre <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>, consulte [extensibilidade de Host de serviço de fluxo de trabalho](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md).</span><span class="sxs-lookup"><span data-stu-id="3a82f-119">For more information about <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>, see [Workflow Service Host Extensibility](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a82f-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3a82f-120">See also</span></span>

- [<span data-ttu-id="3a82f-121">Extensibilidade de host de serviço do fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="3a82f-121">Workflow Service Host Extensibility</span></span>](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)
- [<span data-ttu-id="3a82f-122">Serviços de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="3a82f-122">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)
