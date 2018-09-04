---
title: Canais habilitados ReceiveContext do WCF
ms.date: 03/30/2017
ms.assetid: d990d119-7321-4b8c-852b-10256f59f9b0
ms.openlocfilehash: d7f80d0874606129876fbf7dfa30c0327680b922
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43515924"
---
# <a name="receivecontext-enabled-wcf-channels"></a><span data-ttu-id="2e324-102">Canais habilitados ReceiveContext do WCF</span><span class="sxs-lookup"><span data-stu-id="2e324-102">ReceiveContext-Enabled WCF Channels</span></span>
<span data-ttu-id="2e324-103">Este exemplo demonstra a utilidade dos <xref:System.ServiceModel.Channels.ReceiveContext>-habilitado canais do WCF.</span><span class="sxs-lookup"><span data-stu-id="2e324-103">This sample demonstrates the usefulness of <xref:System.ServiceModel.Channels.ReceiveContext>-enabled WCF channels.</span></span> <span data-ttu-id="2e324-104">O exemplo implementa um serviço para localizar o produto dos dois números usando um canal NetMSMQ.</span><span class="sxs-lookup"><span data-stu-id="2e324-104">The sample implements a service to find the product of two numbers using a NetMSMQ channel.</span></span>  
  
 <span data-ttu-id="2e324-105">O <xref:System.ServiceModel.Channels.ReceiveContext> classe permite que um aplicativo decidir se deve acessar a mensagem ou deixá-lo na fila para processamento adicional, mesmo depois que o conteúdo da mensagem tiver sido inspecionado.</span><span class="sxs-lookup"><span data-stu-id="2e324-105">The <xref:System.ServiceModel.Channels.ReceiveContext> class enables an application to decide whether to access the message or leave it in the queue for further processing, even after the contents of the message have been inspected.</span></span> <span data-ttu-id="2e324-106">Neste exemplo, um cliente envia inteiros aleatórios para uma fila transacional.</span><span class="sxs-lookup"><span data-stu-id="2e324-106">In this sample, a client sends random integers to a transactional queue.</span></span> <span data-ttu-id="2e324-107">O `ProductCalculator` serviço recebe as mensagens e inspeciona o conteúdo da mensagem, que são inteiros, para determinar se o produto pode ser computado.</span><span class="sxs-lookup"><span data-stu-id="2e324-107">The `ProductCalculator` service receives the messages and inspects the message contents, which are integers, to determine whether the product can be computed.</span></span> <span data-ttu-id="2e324-108">Se a operação de serviço não calcula o produto, a mensagem é colocada de volta na fila e pode ser recebida novamente pelo serviço escutando na fila.</span><span class="sxs-lookup"><span data-stu-id="2e324-108">If the service operation does not compute the product, the message is put back into the queue and can be received again by the service listening on the queue.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="2e324-109">Os exemplos podem mais ser instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="2e324-109">The samples may already be installed on your computer.</span></span> <span data-ttu-id="2e324-110">Verificar o seguinte diretório (padrão) antes de continuar:</span><span class="sxs-lookup"><span data-stu-id="2e324-110">Check for the following (default) directory before continuing:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="2e324-111">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="2e324-111">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="2e324-112">Este exemplo está no seguinte diretório:</span><span class="sxs-lookup"><span data-stu-id="2e324-112">This sample is located in the following directory:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\ReceiveContextProductGenerator`  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="2e324-113">Para usar este exemplo</span><span class="sxs-lookup"><span data-stu-id="2e324-113">To use this sample</span></span>  
  
1.  <span data-ttu-id="2e324-114">Certifique-se de que o Microsoft Message Queuing (MSMQ) está instalado.</span><span class="sxs-lookup"><span data-stu-id="2e324-114">Ensure that Microsoft Message Queuing (MSMQ) is installed.</span></span>  
  
    1.  <span data-ttu-id="2e324-115">Para instalar o MSMQ em [!INCLUDE[lserver](../../../../includes/lserver-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="2e324-115">To install MSMQ on [!INCLUDE[lserver](../../../../includes/lserver-md.md)]:</span></span>  
  
        1.  <span data-ttu-id="2e324-116">Na **Gerenciador de servidores**, clique em **recursos**.</span><span class="sxs-lookup"><span data-stu-id="2e324-116">In **Server Manager**, click **Features**.</span></span>  
  
        2.  <span data-ttu-id="2e324-117">No painel direito, sob **resumo de recursos**, clique em **adicionar recursos**.</span><span class="sxs-lookup"><span data-stu-id="2e324-117">In the right pane under **Features Summary**, click **Add Features**.</span></span>  
  
        3.  <span data-ttu-id="2e324-118">Na janela resultante, expanda **enfileiramento**.</span><span class="sxs-lookup"><span data-stu-id="2e324-118">In the resulting window, expand **Message Queuing**.</span></span>  
  
        4.  <span data-ttu-id="2e324-119">Expandir **serviços de enfileiramento de mensagens**.</span><span class="sxs-lookup"><span data-stu-id="2e324-119">Expand **Message Queuing Services**.</span></span>  
  
        5.  <span data-ttu-id="2e324-120">Clique em **integração de serviços de diretório** (para computadores que ingressaram em um domínio) e, em seguida, clique em **suporte HTTP**.</span><span class="sxs-lookup"><span data-stu-id="2e324-120">Click **Directory Services Integration** (for computers joined to a domain), and then click **HTTP Support**.</span></span>  
  
        6.  <span data-ttu-id="2e324-121">Clique em **próxima**e, em seguida, clique em **instalar**.</span><span class="sxs-lookup"><span data-stu-id="2e324-121">Click **Next**, and then click **Install**.</span></span>  
  
    2.  <span data-ttu-id="2e324-122">Para instalar o MSMQ em [!INCLUDE[wv](../../../../includes/wv-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="2e324-122">To install MSMQ on [!INCLUDE[wv](../../../../includes/wv-md.md)]:</span></span>  
  
        1.  <span data-ttu-id="2e324-123">Abra **Painel de Controle**.</span><span class="sxs-lookup"><span data-stu-id="2e324-123">Open **Control Panel**.</span></span>  
  
        2.  <span data-ttu-id="2e324-124">Clique em **programas** e, em **programas e recursos**, clique em **ativar e desativar recursos do Windows**.</span><span class="sxs-lookup"><span data-stu-id="2e324-124">Click **Programs** and then, under **Programs and Features**, click **Turn Windows Features on and off**.</span></span>  
  
        3.  <span data-ttu-id="2e324-125">Expandir **servidor do Microsoft Message Queue (MSMQ)**, expanda **Server Core do Microsoft Message Queue (MSMQ)** e, em seguida, selecione as caixas de seleção para os seguintes recursos instalar o enfileiramento de mensagens:</span><span class="sxs-lookup"><span data-stu-id="2e324-125">Expand **Microsoft Message Queue (MSMQ) Server**, expand **Microsoft Message Queue (MSMQ) Server Core**, and then select the check boxes for the following Message Queuing features to install:</span></span>  
  
            -   <span data-ttu-id="2e324-126">Servidor de enfileiramento de mensagens</span><span class="sxs-lookup"><span data-stu-id="2e324-126">Message Queuing Server</span></span>  
  
            -   <span data-ttu-id="2e324-127">MSMQ domínio serviços de integração do Active Directory (para computadores que ingressaram em um domínio)</span><span class="sxs-lookup"><span data-stu-id="2e324-127">MSMQ Active Directory Domain Services Integration (for computers joined to a domain)</span></span>  
  
            -   <span data-ttu-id="2e324-128">Suporte a HTTP do MSMQ</span><span class="sxs-lookup"><span data-stu-id="2e324-128">MSMQ HTTP Support</span></span>  
  
        4.  <span data-ttu-id="2e324-129">Clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="2e324-129">Click **OK**.</span></span>  
  
        5.  <span data-ttu-id="2e324-130">Se você for solicitado a reiniciar o computador, clique em **Okey** para concluir a instalação.</span><span class="sxs-lookup"><span data-stu-id="2e324-130">If you are prompted to restart the computer, click **OK** to complete the installation.</span></span>  
  
2.  <span data-ttu-id="2e324-131">Certifique-se de que [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] está instalado no computador.</span><span class="sxs-lookup"><span data-stu-id="2e324-131">Ensure that [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] is installed on the computer.</span></span>  
  
3.  <span data-ttu-id="2e324-132">Usando [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], abra o arquivo de solução ReceiveContextProductGenerator.sln.</span><span class="sxs-lookup"><span data-stu-id="2e324-132">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open the ReceiveContextProductGenerator.sln solution file.</span></span>  
  
4.  <span data-ttu-id="2e324-133">Para criar a solução, pressione CTRL+SHIFT+B.</span><span class="sxs-lookup"><span data-stu-id="2e324-133">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
5.  <span data-ttu-id="2e324-134">Para executar a solução, pressione CTRL+F5.</span><span class="sxs-lookup"><span data-stu-id="2e324-134">To run the solution, press CTRL+F5.</span></span>
