---
title: "Atraso durável em XAMLX"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: efc38df4-2d34-453c-8e59-2c21d1307354
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a52f3444b51f91d7076d6bc5a580d6efb6e26eb2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="durable-delay-in-xamlx"></a><span data-ttu-id="85efa-102">Atraso durável em XAMLX</span><span class="sxs-lookup"><span data-stu-id="85efa-102">Durable Delay in XAMLX</span></span>
<span data-ttu-id="85efa-103">Este exemplo demonstra como usar um atraso durável, que é um atraso que persiste o fluxo de trabalho para um dispositivo durável durante o atraso.</span><span class="sxs-lookup"><span data-stu-id="85efa-103">This sample demonstrates how to use a durable delay, which is a delay that persists the workflow to a durable device during the delay.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="85efa-104">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="85efa-104">The samples may already be installed on your machine.</span></span> <span data-ttu-id="85efa-105">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="85efa-105">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="85efa-106">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="85efa-106">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="85efa-107">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="85efa-107">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\DurableDelayXamlx`  
  
## <a name="discussion"></a><span data-ttu-id="85efa-108">Discussão</span><span class="sxs-lookup"><span data-stu-id="85efa-108">Discussion</span></span>  
 <span data-ttu-id="85efa-109">O fluxo de trabalho de exemplo contém duas mensagens em um arquivo local que são separadas por um atraso.</span><span class="sxs-lookup"><span data-stu-id="85efa-109">The sample workflow contains two messages to a local file that are separated by a delay.</span></span> <span data-ttu-id="85efa-110">Quando o atraso é disparado, o trabalho são descarregados e esperam 5 segundos no armazenamento de instância de trabalho antes de ser recarregado na memória.</span><span class="sxs-lookup"><span data-stu-id="85efa-110">When the delay is triggered, the workflow is unloaded and waits 5 seconds in the workflow instance store before being reloaded in memory.</span></span>  
  
 <span data-ttu-id="85efa-111">O arquivo de .xamlx é um serviço de fluxo de trabalho que está hospedado em [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="85efa-111">The .xamlx file is a workflow service that is hosted in [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)].</span></span> [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)]<span data-ttu-id="85efa-112"> usa Cassini que usa um host serviço de fluxo de trabalho para hospedar o fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="85efa-112"> uses Cassini that uses a workflow service host to host the workflow.</span></span>  
  
 <span data-ttu-id="85efa-113">Além de hospedar o trabalho, o host serviço de trabalho gerencia as instâncias de fluxo de trabalho carregar e descarregando as.</span><span class="sxs-lookup"><span data-stu-id="85efa-113">In addition to hosting the workflow, the workflow service host manages the workflow instances by loading and unloading them.</span></span> <span data-ttu-id="85efa-114">Para iniciar uma instância de definição de [!INCLUDE[wf](../../../../includes/wf-md.md)] (no host serviço de fluxo de trabalho), defina um cliente que enviar uma mensagem a atividade de <xref:System.ServiceModel.Activities.Receive> no fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="85efa-114">To start an instance of the [!INCLUDE[wf](../../../../includes/wf-md.md)] definition (on the workflow service host), set a client that sends a message to the <xref:System.ServiceModel.Activities.Receive> activity in the workflow.</span></span> <span data-ttu-id="85efa-115">Este <xref:System.ServiceModel.Activities.Receive> tem sua propriedade de <xref:System.ServiceModel.Activities.Receive.CanCreateInstance%2A> definida como `true`, permitindo que você criar uma nova instância de fluxo de trabalho uma vez que recebe uma mensagem.</span><span class="sxs-lookup"><span data-stu-id="85efa-115">This <xref:System.ServiceModel.Activities.Receive> has its <xref:System.ServiceModel.Activities.Receive.CanCreateInstance%2A> property set to `true`, enabling it to create a new instance of the workflow once it receives a message.</span></span>  
  
 <span data-ttu-id="85efa-116">Durante a inicialização, um comportamento de instância de unload é adicionado ao arquivo de configuração que especifica ao host serviço de fluxo de trabalho em que deve descarregar uma instância no armazenamento de persistência (base de dados).</span><span class="sxs-lookup"><span data-stu-id="85efa-116">During initialization, an unload instance behavior is added to the configuration file that specifies to the workflow service host under which it should unload an instance to the persistence store (database).</span></span> <span data-ttu-id="85efa-117">Para esse exemplo, descarrega a instância imediatamente após o fluxo de trabalho aparece ociosa (quando o atraso é disparado).</span><span class="sxs-lookup"><span data-stu-id="85efa-117">For this sample, it unloads the instance immediately after the workflow goes idle (when the delay is triggered).</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="85efa-118">Para usar este exemplo</span><span class="sxs-lookup"><span data-stu-id="85efa-118">To use this sample</span></span>  
  
1.  <span data-ttu-id="85efa-119">Abra um prompt de comando do [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="85efa-119">Open a [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] command prompt.</span></span>  
  
2.  <span data-ttu-id="85efa-120">Navegue até a pasta de DurableDelayXamlx \ CS.</span><span class="sxs-lookup"><span data-stu-id="85efa-120">Navigate to the DurableDelayXamlx\CS folder.</span></span>  
  
3.  <span data-ttu-id="85efa-121">Executar Setup.cmd.</span><span class="sxs-lookup"><span data-stu-id="85efa-121">Run Setup.cmd.</span></span>  
  
4.  <span data-ttu-id="85efa-122">Execução [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] como um administrador.</span><span class="sxs-lookup"><span data-stu-id="85efa-122">Run [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] as an administrator.</span></span>  
  
5.  <span data-ttu-id="85efa-123">Abra o arquivo de solução de DurableDelayXamlx.sln.</span><span class="sxs-lookup"><span data-stu-id="85efa-123">Open the DurableDelayXamlx.sln solution file.</span></span>  
  
6.  <span data-ttu-id="85efa-124">Em **Solution Explorer**, a solução e selecione **propriedades**.</span><span class="sxs-lookup"><span data-stu-id="85efa-124">In **Solution Explorer**, right-click the solution and select **Properties**.</span></span>  
  
7.  <span data-ttu-id="85efa-125">Selecione **vários projetos de inicialização** e defina os dois projetos como **iniciar**.</span><span class="sxs-lookup"><span data-stu-id="85efa-125">Select **Multiple startup projects** and set both projects to **Start**.</span></span>  
  
8.  <span data-ttu-id="85efa-126">Para criar a solução, pressione CTRL+SHIFT+B.</span><span class="sxs-lookup"><span data-stu-id="85efa-126">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
9. <span data-ttu-id="85efa-127">Para executar a solução, pressione CTRL+F5.</span><span class="sxs-lookup"><span data-stu-id="85efa-127">To run the solution, press CTRL+F5.</span></span>  
  
#### <a name="to-uninstall-this-sample"></a><span data-ttu-id="85efa-128">Para desinstalar este exemplo</span><span class="sxs-lookup"><span data-stu-id="85efa-128">To uninstall this sample</span></span>  
  
1.  <span data-ttu-id="85efa-129">Abra um prompt de comando do [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="85efa-129">Open a [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] command prompt.</span></span>  
  
2.  <span data-ttu-id="85efa-130">Navegue até a pasta de DurableDelayXamlx \ CS.</span><span class="sxs-lookup"><span data-stu-id="85efa-130">Navigate to the DurableDelayXamlx\CS folder.</span></span>  
  
3.  <span data-ttu-id="85efa-131">Execução Cleanup.cmd.</span><span class="sxs-lookup"><span data-stu-id="85efa-131">Run Cleanup.cmd.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="85efa-132">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="85efa-132">The samples may already be installed on your machine.</span></span> <span data-ttu-id="85efa-133">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="85efa-133">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="85efa-134">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="85efa-134">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="85efa-135">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="85efa-135">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\DurableDelayXamlX`
