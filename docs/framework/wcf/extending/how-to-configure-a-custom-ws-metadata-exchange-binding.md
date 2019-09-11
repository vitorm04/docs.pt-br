---
title: 'Como: configurar uma associação personalizada do WS-Metadata Exchange'
ms.date: 03/30/2017
helpviewer_keywords:
- WS-Metadata Exchange [WCF]
- WS-Metadata Exchange [WCF], configuring a custom binding
ms.assetid: cdba4d73-da64-4805-bc56-9822becfd1e4
ms.openlocfilehash: b4a4005a23c8c74edecb00475669e019b50a17af
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70851228"
---
# <a name="how-to-configure-a-custom-ws-metadata-exchange-binding"></a><span data-ttu-id="a9aca-102">Como: configurar uma associação personalizada do WS-Metadata Exchange</span><span class="sxs-lookup"><span data-stu-id="a9aca-102">How to: Configure a Custom WS-Metadata Exchange Binding</span></span>
<span data-ttu-id="a9aca-103">Este tópico explicará como configurar uma associação de troca personalizada de WS-Metadata.</span><span class="sxs-lookup"><span data-stu-id="a9aca-103">This topic will explain how to configure a custom WS-Metadata exchange binding.</span></span> <span data-ttu-id="a9aca-104">O Windows Communication Foundation (WCF) inclui quatro associações de metadados definidas pelo sistema, mas você pode publicar metadados usando qualquer associação desejada.</span><span class="sxs-lookup"><span data-stu-id="a9aca-104">Windows Communication Foundation (WCF) includes four system-defined metadata bindings, but you can publish metadata using any binding you want.</span></span> <span data-ttu-id="a9aca-105">Este tópico mostrará como publicar metadados usando o `wsHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="a9aca-105">This topic will show you how to publish metadata using the `wsHttpBinding`.</span></span> <span data-ttu-id="a9aca-106">Essa associação oferece a opção de expor metadados de forma segura.</span><span class="sxs-lookup"><span data-stu-id="a9aca-106">This binding gives you the option of exposing metadata in a secure way.</span></span> <span data-ttu-id="a9aca-107">O código neste artigo se baseia na [introdução](../samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="a9aca-107">The code in this article is based on the [Getting Started](../samples/getting-started-sample.md).</span></span>  
  
### <a name="using-a-configuration-file"></a><span data-ttu-id="a9aca-108">Usando um arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="a9aca-108">Using a configuration file</span></span>  
  
1. <span data-ttu-id="a9aca-109">No arquivo de configuração do serviço, adicione um comportamento de serviço que contenha a `serviceMetadata` marca:</span><span class="sxs-lookup"><span data-stu-id="a9aca-109">In the service's configuration file, add a service behavior that contains the `serviceMetadata` tag:</span></span>  
  
    ```xml  
    <behaviors>  
       <serviceBehaviors>  
         <behavior name="CalculatorServiceBehavior">  
           <serviceMetadata httpGetEnabled="True"/>  
         </behavior>  
       </serviceBehaviors>  
    </behaviors>  
    ```  
  
2. <span data-ttu-id="a9aca-110">Adicione um `behaviorConfiguration` atributo à marca de serviço que faz referência a esse novo comportamento:</span><span class="sxs-lookup"><span data-stu-id="a9aca-110">Add a `behaviorConfiguration` attribute to the service tag that references this new behavior:</span></span>  
  
    ```xml  
    <service        name="Microsoft.ServiceModel.Samples.CalculatorService"  
    behaviorConfiguration="CalculatorServiceBehavior">   
    ```  
  
3. <span data-ttu-id="a9aca-111">Adicione um ponto de extremidade de metadados especificando mex como `wsHttpBinding` o endereço, como a <xref:System.ServiceModel.Description.IMetadataExchange> associação e como o contrato:</span><span class="sxs-lookup"><span data-stu-id="a9aca-111">Add a metadata endpoint specifying mex as the address, `wsHttpBinding` as the binding, and <xref:System.ServiceModel.Description.IMetadataExchange> as the contract:</span></span>  
  
    ```xml  
    <endpoint address="mex"  
              binding="wsHttpBinding"  
              contract="IMetadataExchange" />  
    ```  
  
4. <span data-ttu-id="a9aca-112">Para verificar se o ponto de extremidade de troca de metadados está funcionando corretamente, adicione uma marca de ponto de extremidade no arquivo de configuração do cliente:</span><span class="sxs-lookup"><span data-stu-id="a9aca-112">To verify the metadata exchange endpoint is working correctly add an endpoint tag in the client configuration file:</span></span>  
  
    ```xml  
    <endpoint name="MyMexEndpoint"               address="http://localhost:8000/servicemodelsamples/service/mex"  
              binding="wsHttpBinding"  
              contract="IMetadataExchange"/>  
    ```  
  
5. <span data-ttu-id="a9aca-113">No método Main () do cliente, crie uma <xref:System.ServiceModel.Description.MetadataExchangeClient> nova instância, defina sua <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> Propriedade como `true`, chame <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> e, em seguida, itere pela coleção de metadados retornada:</span><span class="sxs-lookup"><span data-stu-id="a9aca-113">In the client's Main() method, create a new <xref:System.ServiceModel.Description.MetadataExchangeClient> instance, set its <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> property to `true`, call <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> and then iterate through the collection of metadata returned:</span></span>  
  
    ```csharp
    string mexAddress = "http://localhost:8000/servicemodelsamples/service/mex";  
  
    MetadataExchangeClient mexClient = new MetadataExchangeClient("MyMexEndpoint");  
    mexClient.ResolveMetadataReferences = true;  
    MetadataSet mdSet = mexClient.GetMetadata(new EndpointAddress(mexAddress));  
    foreach (MetadataSection section in mdSet.MetadataSections)  
    Console.WriteLine("Metadata section: " + section.Dialect.ToString());  
    ```  
  
### <a name="configuring-by-code"></a><span data-ttu-id="a9aca-114">Configurando por código</span><span class="sxs-lookup"><span data-stu-id="a9aca-114">Configuring by code</span></span>  
  
1. <span data-ttu-id="a9aca-115">Criar uma <xref:System.ServiceModel.WSHttpBinding> instância de associação:</span><span class="sxs-lookup"><span data-stu-id="a9aca-115">Create a <xref:System.ServiceModel.WSHttpBinding> binding instance:</span></span>  
  
    ```csharp  
    WSHttpBinding binding = new WSHttpBinding();  
    ```  
  
2. <span data-ttu-id="a9aca-116">Criar uma <xref:System.ServiceModel.ServiceHost> instância:</span><span class="sxs-lookup"><span data-stu-id="a9aca-116">Create a <xref:System.ServiceModel.ServiceHost> instance:</span></span>  
  
    ```csharp  
    ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress);  
    ```  
  
3. <span data-ttu-id="a9aca-117">Adicione um ponto de extremidade de serviço <xref:System.ServiceModel.Description.ServiceMetadataBehavior> e adicione uma instância:</span><span class="sxs-lookup"><span data-stu-id="a9aca-117">Add a service endpoint and add a <xref:System.ServiceModel.Description.ServiceMetadataBehavior> instance:</span></span>  
  
    ```csharp  
    serviceHost.AddServiceEndpoint(typeof(ICalculator), binding, baseAddress);  
    ServiceMetadataBehavior smb = new ServiceMetadataBehavior();  
    smb.HttpGetEnabled = true;  
    serviceHost.Description.Behaviors.Add(smb);  
    ```  
  
4. <span data-ttu-id="a9aca-118">Adicione um ponto de extremidade de troca de <xref:System.ServiceModel.WSHttpBinding> metadados, especificando o criado anteriormente:</span><span class="sxs-lookup"><span data-stu-id="a9aca-118">Add a metadata exchange endpoint, specifying the <xref:System.ServiceModel.WSHttpBinding> created earlier:</span></span>  
  
    ```csharp  
    serviceHost.AddServiceEndpoint(typeof(IMetadataExchange), binding, mexAddress);  
    ```  
  
5. <span data-ttu-id="a9aca-119">Para verificar se o ponto de extremidade de troca de metadados está funcionando corretamente, adicione uma marca de ponto de extremidade no arquivo de configuração do cliente:</span><span class="sxs-lookup"><span data-stu-id="a9aca-119">To verify that the metadata exchange endpoint is working correctly, add an endpoint tag in the client configuration file:</span></span>  
  
    ```xml  
    <endpoint name="MyMexEndpoint"               address="http://localhost:8000/servicemodelsamples/service/mex"  
              binding="wsHttpBinding"  
              contract="IMetadataExchange"/>  
    ```  
  
6. <span data-ttu-id="a9aca-120">No método Main () do cliente, crie uma <xref:System.ServiceModel.Description.MetadataExchangeClient> nova instância, defina a <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> Propriedade como `true`, chame <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> e, em seguida, itere pela coleção de metadados retornada:</span><span class="sxs-lookup"><span data-stu-id="a9aca-120">In the client's Main() method, create a new <xref:System.ServiceModel.Description.MetadataExchangeClient> instance, set the <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> property to `true`, call <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> and then iterate through the collection of metadata returned:</span></span>  
  
    ```csharp  
    string mexAddress = "http://localhost:8000/servicemodelsamples/service/mex";  
  
    MetadataExchangeClient mexClient = new MetadataExchangeClient("MyMexEndpoint");  
    mexClient.ResolveMetadataReferences = true;  
    MetadataSet mdSet = mexClient.GetMetadata(new EndpointAddress(mexAddress));  
    foreach (MetadataSection section in mdSet.MetadataSections)  
    Console.WriteLine("Metadata section: " + section.Dialect.ToString());  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="a9aca-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a9aca-121">See also</span></span>

- [<span data-ttu-id="a9aca-122">Comportamento de publicação de metadados</span><span class="sxs-lookup"><span data-stu-id="a9aca-122">Metadata Publishing Behavior</span></span>](../samples/metadata-publishing-behavior.md)
- [<span data-ttu-id="a9aca-123">Recuperar metadados</span><span class="sxs-lookup"><span data-stu-id="a9aca-123">Retrieve Metadata</span></span>](../samples/retrieve-metadata.md)
- [<span data-ttu-id="a9aca-124">Metadados</span><span class="sxs-lookup"><span data-stu-id="a9aca-124">Metadata</span></span>](../feature-details/metadata.md)
- [<span data-ttu-id="a9aca-125">Publicando metadados</span><span class="sxs-lookup"><span data-stu-id="a9aca-125">Publishing Metadata</span></span>](../feature-details/publishing-metadata.md)
- [<span data-ttu-id="a9aca-126">Publicando pontos de extremidade de metadados</span><span class="sxs-lookup"><span data-stu-id="a9aca-126">Publishing Metadata Endpoints</span></span>](../publishing-metadata-endpoints.md)
