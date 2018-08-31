---
title: Indexador de resumo de WorkflowHostingEndpoint
ms.date: 03/30/2017
ms.assetid: a708064f-50b0-4751-b44e-d5410d08d451
ms.openlocfilehash: 8b435a50801e03ec6ed00bcfef3c7e9198a7e7e5
ms.sourcegitcommit: a368166a51e5204c0224fbf5e46476e3ed122817
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/31/2018
ms.locfileid: "43332155"
---
# <a name="workflowhostingendpoint-resume-bookmark"></a><span data-ttu-id="3ae8d-102">Indexador de resumo de WorkflowHostingEndpoint</span><span class="sxs-lookup"><span data-stu-id="3ae8d-102">WorkflowHostingEndpoint Resume Bookmark</span></span>
<span data-ttu-id="3ae8d-103">Este exemplo demonstra como <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> pode ser usado com <xref:System.ServiceModel.Activities.WorkflowServiceHost> para criar instâncias de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="3ae8d-103">This sample demonstrates how the <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> can be used with <xref:System.ServiceModel.Activities.WorkflowServiceHost> to create workflow instances.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="3ae8d-104">Demonstra</span><span class="sxs-lookup"><span data-stu-id="3ae8d-104">Demonstrates</span></span>  
 <span data-ttu-id="3ae8d-105"><xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>, <xref:System.ServiceModel.Activities.WorkflowServiceHost></span><span class="sxs-lookup"><span data-stu-id="3ae8d-105"><xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>, <xref:System.ServiceModel.Activities.WorkflowServiceHost></span></span>  
  
## <a name="discussion"></a><span data-ttu-id="3ae8d-106">Discussão</span><span class="sxs-lookup"><span data-stu-id="3ae8d-106">Discussion</span></span>  
 <span data-ttu-id="3ae8d-107">Este exemplo usa <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> para criar uma instância de fluxo de trabalho hospedada usando <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="3ae8d-107">This sample uses the <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> to create a workflow instance hosted using <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span> <span data-ttu-id="3ae8d-108"><xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> é um ponto de extensibilidade para <xref:System.ServiceModel.Activities.WorkflowServiceHost> que pode ser usada nos seguintes situações:</span><span class="sxs-lookup"><span data-stu-id="3ae8d-108"><xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> is an extensibility point for <xref:System.ServiceModel.Activities.WorkflowServiceHost> that can be used in the following scenarios:</span></span>  
  
-   <span data-ttu-id="3ae8d-109">Criando novas instâncias de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="3ae8d-109">Creating new workflow instances.</span></span>  
  
-   <span data-ttu-id="3ae8d-110">Continuando indicadores em uma instância de fluxo de trabalho hospedada em <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="3ae8d-110">Resuming bookmarks on a workflow instance hosted in a <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span>  
  
 <span data-ttu-id="3ae8d-111">O ponto final de exemplo que é expõe incluídas o contrato que fornece operações para criar um fluxo de trabalho e retornar um ID de instância, ou para criar uma instância com uma identificação específica</span><span class="sxs-lookup"><span data-stu-id="3ae8d-111">The sample endpoint that is included exposes a contract that provides operations to create a workflow and return an instance ID, or to create an instance with a specific ID.</span></span> <span data-ttu-id="3ae8d-112">O aplicativo de console do exemplo cria uma instância de <xref:System.ServiceModel.Activities.WorkflowServiceHost> com uma definição básica de fluxo de trabalho, e adicione `CreationEndpoint` para o host.</span><span class="sxs-lookup"><span data-stu-id="3ae8d-112">The sample console application creates a <xref:System.ServiceModel.Activities.WorkflowServiceHost> instance with a basic workflow definition, and adds a `CreationEndpoint` to the host.</span></span> <span data-ttu-id="3ae8d-113">Então chama a operação de `Create` no ponto de extremidade para criar uma nova instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="3ae8d-113">It then calls the `Create` operation on the endpoint to create a new workflow instance.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="3ae8d-114">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="3ae8d-114">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="3ae8d-115">Compile a solução.</span><span class="sxs-lookup"><span data-stu-id="3ae8d-115">Build the solution.</span></span>  
  
2.  <span data-ttu-id="3ae8d-116">Execute o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3ae8d-116">Run the application.</span></span> <span data-ttu-id="3ae8d-117">O console de `CreationEndpoint` mostra uma mensagem que inclui a ID da instância quando a instância do fluxo de trabalho é criada.</span><span class="sxs-lookup"><span data-stu-id="3ae8d-117">The `CreationEndpoint` console shows a message that includes the instance ID when the workflow instance is created.</span></span> <span data-ttu-id="3ae8d-118">A mensagem "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="3ae8d-118">The message "Hello World!"</span></span> <span data-ttu-id="3ae8d-119">é impresso pelo fluxo de trabalho em ressunção com êxito do indicador.</span><span class="sxs-lookup"><span data-stu-id="3ae8d-119">is printed by the workflow on successful resumption of the bookmark.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="3ae8d-120">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="3ae8d-120">The samples may already be installed on your machine.</span></span> <span data-ttu-id="3ae8d-121">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="3ae8d-121">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="3ae8d-122">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="3ae8d-122">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="3ae8d-123">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="3ae8d-123">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\ResumeBookmarkEndpoint`
