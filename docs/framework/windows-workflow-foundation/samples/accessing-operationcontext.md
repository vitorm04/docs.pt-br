---
title: Acessando OperationContext
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4e92efe8-7e79-41f3-b50e-bdc38b9f41f8
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8ca0290f658dfc5e34ec7e1e1be228213c521ce0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="accessing-operationcontext"></a><span data-ttu-id="bfdc3-102">Acessando OperationContext</span><span class="sxs-lookup"><span data-stu-id="bfdc3-102">Accessing OperationContext</span></span>
<span data-ttu-id="bfdc3-103">Este exemplo demonstra como as atividades de mensagens (<xref:System.ServiceModel.Activities.Receive> e <xref:System.ServiceModel.Activities.Send>) pode ser usado com uma atividade de escopo personalizado para acessar <xref:System.ServiceModel.OperationContext.Current%2A> e anexar ou recuperar um cabeçalho de mensagem personalizada em uma mensagem de entrada ou de saída.</span><span class="sxs-lookup"><span data-stu-id="bfdc3-103">This sample demonstrates how the messaging activities (<xref:System.ServiceModel.Activities.Receive> and <xref:System.ServiceModel.Activities.Send>) can be used with a custom scope activity to access <xref:System.ServiceModel.OperationContext.Current%2A> and attach or retrieve a custom message header within an outgoing or incoming message.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="bfdc3-104">Demonstra</span><span class="sxs-lookup"><span data-stu-id="bfdc3-104">Demonstrates</span></span>  
 <span data-ttu-id="bfdc3-105">Atividades de mensagem, <xref:System.ServiceModel.Activities.ISendMessageCallback>, <xref:System.ServiceModel.Activities.IReceiveMessageCallback>.</span><span class="sxs-lookup"><span data-stu-id="bfdc3-105">Messaging Activities, <xref:System.ServiceModel.Activities.ISendMessageCallback>, <xref:System.ServiceModel.Activities.IReceiveMessageCallback>.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="bfdc3-106">Discussão</span><span class="sxs-lookup"><span data-stu-id="bfdc3-106">Discussion</span></span>  
 <span data-ttu-id="bfdc3-107">Este exemplo mostra como usar pontos de extensibilidade (<xref:System.ServiceModel.Activities.ISendMessageCallback>) <xref:System.ServiceModel.Activities.IReceiveMessageCallback>) nas atividades de mensagem para acessar <xref:System.ServiceModel.OperationContext.Current%2A>.</span><span class="sxs-lookup"><span data-stu-id="bfdc3-107">This sample shows how to use extensibility points (<xref:System.ServiceModel.Activities.ISendMessageCallback>) <xref:System.ServiceModel.Activities.IReceiveMessageCallback>) in the messaging activities to access <xref:System.ServiceModel.OperationContext.Current%2A>.</span></span> <span data-ttu-id="bfdc3-108">As callbacks são registrados no tempo de execução de fluxo de trabalho como uma implementação de <xref:System.Activities.IExecutionProperty> que é pegarada por atividades de mensagem em cima de execução.</span><span class="sxs-lookup"><span data-stu-id="bfdc3-108">The callbacks are registered within the workflow runtime as an implementation of <xref:System.Activities.IExecutionProperty> that is picked up by the messaging activities upon execution.</span></span> <span data-ttu-id="bfdc3-109">Quaisquer atividades de mensagem no mesmo define o escopo como essa implementação de <xref:System.Activities.IExecutionProperty> é afetado.</span><span class="sxs-lookup"><span data-stu-id="bfdc3-109">Any messaging activity in the same scope as that <xref:System.Activities.IExecutionProperty> implementation is affected.</span></span> <span data-ttu-id="bfdc3-110">Em particular, este exemplo usa uma atividade personalizado de escopo para forçar o comportamento de retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="bfdc3-110">In particular, this sample uses a custom scope activity to enforce the callback behavior.</span></span> <span data-ttu-id="bfdc3-111"><xref:System.ServiceModel.Activities.ISendMessageCallback> é usado no fluxo de trabalho de cliente para incluir <xref:System.Activities.WorkflowApplication.Id%2A> de fluxo de trabalho como <xref:System.ServiceModel.Channels.MessageHeader>de saída.</span><span class="sxs-lookup"><span data-stu-id="bfdc3-111">The <xref:System.ServiceModel.Activities.ISendMessageCallback> is used in the client workflow to include the workflow’s <xref:System.Activities.WorkflowApplication.Id%2A> as an outgoing <xref:System.ServiceModel.Channels.MessageHeader>.</span></span> <span data-ttu-id="bfdc3-112">Este cabeçalho é capturado no serviço usando <xref:System.ServiceModel.Activities.IReceiveMessageCallback> e o valor de cabeçalho é impresso - ao console.</span><span class="sxs-lookup"><span data-stu-id="bfdc3-112">This header is then picked up in the service using the <xref:System.ServiceModel.Activities.IReceiveMessageCallback> and the value of the header is printed out to the console.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="bfdc3-113">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="bfdc3-113">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="bfdc3-114">Este exemplo exibe um serviço de fluxo de trabalho usando pontos de extremidade HTTP.</span><span class="sxs-lookup"><span data-stu-id="bfdc3-114">This sample exposes a workflow service using HTTP endpoints.</span></span> <span data-ttu-id="bfdc3-115">Para executar este exemplo, adequado ACLs de URL deve ser adicionado (consulte [Configurando HTTP e HTTPS](http://go.microsoft.com/fwlink/?LinkId=70353) para obter detalhes), executando o Visual Studio como administrador ou executando o seguinte comando em um prompt elevado para adicionar as ACLs corretas.</span><span class="sxs-lookup"><span data-stu-id="bfdc3-115">To run this sample, proper URL ACLs must be added (see [Configuring HTTP and HTTPS](http://go.microsoft.com/fwlink/?LinkId=70353) for details), either by running Visual Studio as Administrator or by executing the following command at an elevated prompt to add the appropriate ACLs.</span></span> <span data-ttu-id="bfdc3-116">Certifique-se de que seu domínio e nome de usuário são substituídos.</span><span class="sxs-lookup"><span data-stu-id="bfdc3-116">Ensure that your Domain and Username are substituted.</span></span>  
  
    ```  
    netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%  
    ```  
  
2.  <span data-ttu-id="bfdc3-117">Uma vez que o URL ACLs é adicionado, use as seguintes etapas.</span><span class="sxs-lookup"><span data-stu-id="bfdc3-117">Once the URL ACLs are added, use the following steps.</span></span>  
  
    1.  <span data-ttu-id="bfdc3-118">Compile a solução.</span><span class="sxs-lookup"><span data-stu-id="bfdc3-118">Build the solution.</span></span>  
  
    2.  <span data-ttu-id="bfdc3-119">Definir vários projetos de inicialização, clicando duas vezes a solução e selecionando **definir projetos de inicialização**.</span><span class="sxs-lookup"><span data-stu-id="bfdc3-119">Set multiple start-up projects by right-clicking the solution and selecting **Set Startup Projects**.</span></span>  
  
    3.  <span data-ttu-id="bfdc3-120">Adicionar **Service** e **cliente** (nessa ordem) como vários projetos de inicialização.</span><span class="sxs-lookup"><span data-stu-id="bfdc3-120">Add **Service** and **Client** (in that order) as multiple start-up projects.</span></span>  
  
    4.  <span data-ttu-id="bfdc3-121">Execute o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="bfdc3-121">Run the application.</span></span> <span data-ttu-id="bfdc3-122">O console de cliente mostra um fluxo de trabalho que executa duas vezes na janela de serviço mostra a ID da instância desses fluxos de trabalho.</span><span class="sxs-lookup"><span data-stu-id="bfdc3-122">The client console shows a workflow running twice and the Service window shows the instance ID of those workflows.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="bfdc3-123">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="bfdc3-123">The samples may already be installed on your machine.</span></span> <span data-ttu-id="bfdc3-124">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="bfdc3-124">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="bfdc3-125">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="bfdc3-125">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="bfdc3-126">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="bfdc3-126">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\Accessing Operation Context`
