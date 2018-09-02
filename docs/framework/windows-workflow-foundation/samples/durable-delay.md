---
title: Atraso durável
ms.date: 03/30/2017
ms.assetid: 220ec240-b958-430c-81ff-b734a6aa97ae
ms.openlocfilehash: 2a7692e28d60232913ae5d11a90025e59664c0e5
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43406570"
---
# <a name="durable-delay"></a><span data-ttu-id="2efc8-102">Atraso durável</span><span class="sxs-lookup"><span data-stu-id="2efc8-102">Durable Delay</span></span>
<span data-ttu-id="2efc8-103">Este exemplo demonstra como usar um atraso durável, que é um atraso que persiste o fluxo de trabalho para um dispositivo durável durante o atraso.</span><span class="sxs-lookup"><span data-stu-id="2efc8-103">This sample demonstrates how to use a durable delay, which is a delay that persists the workflow to a durable device during the delay.</span></span> <span data-ttu-id="2efc8-104">O fluxo de trabalho de exemplo contém duas mensagens ao console que são separadas por um atraso.</span><span class="sxs-lookup"><span data-stu-id="2efc8-104">The sample workflow contains two messages to the console that are separated by a delay.</span></span> <span data-ttu-id="2efc8-105">Quando o atraso é disparado, o trabalho são descarregados e esperam 5 segundos no armazenamento de instância de trabalho antes de ser recarregado na memória.</span><span class="sxs-lookup"><span data-stu-id="2efc8-105">When the delay is triggered, the workflow is unloaded and waits 5 seconds in the workflow instance store before being reloaded in memory.</span></span>  
  
## <a name="workflow-details"></a><span data-ttu-id="2efc8-106">Detalhes de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="2efc8-106">Workflow Details</span></span>  
 <span data-ttu-id="2efc8-107">O host serviço de fluxo de trabalho hospeda o fluxo de trabalho e gerenciar as instâncias de fluxo de trabalho carregar e descarregando as.</span><span class="sxs-lookup"><span data-stu-id="2efc8-107">The workflow service host hosts the workflow and manages the workflow instances by loading and unloading them.</span></span> <span data-ttu-id="2efc8-108">Para iniciar uma instância de definição de fluxo de trabalho, o exemplo define um proxy que enviar uma mensagem a atividade de <xref:System.ServiceModel.Activities.Receive> no fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="2efc8-108">To start an instance of the workflow definition, the sample sets a proxy that sends a message to the <xref:System.ServiceModel.Activities.Receive> activity in the workflow.</span></span> <span data-ttu-id="2efc8-109">A propriedade de <xref:System.ServiceModel.Activities.Receive.CanCreateInstance%2A> é definida como `true`, permitindo que você criar uma nova instância de fluxo de trabalho uma vez que recebe uma mensagem.</span><span class="sxs-lookup"><span data-stu-id="2efc8-109">The <xref:System.ServiceModel.Activities.Receive.CanCreateInstance%2A> property is set to `true`, enabling it to create a new instance of the workflow once it receives a message.</span></span>  
  
 <span data-ttu-id="2efc8-110">A lista a seguir detalha a configuração pelo host serviço de fluxo de trabalho durante a inicialização.</span><span class="sxs-lookup"><span data-stu-id="2efc8-110">The following list details the set-up by the workflow service host during initialization.</span></span>  
  
1.  <span data-ttu-id="2efc8-111">Cria um host de serviço com um endereço (http://localhost:8080/Client).</span><span class="sxs-lookup"><span data-stu-id="2efc8-111">Creates a service host with an address (http://localhost:8080/Client).</span></span>  
  
2.  <span data-ttu-id="2efc8-112">Cria um ponto de extremidade no host serviço para habilitar comunicação com a atividade de <xref:System.ServiceModel.Activities.Receive> dentro de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="2efc8-112">Creates an endpoint in the service host to enable communication with the <xref:System.ServiceModel.Activities.Receive> activity inside the workflow.</span></span>  
  
3.  <span data-ttu-id="2efc8-113">Configura de um armazenamento de instância de SQL.</span><span class="sxs-lookup"><span data-stu-id="2efc8-113">Sets up a SQL instance store.</span></span>  
  
4.  <span data-ttu-id="2efc8-114">Adiciona um comportamento de instância de unload que especifica as circunstâncias em que o host serviço de fluxo de trabalho deve descarregar uma instância de fluxo de trabalho para o armazenamento de persistência SQL.</span><span class="sxs-lookup"><span data-stu-id="2efc8-114">Adds an unload instance behavior that specifies the conditions under which the workflow service host should unload a workflow instance to the SQL persistence store.</span></span> <span data-ttu-id="2efc8-115">Para esse exemplo, descarrega a instância imediatamente após o fluxo de trabalho aparece ociosa (quando o atraso é disparado).</span><span class="sxs-lookup"><span data-stu-id="2efc8-115">For this sample, it unloads the instance immediately after the workflow goes idle (when the delay is triggered).</span></span>  
  
5.  <span data-ttu-id="2efc8-116">Cria o proxy que envia uma mensagem à atividade de <xref:System.ServiceModel.Activities.Receive> no fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="2efc8-116">Creates the proxy that sends a message to the <xref:System.ServiceModel.Activities.Receive> activity in the workflow.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="2efc8-117">Para usar este exemplo</span><span class="sxs-lookup"><span data-stu-id="2efc8-117">To use this sample</span></span>  
  
1.  <span data-ttu-id="2efc8-118">Configurar o base de dados de persistência.</span><span class="sxs-lookup"><span data-stu-id="2efc8-118">Set up the persistence database.</span></span>  
  
    1.  <span data-ttu-id="2efc8-119">Abra um prompt de comando do [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2efc8-119">Open a [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] command prompt.</span></span>  
  
    2.  <span data-ttu-id="2efc8-120">Navegue até o [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] diretório (C:\Windows\Microsoft.NET\Framework\v4. X\\).</span><span class="sxs-lookup"><span data-stu-id="2efc8-120">Navigate to the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] directory (C:\Windows\Microsoft.NET\Framework\v4.X\\).</span></span>  
  
    3.  <span data-ttu-id="2efc8-121">Edite o arquivo de Workflowmanagementservice e adicione a seguinte cadeia de conexão dentro de <`database`> elemento.</span><span class="sxs-lookup"><span data-stu-id="2efc8-121">Edit the WorkflowManagementService.exe.config file and add the following connection string inside the <`database`> element.</span></span>  
  
        ```xml  
        <database connectionString="Data Source=localhost\SQLEXPRESS;Initial Catalog=DefaultSampleStore;Integrated Security=True;Asynchronous Processing=True" />  
        ```  
  
    4.  <span data-ttu-id="2efc8-122">Navegue para o diretório de DurableDelay \ CS.</span><span class="sxs-lookup"><span data-stu-id="2efc8-122">Navigate to the DurableDelay\CS directory.</span></span>  
  
    5.  <span data-ttu-id="2efc8-123">Executar Setup.cmd.</span><span class="sxs-lookup"><span data-stu-id="2efc8-123">Run Setup.cmd.</span></span>  
  
2.  <span data-ttu-id="2efc8-124">Execute [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] usando permissões elevadas clicando com o [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] ícone e selecionando **executar como administrador**.</span><span class="sxs-lookup"><span data-stu-id="2efc8-124">Run [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] using elevated permissions by right-clicking the [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] icon and selecting **Run as administrator**.</span></span>  
  
3.  <span data-ttu-id="2efc8-125">Abra o arquivo de solução de Delay.sln.</span><span class="sxs-lookup"><span data-stu-id="2efc8-125">Open the Delay.sln solution file.</span></span>  
  
4.  <span data-ttu-id="2efc8-126">Pressione CTRL+SHIFT+B para criar a solução.</span><span class="sxs-lookup"><span data-stu-id="2efc8-126">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
5.  <span data-ttu-id="2efc8-127">Pressione CTRL+F5 para executar a solução.</span><span class="sxs-lookup"><span data-stu-id="2efc8-127">Press CTRL+F5 to run the solution.</span></span>  
  
#### <a name="to-uninstall-this-sample"></a><span data-ttu-id="2efc8-128">Para desinstalar este exemplo</span><span class="sxs-lookup"><span data-stu-id="2efc8-128">To uninstall this sample</span></span>  
  
1.  <span data-ttu-id="2efc8-129">Abra um prompt de comando do [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2efc8-129">Open a [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] command prompt.</span></span>  
  
2.  <span data-ttu-id="2efc8-130">Navegue para o diretório de DurableDelay \ CS.</span><span class="sxs-lookup"><span data-stu-id="2efc8-130">Navigate to the DurableDelay\CS directory.</span></span>  
  
3.  <span data-ttu-id="2efc8-131">Execução Cleanup.cmd.</span><span class="sxs-lookup"><span data-stu-id="2efc8-131">Run Cleanup.cmd.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="2efc8-132">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="2efc8-132">The samples may already be installed on your machine.</span></span> <span data-ttu-id="2efc8-133">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="2efc8-133">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="2efc8-134">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="2efc8-134">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="2efc8-135">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="2efc8-135">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\DurableDelay`