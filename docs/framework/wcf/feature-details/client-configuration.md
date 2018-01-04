---
title: "Configuração do cliente"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5da5bd3b-65d9-43b7-91b9-cc9e989b1350
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7ece2585287f6e2767e64c2ec03c75adcfe161c5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="client-configuration"></a><span data-ttu-id="6bc1c-102">Configuração do cliente</span><span class="sxs-lookup"><span data-stu-id="6bc1c-102">Client Configuration</span></span>
<span data-ttu-id="6bc1c-103">Você pode usar o [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] configuração do cliente para especificar o endereço, associação de comportamento e de contrato, as propriedades de "ABC" do ponto de extremidade de cliente, que os clientes usam para se conectar aos pontos de extremidade de serviço.</span><span class="sxs-lookup"><span data-stu-id="6bc1c-103">You can use the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] client configuration to specify the address, binding, behavior, and contract, the "ABC" properties of the client endpoint, which clients use to connect to service endpoints.</span></span> <span data-ttu-id="6bc1c-104">O [ \<cliente >](../../../../docs/framework/configure-apps/file-schema/wcf/client.md) elemento tem um [ \<ponto de extremidade >](http://msdn.microsoft.com/en-us/13aa23b7-2f08-4add-8dbf-a99f8127c017) elemento cujos atributos são usados para configurar o ponto de extremidade ABC.</span><span class="sxs-lookup"><span data-stu-id="6bc1c-104">The [\<client>](../../../../docs/framework/configure-apps/file-schema/wcf/client.md) element has an [\<endpoint>](http://msdn.microsoft.com/en-us/13aa23b7-2f08-4add-8dbf-a99f8127c017) element whose attributes are used to configure the endpoint ABCs.</span></span> <span data-ttu-id="6bc1c-105">Esses atributos são discutidos na seção "Configurando pontos de extremidade" deste tópico.</span><span class="sxs-lookup"><span data-stu-id="6bc1c-105">These attributes are discussed in the "Configuring Endpoints" section of this topic.</span></span>  
  
 <span data-ttu-id="6bc1c-106">O [ \<ponto de extremidade >](http://msdn.microsoft.com/en-us/13aa23b7-2f08-4add-8dbf-a99f8127c017) também contém um [ \<metadados >](../../../../docs/framework/configure-apps/file-schema/wcf/metadata.md) elemento que é usado para especificar configurações de importação e exportação de metadados, um [ \<cabeçalhos >](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md) elemento que contém uma coleção de cabeçalhos de endereço personalizado, e um [ \<identidade >](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md) elemento que permite a autenticação de um ponto de extremidade por outros pontos de extremidade troca de mensagens com ele.</span><span class="sxs-lookup"><span data-stu-id="6bc1c-106">The [\<endpoint>](http://msdn.microsoft.com/en-us/13aa23b7-2f08-4add-8dbf-a99f8127c017) element also contains a [\<metadata>](../../../../docs/framework/configure-apps/file-schema/wcf/metadata.md) element that is used to specify settings for importing and exporting metadata , a [\<headers>](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md) element that contains a collection of custom address headers, and an [\<identity>](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md) element that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span> <span data-ttu-id="6bc1c-107">O [ \<cabeçalhos >](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md) e [ \<identidade >](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md) elementos fazem parte do <xref:System.ServiceModel.EndpointAddress> e são discutidas no [endereços](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md) tópico.</span><span class="sxs-lookup"><span data-stu-id="6bc1c-107">The [\<headers>](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md) and [\<identity>](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md) elements are part of the <xref:System.ServiceModel.EndpointAddress> and are discussed in the [Addresses](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md) topic.</span></span> <span data-ttu-id="6bc1c-108">Links para tópicos que explicam o uso de extensões de metadados são fornecidos na seção Configuração de metadados sub deste tópico.</span><span class="sxs-lookup"><span data-stu-id="6bc1c-108">Links to topics that explain the use of metadata extensions are provided in the Configuring Metadata sub-section of this topic.</span></span>  
  
## <a name="configuring-endpoints"></a><span data-ttu-id="6bc1c-109">Configurando pontos de extremidade</span><span class="sxs-lookup"><span data-stu-id="6bc1c-109">Configuring Endpoints</span></span>  
 <span data-ttu-id="6bc1c-110">A configuração do cliente é projetada para permitir que o cliente especificar um ou mais pontos de extremidade, cada um com seu próprio nome, endereço e contrato, com cada referência a [ \<associações >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) e [ \< comportamentos >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) elementos na configuração do cliente a ser usado para configurar o ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="6bc1c-110">The client configuration is designed to allow the client to specify one or more endpoints, each with its own name, address, and contract, with each referencing the [\<bindings>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) and [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) elements in the client configuration to be used to configure that endpoint.</span></span> <span data-ttu-id="6bc1c-111">O arquivo de configuração do cliente deve ser nomeado "App. config" porque esse é o nome que o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] espera de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="6bc1c-111">The client configuration file should be named "App.config" because this is the name that the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] runtime expects.</span></span> <span data-ttu-id="6bc1c-112">O exemplo a seguir mostra o arquivo de configuração de um cliente.</span><span class="sxs-lookup"><span data-stu-id="6bc1c-112">The following example shows a client configuration file.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
        <client>  
          <endpoint  
            name="endpoint1"  
            address="http://localhost/ServiceModelSamples/service.svc"  
            binding="wsHttpBinding"  
            bindingConfiguration="WSHttpBinding_IHello"  
            behaviorConfiguration="IHello_Behavior"  
            contract="IHello" >  
  
            <metadata>  
              <wsdlImporters>  
                <extension  
                  type="Microsoft.ServiceModel.Samples.WsdlDocumentationImporter, WsdlDocumentation"/>  
              </wsdlImporters>  
            </metadata>  
  
            <identity>  
              <servicePrincipalName value="host/localhost" />  
            </identity>  
          </endpoint>  
// Add another endpoint by adding another <endpoint> element.  
          <endpoint  
            name="endpoint2">  
           //Configure another endpoint here.  
          </endpoint>  
        </client>  
  
//The bindings section references by the bindingConfiguration endpoint attribute.  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_IHello"   
                 bypassProxyOnLocal="false"   
                 hostNameComparisonMode="StrongWildcard">  
          <readerQuotas maxDepth="32"/>  
          <reliableSession ordered="true"   
                           enabled="false" />  
          <security mode="Message">  
           //Security settings go here.  
          </security>  
        </binding>  
        <binding name="Another Binding"  
        //Configure this binding here.  
        </binding>  
          </wsHttpBinding>  
        </bindings>  
  
//The behavior section references by the behaviorConfiguration endpoint attribute.  
        <behaviors>  
            <endpointBehaviors>  
                <behavior name=" IHello_Behavior ">  
                    <clientVia />  
                </behavior>  
            </endpointBehaviors>  
        </behaviors>  
  
    </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="6bc1c-113">Opcional `name` atributo identifica exclusivamente um ponto de extremidade para um dado contrato.</span><span class="sxs-lookup"><span data-stu-id="6bc1c-113">The optional `name` attribute uniquely identifies an endpoint for a given contract.</span></span> <span data-ttu-id="6bc1c-114">Ele é usado pelo <xref:System.ServiceModel.ChannelFactory%601.%23ctor%2A> ou o <xref:System.ServiceModel.ClientBase%601.%23ctor%2A> para especificar qual ponto de extremidade na configuração do cliente está sendo direcionado e deve ser carregado quando um canal é criado para o serviço.</span><span class="sxs-lookup"><span data-stu-id="6bc1c-114">It is used by the <xref:System.ServiceModel.ChannelFactory%601.%23ctor%2A> or by the <xref:System.ServiceModel.ClientBase%601.%23ctor%2A> to specify which endpoint in the client configuration is being targeted and must be loaded when a channel is created to service.</span></span> <span data-ttu-id="6bc1c-115">Um nome de configuração de ponto de extremidade de curinga "*" está disponível e indica para o <xref:System.ServiceModel.ChannelFactory.ApplyConfiguration%2A> método que ele deve carregar qualquer configuração de ponto de extremidade no arquivo, desde que haja precisamente uma disponível e, caso contrário gerará uma exceção.</span><span class="sxs-lookup"><span data-stu-id="6bc1c-115">A wildcard endpoint configuration name "*" is available and indicates to the <xref:System.ServiceModel.ChannelFactory.ApplyConfiguration%2A> method that it should load any endpoint configuration in the file, provided there is precisely one available, and otherwise throws an exception.</span></span> <span data-ttu-id="6bc1c-116">Se esse atributo for omitido, o ponto de extremidade correspondente é usado como o ponto de extremidade padrão associado ao tipo de contrato especificado.</span><span class="sxs-lookup"><span data-stu-id="6bc1c-116">If this attribute is omitted, the corresponding endpoint is used as the default endpoint associated with the specified contract type.</span></span> <span data-ttu-id="6bc1c-117">O valor padrão para o `name` atributo é uma cadeia de caracteres vazia, o que é comparada como qualquer outro nome.</span><span class="sxs-lookup"><span data-stu-id="6bc1c-117">The default value for the `name` attribute is an empty string which is matched like any other name.</span></span>  
  
 <span data-ttu-id="6bc1c-118">Cada ponto de extremidade deve ter um endereço associado a ele para localizar e identificar o ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="6bc1c-118">Every endpoint must have an address associated with it to locate and identify the endpoint.</span></span> <span data-ttu-id="6bc1c-119">O `address` atributo pode ser usado para especificar a URL que fornece o local do ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="6bc1c-119">The `address` attribute can be used to specify the URL that provides the location of the endpoint.</span></span> <span data-ttu-id="6bc1c-120">Mas o endereço de um ponto de extremidade de serviço também pode ser especificado no código, criando um identificador de recurso uniforme (URI) e é adicionado para o <xref:System.ServiceModel.ServiceHost> usando um do <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> métodos.</span><span class="sxs-lookup"><span data-stu-id="6bc1c-120">But the address for a service endpoint can also be specified in code by creating a Uniform Resource Identifier (URI) and is added to the <xref:System.ServiceModel.ServiceHost> using one of the <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> methods.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="6bc1c-121">[Endereços](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md).</span><span class="sxs-lookup"><span data-stu-id="6bc1c-121"> [Addresses](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md).</span></span> <span data-ttu-id="6bc1c-122">Como introdução indica, o [ \<cabeçalhos >](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md) e [ \<identidade >](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md) elementos fazem parte do <xref:System.ServiceModel.EndpointAddress> e também são discutidas no [ Endereços](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md) tópico.</span><span class="sxs-lookup"><span data-stu-id="6bc1c-122">As the introduction indicates, the [\<headers>](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md) and [\<identity>](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md) elements are part of the <xref:System.ServiceModel.EndpointAddress> and are also discussed in the [Addresses](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md) topic.</span></span>  
  
 <span data-ttu-id="6bc1c-123">O `binding` atributo indica o tipo de ponto de extremidade de associação espera usar ao se conectar a um serviço.</span><span class="sxs-lookup"><span data-stu-id="6bc1c-123">The `binding` attribute indicates the type of binding the endpoint expects to use when connecting to a service.</span></span> <span data-ttu-id="6bc1c-124">O tipo deve ter uma seção de configuração registrados se é para ser referenciado.</span><span class="sxs-lookup"><span data-stu-id="6bc1c-124">The type must have a registered configuration section if it is to be referenced.</span></span> <span data-ttu-id="6bc1c-125">No exemplo anterior, este é o [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) seção, o que indica que o ponto de extremidade usa um <xref:System.ServiceModel.WSHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="6bc1c-125">In the previous example, this is the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) section, which indicates that the endpoint uses a <xref:System.ServiceModel.WSHttpBinding>.</span></span> <span data-ttu-id="6bc1c-126">Mas, pode haver mais de uma associação de um determinado tipo pode usar o ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="6bc1c-126">But there may be more than one binding of a given type that the endpoint can use.</span></span> <span data-ttu-id="6bc1c-127">Cada um deles tem seu próprio [ \<associação >](../../../../docs/framework/misc/binding.md) elemento dentro do elemento type (binding).</span><span class="sxs-lookup"><span data-stu-id="6bc1c-127">Each of these has its own [\<binding>](../../../../docs/framework/misc/binding.md) element within the (binding) type element.</span></span> <span data-ttu-id="6bc1c-128">O `bindingconfiguration` atributo é usado para distinguir entre as ligações do mesmo tipo.</span><span class="sxs-lookup"><span data-stu-id="6bc1c-128">The `bindingconfiguration` attribute is used to distinguish between bindings of the same type.</span></span> <span data-ttu-id="6bc1c-129">Seu valor é correspondido com o `name` atributo o [ \<associação >](../../../../docs/framework/misc/binding.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="6bc1c-129">Its value is matched with the `name` attribute of the [\<binding>](../../../../docs/framework/misc/binding.md) element.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="6bc1c-130">como configurar um cliente de associação usando a configuração, consulte [como: especificar uma associação de cliente em configuração](../../../../docs/framework/wcf/how-to-specify-a-client-binding-in-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="6bc1c-130"> how to configure a client binding using configuration, see [How to: Specify a Client Binding in Configuration](../../../../docs/framework/wcf/how-to-specify-a-client-binding-in-configuration.md).</span></span>  
  
 <span data-ttu-id="6bc1c-131">O `behaviorConfiguration` atributo é usado para especificar quais [ \<comportamento >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) do [ \<endpointBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md) deve usar o ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="6bc1c-131">The `behaviorConfiguration` attribute is used to specify which [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) of the [\<endpointBehaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md) the endpoint should use.</span></span> <span data-ttu-id="6bc1c-132">Seu valor é correspondido com o `name` atributo o [ \<comportamento >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="6bc1c-132">Its value is matched with the `name` attribute of the [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) element.</span></span> <span data-ttu-id="6bc1c-133">Para obter um exemplo do uso da configuração para especificar o comportamento do cliente, consulte [Configurando comportamentos do cliente](../../../../docs/framework/wcf/configuring-client-behaviors.md).</span><span class="sxs-lookup"><span data-stu-id="6bc1c-133">For an example of using configuration to specify client behaviors, see [Configuring Client Behaviors](../../../../docs/framework/wcf/configuring-client-behaviors.md).</span></span>  
  
 <span data-ttu-id="6bc1c-134">O `contract` atributo especifica qual contrato que o ponto de extremidade está expondo.</span><span class="sxs-lookup"><span data-stu-id="6bc1c-134">The `contract` attribute specifies which contract the endpoint is exposing.</span></span> <span data-ttu-id="6bc1c-135">Esse valor é mapeado para o <xref:System.ServiceModel.ServiceContractAttribute.ConfigurationName%2A> do <xref:System.ServiceModel.ServiceContractAttribute>.</span><span class="sxs-lookup"><span data-stu-id="6bc1c-135">This value maps to the <xref:System.ServiceModel.ServiceContractAttribute.ConfigurationName%2A> of the <xref:System.ServiceModel.ServiceContractAttribute>.</span></span> <span data-ttu-id="6bc1c-136">O valor padrão é o nome de tipo completo da classe que implementa o serviço.</span><span class="sxs-lookup"><span data-stu-id="6bc1c-136">The default value is the full type name of the class that implements the service.</span></span>  
  
### <a name="configuring-metadata"></a><span data-ttu-id="6bc1c-137">Configuração de metadados</span><span class="sxs-lookup"><span data-stu-id="6bc1c-137">Configuring Metadata</span></span>  
 <span data-ttu-id="6bc1c-138">O [ \<metadados >](../../../../docs/framework/configure-apps/file-schema/wcf/metadata.md) elemento é usado para especificar configurações usadas para registrar metadados importar extensões.</span><span class="sxs-lookup"><span data-stu-id="6bc1c-138">The [\<metadata>](../../../../docs/framework/configure-apps/file-schema/wcf/metadata.md) element is used to specify settings used to register metadata import extensions.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="6bc1c-139">Estendendo o sistema de metadados, consulte[estendendo o sistema de metadados](../../../../docs/framework/wcf/extending/extending-the-metadata-system.md).</span><span class="sxs-lookup"><span data-stu-id="6bc1c-139"> extending the metadata system, see[Extending the Metadata System](../../../../docs/framework/wcf/extending/extending-the-metadata-system.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6bc1c-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6bc1c-140">See Also</span></span>  
 [<span data-ttu-id="6bc1c-141">Pontos de extremidade: endereços, associações e contratos</span><span class="sxs-lookup"><span data-stu-id="6bc1c-141">Endpoints: Addresses, Bindings, and Contracts</span></span>](../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)  
 [<span data-ttu-id="6bc1c-142">Configurando comportamentos do cliente</span><span class="sxs-lookup"><span data-stu-id="6bc1c-142">Configuring Client Behaviors</span></span>](../../../../docs/framework/wcf/configuring-client-behaviors.md)
