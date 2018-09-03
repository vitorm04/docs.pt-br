---
title: CustomDiscoveryMetadata
ms.date: 03/30/2017
ms.assetid: c42455fd-3652-4b7e-b698-ab3a2bb52e48
ms.openlocfilehash: 181910db3f1dd6da892f6ae2ddcbf7bd5859ff17
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2018
ms.locfileid: "43465571"
---
# <a name="customdiscoverymetadata"></a><span data-ttu-id="0b202-102">CustomDiscoveryMetadata</span><span class="sxs-lookup"><span data-stu-id="0b202-102">CustomDiscoveryMetadata</span></span>
<span data-ttu-id="0b202-103">Este exemplo mostra como inserir metadados personalizados do XML de metadados de descoberta para um ponto de extremidade podem ser descoberto exposto por um serviço.</span><span class="sxs-lookup"><span data-stu-id="0b202-103">This sample shows how to insert custom XML metadata into the discovery metadata for a discoverable endpoint exposed by a service.</span></span> <span data-ttu-id="0b202-104">O exemplo, em seguida, mostra como um cliente pode procurar o serviço e extrair esses dados.</span><span class="sxs-lookup"><span data-stu-id="0b202-104">The sample then shows how a client can search for the service and extract this custom data.</span></span> <span data-ttu-id="0b202-105">Esse exemplo consiste em dois projetos, serviço e cliente.</span><span class="sxs-lookup"><span data-stu-id="0b202-105">This sample consists of two projects, service and client.</span></span>  
  
## <a name="service"></a><span data-ttu-id="0b202-106">Serviço</span><span class="sxs-lookup"><span data-stu-id="0b202-106">Service</span></span>  
 <span data-ttu-id="0b202-107">No `main` método, o exemplo mostra que um objeto do tipo <xref:System.Xml.Linq.XElement> é preenchida com os campos desejados e é adicionado ao <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>.</span><span class="sxs-lookup"><span data-stu-id="0b202-107">In the `main` method, the sample shows that an object of type <xref:System.Xml.Linq.XElement> is populated with the desired fields and is added to the <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>.</span></span> <span data-ttu-id="0b202-108">Isso <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> é adicionado a um ponto de extremidade específico.</span><span class="sxs-lookup"><span data-stu-id="0b202-108">This <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> is added to a particular endpoint.</span></span> <span data-ttu-id="0b202-109">Quando esse ponto de extremidade é descoberto, os metadados de descoberta contém os dados personalizados que foi adicionados aqui.</span><span class="sxs-lookup"><span data-stu-id="0b202-109">When that particular endpoint is discovered, the discovery metadata contains the custom data that was added here.</span></span>  
  
## <a name="client"></a><span data-ttu-id="0b202-110">Cliente</span><span class="sxs-lookup"><span data-stu-id="0b202-110">Client</span></span>  
 <span data-ttu-id="0b202-111">O exemplo mostra a <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> método sendo chamado em um <xref:System.ServiceModel.Discovery.DiscoveryClient>.</span><span class="sxs-lookup"><span data-stu-id="0b202-111">The sample shows the <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> method being called on a <xref:System.ServiceModel.Discovery.DiscoveryClient>.</span></span> <span data-ttu-id="0b202-112">Resultante <xref:System.ServiceModel.Discovery.FindResponse> é consultada para os elementos XML apropriados e esperados.</span><span class="sxs-lookup"><span data-stu-id="0b202-112">The resulting <xref:System.ServiceModel.Discovery.FindResponse> is then queried for the appropriate and expected XML elements.</span></span> <span data-ttu-id="0b202-113">Esses elementos, em seguida, são impressas no console.</span><span class="sxs-lookup"><span data-stu-id="0b202-113">These elements are then printed to the console.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="0b202-114">Para usar este exemplo</span><span class="sxs-lookup"><span data-stu-id="0b202-114">To use this sample</span></span>  
  
1.  <span data-ttu-id="0b202-115">Carregar a solução do projeto em [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] e compile o projeto.</span><span class="sxs-lookup"><span data-stu-id="0b202-115">Load the project solution in [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] and build the project.</span></span>  
  
2.  <span data-ttu-id="0b202-116">Executar o aplicativo de serviço, gerado em [diretório da solução] \service\bin\debug, primeiro e, em seguida, execute o aplicativo de cliente gerado em [diretório da solução] \Client\bin\debug</span><span class="sxs-lookup"><span data-stu-id="0b202-116">First run the Service application, generated in [solution base directory]\service\bin\debug, and then run the Client application, generated in [solution base directory]\Client\bin\debug</span></span>  
  
3.  <span data-ttu-id="0b202-117">Observe que o serviço fica online, o cliente localiza o serviço e imprime os publicado no ponto de extremidade de metadados.</span><span class="sxs-lookup"><span data-stu-id="0b202-117">Note that the service comes online, the client locates the service and prints the metadata published in the endpoint.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="0b202-118">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="0b202-118">The samples may already be installed on your machine.</span></span> <span data-ttu-id="0b202-119">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="0b202-119">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="0b202-120">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="0b202-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="0b202-121">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="0b202-121">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\DiscoveryExtensibility\CustomDiscoveryMetadata`  
  
## <a name="see-also"></a><span data-ttu-id="0b202-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0b202-122">See Also</span></span>
