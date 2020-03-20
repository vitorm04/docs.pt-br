---
title: Serviço de roteador de descoberta
ms.date: 03/30/2017
ms.assetid: 3d30af47-b24f-40e5-833a-24d77125c9e6
ms.openlocfilehash: 149dd69cdd1972465f4b7cb48ab657492d3f21d7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183724"
---
# <a name="discovery-router-service"></a><span data-ttu-id="7c8c1-102">Serviço de roteador de descoberta</span><span class="sxs-lookup"><span data-stu-id="7c8c1-102">Discovery Router Service</span></span>
<span data-ttu-id="7c8c1-103">Esta amostra demonstra como encaminhar mensagens de descoberta para outro ponto final.</span><span class="sxs-lookup"><span data-stu-id="7c8c1-103">This sample demonstrates how to forward discovery messages to another endpoint.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="7c8c1-104">Demonstra</span><span class="sxs-lookup"><span data-stu-id="7c8c1-104">Demonstrates</span></span>  
 <span data-ttu-id="7c8c1-105">Roteamento de descobertas</span><span class="sxs-lookup"><span data-stu-id="7c8c1-105">Discovery Routing</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="7c8c1-106">Discussão</span><span class="sxs-lookup"><span data-stu-id="7c8c1-106">Discussion</span></span>  
 <span data-ttu-id="7c8c1-107">O roteamento de descobertas é útil em um cenário no qual um cliente está procurando um serviço usando um proxy e o proxy desconhece tal serviço, mas sabe de outro proxy.</span><span class="sxs-lookup"><span data-stu-id="7c8c1-107">Discovery routing is useful in a scenario in which a client is looking for a service using a proxy and the proxy is unaware of such a service, but knows of another proxy.</span></span> <span data-ttu-id="7c8c1-108">Este proxy pode encaminhar o pacote de detecção deste cliente para o segundo proxy.</span><span class="sxs-lookup"><span data-stu-id="7c8c1-108">This proxy can forward the discovery packet from this client to the second proxy.</span></span> <span data-ttu-id="7c8c1-109">O segundo proxy pode procurar o serviço e retornar as respostas ao cliente original.</span><span class="sxs-lookup"><span data-stu-id="7c8c1-109">The second proxy can look for the service and return the responses to the original client.</span></span>  
  
 <span data-ttu-id="7c8c1-110">Nesta amostra, um cliente envia uma mensagem para um componente de roteamento de descobertas.</span><span class="sxs-lookup"><span data-stu-id="7c8c1-110">In this sample, a client sends a message to a discovery routing component.</span></span> <span data-ttu-id="7c8c1-111">Esta mensagem é enviada para um ponto final específico no roteador de descobertas.</span><span class="sxs-lookup"><span data-stu-id="7c8c1-111">This message is sent to a specific endpoint on the discovery router.</span></span> <span data-ttu-id="7c8c1-112">Em seguida, o roteador encaminha a mensagem para um ponto final multicast UDP.</span><span class="sxs-lookup"><span data-stu-id="7c8c1-112">The router then forwards the message to a UDP multicast endpoint.</span></span> <span data-ttu-id="7c8c1-113">A mensagem do teste vai para o ponto final de multicast e um serviço ouvindo em um endereço multicast UDP responde a esse roteador de detecção.</span><span class="sxs-lookup"><span data-stu-id="7c8c1-113">The probe message goes out to the multicast endpoint and a service listening on a UDP multicast address responds to that discovery router.</span></span> <span data-ttu-id="7c8c1-114">O roteador de descoberta coleta as respostas e as envia de volta para o cliente.</span><span class="sxs-lookup"><span data-stu-id="7c8c1-114">The discovery router collects the responses and sends them back to the client.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="7c8c1-115">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="7c8c1-115">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="7c8c1-116">Compile o exemplo.</span><span class="sxs-lookup"><span data-stu-id="7c8c1-116">Build the sample.</span></span>  
  
2. <span data-ttu-id="7c8c1-117">Execute o executável DiscoveryRouter.</span><span class="sxs-lookup"><span data-stu-id="7c8c1-117">Run the DiscoveryRouter executable.</span></span>  
  
3. <span data-ttu-id="7c8c1-118">Execute o executável de serviço a partir do diretório de compilação.</span><span class="sxs-lookup"><span data-stu-id="7c8c1-118">Run the service executable from the build directory.</span></span>  
  
4. <span data-ttu-id="7c8c1-119">Execute o cliente executável.</span><span class="sxs-lookup"><span data-stu-id="7c8c1-119">Run the client executable.</span></span> <span data-ttu-id="7c8c1-120">Observe que o cliente localiza o serviço.</span><span class="sxs-lookup"><span data-stu-id="7c8c1-120">Note that the client locates the service.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="7c8c1-121">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="7c8c1-121">The samples may already be installed on your machine.</span></span> <span data-ttu-id="7c8c1-122">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="7c8c1-122">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="7c8c1-123">Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation).</span><span class="sxs-lookup"><span data-stu-id="7c8c1-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="7c8c1-124">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="7c8c1-124">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\DiscoveryRouter`
