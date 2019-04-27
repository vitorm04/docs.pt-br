---
title: Configurando a descoberta em um arquivo de configuração
ms.date: 03/30/2017
ms.assetid: b9884c11-8011-4763-bc2c-c526b80175d0
ms.openlocfilehash: c282767e686ac8a6382268aee8b45eb2d1297f5a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61857513"
---
# <a name="configuring-discovery-in-a-configuration-file"></a><span data-ttu-id="6d902-102">Configurando a descoberta em um arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="6d902-102">Configuring Discovery in a Configuration File</span></span>
<span data-ttu-id="6d902-103">Há quatro grupos principais de definições de configuração usados na descoberta.</span><span class="sxs-lookup"><span data-stu-id="6d902-103">There are four major groups of configuration settings used in discovery.</span></span> <span data-ttu-id="6d902-104">Este tópico será brevemente descrevem cada e mostram exemplos de como configurá-los.</span><span class="sxs-lookup"><span data-stu-id="6d902-104">This topic will briefly describe each and show examples of how to configure them.</span></span> <span data-ttu-id="6d902-105">Cada seção a seguir será um link para obter mais documentação detalhada sobre cada área.</span><span class="sxs-lookup"><span data-stu-id="6d902-105">Following each section will be a link to more in-depth documentation about each area.</span></span>  
  
## <a name="behavior-configuration"></a><span data-ttu-id="6d902-106">Configuração de comportamento</span><span class="sxs-lookup"><span data-stu-id="6d902-106">Behavior Configuration</span></span>  
 <span data-ttu-id="6d902-107">A descoberta usa comportamentos de serviço e comportamentos de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="6d902-107">Discovery uses service behaviors and endpoint behaviors.</span></span> <span data-ttu-id="6d902-108">O <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> comportamento permite a descoberta para todos os pontos de extremidade do serviço e permite que você especifique os pontos de extremidade de comunicado.</span><span class="sxs-lookup"><span data-stu-id="6d902-108">The <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> behavior enables discovery for all of a service’s endpoints and allows you to specify announcement endpoints.</span></span>  <span data-ttu-id="6d902-109">O exemplo a seguir mostra como adicionar o <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> e especifique um ponto de extremidade de comunicado.</span><span class="sxs-lookup"><span data-stu-id="6d902-109">The following example shows how to add the <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> and specify an announcement endpoint.</span></span>  
  
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
  
 <span data-ttu-id="6d902-110">Depois de especificar o comportamento, referenciá-lo de um <`service`> elemento, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="6d902-110">Once you specify the behavior, reference it from a <`service`> element as shown in the following sample.</span></span>  
  
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
  
 <span data-ttu-id="6d902-111">Em ordem para um serviço seja detectável, você também deve adicionar um ponto de extremidade de descoberta, o exemplo acima adiciona um <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> ponto de extremidade padrão.</span><span class="sxs-lookup"><span data-stu-id="6d902-111">In order for a service to be discoverable, you must also add a discovery endpoint, the example above adds a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> standard endpoint.</span></span>  
  
 <span data-ttu-id="6d902-112">Quando você adiciona pontos de extremidade de comunicado, você também deve adicionar um serviço de escuta de comunicado para o <`services`> elemento, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="6d902-112">When you add announcement endpoints you must also add an announcement listener service to the <`services`> element as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="6d902-113">O <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> comportamento é usado para habilitar ou desabilitar a descoberta de um ponto de extremidade específico.</span><span class="sxs-lookup"><span data-stu-id="6d902-113">The <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> behavior is used to enable or disable discovery of a specific endpoint.</span></span>  <span data-ttu-id="6d902-114">O exemplo a seguir configura um serviço com dois pontos de extremidade do aplicativo, uma com a descoberta habilitada e outra com a descoberta desabilitada.</span><span class="sxs-lookup"><span data-stu-id="6d902-114">The following example configures a service with two application endpoints, one with discovery enabled and one with discovery disabled.</span></span> <span data-ttu-id="6d902-115">Para cada ponto de extremidade uma <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> comportamento é adicionado.</span><span class="sxs-lookup"><span data-stu-id="6d902-115">For each endpoint an <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> behavior is added.</span></span>  
  
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
  
 <span data-ttu-id="6d902-116">O <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> comportamento também pode ser usado para adicionar metadados personalizados para os metadados do ponto de extremidade retornado pelo serviço.</span><span class="sxs-lookup"><span data-stu-id="6d902-116">The <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> behavior can also be used to add custom metadata to the endpoint metadata returned by the service.</span></span> <span data-ttu-id="6d902-117">O exemplo a seguir mostra como fazer isso.</span><span class="sxs-lookup"><span data-stu-id="6d902-117">The following example shows how to do this.</span></span>  
  
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
  
 <span data-ttu-id="6d902-118">O <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> comportamento também pode ser usado para adicionar escopos e tipos que os clientes usam para pesquisar para serviços.</span><span class="sxs-lookup"><span data-stu-id="6d902-118">The <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> behavior can also be used to add scopes and types that clients use to search for services.</span></span> <span data-ttu-id="6d902-119">O exemplo a seguir mostra como fazer isso em um arquivo de configuração do lado cliente.</span><span class="sxs-lookup"><span data-stu-id="6d902-119">The following example shows how to do this in a client side configuration file.</span></span>  
  
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
  
 <span data-ttu-id="6d902-120">Para obter mais informações sobre <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> e <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> consulte [visão geral de descoberta do WCF](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md).</span><span class="sxs-lookup"><span data-stu-id="6d902-120">For more information about <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> and <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> see [WCF Discovery Overview](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md).</span></span>  
  
## <a name="binding-element-configuration"></a><span data-ttu-id="6d902-121">Configuração do elemento de associação</span><span class="sxs-lookup"><span data-stu-id="6d902-121">Binding Element Configuration</span></span>  
 <span data-ttu-id="6d902-122">Configuração do elemento de associação é mais interessante no lado do cliente.</span><span class="sxs-lookup"><span data-stu-id="6d902-122">Binding element configuration is most interesting on the client side.</span></span> <span data-ttu-id="6d902-123">Você pode usar a configuração para especificar os critérios de localização usados para descobrir os serviços de um aplicativo de cliente do WCF.</span><span class="sxs-lookup"><span data-stu-id="6d902-123">You can use configuration to specify the find criteria used to discover services from a WCF client application.</span></span>  <span data-ttu-id="6d902-124">O exemplo a seguir cria uma associação personalizada com o <xref:System.ServiceModel.Discovery.DiscoveryClient> de canal e especifica os critérios de localização que inclui um tipo e escopo.</span><span class="sxs-lookup"><span data-stu-id="6d902-124">The following example creates a custom binding with the <xref:System.ServiceModel.Discovery.DiscoveryClient> channel and specifies find criteria that includes a type and scope.</span></span> <span data-ttu-id="6d902-125">Além dele especifica valores para o <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> e <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> propriedades.</span><span class="sxs-lookup"><span data-stu-id="6d902-125">In addition it specifies values for the <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> and <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> properties.</span></span>  
  
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
  
 <span data-ttu-id="6d902-126">Essa configuração de associação personalizado deve ser referenciada por um ponto de extremidade do cliente:</span><span class="sxs-lookup"><span data-stu-id="6d902-126">This custom binding configuration must be referenced by a client endpoint:</span></span>  
  
```xml  
<client>  
      <endpoint address="http://schemas.microsoft.com/discovery/dynamic"  
                binding="customBinding"  
                bindingConfiguration="discoBindingConfiguration"  
                contract="IHelloWorldService" />  
    </client>  
```  
  
 <span data-ttu-id="6d902-127">Para obter mais informações sobre critérios de localização, consulte [FindCriteria e descoberta localizar](../../../../docs/framework/wcf/feature-details/discovery-find-and-findcriteria.md).</span><span class="sxs-lookup"><span data-stu-id="6d902-127">For more information about find criteria see [Discovery Find and FindCriteria](../../../../docs/framework/wcf/feature-details/discovery-find-and-findcriteria.md).</span></span> <span data-ttu-id="6d902-128">Para obter mais informações sobre a descoberta e elementos de associação, consulte [visão geral de descoberta do WCF](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)</span><span class="sxs-lookup"><span data-stu-id="6d902-128">For more information about discovery and binding elements see, [WCF Discovery Overview](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)</span></span>  
  
## <a name="standard-endpoint-configuration"></a><span data-ttu-id="6d902-129">Configuração de ponto de extremidade padrão</span><span class="sxs-lookup"><span data-stu-id="6d902-129">Standard Endpoint Configuration</span></span>  
 <span data-ttu-id="6d902-130">Pontos de extremidade padrão são pontos de extremidade predefinidos que têm valores padrão para uma ou mais propriedades (endereço, associação ou contrato) ou um ou mais valores de propriedade que não podem alterar.</span><span class="sxs-lookup"><span data-stu-id="6d902-130">Standard endpoints are predefined endpoints that have default values for one or more properties (address, binding, or contract) or one or more property values that cannot change.</span></span> <span data-ttu-id="6d902-131">Acompanha o .NET 4 3 descoberta relacionadas a pontos de extremidade padrão: <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>, e <xref:System.ServiceModel.Discovery.DynamicEndpoint>.</span><span class="sxs-lookup"><span data-stu-id="6d902-131">.NET 4 ships with 3 discovery related standard endpoints: <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>, and <xref:System.ServiceModel.Discovery.DynamicEndpoint>.</span></span>  <span data-ttu-id="6d902-132">O <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> está se associando um ponto de extremidade padrão que é pré-configurado para operações de descoberta por meio de um multicast UDP.</span><span class="sxs-lookup"><span data-stu-id="6d902-132">The <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> is a standard endpoint that is pre-configured for discovery operations over a UDP multicast binding.</span></span> <span data-ttu-id="6d902-133">O <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> é um ponto de extremidade padrão que é pré-configurado para enviar mensagens de comunicado por uma associação de UDP.</span><span class="sxs-lookup"><span data-stu-id="6d902-133">The <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> is a standard endpoint that is pre-configured to send announcement messages over a UDP binding.</span></span> <span data-ttu-id="6d902-134">O <xref:System.ServiceModel.Discovery.DynamicEndpoint> é um ponto de extremidade padrão que usa a descoberta para localizar o endereço de ponto de extremidade de um serviço descoberto dinamicamente em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="6d902-134">The <xref:System.ServiceModel.Discovery.DynamicEndpoint> is a standard endpoint that uses discovery to find the endpoint address of a discovered service dynamically at runtime.</span></span>  <span data-ttu-id="6d902-135">Associações padrão são especificadas com um <`endpoint`> elemento que contém o atributo do tipo que especificou o tipo de ponto de extremidade padrão para adicionar.</span><span class="sxs-lookup"><span data-stu-id="6d902-135">Standard bindings are specified with an <`endpoint`> element that contains kind attribute that specified the type of standard endpoint to add.</span></span> <span data-ttu-id="6d902-136">O exemplo a seguir mostra como adicionar um <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> e um <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>.</span><span class="sxs-lookup"><span data-stu-id="6d902-136">The following example shows how to add a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> and a <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>.</span></span>  
  
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
  
 <span data-ttu-id="6d902-137">Pontos de extremidade padrão são configurados em um <`standardEndpoints`> elemento.</span><span class="sxs-lookup"><span data-stu-id="6d902-137">Standard endpoints are configured in a <`standardEndpoints`> element.</span></span> <span data-ttu-id="6d902-138">O exemplo a seguir mostra como configurar o <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> e o <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>.</span><span class="sxs-lookup"><span data-stu-id="6d902-138">The following example shows how to configure the <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> and the <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>.</span></span>  
  
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
  
 <span data-ttu-id="6d902-139">Depois de adicionar a configuração de ponto de extremidade padrão, a configuração de referência a <`endpoint`> elemento para cada ponto de extremidade, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="6d902-139">Once you’ve added the standard endpoint configuration, reference the configuration in the <`endpoint`> element for each endpoint as shown in the following sample.</span></span>  
  
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
  
 <span data-ttu-id="6d902-140">Ao contrário de outros pontos de extremidade padrão usados na descoberta, você pode especificar uma associação e contrato para <xref:System.ServiceModel.Discovery.DynamicEndpoint>.</span><span class="sxs-lookup"><span data-stu-id="6d902-140">Unlike the other standard endpoints used in discovery, you specify a binding and contract for <xref:System.ServiceModel.Discovery.DynamicEndpoint>.</span></span> <span data-ttu-id="6d902-141">O exemplo a seguir mostra como adicionar e configurar um <xref:System.ServiceModel.Discovery.DynamicEndpoint>.</span><span class="sxs-lookup"><span data-stu-id="6d902-141">The following example shows how to add and configure a <xref:System.ServiceModel.Discovery.DynamicEndpoint>.</span></span>  
  
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
  
 <span data-ttu-id="6d902-142">Para obter mais informações sobre pontos de extremidade padrão consulte [pontos de extremidade padrão](../../../../docs/framework/wcf/feature-details/standard-endpoints.md)</span><span class="sxs-lookup"><span data-stu-id="6d902-142">For more information about standard endpoints see [Standard Endpoints](../../../../docs/framework/wcf/feature-details/standard-endpoints.md)</span></span>
