---
title: 'Como: Ativar persistência para fluxos de trabalho e serviços de fluxo de trabalho'
ms.date: 03/30/2017
ms.assetid: 2b1c8bf3-9866-45a4-b06d-ee562393e503
ms.openlocfilehash: 5d0eeb8ad40f2f4f3349ab48487316014a561a1b
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460885"
---
# <a name="how-to-enable-persistence-for-workflows-and-workflow-services"></a><span data-ttu-id="c2e08-102">Como: Ativar persistência para fluxos de trabalho e serviços de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="c2e08-102">How to: Enable Persistence for Workflows and Workflow Services</span></span>

<span data-ttu-id="c2e08-103">Este tópico descreve como ativar persistência para fluxos de trabalho e serviços de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="c2e08-103">This topic describes how to enable persistence for workflows and workflow services.</span></span>

## <a name="enable-persistence-for-workflows"></a><span data-ttu-id="c2e08-104">Ativar persistência para fluxos de trabalho</span><span class="sxs-lookup"><span data-stu-id="c2e08-104">Enable Persistence for Workflows</span></span>

<span data-ttu-id="c2e08-105">Você pode associar um repositório de instância com um **WorkflowApplication** usando a propriedade <xref:System.Activities.WorkflowApplication.InstanceStore%2A> da classe <xref:System.Activities.WorkflowApplication>.</span><span class="sxs-lookup"><span data-stu-id="c2e08-105">You can associate an instance store with a **WorkflowApplication** by using the <xref:System.Activities.WorkflowApplication.InstanceStore%2A> property of the <xref:System.Activities.WorkflowApplication> class.</span></span> <span data-ttu-id="c2e08-106">O método de <xref:System.Activities.WorkflowApplication.Persist%2A> salva ou persiste um fluxo de trabalho no armazenamento de instância associada ao aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c2e08-106">The <xref:System.Activities.WorkflowApplication.Persist%2A> method saves or persists a workflow into the instance store associated with the application.</span></span> <span data-ttu-id="c2e08-107">O método de <xref:System.Activities.WorkflowApplication.Unload%2A> persiste um fluxo de trabalho no armazenamento de instância e então descarrega a instância de memória.</span><span class="sxs-lookup"><span data-stu-id="c2e08-107">The <xref:System.Activities.WorkflowApplication.Unload%2A> method persists a workflow into the instance store and then unloads the instance from the memory.</span></span> <span data-ttu-id="c2e08-108">O método **Load** carrega um fluxo de trabalho na memória usando os dados de fluxo de trabalho armazenados no repositório de persistência da instância.</span><span class="sxs-lookup"><span data-stu-id="c2e08-108">The **Load** method loads a workflow into memory using the workflow data stored in the instance persistence store.</span></span>

<span data-ttu-id="c2e08-109">O método **Persist** executa as seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="c2e08-109">The **Persist** method performs the following steps:</span></span>

1. <span data-ttu-id="c2e08-110">Pausa o agendador de fluxo de trabalho e aguarda até que o fluxo de trabalho entre o estado ocioso.</span><span class="sxs-lookup"><span data-stu-id="c2e08-110">Pauses the workflow scheduler and waits until the workflow enters the idle state.</span></span>

2. <span data-ttu-id="c2e08-111">Persiste ou salva o fluxo de trabalho no armazenamento de persistência.</span><span class="sxs-lookup"><span data-stu-id="c2e08-111">Persists or saves the workflow into the persistence store.</span></span>

3. <span data-ttu-id="c2e08-112">Continua o agendador de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="c2e08-112">Resumes the workflow scheduler.</span></span>

 <span data-ttu-id="c2e08-113">O método **Unload** executa as seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="c2e08-113">The **Unload** method performs the following steps:</span></span>

1. <span data-ttu-id="c2e08-114">Pausa o agendador de fluxo de trabalho e aguarda até que o fluxo de trabalho entre o estado ocioso.</span><span class="sxs-lookup"><span data-stu-id="c2e08-114">Pauses the workflow scheduler and waits until the workflow enters the idle state.</span></span>

2. <span data-ttu-id="c2e08-115">Persiste ou salva o fluxo de trabalho no armazenamento de persistência.</span><span class="sxs-lookup"><span data-stu-id="c2e08-115">Persists or saves the workflow into the persistence store.</span></span>

3. <span data-ttu-id="c2e08-116">Descarte a instância de fluxo de trabalho na memória.</span><span class="sxs-lookup"><span data-stu-id="c2e08-116">Disposes the workflow instance in the memory.</span></span>

<span data-ttu-id="c2e08-117">Os métodos **Persist** e **Unload** serão bloqueados enquanto um fluxo de trabalho estiver em uma zona de não persistência até que o fluxo de trabalho saia da zona sem persistência.</span><span class="sxs-lookup"><span data-stu-id="c2e08-117">Both the **Persist** and **Unload** methods will block while a workflow is in a no-persist zone until the workflow exits the no-persist zone.</span></span> <span data-ttu-id="c2e08-118">O método continua com persistir ou descarrega a operação após a zona sem persistir completa.</span><span class="sxs-lookup"><span data-stu-id="c2e08-118">The method continues with the persist or unload operation after the no-persist zone completes.</span></span> <span data-ttu-id="c2e08-119">Se a zona sem persistir não concluir passa antes do tempo limite, ou se o processo de persistência leva muito longas, um TimeoutException será lançada.</span><span class="sxs-lookup"><span data-stu-id="c2e08-119">If the no-persist zone does not complete before the time-out elapses, or if the persistence process takes too long, a TimeoutException will be thrown.</span></span>

## <a name="enable-persistence-for-workflow-services-in-code"></a><span data-ttu-id="c2e08-120">Ativar persistência para serviços de fluxo de trabalho no código</span><span class="sxs-lookup"><span data-stu-id="c2e08-120">Enable Persistence for Workflow Services in Code</span></span>

<span data-ttu-id="c2e08-121">O membro **DurableInstancingOptions** da classe <xref:System.ServiceModel.WorkflowServiceHost> tem uma propriedade chamada **InstanceStore** que você pode usar para associar um repositório de instância ao **WorkflowServiceHost**.</span><span class="sxs-lookup"><span data-stu-id="c2e08-121">The **DurableInstancingOptions** member of the <xref:System.ServiceModel.WorkflowServiceHost> class has a property named **InstanceStore** that you can use to associate an instance store with the **WorkflowServiceHost**.</span></span>

```csharp
// wsh is an instance of WorkflowServiceHost class
wsh.DurableInstancingOptions.InstanceStore = new SqlWorkflowInstanceStore();
```

<span data-ttu-id="c2e08-122">Quando o **WorkflowServiceHost** for aberto, a persistência será habilitada automaticamente se o **DurableInstancingOptions. InstanceStore** não for nulo.</span><span class="sxs-lookup"><span data-stu-id="c2e08-122">When the **WorkflowServiceHost** is opened, persistence is automatically enabled if the **DurableInstancingOptions.InstanceStore** is not null.</span></span>

<span data-ttu-id="c2e08-123">Normalmente, um comportamento de serviço fornece o armazenamento de instância concreto a ser usado com um host de serviço de fluxo de trabalho usando a propriedade **InstanceStore** .</span><span class="sxs-lookup"><span data-stu-id="c2e08-123">Typically, a service behavior provides the concrete instance store to be used with a workflow service host by using the **InstanceStore** property.</span></span> <span data-ttu-id="c2e08-124">Por exemplo, o SqlWorkflowInstanceStoreBehavior cria uma instância do **SqlWorkflowInstanceStore**, configura-a e a atribui ao **DurableInstancingOptions. InstanceStore**.</span><span class="sxs-lookup"><span data-stu-id="c2e08-124">For example, the SqlWorkflowInstanceStoreBehavior creates an instance of the **SqlWorkflowInstanceStore**, configures it, and assigns it to the **DurableInstancingOptions.InstanceStore**.</span></span>

## <a name="enable-persistence-for-workflow-services-using-an-application-configuration-file"></a><span data-ttu-id="c2e08-125">Ativar persistência para serviços de fluxo de trabalho usando um arquivo de configuração do aplicativo</span><span class="sxs-lookup"><span data-stu-id="c2e08-125">Enable Persistence for Workflow Services Using an Application Configuration File</span></span>

<span data-ttu-id="c2e08-126">Persistência pode ser ativada usando um arquivo de configuração do aplicativo adicionando o seguinte código ao seu arquivo app.config ou web.config:</span><span class="sxs-lookup"><span data-stu-id="c2e08-126">Persistence can be enabled using an application configuration file by adding the following code to your app.config or web.config file:</span></span>

```xml
<configuration>
  <system.serviceModel>
    <behaviors>
      <serviceBehaviors>
        <behavior name="myBehavior">
          <sqlWorkflowInstanceStore connectionString="Data Source=myDatabaseServer;Initial Catalog=myPersistenceDatabase" />
        </behavior>
      </serviceBehaviors>
    </behaviors>
  </system.serviceModel>
</configuration>
```
