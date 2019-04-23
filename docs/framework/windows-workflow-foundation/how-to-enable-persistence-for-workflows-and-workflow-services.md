---
title: 'Como: habilitar a persistência para fluxos de trabalho e serviços de fluxo de trabalho'
ms.date: 03/30/2017
ms.assetid: 2b1c8bf3-9866-45a4-b06d-ee562393e503
ms.openlocfilehash: 6a2a8d73298e14f92f376b97b9637db91532e937
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59772676"
---
# <a name="how-to-enable-persistence-for-workflows-and-workflow-services"></a><span data-ttu-id="4ef50-102">Como: habilitar a persistência para fluxos de trabalho e serviços de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="4ef50-102">How to: Enable Persistence for Workflows and Workflow Services</span></span>
<span data-ttu-id="4ef50-103">Este tópico descreve como ativar persistência para fluxos de trabalho e serviços de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="4ef50-103">This topic describes how to enable persistence for workflows and workflow services.</span></span>  
  
## <a name="enable-persistence-for-workflows"></a><span data-ttu-id="4ef50-104">Ativar persistência para fluxos de trabalho</span><span class="sxs-lookup"><span data-stu-id="4ef50-104">Enable Persistence for Workflows</span></span>  
 <span data-ttu-id="4ef50-105">Você pode associar um armazenamento de instância com um **WorkflowApplication** usando o <xref:System.Activities.WorkflowApplication.InstanceStore%2A> propriedade o <xref:System.Activities.WorkflowApplication> classe.</span><span class="sxs-lookup"><span data-stu-id="4ef50-105">You can associate an instance store with a **WorkflowApplication** by using the <xref:System.Activities.WorkflowApplication.InstanceStore%2A> property of the <xref:System.Activities.WorkflowApplication> class.</span></span> <span data-ttu-id="4ef50-106">O método de <xref:System.Activities.WorkflowApplication.Persist%2A> salva ou persiste um fluxo de trabalho no armazenamento de instância associada ao aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4ef50-106">The <xref:System.Activities.WorkflowApplication.Persist%2A> method saves or persists a workflow into the instance store associated with the application.</span></span> <span data-ttu-id="4ef50-107">O método de <xref:System.Activities.WorkflowApplication.Unload%2A> persiste um fluxo de trabalho no armazenamento de instância e então descarrega a instância de memória.</span><span class="sxs-lookup"><span data-stu-id="4ef50-107">The <xref:System.Activities.WorkflowApplication.Unload%2A> method persists a workflow into the instance store and then unloads the instance from the memory.</span></span> <span data-ttu-id="4ef50-108">O **carga** método carrega um fluxo de trabalho na memória usando os dados de fluxo de trabalho armazenados no repositório de persistência de instância.</span><span class="sxs-lookup"><span data-stu-id="4ef50-108">The **Load** method loads a workflow into memory using the workflow data stored in the instance persistence store.</span></span>  
  
 <span data-ttu-id="4ef50-109">O **Persist** método executa as seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="4ef50-109">The **Persist** method performs the following steps:</span></span>  
  
1. <span data-ttu-id="4ef50-110">Pausa o agendador de fluxo de trabalho e aguarda até que o fluxo de trabalho entre o estado ocioso.</span><span class="sxs-lookup"><span data-stu-id="4ef50-110">Pauses the workflow scheduler and waits until the workflow enters the idle state.</span></span>  
  
2. <span data-ttu-id="4ef50-111">Persiste ou salva o fluxo de trabalho no armazenamento de persistência.</span><span class="sxs-lookup"><span data-stu-id="4ef50-111">Persists or saves the workflow into the persistence store.</span></span>  
  
3. <span data-ttu-id="4ef50-112">Continua o agendador de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="4ef50-112">Resumes the workflow scheduler.</span></span>  
  
 <span data-ttu-id="4ef50-113">O **Unload** método executa as seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="4ef50-113">The **Unload** method performs the following steps:</span></span>  
  
1. <span data-ttu-id="4ef50-114">Pausa o agendador de fluxo de trabalho e aguarda até que o fluxo de trabalho entre o estado ocioso.</span><span class="sxs-lookup"><span data-stu-id="4ef50-114">Pauses the workflow scheduler and waits until the workflow enters the idle state.</span></span>  
  
2. <span data-ttu-id="4ef50-115">Persiste ou salva o fluxo de trabalho no armazenamento de persistência.</span><span class="sxs-lookup"><span data-stu-id="4ef50-115">Persists or saves the workflow into the persistence store.</span></span>  
  
3. <span data-ttu-id="4ef50-116">Descarte a instância de fluxo de trabalho na memória.</span><span class="sxs-lookup"><span data-stu-id="4ef50-116">Disposes the workflow instance in the memory.</span></span>  
  
 <span data-ttu-id="4ef50-117">Os dois os **Persist** e **Unload** métodos bloquearão quando um fluxo de trabalho está em uma zona sem persistir até que o fluxo de trabalho sai da zona sem persistir.</span><span class="sxs-lookup"><span data-stu-id="4ef50-117">Both the **Persist** and **Unload** methods will block while a workflow is in a no-persist zone until the workflow exits the no-persist zone.</span></span> <span data-ttu-id="4ef50-118">O método continua com persistir ou descarrega a operação após a zona sem persistir completa.</span><span class="sxs-lookup"><span data-stu-id="4ef50-118">The method continues with the persist or unload operation after the no-persist zone completes.</span></span> <span data-ttu-id="4ef50-119">Se a zona sem persistir não concluir passa antes do tempo limite, ou se o processo de persistência leva muito longas, um TimeoutException será lançada.</span><span class="sxs-lookup"><span data-stu-id="4ef50-119">If the no-persist zone does not complete before the time-out elapses, or if the persistence process takes too long, a TimeoutException will be thrown.</span></span>  
  
## <a name="enable-persistence-for-workflow-services-in-code"></a><span data-ttu-id="4ef50-120">Ativar persistência para serviços de fluxo de trabalho no código</span><span class="sxs-lookup"><span data-stu-id="4ef50-120">Enable Persistence for Workflow Services in Code</span></span>  
 <span data-ttu-id="4ef50-121">O **DurableInstancingOptions** membro a <xref:System.ServiceModel.WorkflowServiceHost> classe tem uma propriedade chamada **InstanceStore** que você pode usar para associar um armazenamento de instância com o **WorkflowServiceHost** .</span><span class="sxs-lookup"><span data-stu-id="4ef50-121">The **DurableInstancingOptions** member of the <xref:System.ServiceModel.WorkflowServiceHost> class has a property named **InstanceStore** that you can use to associate an instance store with the **WorkflowServiceHost**.</span></span>  
  
```  
// wsh is an instance of WorkflowServiceHost class  
wsh.DurableInstancingOptions.InstanceStore = new SqlWorkflowInstanceStore();  
```  
  
 <span data-ttu-id="4ef50-122">Quando o **WorkflowServiceHost** é aberto, persistência é automaticamente ativada se a **Durableinstancingoptions** não é nulo.</span><span class="sxs-lookup"><span data-stu-id="4ef50-122">When the **WorkflowServiceHost** is opened, persistence is automatically enabled if the **DurableInstancingOptions.InstanceStore** is not null.</span></span>  
  
 <span data-ttu-id="4ef50-123">Normalmente, um comportamento de serviço fornece o armazenamento concreto de instância a ser usado com um host de serviço de fluxo de trabalho usando o **InstanceStore** propriedade.</span><span class="sxs-lookup"><span data-stu-id="4ef50-123">Typically, a service behavior provides the concrete instance store to be used with a workflow service host by using the **InstanceStore** property.</span></span> <span data-ttu-id="4ef50-124">Por exemplo, o SqlWorkflowInstanceStoreBehavior cria uma instância das **SqlWorkflowInstanceStore**, configura e atribui-lo para o **Durableinstancingoptions**.</span><span class="sxs-lookup"><span data-stu-id="4ef50-124">For example, the SqlWorkflowInstanceStoreBehavior creates an instance of the **SqlWorkflowInstanceStore**, configures it, and assigns it to the **DurableInstancingOptions.InstanceStore**.</span></span>  
  
## <a name="enable-persistence-for-workflow-services-using-an-application-configuration-file"></a><span data-ttu-id="4ef50-125">Ativar persistência para serviços de fluxo de trabalho usando um arquivo de configuração do aplicativo</span><span class="sxs-lookup"><span data-stu-id="4ef50-125">Enable Persistence for Workflow Services Using an Application Configuration File</span></span>  
 <span data-ttu-id="4ef50-126">Persistência pode ser ativada usando um arquivo de configuração do aplicativo adicionando o seguinte código ao seu arquivo app.config ou web.config:</span><span class="sxs-lookup"><span data-stu-id="4ef50-126">Persistence can be enabled using an application configuration file by adding the following code to your app.config or web.config file:</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="myBehavior">  
          <SqlWorkflowInstanceStore connectionString="Data Source=myDatatbaseServer;Initial Catalog=myPersistenceDatabase">  
        </behavior>  
      </serviceBehaviors>  
    <behaviors>  
  </system.serviceModel>  
</configuration>  
```
