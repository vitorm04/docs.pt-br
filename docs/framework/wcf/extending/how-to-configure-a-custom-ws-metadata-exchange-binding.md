---
title: Como configurar uma associação de intercâmbio de WS-Metadata
ms.date: 03/30/2017
helpviewer_keywords:
- WS-Metadata Exchange [WCF]
- WS-Metadata Exchange [WCF], configuring a custom binding
ms.assetid: cdba4d73-da64-4805-bc56-9822becfd1e4
ms.openlocfilehash: 4e0c583eeef4bf068c08b273c833506ce80cbc3a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185606"
---
# <a name="how-to-configure-a-custom-ws-metadata-exchange-binding"></a><span data-ttu-id="2789e-102">Como configurar uma associação de intercâmbio de WS-Metadata</span><span class="sxs-lookup"><span data-stu-id="2789e-102">How to: Configure a Custom WS-Metadata Exchange Binding</span></span>
<span data-ttu-id="2789e-103">Este tópico explicará como configurar uma vinculação personalizada de troca WS-Metadata.</span><span class="sxs-lookup"><span data-stu-id="2789e-103">This topic will explain how to configure a custom WS-Metadata exchange binding.</span></span> <span data-ttu-id="2789e-104">O Windows Communication Foundation (WCF) inclui quatro vinculações de metadados definidas pelo sistema, mas você pode publicar metadados usando qualquer vinculação desejada.</span><span class="sxs-lookup"><span data-stu-id="2789e-104">Windows Communication Foundation (WCF) includes four system-defined metadata bindings, but you can publish metadata using any binding you want.</span></span> <span data-ttu-id="2789e-105">Este tópico mostrará como publicar metadados usando o `wsHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="2789e-105">This topic will show you how to publish metadata using the `wsHttpBinding`.</span></span> <span data-ttu-id="2789e-106">Essa vinculação lhe dá a opção de expor metadados de forma segura.</span><span class="sxs-lookup"><span data-stu-id="2789e-106">This binding gives you the option of exposing metadata in a secure way.</span></span> <span data-ttu-id="2789e-107">O código deste artigo é baseado no [Getting Started](../samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="2789e-107">The code in this article is based on the [Getting Started](../samples/getting-started-sample.md).</span></span>  
  
### <a name="using-a-configuration-file"></a><span data-ttu-id="2789e-108">Usando um arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="2789e-108">Using a configuration file</span></span>  
  
1. <span data-ttu-id="2789e-109">No arquivo de configuração do serviço, adicione `serviceMetadata` um comportamento de serviço que contenha a tag:</span><span class="sxs-lookup"><span data-stu-id="2789e-109">In the service's configuration file, add a service behavior that contains the `serviceMetadata` tag:</span></span>  
  
    ```xml  
    <behaviors>  
       <serviceBehaviors>  
         <behavior name="CalculatorServiceBehavior">  
           <serviceMetadata httpGetEnabled="True"/>  
         </behavior>  
       </serviceBehaviors>  
    </behaviors>  
    ```  
  
2. <span data-ttu-id="2789e-110">Adicione `behaviorConfiguration` um atributo à tag de serviço que faz referência a esse novo comportamento:</span><span class="sxs-lookup"><span data-stu-id="2789e-110">Add a `behaviorConfiguration` attribute to the service tag that references this new behavior:</span></span>  
  
    ```xml  
    <service        name="Microsoft.ServiceModel.Samples.CalculatorService"  
    behaviorConfiguration="CalculatorServiceBehavior">
    ```  
  
3. <span data-ttu-id="2789e-111">Adicione um ponto final de metadados especificando mex como endereço, `wsHttpBinding` como a vinculação e <xref:System.ServiceModel.Description.IMetadataExchange> como contrato:</span><span class="sxs-lookup"><span data-stu-id="2789e-111">Add a metadata endpoint specifying mex as the address, `wsHttpBinding` as the binding, and <xref:System.ServiceModel.Description.IMetadataExchange> as the contract:</span></span>  
  
    ```xml  
    <endpoint address="mex"  
              binding="wsHttpBinding"  
              contract="IMetadataExchange" />  
    ```  
  
4. <span data-ttu-id="2789e-112">Para verificar se o ponto final da troca de metadados está funcionando corretamente, adicione uma tag de ponto final no arquivo de configuração do cliente:</span><span class="sxs-lookup"><span data-stu-id="2789e-112">To verify the metadata exchange endpoint is working correctly add an endpoint tag in the client configuration file:</span></span>  
  
    ```xml  
    <endpoint name="MyMexEndpoint"               address="http://localhost:8000/servicemodelsamples/service/mex"  
              binding="wsHttpBinding"  
              contract="IMetadataExchange"/>  
    ```  
  
5. <span data-ttu-id="2789e-113">No método Principal() do cliente, <xref:System.ServiceModel.Description.MetadataExchangeClient> crie uma <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> nova `true`instância, <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> defina sua propriedade para, ligue e, em seguida, iteraatravés da coleta de metadados devolvidos:</span><span class="sxs-lookup"><span data-stu-id="2789e-113">In the client's Main() method, create a new <xref:System.ServiceModel.Description.MetadataExchangeClient> instance, set its <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> property to `true`, call <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> and then iterate through the collection of metadata returned:</span></span>  
  
    ```csharp
    string mexAddress = "http://localhost:8000/servicemodelsamples/service/mex";  
  
    MetadataExchangeClient mexClient = new MetadataExchangeClient("MyMexEndpoint");  
    mexClient.ResolveMetadataReferences = true;  
    MetadataSet mdSet = mexClient.GetMetadata(new EndpointAddress(mexAddress));  
    foreach (MetadataSection section in mdSet.MetadataSections)  
    Console.WriteLine("Metadata section: " + section.Dialect.ToString());  
    ```  
  
### <a name="configuring-by-code"></a><span data-ttu-id="2789e-114">Configuração por código</span><span class="sxs-lookup"><span data-stu-id="2789e-114">Configuring by code</span></span>  
  
1. <span data-ttu-id="2789e-115">Criar <xref:System.ServiceModel.WSHttpBinding> uma instância vinculante:</span><span class="sxs-lookup"><span data-stu-id="2789e-115">Create a <xref:System.ServiceModel.WSHttpBinding> binding instance:</span></span>  
  
    ```csharp  
    WSHttpBinding binding = new WSHttpBinding();  
    ```  
  
2. <span data-ttu-id="2789e-116">Criar <xref:System.ServiceModel.ServiceHost> uma instância:</span><span class="sxs-lookup"><span data-stu-id="2789e-116">Create a <xref:System.ServiceModel.ServiceHost> instance:</span></span>  
  
    ```csharp  
    ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress);  
    ```  
  
3. <span data-ttu-id="2789e-117">Adicione um ponto final <xref:System.ServiceModel.Description.ServiceMetadataBehavior> de serviço e adicione uma instância:</span><span class="sxs-lookup"><span data-stu-id="2789e-117">Add a service endpoint and add a <xref:System.ServiceModel.Description.ServiceMetadataBehavior> instance:</span></span>  
  
    ```csharp  
    serviceHost.AddServiceEndpoint(typeof(ICalculator), binding, baseAddress);  
    ServiceMetadataBehavior smb = new ServiceMetadataBehavior();  
    smb.HttpGetEnabled = true;  
    serviceHost.Description.Behaviors.Add(smb);  
    ```  
  
4. <span data-ttu-id="2789e-118">Adicionar um ponto final de troca <xref:System.ServiceModel.WSHttpBinding> de metadados, especificando o criado anteriormente:</span><span class="sxs-lookup"><span data-stu-id="2789e-118">Add a metadata exchange endpoint, specifying the <xref:System.ServiceModel.WSHttpBinding> created earlier:</span></span>  
  
    ```csharp  
    serviceHost.AddServiceEndpoint(typeof(IMetadataExchange), binding, mexAddress);  
    ```  
  
5. <span data-ttu-id="2789e-119">Para verificar se o ponto final da troca de metadados está funcionando corretamente, adicione uma tag endpoint no arquivo de configuração do cliente:</span><span class="sxs-lookup"><span data-stu-id="2789e-119">To verify that the metadata exchange endpoint is working correctly, add an endpoint tag in the client configuration file:</span></span>  
  
    ```xml  
    <endpoint name="MyMexEndpoint"               address="http://localhost:8000/servicemodelsamples/service/mex"  
              binding="wsHttpBinding"  
              contract="IMetadataExchange"/>  
    ```  
  
6. <span data-ttu-id="2789e-120">No método Principal() do cliente, <xref:System.ServiceModel.Description.MetadataExchangeClient> crie uma <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> nova `true`instância, <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> defina a propriedade para, ligue e, em seguida, iteraatravés da coleta de metadados devolvidos:</span><span class="sxs-lookup"><span data-stu-id="2789e-120">In the client's Main() method, create a new <xref:System.ServiceModel.Description.MetadataExchangeClient> instance, set the <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> property to `true`, call <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> and then iterate through the collection of metadata returned:</span></span>  
  
    ```csharp  
    string mexAddress = "http://localhost:8000/servicemodelsamples/service/mex";  
  
    MetadataExchangeClient mexClient = new MetadataExchangeClient("MyMexEndpoint");  
    mexClient.ResolveMetadataReferences = true;  
    MetadataSet mdSet = mexClient.GetMetadata(new EndpointAddress(mexAddress));  
    foreach (MetadataSection section in mdSet.MetadataSections)  
    Console.WriteLine("Metadata section: " + section.Dialect.ToString());  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="2789e-121">Confira também</span><span class="sxs-lookup"><span data-stu-id="2789e-121">See also</span></span>

- [<span data-ttu-id="2789e-122">Comportamento de publicação de metadados</span><span class="sxs-lookup"><span data-stu-id="2789e-122">Metadata Publishing Behavior</span></span>](../samples/metadata-publishing-behavior.md)
- [<span data-ttu-id="2789e-123">Recuperar metadados</span><span class="sxs-lookup"><span data-stu-id="2789e-123">Retrieve Metadata</span></span>](../samples/retrieve-metadata.md)
- [<span data-ttu-id="2789e-124">Metadados</span><span class="sxs-lookup"><span data-stu-id="2789e-124">Metadata</span></span>](../feature-details/metadata.md)
- [<span data-ttu-id="2789e-125">Publicando metadados</span><span class="sxs-lookup"><span data-stu-id="2789e-125">Publishing Metadata</span></span>](../feature-details/publishing-metadata.md)
- [<span data-ttu-id="2789e-126">Publicando pontos de extremidade de metadados</span><span class="sxs-lookup"><span data-stu-id="2789e-126">Publishing Metadata Endpoints</span></span>](../publishing-metadata-endpoints.md)
