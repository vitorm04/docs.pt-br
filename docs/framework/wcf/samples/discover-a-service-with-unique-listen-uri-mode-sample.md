---
title: Descubra um serviço com exemplo de modo único de URI de escuta
ms.date: 03/30/2017
ms.assetid: 9a6d35b2-0469-43c8-a0c9-63623e3d2733
ms.openlocfilehash: 7e1c5ae0cb1a44c72a27566035b4bc20acbf1614
ms.sourcegitcommit: f513a91160b3fec289dd06646d0d6f81f8fcf910
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46320796"
---
# <a name="discover-a-service-with-unique-listen-uri-mode-sample"></a><span data-ttu-id="2c9a3-102">Descubra um serviço com exemplo de modo único de URI de escuta</span><span class="sxs-lookup"><span data-stu-id="2c9a3-102">Discover a Service with Unique Listen Uri Mode Sample</span></span>
<span data-ttu-id="2c9a3-103">Este exemplo demonstra como descobrir um serviço que tem o <xref:System.ServiceModel.Channels.BindingContext.ListenUriMode%2A> propriedade definida como <xref:System.ServiceModel.Description.ListenUriMode.Unique>.</span><span class="sxs-lookup"><span data-stu-id="2c9a3-103">This sample demonstrates how to discover a service that has the <xref:System.ServiceModel.Channels.BindingContext.ListenUriMode%2A> property set to <xref:System.ServiceModel.Description.ListenUriMode.Unique>.</span></span> <span data-ttu-id="2c9a3-104">Quando o <xref:System.ServiceModel.Channels.BindingContext.ListenUriMode%2A> estiver definida como <xref:System.ServiceModel.Description.ListenUriMode.Unique>, o ListenUri é garantido para ser exclusivo, definindo a porta ser exclusivo ou o caminho ser exclusivo, acrescentando um GUID.</span><span class="sxs-lookup"><span data-stu-id="2c9a3-104">When the <xref:System.ServiceModel.Channels.BindingContext.ListenUriMode%2A> property is set to <xref:System.ServiceModel.Description.ListenUriMode.Unique>, the ListenUri is ensured to be unique by either setting the port to be unique or for the path to be unique by appending a GUID.</span></span>  
  
### <a name="features-on-the-service"></a><span data-ttu-id="2c9a3-105">Recursos do serviço</span><span class="sxs-lookup"><span data-stu-id="2c9a3-105">Features on the Service</span></span>  
 <span data-ttu-id="2c9a3-106">O <xref:System.ServiceModel.Channels.BindingContext.ListenUriMode%2A> estiver definida como <xref:System.ServiceModel.Description.ListenUriMode.Unique> para o ponto de extremidade TCP.</span><span class="sxs-lookup"><span data-stu-id="2c9a3-106">The <xref:System.ServiceModel.Channels.BindingContext.ListenUriMode%2A> property is set to <xref:System.ServiceModel.Description.ListenUriMode.Unique> for the TCP endpoint.</span></span> <span data-ttu-id="2c9a3-107">O serviço é feito, em seguida, podem ser descoberto por um <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="2c9a3-107">The service is then made discoverable over a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> endpoint.</span></span>  
  
### <a name="features-on-the-client"></a><span data-ttu-id="2c9a3-108">Recursos no cliente</span><span class="sxs-lookup"><span data-stu-id="2c9a3-108">Features on the Client</span></span>  
 <span data-ttu-id="2c9a3-109">Esse cliente se conecta ao serviço usando o correto `Via.Uri` usando o <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> método.</span><span class="sxs-lookup"><span data-stu-id="2c9a3-109">This client connects to the service using the correct `Via.Uri` by using the <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> method.</span></span> <span data-ttu-id="2c9a3-110">O <xref:System.ServiceModel.Discovery.FindResponse> que é retornado do método, em seguida, é consultado sobre se ele contém um válido <xref:System.ServiceModel.Endpoint.ListenUri%2A> e se ele é diferente de `Address.Uri`.</span><span class="sxs-lookup"><span data-stu-id="2c9a3-110">The <xref:System.ServiceModel.Discovery.FindResponse> that is returned from the method is then queried for whether it contains a valid <xref:System.ServiceModel.Endpoint.ListenUri%2A> and whether it is different than `Address.Uri`.</span></span> <span data-ttu-id="2c9a3-111">As informações apropriadas, em seguida, são passadas para o `InvokeCalculatorService` método.</span><span class="sxs-lookup"><span data-stu-id="2c9a3-111">The appropriate information is then passed to the `InvokeCalculatorService` method.</span></span> <span data-ttu-id="2c9a3-112">No `InvokeCalculatorService` método, o <xref:System.ServiceModel.Endpoint.ListenUri%2A> foi passado pelo chamador, em seguida, um `ClientViaBehavior` com o nome correto `Via.Uri` é adicionado ao ponto de extremidade do cliente.</span><span class="sxs-lookup"><span data-stu-id="2c9a3-112">In the `InvokeCalculatorService` method, the <xref:System.ServiceModel.Endpoint.ListenUri%2A> was passed in by the caller, then a `ClientViaBehavior` with the correct `Via.Uri` is added to the client’s endpoint.</span></span>  
  
##### <a name="to-use-this-sample"></a><span data-ttu-id="2c9a3-113">Para usar este exemplo</span><span class="sxs-lookup"><span data-stu-id="2c9a3-113">To use this sample</span></span>  
  
1.  <span data-ttu-id="2c9a3-114">Usando [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], abra UniqueListenUriMode.sln.</span><span class="sxs-lookup"><span data-stu-id="2c9a3-114">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open UniqueListenUriMode.sln.</span></span>  
  
2.  <span data-ttu-id="2c9a3-115">Para criar a solução, pressione CTRL+SHIFT+B.</span><span class="sxs-lookup"><span data-stu-id="2c9a3-115">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="2c9a3-116">Execute o aplicativo de serviço, que é gerado na pasta \service\bin\debug [diretório da solução].</span><span class="sxs-lookup"><span data-stu-id="2c9a3-116">Run the service application, which is generated in the [solution base directory]\service\bin\debug folder.</span></span>  
  
4.  <span data-ttu-id="2c9a3-117">Execute o aplicativo cliente, que é gerado na pasta \Client\bin\debug [diretório da solução].</span><span class="sxs-lookup"><span data-stu-id="2c9a3-117">Run the client application, which is generated in the [solution base directory]\Client\bin\debug folder.</span></span>  
  
     <span data-ttu-id="2c9a3-118">O cliente localiza o serviço em execução e grava os metadados publicados pelo ponto de extremidade do serviço no console.</span><span class="sxs-lookup"><span data-stu-id="2c9a3-118">The client locates the running service and writes to the console the metadata published by the service’s endpoint.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="2c9a3-119">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="2c9a3-119">The samples may already be installed on your machine.</span></span> <span data-ttu-id="2c9a3-120">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="2c9a3-120">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="2c9a3-121">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="2c9a3-121">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="2c9a3-122">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="2c9a3-122">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\UniqueListenUriMode`  
  
## <a name="see-also"></a><span data-ttu-id="2c9a3-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2c9a3-123">See Also</span></span>
