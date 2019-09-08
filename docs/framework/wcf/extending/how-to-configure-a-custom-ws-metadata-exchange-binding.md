---
title: 'Como: configurar uma associação personalizada do WS-Metadata Exchange'
ms.date: 03/30/2017
helpviewer_keywords:
- WS-Metadata Exchange [WCF]
- WS-Metadata Exchange [WCF], configuring a custom binding
ms.assetid: cdba4d73-da64-4805-bc56-9822becfd1e4
ms.openlocfilehash: c3582ba3c434bb763889faebcc27407f67af7b1e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795660"
---
# <a name="how-to-configure-a-custom-ws-metadata-exchange-binding"></a><span data-ttu-id="60f86-102">Como: configurar uma associação personalizada do WS-Metadata Exchange</span><span class="sxs-lookup"><span data-stu-id="60f86-102">How to: Configure a Custom WS-Metadata Exchange Binding</span></span>
<span data-ttu-id="60f86-103">Este tópico explicará como configurar uma associação de troca personalizada de WS-Metadata.</span><span class="sxs-lookup"><span data-stu-id="60f86-103">This topic will explain how to configure a custom WS-Metadata exchange binding.</span></span> <span data-ttu-id="60f86-104">O Windows Communication Foundation (WCF) inclui quatro associações de metadados definidas pelo sistema, mas você pode publicar metadados usando qualquer associação desejada.</span><span class="sxs-lookup"><span data-stu-id="60f86-104">Windows Communication Foundation (WCF) includes four system-defined metadata bindings, but you can publish metadata using any binding you want.</span></span> <span data-ttu-id="60f86-105">Este tópico mostrará como publicar metadados usando o `wsHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="60f86-105">This topic will show you how to publish metadata using the `wsHttpBinding`.</span></span> <span data-ttu-id="60f86-106">Essa associação oferece a opção de expor metadados de forma segura.</span><span class="sxs-lookup"><span data-stu-id="60f86-106">This binding gives you the option of exposing metadata in a secure way.</span></span> <span data-ttu-id="60f86-107">O código neste artigo se baseia na [introdução](../samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="60f86-107">The code in this article is based on the [Getting Started](../samples/getting-started-sample.md).</span></span>  
  
### <a name="using-a-configuration-file"></a><span data-ttu-id="60f86-108">Usando um arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="60f86-108">Using a configuration file</span></span>  
  
1. <span data-ttu-id="60f86-109">No arquivo de configuração do serviço, adicione um comportamento de serviço que contenha a `serviceMetadata` marca:</span><span class="sxs-lookup"><span data-stu-id="60f86-109">In the service's configuration file, add a service behavior that contains the `serviceMetadata` tag:</span></span>  
  
    ```xml  
    <behaviors>  
       <serviceBehaviors>  
         <behavior name="CalculatorServiceBehavior">  
           <serviceMetadata httpGetEnabled="True"/>  
         </behavior>  
       </serviceBehaviors>  
    </behaviors>  
    ```  
  
2. <span data-ttu-id="60f86-110">Adicione um `behaviorConfiguration` atributo à marca de serviço que faz referência a esse novo comportamento:</span><span class="sxs-lookup"><span data-stu-id="60f86-110">Add a `behaviorConfiguration` attribute to the service tag that references this new behavior:</span></span>  
  
    ```xml  
    <service        name="Microsoft.ServiceModel.Samples.CalculatorService"  
    behaviorConfiguration="CalculatorServiceBehavior">   
    ```  
  
3. <span data-ttu-id="60f86-111">Adicione um ponto de extremidade de metadados especificando mex como `wsHttpBinding` o endereço, como a <xref:System.ServiceModel.Description.IMetadataExchange> associação e como o contrato:</span><span class="sxs-lookup"><span data-stu-id="60f86-111">Add a metadata endpoint specifying mex as the address, `wsHttpBinding` as the binding, and <xref:System.ServiceModel.Description.IMetadataExchange> as the contract:</span></span>  
  
    ```xml  
    <endpoint address="mex"  
              binding="wsHttpBinding"  
              contract="IMetadataExchange" />  
    ```  
  
4. <span data-ttu-id="60f86-112">Para verificar se o ponto de extremidade de troca de metadados está funcionando corretamente, adicione uma marca de ponto de extremidade no arquivo de configuração do cliente:</span><span class="sxs-lookup"><span data-stu-id="60f86-112">To verify the metadata exchange endpoint is working correctly add an endpoint tag in the client configuration file:</span></span>  
  
    ```xml  
    <endpoint name="MyMexEndpoint"               address="http://localhost:8000/servicemodelsamples/service/mex"  
              binding="wsHttpBinding"  
              contract="IMetadataExchange"/>  
    ```  
  
5. <span data-ttu-id="60f86-113">No método Main () do cliente, crie uma <xref:System.ServiceModel.Description.MetadataExchangeClient> nova instância, defina sua <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> Propriedade como `true`, chame <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> e, em seguida, itere pela coleção de metadados retornada:</span><span class="sxs-lookup"><span data-stu-id="60f86-113">In the client's Main() method, create a new <xref:System.ServiceModel.Description.MetadataExchangeClient> instance, set its <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> property to `true`, call <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> and then iterate through the collection of metadata returned:</span></span>  
  
    ```  
    string mexAddress = "http://localhost:8000/servicemodelsamples/service/mex";  
  
    MetadataExchangeClient mexClient = new MetadataExchangeClient("MyMexEndpoint");  
    mexClient.ResolveMetadataReferences = true;  
    MetadataSet mdSet = mexClient.GetMetadata(new EndpointAddress(mexAddress));  
    foreach (MetadataSection section in mdSet.MetadataSections)  
    Console.WriteLine("Metadata section: " + section.Dialect.ToString());  
    ```  
  
### <a name="configuring-by-code"></a><span data-ttu-id="60f86-114">Configurando por código</span><span class="sxs-lookup"><span data-stu-id="60f86-114">Configuring by code</span></span>  
  
1. <span data-ttu-id="60f86-115">Criar uma <xref:System.ServiceModel.WSHttpBinding> instância de associação:</span><span class="sxs-lookup"><span data-stu-id="60f86-115">Create a <xref:System.ServiceModel.WSHttpBinding> binding instance:</span></span>  
  
    ```  
    WSHttpBinding binding = new WSHttpBinding();  
    ```  
  
2. <span data-ttu-id="60f86-116">Criar uma <xref:System.ServiceModel.ServiceHost> instância:</span><span class="sxs-lookup"><span data-stu-id="60f86-116">Create a <xref:System.ServiceModel.ServiceHost> instance:</span></span>  
  
    ```  
    ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress);  
    ```  
  
3. <span data-ttu-id="60f86-117">Adicione um ponto de extremidade de serviço <xref:System.ServiceModel.Description.ServiceMetadataBehavior> e adicione uma instância:</span><span class="sxs-lookup"><span data-stu-id="60f86-117">Add a service endpoint and add a <xref:System.ServiceModel.Description.ServiceMetadataBehavior> instance:</span></span>  
  
    ```  
    serviceHost.AddServiceEndpoint(typeof(ICalculator), binding, baseAddress);  
    ServiceMetadataBehavior smb = new ServiceMetadataBehavior();  
    smb.HttpGetEnabled = true;  
    serviceHost.Description.Behaviors.Add(smb);  
    ```  
  
4. <span data-ttu-id="60f86-118">Adicione um ponto de extremidade de troca de <xref:System.ServiceModel.WSHttpBinding> metadados, especificando o criado anteriormente:</span><span class="sxs-lookup"><span data-stu-id="60f86-118">Add a metadata exchange endpoint, specifying the <xref:System.ServiceModel.WSHttpBinding> created earlier:</span></span>  
  
    ```  
    serviceHost.AddServiceEndpoint(typeof(IMetadataExchange), binding, mexAddress);  
    ```  
  
5. <span data-ttu-id="60f86-119">Para verificar se o ponto de extremidade de troca de metadados está funcionando corretamente, adicione uma marca de ponto de extremidade no arquivo de configuração do cliente:</span><span class="sxs-lookup"><span data-stu-id="60f86-119">To verify that the metadata exchange endpoint is working correctly, add an endpoint tag in the client configuration file:</span></span>  
  
    ```xml  
    <endpoint name="MyMexEndpoint"               address="http://localhost:8000/servicemodelsamples/service/mex"  
              binding="wsHttpBinding"  
              contract="IMetadataExchange"/>  
    ```  
  
6. <span data-ttu-id="60f86-120">No método Main () do cliente, crie uma <xref:System.ServiceModel.Description.MetadataExchangeClient> nova instância, defina a <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> Propriedade como `true`, chame <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> e, em seguida, itere pela coleção de metadados retornada:</span><span class="sxs-lookup"><span data-stu-id="60f86-120">In the client's Main() method, create a new <xref:System.ServiceModel.Description.MetadataExchangeClient> instance, set the <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> property to `true`, call <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> and then iterate through the collection of metadata returned:</span></span>  
  
    ```  
    string mexAddress = "http://localhost:8000/servicemodelsamples/service/mex";  
  
    MetadataExchangeClient mexClient = new MetadataExchangeClient("MyMexEndpoint");  
    mexClient.ResolveMetadataReferences = true;  
    MetadataSet mdSet = mexClient.GetMetadata(new EndpointAddress(mexAddress));  
    foreach (MetadataSection section in mdSet.MetadataSections)  
    Console.WriteLine("Metadata section: " + section.Dialect.ToString());  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="60f86-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="60f86-121">See also</span></span>

- [<span data-ttu-id="60f86-122">Comportamento de publicação de metadados</span><span class="sxs-lookup"><span data-stu-id="60f86-122">Metadata Publishing Behavior</span></span>](../samples/metadata-publishing-behavior.md)
- [<span data-ttu-id="60f86-123">Recuperar metadados</span><span class="sxs-lookup"><span data-stu-id="60f86-123">Retrieve Metadata</span></span>](../samples/retrieve-metadata.md)
- [<span data-ttu-id="60f86-124">Metadados</span><span class="sxs-lookup"><span data-stu-id="60f86-124">Metadata</span></span>](../feature-details/metadata.md)
- [<span data-ttu-id="60f86-125">Publicando metadados</span><span class="sxs-lookup"><span data-stu-id="60f86-125">Publishing Metadata</span></span>](../feature-details/publishing-metadata.md)
- [<span data-ttu-id="60f86-126">Publicando pontos de extremidade de metadados</span><span class="sxs-lookup"><span data-stu-id="60f86-126">Publishing Metadata Endpoints</span></span>](../publishing-metadata-endpoints.md)
