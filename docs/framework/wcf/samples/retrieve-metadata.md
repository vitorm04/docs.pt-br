---
title: Recuperar metadados
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e8a6ef8c-a195-495a-a15e-7d92bdf0b28c
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7321578cb76b9f06f09086834c2826a72631e49f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="retrieve-metadata"></a><span data-ttu-id="07bed-102">Recuperar metadados</span><span class="sxs-lookup"><span data-stu-id="07bed-102">Retrieve Metadata</span></span>
<span data-ttu-id="07bed-103">Este exemplo demonstra como implementar um cliente que dinamicamente recupera metadados de um serviço para escolher um ponto de extremidade com a qual se comunicar.</span><span class="sxs-lookup"><span data-stu-id="07bed-103">This sample demonstrates how to implement a client that dynamically retrieves metadata from a service to choose an endpoint with which to communicate.</span></span> <span data-ttu-id="07bed-104">Este exemplo se baseia o [Introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="07bed-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span> <span data-ttu-id="07bed-105">O serviço foi modificado para expor os dois pontos de extremidade — um ponto de extremidade no endereço base usando o `basicHttpBinding` de associação e um ponto de extremidade seguro em {*baseaddress*} / seguro usando o `wsHttpBinding` associação.</span><span class="sxs-lookup"><span data-stu-id="07bed-105">The service has been modified to expose two endpoints—an endpoint at the base address using the `basicHttpBinding` binding, and a secure endpoint at {*baseaddress*}/secure using the `wsHttpBinding` binding.</span></span> <span data-ttu-id="07bed-106">Em vez de configurar o cliente com os endereços de ponto de extremidade e associações, o cliente recupera dinamicamente os metadados para o serviço usando o <xref:System.ServiceModel.Description.MetadataExchangeClient> classe e, em seguida, importa os metadados como um <xref:System.ServiceModel.Description.ServiceEndpointCollection> usando o <xref:System.ServiceModel.Description.WsdlImporter> classe.</span><span class="sxs-lookup"><span data-stu-id="07bed-106">Instead of configuring the client with the endpoint addresses and bindings, the client dynamically retrieves the metadata for the service using the <xref:System.ServiceModel.Description.MetadataExchangeClient> class and then imports the metadata as a <xref:System.ServiceModel.Description.ServiceEndpointCollection> using the <xref:System.ServiceModel.Description.WsdlImporter> class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="07bed-107">As instruções de procedimento e a compilação de configuração para este exemplo estão localizadas no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="07bed-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="07bed-108">O aplicativo cliente usa o importados <xref:System.ServiceModel.Description.ServiceEndpointCollection> para criar clientes para se comunicar com o serviço.</span><span class="sxs-lookup"><span data-stu-id="07bed-108">The client application uses the imported <xref:System.ServiceModel.Description.ServiceEndpointCollection> to create clients to communicate with the service.</span></span> <span data-ttu-id="07bed-109">O aplicativo cliente itera por meio de cada ponto de extremidade recuperado e se comunica com cada ponto de extremidade que implementa o `ICalculator` contrato.</span><span class="sxs-lookup"><span data-stu-id="07bed-109">The client application iterates through each retrieved endpoint and communicates with each endpoint that implements the `ICalculator` contract.</span></span> <span data-ttu-id="07bed-110">O endereço apropriado e associação são fornecidos com o ponto de extremidade recuperado, para que o cliente está configurado para se comunicar com cada ponto de extremidade, conforme mostrado no código de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="07bed-110">The appropriate address and binding are provided with the retrieved endpoint, so that the client is configured to communicate with each endpoint, as shown in the following sample code.</span></span>  
  
```  
// Create a MetadataExchangeClient for retrieving metadata.  
EndpointAddress mexAddress = new EndpointAddress(ConfigurationManager.AppSettings["mexAddress"]);  
MetadataExchangeClient mexClient = new MetadataExchangeClient(mexAddress);  
  
// Retrieve the metadata for all endpoints using metadata exchange protocol (mex).  
MetadataSet metadataSet = mexClient.GetMetadata();  
  
//Convert the metadata into endpoints.  
WsdlImporter importer = new WsdlImporter(metadataSet);  
ServiceEndpointCollection endpoints = importer.ImportAllEndpoints();  
  
CalculatorClient client = null;  
ContractDescription contract = ContractDescription.GetContract(typeof(ICalculator));  
// Communicate with each endpoint that supports the ICalculator contract.  
foreach (ServiceEndpoint ep in endpoints)  
{  
    if (ep.Contract.Namespace.Equals(contract.Namespace) && ep.Contract.Name.Equals(contract.Name))  
    {  
        // Create a client using the endpoint address and binding.  
        client = new CalculatorClient(ep.Binding, new EndpointAddress(ep.Address.Uri));  
        Console.WriteLine("Communicate with endpoint: ");  
        Console.WriteLine("   AddressPath={0}", ep.Address.Uri.PathAndQuery);  
        Console.WriteLine("   Binding={0}", ep.Binding.Name);  
        // Call operations.  
        DoCalculations(client);  
  
        //Closing the client gracefully closes the connection and cleans up resources.  
        client.Close();  
    }  
}  
```  
  
 <span data-ttu-id="07bed-111">A janela do console de cliente exibe as operações enviadas para cada ponto de extremidade, exibindo o caminho de endereço e o nome da associação.</span><span class="sxs-lookup"><span data-stu-id="07bed-111">The client console window displays the operations sent to each of the endpoints, displaying the address path and binding name.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="07bed-112">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="07bed-112">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="07bed-113">Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="07bed-113">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="07bed-114">Para criar a edição do c#, C++ ou Visual Basic .NET da solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="07bed-114">To build the C#, C++, or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="07bed-115">Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="07bed-115">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="07bed-116">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="07bed-116">The samples may already be installed on your machine.</span></span> <span data-ttu-id="07bed-117">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="07bed-117">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="07bed-118">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="07bed-118">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="07bed-119">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="07bed-119">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\RetrieveMetadata`  
  
## <a name="see-also"></a><span data-ttu-id="07bed-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="07bed-120">See Also</span></span>
