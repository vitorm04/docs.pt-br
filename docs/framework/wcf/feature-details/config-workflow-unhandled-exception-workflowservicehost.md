---
title: Como configurar um comportamento de exceção não tratado de fluxo de trabalho com o WorkflowServiceHost
ms.date: 03/30/2017
ms.assetid: 51b25c86-292c-43e4-8d13-273d2badc8ad
ms.openlocfilehash: 3881d1af21dcc0c211c6738162360e522648d949
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84593588"
---
# <a name="how-to-configure-workflow-unhandled-exception-behavior-with-workflowservicehost"></a><span data-ttu-id="edb11-102">Como configurar um comportamento de exceção não tratado de fluxo de trabalho com o WorkflowServiceHost</span><span class="sxs-lookup"><span data-stu-id="edb11-102">How to: Configure Workflow Unhandled Exception Behavior with WorkflowServiceHost</span></span>
<span data-ttu-id="edb11-103">O <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> é um comportamento que permite que você especifique a ação a ser tomada se uma exceção sem tratamento ocorrer em um fluxo de trabalho hospedado no <xref:System.ServiceModel.Activities.WorkflowServiceHost> .</span><span class="sxs-lookup"><span data-stu-id="edb11-103">The <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> is a behavior that enables you to specify the action to take if an unhandled exception occurs within a workflow hosted in <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span> <span data-ttu-id="edb11-104">Este tópico mostra como configurar esse comportamento em um arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="edb11-104">This topic shows how to configure this behavior in a configuration file.</span></span>  
  
### <a name="to-configure-workflowunhandledexceptionbehavior"></a><span data-ttu-id="edb11-105">Para configurar o WorkflowUnhandledExceptionBehavior</span><span class="sxs-lookup"><span data-stu-id="edb11-105">To configure WorkflowUnhandledExceptionBehavior</span></span>  
  
1. <span data-ttu-id="edb11-106">Adicione um `workflowUnhandledException` elemento <> em um `behavior` elemento <> dentro de um elemento <> `serviceBehaviors` , usando o `action` atributo para especificar a ação a ser tomada quando uma exceção sem tratamento ocorrer, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="edb11-106">Add a <`workflowUnhandledException`> element in a <`behavior`> element within a <`serviceBehaviors`> element, using the `action` attribute to specify the action to take when an unhandled exception occurs as shown in the following example.</span></span>  
  
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
    > <span data-ttu-id="edb11-107">O exemplo de configuração anterior está usando uma configuração simplificada.</span><span class="sxs-lookup"><span data-stu-id="edb11-107">The preceding configuration sample is using simplified configuration.</span></span> <span data-ttu-id="edb11-108">Para obter mais informações, consulte [configuração simplificada](../simplified-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="edb11-108">For more information, see [Simplified Configuration](../simplified-configuration.md).</span></span>  
  
     <span data-ttu-id="edb11-109">Esse comportamento pode ser configurado no código, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="edb11-109">This behavior can be configured in code as shown in the following example.</span></span>  
  
    ```csharp  
    host.Description.Behaviors.Add(new WorkflowUnhandledExceptionBehavior { Action = WorkflowUnhandledExceptionAction.AbandonAndSuspend });  
    ```  
  
     <span data-ttu-id="edb11-110">O `action` atributo do elemento <`workflowUnhandledException`> pode ser definido como um dos seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="edb11-110">The `action` attribute of the <`workflowUnhandledException`> element can be set to one of the following values:</span></span>  
  
     <span data-ttu-id="edb11-111">**Abandon**</span><span class="sxs-lookup"><span data-stu-id="edb11-111">**abandon**</span></span>  
     <span data-ttu-id="edb11-112">Anula a instância na memória sem tocar no estado de instância persistente (ou seja, reverta para o último ponto de persistência).</span><span class="sxs-lookup"><span data-stu-id="edb11-112">Aborts the instance in memory without touching the persisted instance state (that is, roll back to the last persist point).</span></span>  
  
     <span data-ttu-id="edb11-113">**abandonAndSuspend**</span><span class="sxs-lookup"><span data-stu-id="edb11-113">**abandonAndSuspend**</span></span>  
     <span data-ttu-id="edb11-114">Anula a instância na memória e atualiza a instância persistente a ser suspensa.</span><span class="sxs-lookup"><span data-stu-id="edb11-114">Aborts the instance in memory and updates the persisted instance to be suspended.</span></span>  
  
     <span data-ttu-id="edb11-115">**cancel**</span><span class="sxs-lookup"><span data-stu-id="edb11-115">**cancel**</span></span>  
     <span data-ttu-id="edb11-116">Chama manipuladores de cancelamento para a instância e, em seguida, conclui a instância na memória, o que também pode removê-la do repositório de instância</span><span class="sxs-lookup"><span data-stu-id="edb11-116">Calls cancellation handlers for the instance and then completes the instance in memory, which may also remove it from the instance store</span></span>  
  
     <span data-ttu-id="edb11-117">**encerrar**</span><span class="sxs-lookup"><span data-stu-id="edb11-117">**terminate**</span></span>  
     <span data-ttu-id="edb11-118">Conclui a instância na memória e a remove do repositório de instância.</span><span class="sxs-lookup"><span data-stu-id="edb11-118">Completes the instance in memory and removes it from the instance store.</span></span>  
  
     <span data-ttu-id="edb11-119">Para obter mais informações sobre o <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> , consulte [extensibilidade do host do serviço de fluxo de trabalho](workflow-service-host-extensibility.md).</span><span class="sxs-lookup"><span data-stu-id="edb11-119">For more information about <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>, see [Workflow Service Host Extensibility](workflow-service-host-extensibility.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="edb11-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="edb11-120">See also</span></span>

- [<span data-ttu-id="edb11-121">Extensibilidade de host de serviço de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="edb11-121">Workflow Service Host Extensibility</span></span>](workflow-service-host-extensibility.md)
- [<span data-ttu-id="edb11-122">Serviços de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="edb11-122">Workflow Services</span></span>](workflow-services.md)
