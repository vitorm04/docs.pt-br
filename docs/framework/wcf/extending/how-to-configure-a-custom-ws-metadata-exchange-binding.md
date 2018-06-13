---
title: Como configurar uma associação de intercâmbio de WS-Metadata
ms.date: 03/30/2017
helpviewer_keywords:
- WS-Metadata Exchange [WCF]
- WS-Metadata Exchange [WCF], configuring a custom binding
ms.assetid: cdba4d73-da64-4805-bc56-9822becfd1e4
ms.openlocfilehash: 0596e91204a2a9dbaed2fdbe85387ec3785fd3db
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33488693"
---
# <a name="how-to-configure-a-custom-ws-metadata-exchange-binding"></a><span data-ttu-id="3ad50-102">Como configurar uma associação de intercâmbio de WS-Metadata</span><span class="sxs-lookup"><span data-stu-id="3ad50-102">How to: Configure a Custom WS-Metadata Exchange Binding</span></span>
<span data-ttu-id="3ad50-103">Este tópico explicará como configurar um personalizado WS-Metadata exchange associação.</span><span class="sxs-lookup"><span data-stu-id="3ad50-103">This topic will explain how to configure a custom WS-Metadata exchange binding.</span></span> <span data-ttu-id="3ad50-104">Windows Communication Foundation (WCF) inclui quatro associações de metadados definidos pelo sistema, mas você pode publicar metadados usando a associação que você deseja.</span><span class="sxs-lookup"><span data-stu-id="3ad50-104">Windows Communication Foundation (WCF) includes four system-defined metadata bindings, but you can publish metadata using any binding you want.</span></span> <span data-ttu-id="3ad50-105">Neste tópico mostram como publicar metadados usando o `wsHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="3ad50-105">This topic will show you how to publish metadata using the `wsHttpBinding`.</span></span> <span data-ttu-id="3ad50-106">Essa associação oferece a opção de exposição de metadados de forma segura.</span><span class="sxs-lookup"><span data-stu-id="3ad50-106">This binding gives you the option of exposing metadata in a secure way.</span></span> <span data-ttu-id="3ad50-107">O código neste artigo se baseia o [Introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="3ad50-107">The code in this article is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span>  
  
### <a name="using-a-configuration-file"></a><span data-ttu-id="3ad50-108">Usando um arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="3ad50-108">Using a configuration file</span></span>  
  
1.  <span data-ttu-id="3ad50-109">No arquivo de configuração do serviço, adicionar um comportamento de serviço que contém o `serviceMetadata` marca:</span><span class="sxs-lookup"><span data-stu-id="3ad50-109">In the service's configuration file, add a service behavior that contains the `serviceMetadata` tag:</span></span>  
  
    ```xml  
    <behaviors>  
       <serviceBehaviors>  
         <behavior name="CalculatorServiceBehavior">  
           <serviceMetadata httpGetEnabled="True"/>  
         </behavior>  
       </serviceBehaviors>  
    </behaviors>  
    ```  
  
2.  <span data-ttu-id="3ad50-110">Adicionar um `behaviorConfiguration` atributo à marca do serviço que faz referência a esse novo comportamento:</span><span class="sxs-lookup"><span data-stu-id="3ad50-110">Add a `behaviorConfiguration` attribute to the service tag that references this new behavior:</span></span>  
  
    ```xml  
    <service        name="Microsoft.ServiceModel.Samples.CalculatorService"  
    behaviorConfiguration="CalculatorServiceBehavior">   
    ```  
  
3.  <span data-ttu-id="3ad50-111">Adicionar um ponto de extremidade de metadados especificando mex como o endereço `wsHttpBinding` como a associação e <xref:System.ServiceModel.Description.IMetadataExchange> do contrato:</span><span class="sxs-lookup"><span data-stu-id="3ad50-111">Add a metadata endpoint specifying mex as the address, `wsHttpBinding` as the binding, and <xref:System.ServiceModel.Description.IMetadataExchange> as the contract:</span></span>  
  
    ```xml  
    <endpoint address="mex"  
              binding="wsHttpBinding"  
              contract="IMetadataExchange" />  
    ```  
  
4.  <span data-ttu-id="3ad50-112">Para verificar se o ponto de extremidade de troca de metadados é trabalho corretamente adicionar uma marca de ponto de extremidade no arquivo de configuração do cliente:</span><span class="sxs-lookup"><span data-stu-id="3ad50-112">To verify the metadata exchange endpoint is working correctly add an endpoint tag in the client configuration file:</span></span>  
  
    ```xml  
    <endpoint name="MyMexEndpoint"               address="http://localhost:8000/servicemodelsamples/service/mex"  
              binding="wsHttpBinding"  
              contract="IMetadataExchange"/>  
    ```  
  
5.  <span data-ttu-id="3ad50-113">No método de Main () do cliente, crie um novo <xref:System.ServiceModel.Description.MetadataExchangeClient> instância, defina seu <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> propriedade `true`, chame <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> e, em seguida, percorrer a coleção de metadados retornados:</span><span class="sxs-lookup"><span data-stu-id="3ad50-113">In the client's Main() method, create a new <xref:System.ServiceModel.Description.MetadataExchangeClient> instance, set its <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> property to `true`, call <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> and then iterate through the collection of metadata returned:</span></span>  
  
    ```  
    string mexAddress = "http://localhost:8000/servicemodelsamples/service/mex";  
  
    MetadataExchangeClient mexClient = new MetadataExchangeClient("MyMexEndpoint");  
    mexClient.ResolveMetadataReferences = true;  
    MetadataSet mdSet = mexClient.GetMetadata(new EndpointAddress(mexAddress));  
    foreach (MetadataSection section in mdSet.MetadataSections)  
    Console.WriteLine("Metadata section: " + section.Dialect.ToString());  
    ```  
  
### <a name="configuring-by-code"></a><span data-ttu-id="3ad50-114">Configurar o código</span><span class="sxs-lookup"><span data-stu-id="3ad50-114">Configuring by code</span></span>  
  
1.  <span data-ttu-id="3ad50-115">Criar um <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> instância de associação:</span><span class="sxs-lookup"><span data-stu-id="3ad50-115">Create a <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> binding instance:</span></span>  
  
    ```  
    WSHttpBinding binding = new WSHttpBinding();  
    ```  
  
2.  <span data-ttu-id="3ad50-116">Criar um <xref:System.ServiceModel.ServiceHost> instância:</span><span class="sxs-lookup"><span data-stu-id="3ad50-116">Create a <xref:System.ServiceModel.ServiceHost> instance:</span></span>  
  
    ```  
    ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress);  
    ```  
  
3.  <span data-ttu-id="3ad50-117">Adicione um ponto de extremidade de serviço e adicione um <xref:System.ServiceModel.Description.ServiceMetadataBehavior> instância:</span><span class="sxs-lookup"><span data-stu-id="3ad50-117">Add a service endpoint and add a <xref:System.ServiceModel.Description.ServiceMetadataBehavior> instance:</span></span>  
  
    ```  
    serviceHost.AddServiceEndpoint(typeof(ICalculator), binding, baseAddress);  
    ServiceMetadataBehavior smb = new ServiceMetadataBehavior();  
    smb.HttpGetEnabled = true;  
    serviceHost.Description.Behaviors.Add(smb);  
    ```  
  
4.  <span data-ttu-id="3ad50-118">Adicionar um ponto de extremidade de troca de metadados, especificando o <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> criado anteriormente:</span><span class="sxs-lookup"><span data-stu-id="3ad50-118">Add a metadata exchange endpoint, specifying the <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> created earlier:</span></span>  
  
    ```  
    serviceHost.AddServiceEndpoint(typeof(IMetadataExchange), binding, mexAddress);  
    ```  
  
5.  <span data-ttu-id="3ad50-119">Para verificar se o ponto de extremidade de troca de metadados está funcionando corretamente, adicione uma marca de ponto de extremidade no arquivo de configuração do cliente:</span><span class="sxs-lookup"><span data-stu-id="3ad50-119">To verify that the metadata exchange endpoint is working correctly, add an endpoint tag in the client configuration file:</span></span>  
  
    ```xml  
    <endpoint name="MyMexEndpoint"               address="http://localhost:8000/servicemodelsamples/service/mex"  
              binding="wsHttpBinding"  
              contract="IMetadataExchange"/>  
    ```  
  
6.  <span data-ttu-id="3ad50-120">No método de Main () do cliente, crie um novo <xref:System.ServiceModel.Description.MetadataExchangeClient> instância, defina o <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> propriedade `true`, chame <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> e, em seguida, percorrer a coleção de metadados retornados:</span><span class="sxs-lookup"><span data-stu-id="3ad50-120">In the client's Main() method, create a new <xref:System.ServiceModel.Description.MetadataExchangeClient> instance, set the <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> property to `true`, call <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> and then iterate through the collection of metadata returned:</span></span>  
  
    ```  
    string mexAddress = "http://localhost:8000/servicemodelsamples/service/mex";  
  
    MetadataExchangeClient mexClient = new MetadataExchangeClient("MyMexEndpoint");  
    mexClient.ResolveMetadataReferences = true;  
    MetadataSet mdSet = mexClient.GetMetadata(new EndpointAddress(mexAddress));  
    foreach (MetadataSection section in mdSet.MetadataSections)  
    Console.WriteLine("Metadata section: " + section.Dialect.ToString());  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="3ad50-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3ad50-121">See Also</span></span>  
 [<span data-ttu-id="3ad50-122">Comportamento de publicação de metadados</span><span class="sxs-lookup"><span data-stu-id="3ad50-122">Metadata Publishing Behavior</span></span>](../../../../docs/framework/wcf/samples/metadata-publishing-behavior.md)  
 [<span data-ttu-id="3ad50-123">Recuperar metadados</span><span class="sxs-lookup"><span data-stu-id="3ad50-123">Retrieve Metadata</span></span>](../../../../docs/framework/wcf/samples/retrieve-metadata.md)  
 [<span data-ttu-id="3ad50-124">Metadados</span><span class="sxs-lookup"><span data-stu-id="3ad50-124">Metadata</span></span>](../../../../docs/framework/wcf/feature-details/metadata.md)  
 [<span data-ttu-id="3ad50-125">Publicando metadados</span><span class="sxs-lookup"><span data-stu-id="3ad50-125">Publishing Metadata</span></span>](../../../../docs/framework/wcf/feature-details/publishing-metadata.md)  
 [<span data-ttu-id="3ad50-126">Publicando pontos de extremidade de metadados</span><span class="sxs-lookup"><span data-stu-id="3ad50-126">Publishing Metadata Endpoints</span></span>](../../../../docs/framework/wcf/publishing-metadata-endpoints.md)
