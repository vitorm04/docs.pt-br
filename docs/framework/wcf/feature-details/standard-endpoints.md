---
title: Pontos de extremidade padrão
ms.date: 03/30/2017
ms.assetid: 3fcb4225-addc-44f2-935d-30e4943a8812
ms.openlocfilehash: 395d910ddabc553cca47dcdd038f44b1470b3455
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33500591"
---
# <a name="standard-endpoints"></a><span data-ttu-id="3c520-102">Pontos de extremidade padrão</span><span class="sxs-lookup"><span data-stu-id="3c520-102">Standard Endpoints</span></span>
<span data-ttu-id="3c520-103">Pontos de extremidade são definidos pela especificação de um endereço, uma ligação e um contrato.</span><span class="sxs-lookup"><span data-stu-id="3c520-103">Endpoints are defined by specifying an address, a binding, and a contract.</span></span> <span data-ttu-id="3c520-104">Outros parâmetros que podem ser definidos em um ponto de extremidade incluem a configuração de comportamento, cabeçalhos e escutam URIs.</span><span class="sxs-lookup"><span data-stu-id="3c520-104">Other parameters that may be set on an endpoint include behavior configuration, headers, and listen URIs.</span></span>  <span data-ttu-id="3c520-105">Para determinados tipos de pontos de extremidade que não altere esses valores.</span><span class="sxs-lookup"><span data-stu-id="3c520-105">For certain types of endpoints these values do not change.</span></span> <span data-ttu-id="3c520-106">Por exemplo, pontos de extremidade de troca de metadados sempre usam o <xref:System.ServiceModel.Description.IMetadataExchange> contrato.</span><span class="sxs-lookup"><span data-stu-id="3c520-106">For example, metadata exchange endpoints always use the <xref:System.ServiceModel.Description.IMetadataExchange> contract.</span></span> <span data-ttu-id="3c520-107">Outros pontos de extremidade, como <xref:System.ServiceModel.Description.WebHttpEndpoint> sempre exigem um comportamento de ponto de extremidade especificado.</span><span class="sxs-lookup"><span data-stu-id="3c520-107">Other endpoints, such as <xref:System.ServiceModel.Description.WebHttpEndpoint> always require a specified endpoint behavior.</span></span> <span data-ttu-id="3c520-108">O uso de um ponto de extremidade pode ser melhorado por ter pontos de extremidade com valores padrão para propriedades de ponto de extremidade de uso geral.</span><span class="sxs-lookup"><span data-stu-id="3c520-108">The usability of an endpoint can be improved by having endpoints with default values for commonly used endpoint properties.</span></span> <span data-ttu-id="3c520-109">Pontos de extremidade padrão permitem que um desenvolvedor definir um ponto de extremidade que tem valores padrão ou em que as propriedades de um ou mais do ponto de extremidade não é alterado.</span><span class="sxs-lookup"><span data-stu-id="3c520-109">Standard endpoints enable a developer to define an endpoint that has default values or where one or more endpoint’s properties does not change.</span></span>  <span data-ttu-id="3c520-110">Esses pontos de extremidade permitem que você use um ponto de extremidade sem precisar especificar informações de natureza estática.</span><span class="sxs-lookup"><span data-stu-id="3c520-110">These endpoints allow you to use such an endpoint without having to specify information of a static nature.</span></span> <span data-ttu-id="3c520-111">Pontos de extremidade padrão podem ser usados para pontos de extremidade de infraestrutura e aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3c520-111">Standard endpoints can be used for infrastructure and application endpoints.</span></span>  
  
## <a name="infrastructure-endpoints"></a><span data-ttu-id="3c520-112">Pontos de extremidade de infraestrutura</span><span class="sxs-lookup"><span data-stu-id="3c520-112">Infrastructure Endpoints</span></span>  
 <span data-ttu-id="3c520-113">Um serviço pode expor pontos de extremidade com algumas das propriedades não são explicitamente implementadas pelo autor do serviço.</span><span class="sxs-lookup"><span data-stu-id="3c520-113">A service may expose endpoints with some of the properties not explicitly implemented by the service author.</span></span> <span data-ttu-id="3c520-114">Por exemplo, o ponto de extremidade de troca de metadados expõe o <xref:System.ServiceModel.Description.IMetadataExchange> de contrato, mas como um serviço de autor implementa essa interface, ele é implementado pelo WCF.</span><span class="sxs-lookup"><span data-stu-id="3c520-114">For example, the metadata exchange endpoint exposes the <xref:System.ServiceModel.Description.IMetadataExchange> contract but as a service author you do not implement that interface, it is implemented by WCF.</span></span> <span data-ttu-id="3c520-115">Esses pontos de extremidade de infraestrutura têm valores padrão para uma ou mais propriedades de ponto de extremidade, alguns dos quais podem ser inalterável.</span><span class="sxs-lookup"><span data-stu-id="3c520-115">Such infrastructure endpoints have default values for one or more endpoint properties, some of which may be unalterable.</span></span> <span data-ttu-id="3c520-116">O <xref:System.ServiceModel.Description.ServiceEndpoint.Contract%2A> propriedade do ponto de extremidade de troca de metadados deve ser <xref:System.ServiceModel.Description.IMetadataExchange>, enquanto outras propriedades, como associação podem ser fornecidas pelo desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="3c520-116">The <xref:System.ServiceModel.Description.ServiceEndpoint.Contract%2A> property of the metadata exchange endpoint must be <xref:System.ServiceModel.Description.IMetadataExchange>, while other properties like binding can be supplied by the developer.</span></span> <span data-ttu-id="3c520-117">Pontos de extremidade de infraestrutura são identificados, definindo o <xref:System.ServiceModel.Description.ServiceEndpoint.IsSystemEndpoint%2A> propriedade `true`.</span><span class="sxs-lookup"><span data-stu-id="3c520-117">Infrastructure endpoints are identified by setting the <xref:System.ServiceModel.Description.ServiceEndpoint.IsSystemEndpoint%2A> property to `true`.</span></span>  
  
## <a name="application-endpoints"></a><span data-ttu-id="3c520-118">Pontos de extremidade do aplicativo</span><span class="sxs-lookup"><span data-stu-id="3c520-118">Application Endpoints</span></span>  
 <span data-ttu-id="3c520-119">Os desenvolvedores de aplicativos podem definir seus próprios pontos de extremidade padrão que especificam valores padrão para o endereço, associação ou contrato.</span><span class="sxs-lookup"><span data-stu-id="3c520-119">Application developers can define their own standard endpoints which specify default values for the address, binding, or contract.</span></span> <span data-ttu-id="3c520-120">Definir um ponto de extremidade padrão derivando uma classe de <xref:System.ServiceModel.Description.ServiceEndpoint> e definindo as propriedades de ponto de extremidade apropriado.</span><span class="sxs-lookup"><span data-stu-id="3c520-120">You define a standard endpoint by deriving a class from <xref:System.ServiceModel.Description.ServiceEndpoint> and setting the appropriate endpoint properties.</span></span> <span data-ttu-id="3c520-121">Você pode fornecer valores padrão para as propriedades que podem ser alteradas.</span><span class="sxs-lookup"><span data-stu-id="3c520-121">You can provide default values for properties that can be changed.</span></span> <span data-ttu-id="3c520-122">Algumas outras propriedades terão valores estáticos que não é possível alterar.</span><span class="sxs-lookup"><span data-stu-id="3c520-122">Some other properties will have static values that cannot change.</span></span> <span data-ttu-id="3c520-123">O exemplo a seguir mostra como implementar um ponto de extremidade padrão.</span><span class="sxs-lookup"><span data-stu-id="3c520-123">The following example shows how to implement a standard endpoint.</span></span>  
  
```csharp
public class CustomEndpoint : ServiceEndpoint
{
    public CustomEndpoint()
        : this(string.Empty)
    { }  
    
    public CustomEndpoint(string address)
        : this(address, ContractDescription.GetContract(typeof(ICalculator)))
    { }  
    
    // Create the custom endpoint with a fixed binding
    public CustomEndpoint(string address, ContractDescription contract)
        : base(contract)
    {
        this.Binding = new BasicHttpBinding();
        this.IsSystemEndpoint = false;
    }
    
    // Definition of the additional property of this endpoint
    public bool Property { get; set; }
}
```
  
 <span data-ttu-id="3c520-124">Para usar um ponto de extremidade de personalizado definido pelo usuário em um arquivo de configuração, você deve derivar uma classe de <xref:System.ServiceModel.Configuration.StandardEndpointElement>, derive uma classe de <xref:System.ServiceModel.Configuration.StandardEndpointCollectionElement%602>e registrar o novo ponto de extremidade padrão na seção de extensões em App. config ou Machine. config.  O <xref:System.ServiceModel.Configuration.StandardEndpointElement> fornece suporte à configuração para o ponto de extremidade padrão, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="3c520-124">To use a user-defined custom endpoint in a configuration file you must derive a class from <xref:System.ServiceModel.Configuration.StandardEndpointElement>, derive a class from <xref:System.ServiceModel.Configuration.StandardEndpointCollectionElement%602>, and register the new standard endpoint in the extensions section in app.config or machine.config.  The <xref:System.ServiceModel.Configuration.StandardEndpointElement> provides configuration support for the standard endpoint, as shown in the following example.</span></span>  
  
```csharp
public class CustomEndpointElement : StandardEndpointElement
{
    // Definition of the additional property for the standard endpoint element
    public bool Property
    {
        get { return (bool)base["property"]; }
        set { base["property"] = value; }
    }

    // The additional property needs to be added to the properties of the standard endpoint element
    protected override ConfigurationPropertyCollection Properties
    {
        get
        {
            ConfigurationPropertyCollection properties = base.Properties;
            properties.Add(new ConfigurationProperty("property", typeof(bool), false, ConfigurationPropertyOptions.None));
            return properties;
        }
    }

    // Return the type of this standard endpoint
    protected override Type EndpointType
    {
        get { return typeof(CustomEndpoint); }
    }

    // Create the custom service endpoint
    protected override ServiceEndpoint CreateServiceEndpoint(ContractDescription contract)
    {
        return new CustomEndpoint();
    }

    // Read the value given to the property in config and save it
    protected override void OnApplyConfiguration(ServiceEndpoint endpoint, ServiceEndpointElement serviceEndpointElement)
    {
        CustomEndpoint customEndpoint = (CustomEndpoint)endpoint;
        customEndpoint.Property = this.Property;
    }

    // Read the value given to the property in config and save it
    protected override void OnApplyConfiguration(ServiceEndpoint endpoint, ChannelEndpointElement channelEndpointElement)
    {
        CustomEndpoint customEndpoint = (CustomEndpoint)endpoint;
        customEndpoint.Property = this.Property;
    }

    // No validation in this sample
    protected override void OnInitializeAndValidate(ServiceEndpointElement serviceEndpointElement)
    {
    }

    // No validation in this sample
    protected override void OnInitializeAndValidate(ChannelEndpointElement channelEndpointElement)
    {
    }
}
```  
  
 <span data-ttu-id="3c520-125">O <xref:System.ServiceModel.Configuration.StandardEndpointCollectionElement%602> fornece o tipo de backup para a coleção que aparece sob o <`standardEndpoints`> seção na configuração para o ponto de extremidade padrão.</span><span class="sxs-lookup"><span data-stu-id="3c520-125">The <xref:System.ServiceModel.Configuration.StandardEndpointCollectionElement%602> provides the backing type for the collection that appears under the <`standardEndpoints`> section in the configuration for the standard endpoint.</span></span>  <span data-ttu-id="3c520-126">O exemplo a seguir mostra como implementar essa classe.</span><span class="sxs-lookup"><span data-stu-id="3c520-126">The following example shows how to implement this class.</span></span>  
  
```csharp
public class CustomEndpointCollectionElement : StandardEndpointCollectionElement<CustomEndpoint, CustomEndpointElement>
{
    // ...
}
```

<span data-ttu-id="3c520-127">O exemplo a seguir mostra como registrar um ponto de extremidade padrão na seção de extensões.</span><span class="sxs-lookup"><span data-stu-id="3c520-127">The following example shows how to register a standard endpoint in the extensions section.</span></span>

```xml  
<extensions>  
      <standardEndpointExtensions>  
        <add  
          name="customStandardEndpoint"  
          type="CustomEndpointCollectionElement, Example.dll,  
                Version=1.0.0.0, Culture=neutral, PublicKeyToken=ffffffffffffffff"/>  
```  
  
## <a name="configuring-a-standard-endpoint"></a><span data-ttu-id="3c520-128">Configurando um ponto de extremidade padrão</span><span class="sxs-lookup"><span data-stu-id="3c520-128">Configuring a Standard Endpoint</span></span>  
 <span data-ttu-id="3c520-129">Pontos de extremidade padrão podem ser adicionados no código ou na configuração.</span><span class="sxs-lookup"><span data-stu-id="3c520-129">Standard endpoints can be added in code or in configuration.</span></span>  <span data-ttu-id="3c520-130">Para adicionar um ponto de extremidade padrão no código simplesmente instanciar o tipo de ponto de extremidade padrão apropriado e adicioná-lo para o host de serviço, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="3c520-130">To add a standard endpoint in code simply instantiate the appropriate standard endpoint type and add it to the service host as shown in the following example:</span></span>  
  
```csharp  
serviceHost.AddServiceEndpoint(new CustomEndpoint());  
```  
  
 <span data-ttu-id="3c520-131">Para adicionar um ponto de extremidade padrão na configuração, adicione um <`endpoint`> elemento para o <`service`> elemento e quaisquer definições de configuração no é necessário o <`standardEndpoints`> elemento.</span><span class="sxs-lookup"><span data-stu-id="3c520-131">To add a standard endpoint in configuration, add an <`endpoint`> element to the <`service`> element and any needed configuration settings in the <`standardEndpoints`> element.</span></span> <span data-ttu-id="3c520-132">O exemplo a seguir mostra como adicionar um <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, um dos pontos de extremidade padrão que é fornecido com [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3c520-132">The following example shows how to add a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, one of the standard endpoints that ships with [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].</span></span>  
  
```xml  
<services>  
  <service>  
    <endpoint isSystemEndpoint="true" kind="udpDiscoveryEndpoint" />  
  </service>  
</services>  
<standardEndpoints>    
  <udpDiscoveryEndpoint>  
     <standardEndpoint multicastAddress="soap.udp://239.255.255.250:3702" />
  </udpDiscoveryEndpoint>
</standardEndpoints>
```  
  
 <span data-ttu-id="3c520-133">O tipo de ponto de extremidade padrão é especificado usando o atributo de tipo no <`endpoint`> elemento.</span><span class="sxs-lookup"><span data-stu-id="3c520-133">The type of standard endpoint is specified using the kind attribute in the <`endpoint`> element.</span></span> <span data-ttu-id="3c520-134">O ponto de extremidade é configurado dentro de <`standardEndpoints`> elemento.</span><span class="sxs-lookup"><span data-stu-id="3c520-134">The endpoint is configured within the <`standardEndpoints`> element.</span></span> <span data-ttu-id="3c520-135">No exemplo acima, uma <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> ponto de extremidade é adicionado e configurado.</span><span class="sxs-lookup"><span data-stu-id="3c520-135">In the example above, a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> endpoint is added and configured.</span></span> <span data-ttu-id="3c520-136">O <`udpDiscoveryEndpoint`> elemento contém um <`standardEndpoint`> que define o <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint.MulticastAddress%2A> propriedade o <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>.</span><span class="sxs-lookup"><span data-stu-id="3c520-136">The <`udpDiscoveryEndpoint`> element contains a <`standardEndpoint`> that sets the <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint.MulticastAddress%2A> property of the <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>.</span></span>  
  
## <a name="standard-endpoints-shipped-with-the-net-framework"></a><span data-ttu-id="3c520-137">Pontos de extremidade padrão fornecidos com o .NET Framework</span><span class="sxs-lookup"><span data-stu-id="3c520-137">Standard Endpoints Shipped with the .NET Framework</span></span>  
 <span data-ttu-id="3c520-138">A tabela a seguir lista os pontos de extremidade padrão que acompanham o [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3c520-138">The following table lists the standard endpoints shipped with [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].</span></span>  
  
 `Mex Endpoint`  
 <span data-ttu-id="3c520-139">Um ponto de extremidade padrão que é usado para expor metadados de serviço.</span><span class="sxs-lookup"><span data-stu-id="3c520-139">A standard endpoint that is used to expose service metadata.</span></span>  
  
 <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>  
 <span data-ttu-id="3c520-140">Um ponto de extremidade padrão usado pelos serviços para enviar mensagens de comunicado.</span><span class="sxs-lookup"><span data-stu-id="3c520-140">A standard endpoint that is used by services to send announcement messages.</span></span>  
  
 <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>  
 <span data-ttu-id="3c520-141">Um ponto de extremidade padrão que é usado pelos serviços para enviar mensagens de descoberta.</span><span class="sxs-lookup"><span data-stu-id="3c520-141">A standard endpoint that is used by services to send discovery messages.</span></span>  
  
 <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>  
 <span data-ttu-id="3c520-142">Um ponto de extremidade padrão pré-configurado para operações de descoberta por meio de uma associação multicast UDP.</span><span class="sxs-lookup"><span data-stu-id="3c520-142">A standard endpoint that is pre-configured for discovery operations over a UDP multicast binding.</span></span>  
  
 <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>  
 <span data-ttu-id="3c520-143">Um ponto de extremidade padrão usado pelos serviços para enviar mensagens de comunicado por meio de uma associação UDP.</span><span class="sxs-lookup"><span data-stu-id="3c520-143">A standard endpoint that is used by services to send announcement messages over a UDP binding.</span></span>  
  
 <xref:System.ServiceModel.Discovery.DynamicEndpoint>  
 <span data-ttu-id="3c520-144">Um ponto de extremidade padrão que usa o WS-Discovery para localizar o endereço de ponto de extremidade dinamicamente em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="3c520-144">A standard endpoint that uses WS-Discovery to find the endpoint address dynamically at runtime.</span></span>  
  
 <xref:System.ServiceModel.Description.ServiceMetadataEndpoint>  
 <span data-ttu-id="3c520-145">Um ponto de extremidade padrão de troca de metadados.</span><span class="sxs-lookup"><span data-stu-id="3c520-145">A standard endpoint for metadata exchange.</span></span>  
  
 <xref:System.ServiceModel.Description.WebHttpEndpoint>  
 <span data-ttu-id="3c520-146">Um ponto de extremidade padrão com um <xref:System.ServiceModel.WebHttpBinding> associação que automaticamente adiciona o <xref:System.ServiceModel.Description.WebHttpBehavior> comportamento</span><span class="sxs-lookup"><span data-stu-id="3c520-146">A standard endpoint with a <xref:System.ServiceModel.WebHttpBinding> binding that automatically adds the <xref:System.ServiceModel.Description.WebHttpBehavior> behavior</span></span>  
  
 <xref:System.ServiceModel.Description.WebScriptEndpoint>  
 <span data-ttu-id="3c520-147">Um ponto de extremidade padrão com um <xref:System.ServiceModel.WebHttpBinding> associação que automaticamente adiciona o <xref:System.ServiceModel.Description.WebScriptEnablingBehavior> comportamento.</span><span class="sxs-lookup"><span data-stu-id="3c520-147">A standard endpoint with a <xref:System.ServiceModel.WebHttpBinding> binding that automatically adds the <xref:System.ServiceModel.Description.WebScriptEnablingBehavior> behavior.</span></span>  
  
 <xref:System.ServiceModel.Description.WebServiceEndpoint>  
 <span data-ttu-id="3c520-148">Um ponto de extremidade padrão com um <xref:System.ServiceModel.WebHttpBinding> associação.</span><span class="sxs-lookup"><span data-stu-id="3c520-148">A standard endpoint with a <xref:System.ServiceModel.WebHttpBinding> binding.</span></span>  
  
 <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>  
 <span data-ttu-id="3c520-149">Um ponto de extremidade padrão que permite chamar operações de controle em instâncias de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="3c520-149">A standard endpoint that enables you to call control operations on workflow instances.</span></span>  
  
 <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>  
 <span data-ttu-id="3c520-150">Um ponto de extremidade padrão que dá suporte a retomada da criação e o indicador de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="3c520-150">A standard endpoint that supports workflow creation and bookmark resumption.</span></span>
