---
title: Configurando a descoberta em um arquivo de configuração
ms.date: 03/30/2017
ms.assetid: b9884c11-8011-4763-bc2c-c526b80175d0
ms.openlocfilehash: 0ad44d0ad1f0d67d84cc42f6b9938d096c245417
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834759"
---
# <a name="configuring-discovery-in-a-configuration-file"></a><span data-ttu-id="06015-102">Configurando a descoberta em um arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="06015-102">Configuring Discovery in a Configuration File</span></span>
<span data-ttu-id="06015-103">Há quatro grupos principais de definições de configuração usadas na descoberta.</span><span class="sxs-lookup"><span data-stu-id="06015-103">There are four major groups of configuration settings used in discovery.</span></span> <span data-ttu-id="06015-104">Este tópico descreverá brevemente cada um e mostrará exemplos de como configurá-los.</span><span class="sxs-lookup"><span data-stu-id="06015-104">This topic will briefly describe each and show examples of how to configure them.</span></span> <span data-ttu-id="06015-105">Seguir cada seção será um link para uma documentação mais detalhada sobre cada área.</span><span class="sxs-lookup"><span data-stu-id="06015-105">Following each section will be a link to more in-depth documentation about each area.</span></span>  
  
## <a name="behavior-configuration"></a><span data-ttu-id="06015-106">Configuração de comportamento</span><span class="sxs-lookup"><span data-stu-id="06015-106">Behavior Configuration</span></span>  
 <span data-ttu-id="06015-107">A descoberta usa comportamentos de serviço e comportamentos de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="06015-107">Discovery uses service behaviors and endpoint behaviors.</span></span> <span data-ttu-id="06015-108">O comportamento <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> habilita a descoberta para todos os pontos de extremidade de um serviço e permite que você especifique pontos de extremidade de anúncio.</span><span class="sxs-lookup"><span data-stu-id="06015-108">The <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> behavior enables discovery for all of a service’s endpoints and allows you to specify announcement endpoints.</span></span>  <span data-ttu-id="06015-109">O exemplo a seguir mostra como adicionar o <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> e especificar um ponto de extremidade de anúncio.</span><span class="sxs-lookup"><span data-stu-id="06015-109">The following example shows how to add the <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> and specify an announcement endpoint.</span></span>  
  
```xml  
<behaviors>  
      <serviceBehaviors>  
        <behavior name="helloWorldServiceBehavior">  
          <serviceDiscovery>  
            <announcementEndpoints>  
              <endpoint kind="udpAnnouncementEndpoint"/>  
            </announcementEndpoints>  
          </serviceDiscovery>  
        </behavior>  
      </serviceBehaviors>  
```  
  
 <span data-ttu-id="06015-110">Depois de especificar o comportamento, referencie-o de um < `service` > elemento, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="06015-110">Once you specify the behavior, reference it from a <`service`> element as shown in the following sample.</span></span>  
  
```xml  
<system.serviceModel>  
   <services>  
      <service name="HelloWorldService" behaviorConfiguration="helloWorldServiceBehavior">  
         <!-- Application Endpoint -->  
         <endpoint address="endpoint0"  
                   binding="basicHttpBinding"  
                   contract="IHelloWorldService" />  
         <!-- Discovery Endpoints -->  
         <endpoint kind="udpDiscoveryEndpoint" />  
        </service>  
    </service>  
```  
  
 <span data-ttu-id="06015-111">Para que um serviço seja detectável, você também deve adicionar um ponto de extremidade de descoberta, o exemplo acima adiciona um ponto de extremidade padrão <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>.</span><span class="sxs-lookup"><span data-stu-id="06015-111">In order for a service to be discoverable, you must also add a discovery endpoint, the example above adds a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> standard endpoint.</span></span>  
  
 <span data-ttu-id="06015-112">Ao adicionar pontos de extremidade de comunicado, você também deve adicionar um serviço de ouvinte de comunicado ao elemento < `services` >, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="06015-112">When you add announcement endpoints you must also add an announcement listener service to the <`services`> element as shown in the following example.</span></span>  
  
```xml  
<services>  
   <service name="HelloWorldService" behaviorConfiguration="helloWorldServiceBehavior">  
      <!-- Application Endpoint -->  
      <endpoint address="endpoint0"  
                binding="basicHttpBinding"  
                contract="IHelloWorldService" />  
      <!-- Discovery Endpoints -->  
      <endpoint kind="udpDiscoveryEndpoint" />  
   </service>  
   <!-- Announcement Listener Configuration -->  
   <service name="AnnouncementListener">  
      <endpoint kind="udpAnnouncementEndpoint" />  
   </service>  
```  
  
 <span data-ttu-id="06015-113">O comportamento <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> é usado para habilitar ou desabilitar a descoberta de um ponto de extremidade específico.</span><span class="sxs-lookup"><span data-stu-id="06015-113">The <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> behavior is used to enable or disable discovery of a specific endpoint.</span></span>  <span data-ttu-id="06015-114">O exemplo a seguir configura um serviço com dois pontos de extremidade do aplicativo, um com a descoberta habilitada e outro com a descoberta desabilitada.</span><span class="sxs-lookup"><span data-stu-id="06015-114">The following example configures a service with two application endpoints, one with discovery enabled and one with discovery disabled.</span></span> <span data-ttu-id="06015-115">Para cada ponto de extremidade, um comportamento <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> é adicionado.</span><span class="sxs-lookup"><span data-stu-id="06015-115">For each endpoint an <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> behavior is added.</span></span>  
  
```xml  
<system.serviceModel>  
   <services>  
      <service name="HelloWorldService"  
               behaviorConfiguration="helloWorldServiceBehavior">  
  
        <!-- Application Endpoints -->  
        <endpoint address="endpoint0"  
                 binding="basicHttpBinding"  
                 contract="IHelloWorldService"   
                 behaviorConfiguration="ep0Behavior" />  
  
        <endpoint address="endpoint1"  
                  binding="basicHttpBinding"  
                  contract="IHelloWorldService"  
                  behaviorConfiguration="ep1Behavior" />  
  
        <!-- Discovery Endpoints -->  
        <endpoint kind="udpDiscoveryEndpoint" />  
      </service>  
   </services>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="helloWorldServiceBehavior">  
          <serviceDiscovery />  
        </behavior>  
      </serviceBehaviors>  
      <endpointBehaviors>  
        <behavior name="ep0Behavior">  
          <endpointDiscovery enabled="true"/>  
        </behavior>  
        <behavior name="ep1Behavior">  
          <endpointDiscovery enabled="false"/>  
        </behavior>  
     </endpointBehaviors>  
   </behaviors>  
```  
  
 <span data-ttu-id="06015-116">O comportamento <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> também pode ser usado para adicionar metadados personalizados aos metadados do ponto de extremidade retornados pelo serviço.</span><span class="sxs-lookup"><span data-stu-id="06015-116">The <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> behavior can also be used to add custom metadata to the endpoint metadata returned by the service.</span></span> <span data-ttu-id="06015-117">O exemplo a seguir mostra como fazer isso.</span><span class="sxs-lookup"><span data-stu-id="06015-117">The following example shows how to do this.</span></span>  
  
```xml  
<behavior name="ep4Behavior">  
   <endpointDiscovery enabled="true">  
      <extensions>  
         <CustomMetadata>This is custom metadata.</CustomMetadata>  
         <d:Types xmlns:d="http://schemas.xmlsoap.org/ws/2005/04/discovery" xmlns:i="http://printer.example.org/2003/imaging">i:PrintBasic</d:Types>  
         <CustomMetadata netsted="true">  
            <NestedMetadata>This is a nested custom metadata.</NestedMetadata>  
         </CustomMetadata>  
      </extensions>  
   </endpointDiscovery>  
</behavior>  
```  
  
 <span data-ttu-id="06015-118">O comportamento <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> também pode ser usado para adicionar escopos e tipos que os clientes usam para procurar serviços.</span><span class="sxs-lookup"><span data-stu-id="06015-118">The <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> behavior can also be used to add scopes and types that clients use to search for services.</span></span> <span data-ttu-id="06015-119">O exemplo a seguir mostra como fazer isso em um arquivo de configuração do lado do cliente.</span><span class="sxs-lookup"><span data-stu-id="06015-119">The following example shows how to do this in a client side configuration file.</span></span>  
  
```xml  
<behavior name="ep2Behavior">  
   <endpointDiscovery enabled="true">  
      <scopes>  
         <add scope="http://www.microsoft.com/building42/floor1"/>  
         <add scope="ldap:///ou=engineeringo=examplecomc=us"/>  
      </scopes>  
      <types>  
         <add name="test" namespace="http://example.microsoft.com/" />  
         <add name="additionalContract" namespace="http://example.microsoft.com/" />  
      </types>  
   </endpointDiscovery>  
</behavior>  
```  
  
 <span data-ttu-id="06015-120">Para obter mais informações sobre <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> e <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>, consulte [visão geral da descoberta do WCF](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md).</span><span class="sxs-lookup"><span data-stu-id="06015-120">For more information about <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> and <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> see [WCF Discovery Overview](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md).</span></span>  
  
## <a name="binding-element-configuration"></a><span data-ttu-id="06015-121">Configuração do elemento de associação</span><span class="sxs-lookup"><span data-stu-id="06015-121">Binding Element Configuration</span></span>  
 <span data-ttu-id="06015-122">A configuração do elemento de associação é mais interessante no lado do cliente.</span><span class="sxs-lookup"><span data-stu-id="06015-122">Binding element configuration is most interesting on the client side.</span></span> <span data-ttu-id="06015-123">Você pode usar a configuração para especificar os critérios de localização usados para descobrir serviços de um aplicativo cliente WCF.</span><span class="sxs-lookup"><span data-stu-id="06015-123">You can use configuration to specify the find criteria used to discover services from a WCF client application.</span></span>  <span data-ttu-id="06015-124">O exemplo a seguir cria uma associação personalizada com o canal <xref:System.ServiceModel.Discovery.DiscoveryClient> e especifica os critérios de localização que incluem um tipo e um escopo.</span><span class="sxs-lookup"><span data-stu-id="06015-124">The following example creates a custom binding with the <xref:System.ServiceModel.Discovery.DiscoveryClient> channel and specifies find criteria that includes a type and scope.</span></span> <span data-ttu-id="06015-125">Além disso, ele especifica valores para as propriedades <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> e <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A>.</span><span class="sxs-lookup"><span data-stu-id="06015-125">In addition it specifies values for the <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> and <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> properties.</span></span>  
  
```xml  
<bindings>  
   <customBinding>  
      <!-- Binding Configuration for the Application Endpoint -->  
      <binding name="discoBindingConfiguration">  
         <discoveryClient>  
            <endpoint kind="discoveryEndpoint"  
                      address="http://localhost:8000/ConfigTest/Discovery"  
                      binding="customBinding"  
                      bindingConfiguration="httpSoap12WSAddressing10"/>  
            <findCriteria duration="00:00:10" maxResults="2">  
              <types>  
                <add name="IHelloWorldService"/>  
              </types>  
              <scopes>  
                <add scope="http://www.microsoft.com/building42/floor1"/>  
              </scopes>              
            </findCriteria>  
          </discoveryClient>  
          <textMessageEncoding messageVersion="Soap11"/>  
          <httpTransport />  
        </binding>  
```  
  
 <span data-ttu-id="06015-126">Essa configuração de associação personalizada deve ser referenciada por um ponto de extremidade do cliente:</span><span class="sxs-lookup"><span data-stu-id="06015-126">This custom binding configuration must be referenced by a client endpoint:</span></span>  
  
```xml  
<client>  
      <endpoint address="http://schemas.microsoft.com/discovery/dynamic"  
                binding="customBinding"  
                bindingConfiguration="discoBindingConfiguration"  
                contract="IHelloWorldService" />  
    </client>  
```  
  
 <span data-ttu-id="06015-127">Para obter mais informações sobre critérios de localização [, consulte descoberta e FindCriteria](../../../../docs/framework/wcf/feature-details/discovery-find-and-findcriteria.md).</span><span class="sxs-lookup"><span data-stu-id="06015-127">For more information about find criteria see [Discovery Find and FindCriteria](../../../../docs/framework/wcf/feature-details/discovery-find-and-findcriteria.md).</span></span> <span data-ttu-id="06015-128">Para obter mais informações sobre elementos de associação e descoberta, consulte [visão geral da descoberta do WCF](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)</span><span class="sxs-lookup"><span data-stu-id="06015-128">For more information about discovery and binding elements see, [WCF Discovery Overview](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)</span></span>  
  
## <a name="standard-endpoint-configuration"></a><span data-ttu-id="06015-129">Configuração de ponto de extremidade padrão</span><span class="sxs-lookup"><span data-stu-id="06015-129">Standard Endpoint Configuration</span></span>  
 <span data-ttu-id="06015-130">Os pontos de extremidade padrão são pontos de extremidade predefinidos que têm valores padrão para uma ou mais Propriedades (endereço, associação ou contrato) ou um ou mais valores de propriedade que não podem ser alterados.</span><span class="sxs-lookup"><span data-stu-id="06015-130">Standard endpoints are predefined endpoints that have default values for one or more properties (address, binding, or contract) or one or more property values that cannot change.</span></span> <span data-ttu-id="06015-131">O .NET 4 é fornecido com 3 pontos de extremidade padrão relacionados à descoberta: <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> e <xref:System.ServiceModel.Discovery.DynamicEndpoint>.</span><span class="sxs-lookup"><span data-stu-id="06015-131">.NET 4 ships with 3 discovery related standard endpoints: <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>, and <xref:System.ServiceModel.Discovery.DynamicEndpoint>.</span></span>  <span data-ttu-id="06015-132">O <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> é um ponto de extremidade padrão pré-configurado para operações de descoberta em uma associação de multicast UDP.</span><span class="sxs-lookup"><span data-stu-id="06015-132">The <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> is a standard endpoint that is pre-configured for discovery operations over a UDP multicast binding.</span></span> <span data-ttu-id="06015-133">O <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> é um ponto de extremidade padrão que é pré-configurado para enviar mensagens de anúncio por uma associação UDP.</span><span class="sxs-lookup"><span data-stu-id="06015-133">The <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> is a standard endpoint that is pre-configured to send announcement messages over a UDP binding.</span></span> <span data-ttu-id="06015-134">O <xref:System.ServiceModel.Discovery.DynamicEndpoint> é um ponto de extremidade padrão que usa a descoberta para localizar o endereço do ponto de extremidade de um serviço descoberto dinamicamente em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="06015-134">The <xref:System.ServiceModel.Discovery.DynamicEndpoint> is a standard endpoint that uses discovery to find the endpoint address of a discovered service dynamically at runtime.</span></span>  <span data-ttu-id="06015-135">As associações padrão são especificadas com um elemento < `endpoint` > que contém o atributo Kind que especificou o tipo de ponto de extremidade padrão a ser adicionado.</span><span class="sxs-lookup"><span data-stu-id="06015-135">Standard bindings are specified with an <`endpoint`> element that contains kind attribute that specified the type of standard endpoint to add.</span></span> <span data-ttu-id="06015-136">O exemplo a seguir mostra como adicionar um <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> e um <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>.</span><span class="sxs-lookup"><span data-stu-id="06015-136">The following example shows how to add a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> and a <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>.</span></span>  
  
```xml  
<services>  
   <service name="HelloWorldService">  
      <!-- ...  -->          
      <endpoint kind="udpDiscoveryEndpoint" />  
   </service>  
   <service name="AnnouncementListener">  
      <endpoint kind="udpAnnouncementEndpoint" />  
   </service>  
</services>  
```  
  
 <span data-ttu-id="06015-137">Os pontos de extremidade padrão são configurados em um elemento < `standardEndpoints` >.</span><span class="sxs-lookup"><span data-stu-id="06015-137">Standard endpoints are configured in a <`standardEndpoints`> element.</span></span> <span data-ttu-id="06015-138">O exemplo a seguir mostra como configurar o <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> e o <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>.</span><span class="sxs-lookup"><span data-stu-id="06015-138">The following example shows how to configure the <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> and the <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>.</span></span>  
  
```xml  
<standardEndpoints>  
      <udpAnnouncementEndpoint>  
        <standardEndpoint   
            name="udpAnnouncementEndpointSettings"   
            multicastAddress="soap.udp://239.255.255.250:3703"    
            maxAnnouncementDelay="00:00:00.800">  
          <transportSettings  
            duplicateMessageHistoryLength="1028"  
            maxPendingMessageCount="10"  
            maxMulticastRetransmitCount="3"  
            maxUnicastRetransmitCount="2"  
            socketReceiveBufferSize="131072"  
            timeToLive="2" />  
        </standardEndpoint>  
      </udpAnnouncementEndpoint>  
      <udpDiscoveryEndpoint>  
        <standardEndpoint  
            name="udpDiscoveryEndpointSettings"  
            multicastAddress="soap.udp://239.255.255.252:3704"  
            maxResponseDelay="00:00:00.800">  
          <transportSettings  
            duplicateMessageHistoryLength="2048"  
            maxPendingMessageCount="5"  
            maxReceivedMessageSize="8192"  
            maxBufferPoolSize="262144"/>  
        </standardEndpoint>  
      </udpDiscoveryEndpoint>  
```  
  
 <span data-ttu-id="06015-139">Depois de adicionar a configuração de ponto de extremidade padrão, faça referência à configuração no elemento < `endpoint` > para cada ponto de extremidade, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="06015-139">Once you’ve added the standard endpoint configuration, reference the configuration in the <`endpoint`> element for each endpoint as shown in the following sample.</span></span>  
  
```xml  
<services>  
   <service name="HelloWorldService">  
      <!-- ...  -->          
      <endpoint kind="udpDiscoveryEndpoint" endpointConfiguration="udpDiscoveryEndpointSettings"/>  
   </service>  
   <service name="AnnouncementListener">  
      <endpoint kind="udpAnnouncementEndpoint" endpointConfiguration="udpAnnouncementEndpointSettings" >  
   </service>  
</services>  
```  
  
 <span data-ttu-id="06015-140">Ao contrário dos outros pontos de extremidade padrão usados na descoberta, você especifica uma associação e um contrato para <xref:System.ServiceModel.Discovery.DynamicEndpoint>.</span><span class="sxs-lookup"><span data-stu-id="06015-140">Unlike the other standard endpoints used in discovery, you specify a binding and contract for <xref:System.ServiceModel.Discovery.DynamicEndpoint>.</span></span> <span data-ttu-id="06015-141">O exemplo a seguir mostra como adicionar e configurar um <xref:System.ServiceModel.Discovery.DynamicEndpoint>.</span><span class="sxs-lookup"><span data-stu-id="06015-141">The following example shows how to add and configure a <xref:System.ServiceModel.Discovery.DynamicEndpoint>.</span></span>  
  
```xml  
<system.serviceModel>  
    <client>  
      <endpoint kind="dynamicEndpoint" binding="basicHttpBinding" contract="IHelloWorldService" endpointConfiguration="dynamicEndpointConfiguration" />  
    </client>   
   <standardEndpoints>  
      <dynamicEndpoint>  
         <standardEndpoint name="dynamicEndpointConfiguration">  
             <discoveryClientSettings>  
              <findCriteria scopeMatchBy="http://schemas.microsoft.com/ws/2008/06/discovery/rfc" duration="00:00:10" maxResults="2">  
                 <types>  
                   <add name="IHelloWorldService"/>  
                 </types>  
                 <scopes>  
                   <add scope="http://www.microsoft.com/building42/floor1"/>  
                 </scopes>  
                 <extensions>  
                   <CustomMetadata>This is custom metadata.</CustomMetadata>          
                 </extensions>  
               </findCriteria>  
             </discoveryClientSettings>  
           </standardEndpoint>  
         </dynamicEndpoint>  
   </standardEndpoints>  
</system.ServiceModel>  
```  
  
 <span data-ttu-id="06015-142">Para obter mais informações sobre pontos de extremidade padrão, consulte [pontos de extremidade padrão](standard-endpoints.md).</span><span class="sxs-lookup"><span data-stu-id="06015-142">For more information about standard endpoints see [Standard Endpoints](standard-endpoints.md).</span></span>
