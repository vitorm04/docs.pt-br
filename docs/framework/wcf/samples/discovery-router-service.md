---
title: Serviço de roteador de descoberta
ms.date: 03/30/2017
ms.assetid: 3d30af47-b24f-40e5-833a-24d77125c9e6
ms.openlocfilehash: 09309b23d2a3cc672811c2f617e6fb81a2b4e021
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74712284"
---
# <a name="discovery-router-service"></a><span data-ttu-id="59d0b-102">Serviço de roteador de descoberta</span><span class="sxs-lookup"><span data-stu-id="59d0b-102">Discovery Router Service</span></span>
<span data-ttu-id="59d0b-103">Este exemplo demonstra como encaminhar mensagens de descoberta para outro ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="59d0b-103">This sample demonstrates how to forward discovery messages to another endpoint.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="59d0b-104">Demonstra</span><span class="sxs-lookup"><span data-stu-id="59d0b-104">Demonstrates</span></span>  
 <span data-ttu-id="59d0b-105">Roteamento de descoberta</span><span class="sxs-lookup"><span data-stu-id="59d0b-105">Discovery Routing</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="59d0b-106">Discussão</span><span class="sxs-lookup"><span data-stu-id="59d0b-106">Discussion</span></span>  
 <span data-ttu-id="59d0b-107">O roteamento de descoberta é útil em um cenário no qual um cliente está procurando um serviço usando um proxy e o proxy não está ciente desse serviço, mas sabe de outro proxy.</span><span class="sxs-lookup"><span data-stu-id="59d0b-107">Discovery routing is useful in a scenario in which a client is looking for a service using a proxy and the proxy is unaware of such a service, but knows of another proxy.</span></span> <span data-ttu-id="59d0b-108">Esse proxy pode encaminhar o pacote de descoberta deste cliente para o segundo proxy.</span><span class="sxs-lookup"><span data-stu-id="59d0b-108">This proxy can forward the discovery packet from this client to the second proxy.</span></span> <span data-ttu-id="59d0b-109">O segundo proxy pode procurar o serviço e retornar as respostas para o cliente original.</span><span class="sxs-lookup"><span data-stu-id="59d0b-109">The second proxy can look for the service and return the responses to the original client.</span></span>  
  
 <span data-ttu-id="59d0b-110">Neste exemplo, um cliente envia uma mensagem para um componente de roteamento de descoberta.</span><span class="sxs-lookup"><span data-stu-id="59d0b-110">In this sample, a client sends a message to a discovery routing component.</span></span> <span data-ttu-id="59d0b-111">Essa mensagem é enviada para um ponto de extremidade específico no roteador de descoberta.</span><span class="sxs-lookup"><span data-stu-id="59d0b-111">This message is sent to a specific endpoint on the discovery router.</span></span> <span data-ttu-id="59d0b-112">Em seguida, o roteador encaminha a mensagem para um ponto de extremidade de multicast UDP.</span><span class="sxs-lookup"><span data-stu-id="59d0b-112">The router then forwards the message to a UDP multicast endpoint.</span></span> <span data-ttu-id="59d0b-113">A mensagem de investigação sai para o ponto de extremidade de multicast e um serviço que escuta em um endereço de multicast UDP responde a esse roteador de descoberta.</span><span class="sxs-lookup"><span data-stu-id="59d0b-113">The probe message goes out to the multicast endpoint and a service listening on a UDP multicast address responds to that discovery router.</span></span> <span data-ttu-id="59d0b-114">O roteador de descoberta coleta as respostas e as envia de volta para o cliente.</span><span class="sxs-lookup"><span data-stu-id="59d0b-114">The discovery router collects the responses and sends them back to the client.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="59d0b-115">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="59d0b-115">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="59d0b-116">Compile o exemplo.</span><span class="sxs-lookup"><span data-stu-id="59d0b-116">Build the sample.</span></span>  
  
2. <span data-ttu-id="59d0b-117">Execute o executável DiscoveryRouter.</span><span class="sxs-lookup"><span data-stu-id="59d0b-117">Run the DiscoveryRouter executable.</span></span>  
  
3. <span data-ttu-id="59d0b-118">Execute o executável do serviço no diretório de compilação.</span><span class="sxs-lookup"><span data-stu-id="59d0b-118">Run the service executable from the build directory.</span></span>  
  
4. <span data-ttu-id="59d0b-119">Execute o executável do cliente.</span><span class="sxs-lookup"><span data-stu-id="59d0b-119">Run the client executable.</span></span> <span data-ttu-id="59d0b-120">Observe que o cliente localiza o serviço.</span><span class="sxs-lookup"><span data-stu-id="59d0b-120">Note that the client locates the service.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="59d0b-121">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="59d0b-121">The samples may already be installed on your machine.</span></span> <span data-ttu-id="59d0b-122">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="59d0b-122">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="59d0b-123">Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] amostras.</span><span class="sxs-lookup"><span data-stu-id="59d0b-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="59d0b-124">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="59d0b-124">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\DiscoveryRouter`
