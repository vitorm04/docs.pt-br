---
title: Como configurar um comportamento de exceção não tratado de fluxo de trabalho com o WorkflowServiceHost
ms.date: 03/30/2017
ms.assetid: 51b25c86-292c-43e4-8d13-273d2badc8ad
ms.openlocfilehash: 69c6b1ce11d735181390a0c67df2f8dbea4f906c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185320"
---
# <a name="how-to-configure-workflow-unhandled-exception-behavior-with-workflowservicehost"></a><span data-ttu-id="97dbb-102">Como configurar um comportamento de exceção não tratado de fluxo de trabalho com o WorkflowServiceHost</span><span class="sxs-lookup"><span data-stu-id="97dbb-102">How to: Configure Workflow Unhandled Exception Behavior with WorkflowServiceHost</span></span>
<span data-ttu-id="97dbb-103">O <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> é um comportamento que permite especificar a ação a ser tomada se <xref:System.ServiceModel.Activities.WorkflowServiceHost>uma exceção não tratada ocorrer dentro de um fluxo de trabalho hospedado em .</span><span class="sxs-lookup"><span data-stu-id="97dbb-103">The <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> is a behavior that enables you to specify the action to take if an unhandled exception occurs within a workflow hosted in <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span> <span data-ttu-id="97dbb-104">Este tópico mostra como configurar esse comportamento em um arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="97dbb-104">This topic shows how to configure this behavior in a configuration file.</span></span>  
  
### <a name="to-configure-workflowunhandledexceptionbehavior"></a><span data-ttu-id="97dbb-105">Para configurar workflowUnhandledExceptionBehavior</span><span class="sxs-lookup"><span data-stu-id="97dbb-105">To configure WorkflowUnhandledExceptionBehavior</span></span>  
  
1. <span data-ttu-id="97dbb-106">Adicione um `workflowUnhandledException` elemento <`behavior`> em um `serviceBehaviors` elemento> `action` <dentro de um elemento> <, usando o atributo para especificar a ação a ser tomada quando uma exceção não manuseada ocorre como mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="97dbb-106">Add a <`workflowUnhandledException`> element in a <`behavior`> element within a <`serviceBehaviors`> element, using the `action` attribute to specify the action to take when an unhandled exception occurs as shown in the following example.</span></span>  
  
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
    > <span data-ttu-id="97dbb-107">A amostra de configuração anterior está usando configuração simplificada.</span><span class="sxs-lookup"><span data-stu-id="97dbb-107">The preceding configuration sample is using simplified configuration.</span></span> <span data-ttu-id="97dbb-108">Para obter mais informações, consulte [Configuração simplificada](../../../../docs/framework/wcf/simplified-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="97dbb-108">For more information, see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md).</span></span>  
  
     <span data-ttu-id="97dbb-109">Esse comportamento pode ser configurado em código, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="97dbb-109">This behavior can be configured in code as shown in the following example.</span></span>  
  
    ```csharp  
    host.Description.Behaviors.Add(new WorkflowUnhandledExceptionBehavior { Action = WorkflowUnhandledExceptionAction.AbandonAndSuspend });  
    ```  
  
     <span data-ttu-id="97dbb-110">O `action` atributo `workflowUnhandledException` do elemento> <pode ser definido como um dos seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="97dbb-110">The `action` attribute of the <`workflowUnhandledException`> element can be set to one of the following values:</span></span>  
  
     <span data-ttu-id="97dbb-111">**Abandonar**</span><span class="sxs-lookup"><span data-stu-id="97dbb-111">**abandon**</span></span>  
     <span data-ttu-id="97dbb-112">Aborta a instância na memória sem tocar no estado de instância persistida (ou seja, reverter para o último ponto de persistência).</span><span class="sxs-lookup"><span data-stu-id="97dbb-112">Aborts the instance in memory without touching the persisted instance state (that is, roll back to the last persist point).</span></span>  
  
     <span data-ttu-id="97dbb-113">**abandonaresuspender**</span><span class="sxs-lookup"><span data-stu-id="97dbb-113">**abandonAndSuspend**</span></span>  
     <span data-ttu-id="97dbb-114">Aborta a instância na memória e atualiza a instância persistida a ser suspensa.</span><span class="sxs-lookup"><span data-stu-id="97dbb-114">Aborts the instance in memory and updates the persisted instance to be suspended.</span></span>  
  
     <span data-ttu-id="97dbb-115">**Cancelar**</span><span class="sxs-lookup"><span data-stu-id="97dbb-115">**cancel**</span></span>  
     <span data-ttu-id="97dbb-116">Chama os manipuladores de cancelamento, por exemplo, e depois completa a instância na memória, que também pode removê-la do armazenamento de ocorrências</span><span class="sxs-lookup"><span data-stu-id="97dbb-116">Calls cancellation handlers for the instance and then completes the instance in memory, which may also remove it from the instance store</span></span>  
  
     <span data-ttu-id="97dbb-117">**Terminar**</span><span class="sxs-lookup"><span data-stu-id="97dbb-117">**terminate**</span></span>  
     <span data-ttu-id="97dbb-118">Completa a ocorrência na memória e a remove do armazenamento de instâncias.</span><span class="sxs-lookup"><span data-stu-id="97dbb-118">Completes the instance in memory and removes it from the instance store.</span></span>  
  
     <span data-ttu-id="97dbb-119">Para obter <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>mais informações sobre, consulte [Extensibility](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)Host de serviço de fluxo de trabalho .</span><span class="sxs-lookup"><span data-stu-id="97dbb-119">For more information about <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>, see [Workflow Service Host Extensibility](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97dbb-120">Confira também</span><span class="sxs-lookup"><span data-stu-id="97dbb-120">See also</span></span>

- [<span data-ttu-id="97dbb-121">Extensibilidade de host de serviço de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="97dbb-121">Workflow Service Host Extensibility</span></span>](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)
- [<span data-ttu-id="97dbb-122">Serviços de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="97dbb-122">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)
