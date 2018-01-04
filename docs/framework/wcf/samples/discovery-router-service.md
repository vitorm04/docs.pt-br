---
title: "Serviço de roteador de descoberta"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3d30af47-b24f-40e5-833a-24d77125c9e6
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2ec96a4c318b7f9994f04bf2e4dfc6209cadda29
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="discovery-router-service"></a><span data-ttu-id="ff6c0-102">Serviço de roteador de descoberta</span><span class="sxs-lookup"><span data-stu-id="ff6c0-102">Discovery Router Service</span></span>
<span data-ttu-id="ff6c0-103">Este exemplo demonstra como encaminhar mensagens de descoberta para outro ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="ff6c0-103">This sample demonstrates how to forward discovery messages to another endpoint.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="ff6c0-104">Demonstra</span><span class="sxs-lookup"><span data-stu-id="ff6c0-104">Demonstrates</span></span>  
 <span data-ttu-id="ff6c0-105">Roteamento de descoberta</span><span class="sxs-lookup"><span data-stu-id="ff6c0-105">Discovery Routing</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="ff6c0-106">Discussão</span><span class="sxs-lookup"><span data-stu-id="ff6c0-106">Discussion</span></span>  
 <span data-ttu-id="ff6c0-107">Roteamento de descoberta é útil em um cenário em que um cliente está procurando por um serviço usando um proxy e o proxy não sabe nada sobre um serviço, mas sabe de outro proxy.</span><span class="sxs-lookup"><span data-stu-id="ff6c0-107">Discovery routing is useful in a scenario in which a client is looking for a service using a proxy and the proxy is unaware of such a service, but knows of another proxy.</span></span> <span data-ttu-id="ff6c0-108">Este proxy pode encaminhar o pacote de descoberta desse cliente para o proxy de segundo.</span><span class="sxs-lookup"><span data-stu-id="ff6c0-108">This proxy can forward the discovery packet from this client to the second proxy.</span></span> <span data-ttu-id="ff6c0-109">O segundo proxy pode procurar o serviço e retornar a resposta para o cliente original.</span><span class="sxs-lookup"><span data-stu-id="ff6c0-109">The second proxy can look for the service and return the responses to the original client.</span></span>  
  
 <span data-ttu-id="ff6c0-110">Neste exemplo, um cliente envia uma mensagem para um componente de roteamento de descoberta.</span><span class="sxs-lookup"><span data-stu-id="ff6c0-110">In this sample, a client sends a message to a discovery routing component.</span></span> <span data-ttu-id="ff6c0-111">Esta mensagem é enviada para um ponto de extremidade específico do roteador de descoberta.</span><span class="sxs-lookup"><span data-stu-id="ff6c0-111">This message is sent to a specific endpoint on the discovery router.</span></span> <span data-ttu-id="ff6c0-112">O roteador encaminha a mensagem para um UDP multicast do ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="ff6c0-112">The router then forwards the message to a UDP multicast endpoint.</span></span> <span data-ttu-id="ff6c0-113">A mensagem de teste vai para o ponto de extremidade de multicast e um serviço de escuta em um UDP multicast endereço responde a esse roteador de descoberta.</span><span class="sxs-lookup"><span data-stu-id="ff6c0-113">The probe message goes out to the multicast endpoint and a service listening on a UDP multicast address responds to that discovery router.</span></span> <span data-ttu-id="ff6c0-114">O roteador de descoberta coleta as respostas e as envia ao cliente.</span><span class="sxs-lookup"><span data-stu-id="ff6c0-114">The discovery router collects the responses and sends them back to the client.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="ff6c0-115">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="ff6c0-115">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="ff6c0-116">Crie o exemplo.</span><span class="sxs-lookup"><span data-stu-id="ff6c0-116">Build the sample.</span></span>  
  
2.  <span data-ttu-id="ff6c0-117">Execute o executável DiscoveryRouter.</span><span class="sxs-lookup"><span data-stu-id="ff6c0-117">Run the DiscoveryRouter executable.</span></span>  
  
3.  <span data-ttu-id="ff6c0-118">Execute o executável do serviço de diretório de compilação.</span><span class="sxs-lookup"><span data-stu-id="ff6c0-118">Run the service executable from the build directory.</span></span>  
  
4.  <span data-ttu-id="ff6c0-119">Execute o executável do cliente.</span><span class="sxs-lookup"><span data-stu-id="ff6c0-119">Run the client executable.</span></span> <span data-ttu-id="ff6c0-120">Observe que o cliente localiza o serviço.</span><span class="sxs-lookup"><span data-stu-id="ff6c0-120">Note that the client locates the service.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ff6c0-121">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="ff6c0-121">The samples may already be installed on your machine.</span></span> <span data-ttu-id="ff6c0-122">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="ff6c0-122">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="ff6c0-123">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="ff6c0-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ff6c0-124">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="ff6c0-124">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\DiscoveryRouter`
