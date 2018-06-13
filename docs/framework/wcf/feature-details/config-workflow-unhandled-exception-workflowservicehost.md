---
title: Como configurar um comportamento de exceção não tratado de fluxo de trabalho com o WorkflowServiceHost
ms.date: 03/30/2017
ms.assetid: 51b25c86-292c-43e4-8d13-273d2badc8ad
ms.openlocfilehash: e09575a7998f676ea188a0500f31012c25c19738
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33489187"
---
# <a name="how-to-configure-workflow-unhandled-exception-behavior-with-workflowservicehost"></a><span data-ttu-id="c0f27-102">Como configurar um comportamento de exceção não tratado de fluxo de trabalho com o WorkflowServiceHost</span><span class="sxs-lookup"><span data-stu-id="c0f27-102">How to: Configure Workflow Unhandled Exception Behavior with WorkflowServiceHost</span></span>
<span data-ttu-id="c0f27-103">O <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> é um comportamento que permite que você especifique a ação a ser tomada se uma exceção não tratada ocorrer dentro de um fluxo de trabalho hospedado em <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="c0f27-103">The <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> is a behavior that enables you to specify the action to take if an unhandled exception occurs within a workflow hosted in <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span> <span data-ttu-id="c0f27-104">Este tópico mostra como configurar esse comportamento em um arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="c0f27-104">This topic shows how to configure this behavior in a configuration file.</span></span>  
  
### <a name="to-configure-workflowunhandledexceptionbehavior"></a><span data-ttu-id="c0f27-105">Para configurar WorkflowUnhandledExceptionBehavior</span><span class="sxs-lookup"><span data-stu-id="c0f27-105">To configure WorkflowUnhandledExceptionBehavior</span></span>  
  
1.  <span data-ttu-id="c0f27-106">Adicionar um <`workflowUnhandledException`> elemento em um <`behavior`> elemento dentro de um <`serviceBehaviors`> elemento, usando o `action` atributo para especificar a ação a ser tomada quando uma exceção não tratada ocorre conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="c0f27-106">Add a <`workflowUnhandledException`> element in a <`behavior`> element within a <`serviceBehaviors`> element, using the `action` attribute to specify the action to take when an unhandled exception occurs as shown in the following example.</span></span>  
  
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
    >  <span data-ttu-id="c0f27-107">O exemplo de configuração anterior estiver usando a configuração simplificada.</span><span class="sxs-lookup"><span data-stu-id="c0f27-107">The preceding configuration sample is using simplified configuration.</span></span> <span data-ttu-id="c0f27-108">Para obter mais informações, consulte [configuração simplificada](../../../../docs/framework/wcf/simplified-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="c0f27-108">For more information, see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md).</span></span>  
  
     <span data-ttu-id="c0f27-109">Esse comportamento pode ser configurado no código, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="c0f27-109">This behavior can be configured in code as shown in the following example.</span></span>  
  
    ```csharp  
    host.Description.Behaviors.Add(new WorkflowUnhandledExceptionBehavior { Action = WorkflowUnhandledExceptionAction.AbandonAndSuspend });  
    ```  
  
     <span data-ttu-id="c0f27-110">O `action` atributo do <`workflowUnhandledException`> elemento pode ser definido como um dos seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="c0f27-110">The `action` attribute of the <`workflowUnhandledException`> element can be set to one of the following values:</span></span>  
  
     <span data-ttu-id="c0f27-111">**Abandono**</span><span class="sxs-lookup"><span data-stu-id="c0f27-111">**abandon**</span></span>  
     <span data-ttu-id="c0f27-112">Anula a instância na memória sem tocar o estado da instância persistente (isto é, reverter para o último ponto de persistência).</span><span class="sxs-lookup"><span data-stu-id="c0f27-112">Aborts the instance in memory without touching the persisted instance state (that is, roll back to the last persist point).</span></span>  
  
     <span data-ttu-id="c0f27-113">**abandonAndSuspend**</span><span class="sxs-lookup"><span data-stu-id="c0f27-113">**abandonAndSuspend**</span></span>  
     <span data-ttu-id="c0f27-114">Anula a instância na memória e atualiza a instância persistente para ser suspenso.</span><span class="sxs-lookup"><span data-stu-id="c0f27-114">Aborts the instance in memory and updates the persisted instance to be suspended.</span></span>  
  
     <span data-ttu-id="c0f27-115">**cancel**</span><span class="sxs-lookup"><span data-stu-id="c0f27-115">**cancel**</span></span>  
     <span data-ttu-id="c0f27-116">Chama manipuladores de cancelamento para a instância e, em seguida, conclui a instância na memória, o que também pode removê-lo do repositório de instância</span><span class="sxs-lookup"><span data-stu-id="c0f27-116">Calls cancellation handlers for the instance and then completes the instance in memory, which may also remove it from the instance store</span></span>  
  
     <span data-ttu-id="c0f27-117">**terminate**</span><span class="sxs-lookup"><span data-stu-id="c0f27-117">**terminate**</span></span>  
     <span data-ttu-id="c0f27-118">Conclui a instância na memória e a remove do repositório de instância.</span><span class="sxs-lookup"><span data-stu-id="c0f27-118">Completes the instance in memory and removes it from the instance store.</span></span>  
  
     <span data-ttu-id="c0f27-119">Para obter mais informações sobre <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>, consulte [extensibilidade de Host do serviço de fluxo de trabalho](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md).</span><span class="sxs-lookup"><span data-stu-id="c0f27-119">For more information about <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>, see [Workflow Service Host Extensibility](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0f27-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c0f27-120">See Also</span></span>  
 [<span data-ttu-id="c0f27-121">Extensibilidade de host de serviço de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="c0f27-121">Workflow Service Host Extensibility</span></span>](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)  
 [<span data-ttu-id="c0f27-122">Serviços de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="c0f27-122">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)
