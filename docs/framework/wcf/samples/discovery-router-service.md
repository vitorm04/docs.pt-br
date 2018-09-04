---
title: Serviço de roteador de descoberta
ms.date: 03/30/2017
ms.assetid: 3d30af47-b24f-40e5-833a-24d77125c9e6
ms.openlocfilehash: 9c0c409eb6cf3146a198b9f4bcd6d76660f5da36
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43509075"
---
# <a name="discovery-router-service"></a><span data-ttu-id="91486-102">Serviço de roteador de descoberta</span><span class="sxs-lookup"><span data-stu-id="91486-102">Discovery Router Service</span></span>
<span data-ttu-id="91486-103">Este exemplo demonstra como encaminhar mensagens para outro ponto de extremidade de descoberta.</span><span class="sxs-lookup"><span data-stu-id="91486-103">This sample demonstrates how to forward discovery messages to another endpoint.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="91486-104">Demonstra</span><span class="sxs-lookup"><span data-stu-id="91486-104">Demonstrates</span></span>  
 <span data-ttu-id="91486-105">Roteamento de descoberta</span><span class="sxs-lookup"><span data-stu-id="91486-105">Discovery Routing</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="91486-106">Discussão</span><span class="sxs-lookup"><span data-stu-id="91486-106">Discussion</span></span>  
 <span data-ttu-id="91486-107">O roteamento de descoberta é útil em um cenário em que um cliente está procurando por um serviço usando um proxy e o proxy não tem conhecimento de um serviço como esse, mas sabe de outro proxy.</span><span class="sxs-lookup"><span data-stu-id="91486-107">Discovery routing is useful in a scenario in which a client is looking for a service using a proxy and the proxy is unaware of such a service, but knows of another proxy.</span></span> <span data-ttu-id="91486-108">Esse proxy pode encaminhar o pacote de descoberta deste cliente para o proxy do segundo.</span><span class="sxs-lookup"><span data-stu-id="91486-108">This proxy can forward the discovery packet from this client to the second proxy.</span></span> <span data-ttu-id="91486-109">O proxy do segundo pode procurar o serviço e retornar as respostas ao cliente original.</span><span class="sxs-lookup"><span data-stu-id="91486-109">The second proxy can look for the service and return the responses to the original client.</span></span>  
  
 <span data-ttu-id="91486-110">Neste exemplo, um cliente envia uma mensagem a um componente de roteamento de descoberta.</span><span class="sxs-lookup"><span data-stu-id="91486-110">In this sample, a client sends a message to a discovery routing component.</span></span> <span data-ttu-id="91486-111">Esta mensagem é enviada para um ponto de extremidade específico do roteador de descoberta.</span><span class="sxs-lookup"><span data-stu-id="91486-111">This message is sent to a specific endpoint on the discovery router.</span></span> <span data-ttu-id="91486-112">O roteador encaminha a mensagem para um UDP multicast do ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="91486-112">The router then forwards the message to a UDP multicast endpoint.</span></span> <span data-ttu-id="91486-113">A mensagem de teste vai para o ponto de extremidade de multicast e um serviço escutando em um UDP multicast endereço responde a esse roteador de descoberta.</span><span class="sxs-lookup"><span data-stu-id="91486-113">The probe message goes out to the multicast endpoint and a service listening on a UDP multicast address responds to that discovery router.</span></span> <span data-ttu-id="91486-114">O roteador de descoberta coleta as respostas e as envia ao cliente.</span><span class="sxs-lookup"><span data-stu-id="91486-114">The discovery router collects the responses and sends them back to the client.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="91486-115">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="91486-115">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="91486-116">Crie o exemplo.</span><span class="sxs-lookup"><span data-stu-id="91486-116">Build the sample.</span></span>  
  
2.  <span data-ttu-id="91486-117">Execute o executável DiscoveryRouter.</span><span class="sxs-lookup"><span data-stu-id="91486-117">Run the DiscoveryRouter executable.</span></span>  
  
3.  <span data-ttu-id="91486-118">Execute o executável do serviço de diretório de compilação.</span><span class="sxs-lookup"><span data-stu-id="91486-118">Run the service executable from the build directory.</span></span>  
  
4.  <span data-ttu-id="91486-119">Execute o executável do cliente.</span><span class="sxs-lookup"><span data-stu-id="91486-119">Run the client executable.</span></span> <span data-ttu-id="91486-120">Observe que o cliente localiza o serviço.</span><span class="sxs-lookup"><span data-stu-id="91486-120">Note that the client locates the service.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="91486-121">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="91486-121">The samples may already be installed on your machine.</span></span> <span data-ttu-id="91486-122">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="91486-122">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="91486-123">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="91486-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="91486-124">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="91486-124">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\DiscoveryRouter`
