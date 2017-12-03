---
title: Canais de WCF habilitado ReceiveContext
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d990d119-7321-4b8c-852b-10256f59f9b0
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 729bf8bd1371bf64b9b05a235331120608824083
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="receivecontext-enabled-wcf-channels"></a><span data-ttu-id="3ff52-102">Canais de WCF habilitado ReceiveContext</span><span class="sxs-lookup"><span data-stu-id="3ff52-102">ReceiveContext-Enabled WCF Channels</span></span>
<span data-ttu-id="3ff52-103">Este exemplo demonstra a utilidade de <xref:System.ServiceModel.Channels.ReceiveContext>-habilitado canais do WCF.</span><span class="sxs-lookup"><span data-stu-id="3ff52-103">This sample demonstrates the usefulness of <xref:System.ServiceModel.Channels.ReceiveContext>-enabled WCF channels.</span></span> <span data-ttu-id="3ff52-104">O exemplo implementa um serviço para localizar o produto de dois números usando um canal de NetMSMQ.</span><span class="sxs-lookup"><span data-stu-id="3ff52-104">The sample implements a service to find the product of two numbers using a NetMSMQ channel.</span></span>  
  
 <span data-ttu-id="3ff52-105">O <xref:System.ServiceModel.Channels.ReceiveContext> classe permite que um aplicativo decidir se deseja acessar a mensagem ou deixá-lo na fila para processamento adicional, mesmo depois que o conteúdo da mensagem inspecionou.</span><span class="sxs-lookup"><span data-stu-id="3ff52-105">The <xref:System.ServiceModel.Channels.ReceiveContext> class enables an application to decide whether to access the message or leave it in the queue for further processing, even after the contents of the message have been inspected.</span></span> <span data-ttu-id="3ff52-106">Neste exemplo, um cliente envia inteiros aleatórios para uma fila transacional.</span><span class="sxs-lookup"><span data-stu-id="3ff52-106">In this sample, a client sends random integers to a transactional queue.</span></span> <span data-ttu-id="3ff52-107">O `ProductCalculator` serviço recebe as mensagens e inspeciona o conteúdo da mensagem, que é números inteiros, para determinar se o produto pode ser calculado.</span><span class="sxs-lookup"><span data-stu-id="3ff52-107">The `ProductCalculator` service receives the messages and inspects the message contents, which are integers, to determine whether the product can be computed.</span></span> <span data-ttu-id="3ff52-108">Se a operação de serviço não calcula o produto, a mensagem é colocada de volta na fila e pode ser recebida novamente pelo serviço escutando na fila.</span><span class="sxs-lookup"><span data-stu-id="3ff52-108">If the service operation does not compute the product, the message is put back into the queue and can be received again by the service listening on the queue.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="3ff52-109">Os exemplos podem mais ser instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="3ff52-109">The samples may already be installed on your computer.</span></span> <span data-ttu-id="3ff52-110">Verificar o seguinte diretório (padrão) antes de continuar:</span><span class="sxs-lookup"><span data-stu-id="3ff52-110">Check for the following (default) directory before continuing:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="3ff52-111">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="3ff52-111">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="3ff52-112">Este exemplo está no seguinte diretório:</span><span class="sxs-lookup"><span data-stu-id="3ff52-112">This sample is located in the following directory:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\ReceiveContextProductGenerator`  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="3ff52-113">Para usar este exemplo</span><span class="sxs-lookup"><span data-stu-id="3ff52-113">To use this sample</span></span>  
  
1.  <span data-ttu-id="3ff52-114">Certifique-se de que o serviço de enfileiramento de mensagens da Microsoft (MSMQ) está instalado.</span><span class="sxs-lookup"><span data-stu-id="3ff52-114">Ensure that Microsoft Message Queuing (MSMQ) is installed.</span></span>  
  
    1.  <span data-ttu-id="3ff52-115">Para instalar o MSMQ em [!INCLUDE[lserver](../../../../includes/lserver-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="3ff52-115">To install MSMQ on [!INCLUDE[lserver](../../../../includes/lserver-md.md)]:</span></span>  
  
        1.  <span data-ttu-id="3ff52-116">Em **Gerenciador do servidor**, clique em **recursos**.</span><span class="sxs-lookup"><span data-stu-id="3ff52-116">In **Server Manager**, click **Features**.</span></span>  
  
        2.  <span data-ttu-id="3ff52-117">No painel direito, em **resumo dos recursos**, clique em **adicionar recursos**.</span><span class="sxs-lookup"><span data-stu-id="3ff52-117">In the right pane under **Features Summary**, click **Add Features**.</span></span>  
  
        3.  <span data-ttu-id="3ff52-118">Na janela resultante, expanda **enfileiramento**.</span><span class="sxs-lookup"><span data-stu-id="3ff52-118">In the resulting window, expand **Message Queuing**.</span></span>  
  
        4.  <span data-ttu-id="3ff52-119">Expanda **serviços de enfileiramento de mensagens**.</span><span class="sxs-lookup"><span data-stu-id="3ff52-119">Expand **Message Queuing Services**.</span></span>  
  
        5.  <span data-ttu-id="3ff52-120">Clique em **integração dos serviços de diretório** (para computadores que ingressaram em um domínio) e, em seguida, clique em **suporte a HTTP**.</span><span class="sxs-lookup"><span data-stu-id="3ff52-120">Click **Directory Services Integration** (for computers joined to a domain), and then click **HTTP Support**.</span></span>  
  
        6.  <span data-ttu-id="3ff52-121">Clique em **próximo**e, em seguida, clique em **instalar**.</span><span class="sxs-lookup"><span data-stu-id="3ff52-121">Click **Next**, and then click **Install**.</span></span>  
  
    2.  <span data-ttu-id="3ff52-122">Para instalar o MSMQ em [!INCLUDE[wv](../../../../includes/wv-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="3ff52-122">To install MSMQ on [!INCLUDE[wv](../../../../includes/wv-md.md)]:</span></span>  
  
        1.  <span data-ttu-id="3ff52-123">Abra **Painel de Controle**.</span><span class="sxs-lookup"><span data-stu-id="3ff52-123">Open **Control Panel**.</span></span>  
  
        2.  <span data-ttu-id="3ff52-124">Clique em **programas** e, em seguida, em **programas e recursos**, clique em **ativar e desativar recursos do Windows**.</span><span class="sxs-lookup"><span data-stu-id="3ff52-124">Click **Programs** and then, under **Programs and Features**, click **Turn Windows Features on and off**.</span></span>  
  
        3.  <span data-ttu-id="3ff52-125">Expanda **fila de mensagens da Microsoft (MSMQ) Server**, expanda **fila de mensagens da Microsoft (MSMQ) Server Core**e, em seguida, selecione as caixas de seleção para os seguintes recursos instalar o enfileiramento de mensagens:</span><span class="sxs-lookup"><span data-stu-id="3ff52-125">Expand **Microsoft Message Queue (MSMQ) Server**, expand **Microsoft Message Queue (MSMQ) Server Core**, and then select the check boxes for the following Message Queuing features to install:</span></span>  
  
            -   <span data-ttu-id="3ff52-126">Servidor de enfileiramento de mensagens</span><span class="sxs-lookup"><span data-stu-id="3ff52-126">Message Queuing Server</span></span>  
  
            -   <span data-ttu-id="3ff52-127">MSMQ domínio serviços de integração do Active Directory (para computadores que ingressaram em um domínio)</span><span class="sxs-lookup"><span data-stu-id="3ff52-127">MSMQ Active Directory Domain Services Integration (for computers joined to a domain)</span></span>  
  
            -   <span data-ttu-id="3ff52-128">Suporte a HTTP do MSMQ</span><span class="sxs-lookup"><span data-stu-id="3ff52-128">MSMQ HTTP Support</span></span>  
  
        4.  <span data-ttu-id="3ff52-129">Clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="3ff52-129">Click **OK**.</span></span>  
  
        5.  <span data-ttu-id="3ff52-130">Se você for solicitado a reiniciar o computador, clique em **Okey** para concluir a instalação.</span><span class="sxs-lookup"><span data-stu-id="3ff52-130">If you are prompted to restart the computer, click **OK** to complete the installation.</span></span>  
  
2.  <span data-ttu-id="3ff52-131">Certifique-se de que [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] está instalado no computador.</span><span class="sxs-lookup"><span data-stu-id="3ff52-131">Ensure that [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] is installed on the computer.</span></span>  
  
3.  <span data-ttu-id="3ff52-132">Usando [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], abra o arquivo de solução de ReceiveContextProductGenerator.sln.</span><span class="sxs-lookup"><span data-stu-id="3ff52-132">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open the ReceiveContextProductGenerator.sln solution file.</span></span>  
  
4.  <span data-ttu-id="3ff52-133">Para criar a solução, pressione CTRL+SHIFT+B.</span><span class="sxs-lookup"><span data-stu-id="3ff52-133">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
5.  <span data-ttu-id="3ff52-134">Para executar a solução, pressione CTRL+F5.</span><span class="sxs-lookup"><span data-stu-id="3ff52-134">To run the solution, press CTRL+F5.</span></span>
