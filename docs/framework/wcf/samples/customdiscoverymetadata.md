---
title: CustomDiscoveryMetadata
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c42455fd-3652-4b7e-b698-ab3a2bb52e48
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5b3272b642a04821d8343cae776e48f90d266cfe
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="customdiscoverymetadata"></a><span data-ttu-id="4077c-102">CustomDiscoveryMetadata</span><span class="sxs-lookup"><span data-stu-id="4077c-102">CustomDiscoveryMetadata</span></span>
<span data-ttu-id="4077c-103">Este exemplo mostra como inserir metadados XML personalizado para os metadados de descoberta para um ponto de extremidade detectável exposto por um serviço.</span><span class="sxs-lookup"><span data-stu-id="4077c-103">This sample shows how to insert custom XML metadata into the discovery metadata for a discoverable endpoint exposed by a service.</span></span> <span data-ttu-id="4077c-104">O exemplo e mostra como um cliente pode procurar o serviço e extrair esses dados.</span><span class="sxs-lookup"><span data-stu-id="4077c-104">The sample then shows how a client can search for the service and extract this custom data.</span></span> <span data-ttu-id="4077c-105">Este exemplo consiste em dois projetos, serviço e cliente.</span><span class="sxs-lookup"><span data-stu-id="4077c-105">This sample consists of two projects, service and client.</span></span>  
  
## <a name="service"></a><span data-ttu-id="4077c-106">Serviço</span><span class="sxs-lookup"><span data-stu-id="4077c-106">Service</span></span>  
 <span data-ttu-id="4077c-107">No `main` método, o exemplo mostra que um objeto do tipo <xref:System.Xml.Linq.XElement> é preenchida com os campos desejados e é adicionado para o <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>.</span><span class="sxs-lookup"><span data-stu-id="4077c-107">In the `main` method, the sample shows that an object of type <xref:System.Xml.Linq.XElement> is populated with the desired fields and is added to the <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>.</span></span> <span data-ttu-id="4077c-108">Isso <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> é adicionado a um ponto de extremidade específico.</span><span class="sxs-lookup"><span data-stu-id="4077c-108">This <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> is added to a particular endpoint.</span></span> <span data-ttu-id="4077c-109">Quando esse ponto de extremidade for descoberto, o Descoberta de metadados contém os dados personalizados que foram adicionados aqui.</span><span class="sxs-lookup"><span data-stu-id="4077c-109">When that particular endpoint is discovered, the discovery metadata contains the custom data that was added here.</span></span>  
  
## <a name="client"></a><span data-ttu-id="4077c-110">Cliente</span><span class="sxs-lookup"><span data-stu-id="4077c-110">Client</span></span>  
 <span data-ttu-id="4077c-111">O exemplo mostra o <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> método ser chamado em um <xref:System.ServiceModel.Discovery.DiscoveryClient>.</span><span class="sxs-lookup"><span data-stu-id="4077c-111">The sample shows the <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> method being called on a <xref:System.ServiceModel.Discovery.DiscoveryClient>.</span></span> <span data-ttu-id="4077c-112">Resultante <xref:System.ServiceModel.Discovery.FindResponse> é consultada para os elementos XML apropriados e esperados.</span><span class="sxs-lookup"><span data-stu-id="4077c-112">The resulting <xref:System.ServiceModel.Discovery.FindResponse> is then queried for the appropriate and expected XML elements.</span></span> <span data-ttu-id="4077c-113">Esses elementos são impressas, em seguida, no console.</span><span class="sxs-lookup"><span data-stu-id="4077c-113">These elements are then printed to the console.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="4077c-114">Para usar este exemplo</span><span class="sxs-lookup"><span data-stu-id="4077c-114">To use this sample</span></span>  
  
1.  <span data-ttu-id="4077c-115">Carregar a solução do projeto em [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] e compile o projeto.</span><span class="sxs-lookup"><span data-stu-id="4077c-115">Load the project solution in [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] and build the project.</span></span>  
  
2.  <span data-ttu-id="4077c-116">Primeiro execute o aplicativo de serviço, gerado em \service\bin\debug [diretório base de solução] e, em seguida, executar o aplicativo cliente, gerado em \Client\bin\debug [diretório base de solução]</span><span class="sxs-lookup"><span data-stu-id="4077c-116">First run the Service application, generated in [solution base directory]\service\bin\debug, and then run the Client application, generated in [solution base directory]\Client\bin\debug</span></span>  
  
3.  <span data-ttu-id="4077c-117">Observe que o serviço ficar online, o cliente localiza o serviço e imprime os metadados publicado no ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="4077c-117">Note that the service comes online, the client locates the service and prints the metadata published in the endpoint.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="4077c-118">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="4077c-118">The samples may already be installed on your machine.</span></span> <span data-ttu-id="4077c-119">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="4077c-119">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="4077c-120">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="4077c-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="4077c-121">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="4077c-121">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\DiscoveryExtensibility\CustomDiscoveryMetadata`  
  
## <a name="see-also"></a><span data-ttu-id="4077c-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4077c-122">See Also</span></span>
