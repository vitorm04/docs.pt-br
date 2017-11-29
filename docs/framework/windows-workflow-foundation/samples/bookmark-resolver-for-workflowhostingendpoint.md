---
title: "Resolução do indexador para WorkflowHostingEndpoint"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 97fd5816-935e-4625-ad04-e6f6befa07de
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 97e58699573aeae1594c1eea74fe1ce860cf6ed4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="bookmark-resolver-for-workflowhostingendpoint"></a><span data-ttu-id="fac41-102">Resolução do indexador para WorkflowHostingEndpoint</span><span class="sxs-lookup"><span data-stu-id="fac41-102">Bookmark Resolver for WorkflowHostingEndpoint</span></span>
<span data-ttu-id="fac41-103">Este exemplo demonstra como <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> pode ser usado com <xref:System.ServiceModel.Activities.WorkflowServiceHost> para criar instâncias de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="fac41-103">This sample demonstrates how the <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> can be used with <xref:System.ServiceModel.Activities.WorkflowServiceHost> to create workflow instances.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="fac41-104">Demonstra</span><span class="sxs-lookup"><span data-stu-id="fac41-104">Demonstrates</span></span>  
 <span data-ttu-id="fac41-105"><xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>, <xref:System.ServiceModel.Activities.WorkflowServiceHost></span><span class="sxs-lookup"><span data-stu-id="fac41-105"><xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>, <xref:System.ServiceModel.Activities.WorkflowServiceHost></span></span>  
  
## <a name="discussion"></a><span data-ttu-id="fac41-106">Discussão</span><span class="sxs-lookup"><span data-stu-id="fac41-106">Discussion</span></span>  
 <span data-ttu-id="fac41-107">Este exemplo usa <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> para criar instâncias de fluxo de trabalho usando <xref:System.ServiceModel.Activities.WorkflowServiceHost>hospedados.</span><span class="sxs-lookup"><span data-stu-id="fac41-107">This sample uses the <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> to create workflow instances hosted using <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span> <span data-ttu-id="fac41-108"><xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> é um ponto de extensibilidade para <xref:System.ServiceModel.Activities.WorkflowServiceHost> que pode ser usada nos seguintes situações:</span><span class="sxs-lookup"><span data-stu-id="fac41-108"><xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> is an extensibility point for <xref:System.ServiceModel.Activities.WorkflowServiceHost> that can be used in the following scenarios:</span></span>  
  
-   <span data-ttu-id="fac41-109">Criando novas instâncias de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="fac41-109">Creating new workflow instances.</span></span>  
  
-   <span data-ttu-id="fac41-110">Continuando indicadores na instância de fluxo de trabalho hospedada em <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="fac41-110">Resuming bookmarks on workflow instance hosted in a <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span>  
  
 <span data-ttu-id="fac41-111">O ponto final de exemplo que é expõe incluídas o contrato que fornece operações para criar um fluxo de trabalho e retorna a identificação da instância ou cria uma instância com uma identificação específica</span><span class="sxs-lookup"><span data-stu-id="fac41-111">The sample endpoint that is included exposes a contract that provides operations to create a workflow and returns the instance ID or creates an instance with a specific ID.</span></span> <span data-ttu-id="fac41-112">O aplicativo de console do exemplo cria uma instância de <xref:System.ServiceModel.Activities.WorkflowServiceHost> com uma definição de fluxo de trabalho e adiciona `CreationEndpoint` para o host.</span><span class="sxs-lookup"><span data-stu-id="fac41-112">The sample console application creates a <xref:System.ServiceModel.Activities.WorkflowServiceHost> instance with a workflow definition and adds a `CreationEndpoint` to the host.</span></span> <span data-ttu-id="fac41-113">Então chama a operação de `Create` no ponto de extremidade para criar uma nova instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="fac41-113">It then calls the `Create` operation on the endpoint to create a new workflow instance.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="fac41-114">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="fac41-114">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="fac41-115">Compile a solução.</span><span class="sxs-lookup"><span data-stu-id="fac41-115">Build the solution.</span></span>  
  
2.  <span data-ttu-id="fac41-116">Execute o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="fac41-116">Run the application.</span></span> <span data-ttu-id="fac41-117">O console de `CreationEndpoint` mostra uma mensagem que inclui a ID da instância quando a instância do fluxo de trabalho é criada.</span><span class="sxs-lookup"><span data-stu-id="fac41-117">The `CreationEndpoint` console shows a message that includes the instance ID when the workflow instance is created.</span></span> <span data-ttu-id="fac41-118">A mensagem "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="fac41-118">The message "Hello World!"</span></span> <span data-ttu-id="fac41-119">é impressa na instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="fac41-119">is printed by the workflow instance.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="fac41-120">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="fac41-120">The samples may already be installed on your machine.</span></span> <span data-ttu-id="fac41-121">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="fac41-121">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="fac41-122">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="fac41-122">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="fac41-123">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="fac41-123">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\CreationEndpoint`
