---
title: Pontos de extremidade padrão
ms.date: 03/30/2017
ms.assetid: 3fcb4225-addc-44f2-935d-30e4943a8812
ms.openlocfilehash: 880601664d7602e279c5d022fa37c44914a58772
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184398"
---
# <a name="standard-endpoints"></a><span data-ttu-id="42921-102">Pontos de extremidade padrão</span><span class="sxs-lookup"><span data-stu-id="42921-102">Standard Endpoints</span></span>
<span data-ttu-id="42921-103">Os pontos finais são definidos especificando um endereço, uma vinculação e um contrato.</span><span class="sxs-lookup"><span data-stu-id="42921-103">Endpoints are defined by specifying an address, a binding, and a contract.</span></span> <span data-ttu-id="42921-104">Outros parâmetros que podem ser definidos em um ponto final incluem configuração de comportamento, cabeçalhos e URIs de ouvir.</span><span class="sxs-lookup"><span data-stu-id="42921-104">Other parameters that may be set on an endpoint include behavior configuration, headers, and listen URIs.</span></span>  <span data-ttu-id="42921-105">Para certos tipos de pontos finais, esses valores não mudam.</span><span class="sxs-lookup"><span data-stu-id="42921-105">For certain types of endpoints these values do not change.</span></span> <span data-ttu-id="42921-106">Por exemplo, os pontos finais <xref:System.ServiceModel.Description.IMetadataExchange> de troca de metadados sempre usam o contrato.</span><span class="sxs-lookup"><span data-stu-id="42921-106">For example, metadata exchange endpoints always use the <xref:System.ServiceModel.Description.IMetadataExchange> contract.</span></span> <span data-ttu-id="42921-107">Outros pontos finais, <xref:System.ServiceModel.Description.WebHttpEndpoint> como sempre, exigem um comportamento de ponto final especificado.</span><span class="sxs-lookup"><span data-stu-id="42921-107">Other endpoints, such as <xref:System.ServiceModel.Description.WebHttpEndpoint> always require a specified endpoint behavior.</span></span> <span data-ttu-id="42921-108">A usabilidade de um ponto final pode ser melhorada tendo pontos finais com valores padrão para propriedades de ponto final comumente usadas.</span><span class="sxs-lookup"><span data-stu-id="42921-108">The usability of an endpoint can be improved by having endpoints with default values for commonly used endpoint properties.</span></span> <span data-ttu-id="42921-109">Os pontos finais padrão permitem que um desenvolvedor defina um ponto final que tenha valores padrão ou onde as propriedades de um ou mais pontos finais não mudem.</span><span class="sxs-lookup"><span data-stu-id="42921-109">Standard endpoints enable a developer to define an endpoint that has default values or where one or more endpoint’s properties does not change.</span></span>  <span data-ttu-id="42921-110">Esses pontos finais permitem que você use esse ponto final sem ter que especificar informações de natureza estática.</span><span class="sxs-lookup"><span data-stu-id="42921-110">These endpoints allow you to use such an endpoint without having to specify information of a static nature.</span></span> <span data-ttu-id="42921-111">Os pontos finais padrão podem ser usados para pontos finais de infra-estrutura e aplicativos.</span><span class="sxs-lookup"><span data-stu-id="42921-111">Standard endpoints can be used for infrastructure and application endpoints.</span></span>  
  
## <a name="infrastructure-endpoints"></a><span data-ttu-id="42921-112">Pontos finais da infra-estrutura</span><span class="sxs-lookup"><span data-stu-id="42921-112">Infrastructure Endpoints</span></span>  
 <span data-ttu-id="42921-113">Um serviço pode expor pontos finais com algumas das propriedades não explicitamente implementadas pelo autor do serviço.</span><span class="sxs-lookup"><span data-stu-id="42921-113">A service may expose endpoints with some of the properties not explicitly implemented by the service author.</span></span> <span data-ttu-id="42921-114">Por exemplo, o ponto final da <xref:System.ServiceModel.Description.IMetadataExchange> troca de metadados expõe o contrato, mas como um autor de serviço que você não implementa essa interface, ela é implementada pelo WCF.</span><span class="sxs-lookup"><span data-stu-id="42921-114">For example, the metadata exchange endpoint exposes the <xref:System.ServiceModel.Description.IMetadataExchange> contract but as a service author you do not implement that interface, it is implemented by WCF.</span></span> <span data-ttu-id="42921-115">Esses pontos finais de infra-estrutura têm valores padrão para uma ou mais propriedades de ponto final, algumas das quais podem ser inalteráveis.</span><span class="sxs-lookup"><span data-stu-id="42921-115">Such infrastructure endpoints have default values for one or more endpoint properties, some of which may be unalterable.</span></span> <span data-ttu-id="42921-116">A <xref:System.ServiceModel.Description.ServiceEndpoint.Contract%2A> propriedade do ponto final de <xref:System.ServiceModel.Description.IMetadataExchange>troca de metadados deve ser , enquanto outras propriedades como a vinculação podem ser fornecidas pelo desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="42921-116">The <xref:System.ServiceModel.Description.ServiceEndpoint.Contract%2A> property of the metadata exchange endpoint must be <xref:System.ServiceModel.Description.IMetadataExchange>, while other properties like binding can be supplied by the developer.</span></span> <span data-ttu-id="42921-117">Os pontos finais da <xref:System.ServiceModel.Description.ServiceEndpoint.IsSystemEndpoint%2A> infra-estrutura são identificados definindo a propriedade como `true`.</span><span class="sxs-lookup"><span data-stu-id="42921-117">Infrastructure endpoints are identified by setting the <xref:System.ServiceModel.Description.ServiceEndpoint.IsSystemEndpoint%2A> property to `true`.</span></span>  
  
## <a name="application-endpoints"></a><span data-ttu-id="42921-118">Pontos finais do aplicativo</span><span class="sxs-lookup"><span data-stu-id="42921-118">Application Endpoints</span></span>  
 <span data-ttu-id="42921-119">Os desenvolvedores de aplicativos podem definir seus próprios pontos finais padrão que especificam valores padrão para o endereço, vinculação ou contrato.</span><span class="sxs-lookup"><span data-stu-id="42921-119">Application developers can define their own standard endpoints which specify default values for the address, binding, or contract.</span></span> <span data-ttu-id="42921-120">Você define um ponto final padrão, <xref:System.ServiceModel.Description.ServiceEndpoint> derivando uma classe e definindo as propriedades de ponto final apropriadas.</span><span class="sxs-lookup"><span data-stu-id="42921-120">You define a standard endpoint by deriving a class from <xref:System.ServiceModel.Description.ServiceEndpoint> and setting the appropriate endpoint properties.</span></span> <span data-ttu-id="42921-121">Você pode fornecer valores padrão para propriedades que podem ser alteradas.</span><span class="sxs-lookup"><span data-stu-id="42921-121">You can provide default values for properties that can be changed.</span></span> <span data-ttu-id="42921-122">Algumas outras propriedades terão valores estáticos que não podem ser alterados.</span><span class="sxs-lookup"><span data-stu-id="42921-122">Some other properties will have static values that cannot change.</span></span> <span data-ttu-id="42921-123">O exemplo a seguir mostra como implementar um ponto final padrão.</span><span class="sxs-lookup"><span data-stu-id="42921-123">The following example shows how to implement a standard endpoint.</span></span>  
  
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
  
 <span data-ttu-id="42921-124">Para usar um ponto final personalizado definido pelo usuário em <xref:System.ServiceModel.Configuration.StandardEndpointElement>um arquivo <xref:System.ServiceModel.Configuration.StandardEndpointCollectionElement%602>de configuração, você deve derivar uma classe de , derivar uma classe e registrar o novo ponto final padrão na seção de extensões em app.config ou machine.config.  O <xref:System.ServiceModel.Configuration.StandardEndpointElement> fornece suporte de configuração para o ponto final padrão, como mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="42921-124">To use a user-defined custom endpoint in a configuration file you must derive a class from <xref:System.ServiceModel.Configuration.StandardEndpointElement>, derive a class from <xref:System.ServiceModel.Configuration.StandardEndpointCollectionElement%602>, and register the new standard endpoint in the extensions section in app.config or machine.config.  The <xref:System.ServiceModel.Configuration.StandardEndpointElement> provides configuration support for the standard endpoint, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="42921-125">O <xref:System.ServiceModel.Configuration.StandardEndpointCollectionElement%602> fornece o tipo de backup para `standardEndpoints` a coleção que aparece a seção <> na configuração para o ponto final padrão.</span><span class="sxs-lookup"><span data-stu-id="42921-125">The <xref:System.ServiceModel.Configuration.StandardEndpointCollectionElement%602> provides the backing type for the collection that appears under the <`standardEndpoints`> section in the configuration for the standard endpoint.</span></span>  <span data-ttu-id="42921-126">O exemplo a seguir mostra como implementar essa classe.</span><span class="sxs-lookup"><span data-stu-id="42921-126">The following example shows how to implement this class.</span></span>  
  
```csharp
public class CustomEndpointCollectionElement : StandardEndpointCollectionElement<CustomEndpoint, CustomEndpointElement>
{
    // ...
}
```

<span data-ttu-id="42921-127">O exemplo a seguir mostra como registrar um ponto final padrão na seção extensões.</span><span class="sxs-lookup"><span data-stu-id="42921-127">The following example shows how to register a standard endpoint in the extensions section.</span></span>

```xml  
<extensions>  
      <standardEndpointExtensions>  
        <add  
          name="customStandardEndpoint"  
          type="CustomEndpointCollectionElement, Example.dll,  
                Version=1.0.0.0, Culture=neutral, PublicKeyToken=ffffffffffffffff"/>  
```  
  
## <a name="configuring-a-standard-endpoint"></a><span data-ttu-id="42921-128">Configurando um ponto final padrão</span><span class="sxs-lookup"><span data-stu-id="42921-128">Configuring a Standard Endpoint</span></span>  
 <span data-ttu-id="42921-129">Os pontos finais padrão podem ser adicionados em código ou na configuração.</span><span class="sxs-lookup"><span data-stu-id="42921-129">Standard endpoints can be added in code or in configuration.</span></span>  <span data-ttu-id="42921-130">Para adicionar um ponto final padrão no código, basta instanciar o tipo de ponto final padrão apropriado e adicioná-lo ao host de serviço, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="42921-130">To add a standard endpoint in code simply instantiate the appropriate standard endpoint type and add it to the service host as shown in the following example:</span></span>  
  
```csharp  
serviceHost.AddServiceEndpoint(new CustomEndpoint());  
```  
  
 <span data-ttu-id="42921-131">Para adicionar um ponto final padrão `endpoint` na configuração, `service` adicione um elemento> <`standardEndpoints` ao elemento <> e quaisquer configurações necessárias no elemento de> <.</span><span class="sxs-lookup"><span data-stu-id="42921-131">To add a standard endpoint in configuration, add an <`endpoint`> element to the <`service`> element and any needed configuration settings in the <`standardEndpoints`> element.</span></span> <span data-ttu-id="42921-132">O exemplo a seguir <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>mostra como adicionar a , [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]um dos pontos finais padrão com os quais é enviado .</span><span class="sxs-lookup"><span data-stu-id="42921-132">The following example shows how to add a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, one of the standard endpoints that ships with [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].</span></span>  
  
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
  
 <span data-ttu-id="42921-133">O tipo de ponto final padrão é especificado `endpoint` usando o atributo tipo no elemento <>.</span><span class="sxs-lookup"><span data-stu-id="42921-133">The type of standard endpoint is specified using the kind attribute in the <`endpoint`> element.</span></span> <span data-ttu-id="42921-134">O ponto final é configurado dentro do elemento> <. `standardEndpoints`</span><span class="sxs-lookup"><span data-stu-id="42921-134">The endpoint is configured within the <`standardEndpoints`> element.</span></span> <span data-ttu-id="42921-135">No exemplo acima, <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> um ponto final é adicionado e configurado.</span><span class="sxs-lookup"><span data-stu-id="42921-135">In the example above, a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> endpoint is added and configured.</span></span> <span data-ttu-id="42921-136">O `udpDiscoveryEndpoint` elemento> <`standardEndpoint` contém uma <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint.MulticastAddress%2A>> <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint><que define a propriedade do .</span><span class="sxs-lookup"><span data-stu-id="42921-136">The <`udpDiscoveryEndpoint`> element contains a <`standardEndpoint`> that sets the <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint.MulticastAddress%2A> property of the <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>.</span></span>  
  
## <a name="standard-endpoints-shipped-with-the-net-framework"></a><span data-ttu-id="42921-137">Pontos finais padrão enviados com o Framework .NET</span><span class="sxs-lookup"><span data-stu-id="42921-137">Standard Endpoints Shipped with the .NET Framework</span></span>  
 <span data-ttu-id="42921-138">A tabela a seguir lista os [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]pontos finais padrão enviados com .</span><span class="sxs-lookup"><span data-stu-id="42921-138">The following table lists the standard endpoints shipped with [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].</span></span>  
  
 `Mex Endpoint`  
 <span data-ttu-id="42921-139">Um ponto final padrão que é usado para expor metadados de serviço.</span><span class="sxs-lookup"><span data-stu-id="42921-139">A standard endpoint that is used to expose service metadata.</span></span>  
  
 <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>  
 <span data-ttu-id="42921-140">Um ponto de extremidade padrão usado pelos serviços para enviar mensagens de comunicado.</span><span class="sxs-lookup"><span data-stu-id="42921-140">A standard endpoint that is used by services to send announcement messages.</span></span>  
  
 <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>  
 <span data-ttu-id="42921-141">Um ponto final padrão que é usado pelos serviços para enviar mensagens de descoberta.</span><span class="sxs-lookup"><span data-stu-id="42921-141">A standard endpoint that is used by services to send discovery messages.</span></span>  
  
 <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>  
 <span data-ttu-id="42921-142">Um ponto de extremidade padrão pré-configurado para operações de descoberta por meio de uma associação multicast UDP.</span><span class="sxs-lookup"><span data-stu-id="42921-142">A standard endpoint that is pre-configured for discovery operations over a UDP multicast binding.</span></span>  
  
 <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>  
 <span data-ttu-id="42921-143">Um ponto de extremidade padrão usado pelos serviços para enviar mensagens de comunicado por meio de uma associação UDP.</span><span class="sxs-lookup"><span data-stu-id="42921-143">A standard endpoint that is used by services to send announcement messages over a UDP binding.</span></span>  
  
 <xref:System.ServiceModel.Discovery.DynamicEndpoint>  
 <span data-ttu-id="42921-144">Um ponto final padrão que usa o WS-Discovery para encontrar o endereço de ponto final dinamicamente em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="42921-144">A standard endpoint that uses WS-Discovery to find the endpoint address dynamically at runtime.</span></span>  
  
 <xref:System.ServiceModel.Description.ServiceMetadataEndpoint>  
 <span data-ttu-id="42921-145">Um ponto final padrão para troca de metadados.</span><span class="sxs-lookup"><span data-stu-id="42921-145">A standard endpoint for metadata exchange.</span></span>  
  
 <xref:System.ServiceModel.Description.WebHttpEndpoint>  
 <span data-ttu-id="42921-146">Um ponto final <xref:System.ServiceModel.WebHttpBinding> padrão com uma <xref:System.ServiceModel.Description.WebHttpBehavior> vinculação que adiciona automaticamente o comportamento</span><span class="sxs-lookup"><span data-stu-id="42921-146">A standard endpoint with a <xref:System.ServiceModel.WebHttpBinding> binding that automatically adds the <xref:System.ServiceModel.Description.WebHttpBehavior> behavior</span></span>  
  
 <xref:System.ServiceModel.Description.WebScriptEndpoint>  
 <span data-ttu-id="42921-147">Um ponto final <xref:System.ServiceModel.WebHttpBinding> padrão com uma <xref:System.ServiceModel.Description.WebScriptEnablingBehavior> ligação que adiciona automaticamente o comportamento.</span><span class="sxs-lookup"><span data-stu-id="42921-147">A standard endpoint with a <xref:System.ServiceModel.WebHttpBinding> binding that automatically adds the <xref:System.ServiceModel.Description.WebScriptEnablingBehavior> behavior.</span></span>  
  
 <xref:System.ServiceModel.Description.WebServiceEndpoint>  
 <span data-ttu-id="42921-148">Um ponto final <xref:System.ServiceModel.WebHttpBinding> padrão com uma ligação.</span><span class="sxs-lookup"><span data-stu-id="42921-148">A standard endpoint with a <xref:System.ServiceModel.WebHttpBinding> binding.</span></span>  
  
 <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>  
 <span data-ttu-id="42921-149">Um ponto de extremidade padrão que permite chamar operações de controle em instâncias de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="42921-149">A standard endpoint that enables you to call control operations on workflow instances.</span></span>  
  
 <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>  
 <span data-ttu-id="42921-150">Um ponto final padrão que suporta a criação do fluxo de trabalho e a retomada de marcadores.</span><span class="sxs-lookup"><span data-stu-id="42921-150">A standard endpoint that supports workflow creation and bookmark resumption.</span></span>
