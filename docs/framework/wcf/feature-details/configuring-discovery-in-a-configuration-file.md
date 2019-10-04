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
# <a name="configuring-discovery-in-a-configuration-file"></a>Configurando a descoberta em um arquivo de configuração
Há quatro grupos principais de definições de configuração usadas na descoberta. Este tópico descreverá brevemente cada um e mostrará exemplos de como configurá-los. Seguir cada seção será um link para uma documentação mais detalhada sobre cada área.  
  
## <a name="behavior-configuration"></a>Configuração de comportamento  
 A descoberta usa comportamentos de serviço e comportamentos de ponto de extremidade. O comportamento <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> habilita a descoberta para todos os pontos de extremidade de um serviço e permite que você especifique pontos de extremidade de anúncio.  O exemplo a seguir mostra como adicionar o <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> e especificar um ponto de extremidade de anúncio.  
  
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
  
 Depois de especificar o comportamento, referencie-o de um < `service` > elemento, conforme mostrado no exemplo a seguir.  
  
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
  
 Para que um serviço seja detectável, você também deve adicionar um ponto de extremidade de descoberta, o exemplo acima adiciona um ponto de extremidade padrão <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>.  
  
 Ao adicionar pontos de extremidade de comunicado, você também deve adicionar um serviço de ouvinte de comunicado ao elemento < `services` >, conforme mostrado no exemplo a seguir.  
  
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
  
 O comportamento <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> é usado para habilitar ou desabilitar a descoberta de um ponto de extremidade específico.  O exemplo a seguir configura um serviço com dois pontos de extremidade do aplicativo, um com a descoberta habilitada e outro com a descoberta desabilitada. Para cada ponto de extremidade, um comportamento <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> é adicionado.  
  
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
  
 O comportamento <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> também pode ser usado para adicionar metadados personalizados aos metadados do ponto de extremidade retornados pelo serviço. O exemplo a seguir mostra como fazer isso.  
  
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
  
 O comportamento <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> também pode ser usado para adicionar escopos e tipos que os clientes usam para procurar serviços. O exemplo a seguir mostra como fazer isso em um arquivo de configuração do lado do cliente.  
  
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
  
 Para obter mais informações sobre <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> e <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>, consulte [visão geral da descoberta do WCF](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md).  
  
## <a name="binding-element-configuration"></a>Configuração do elemento de associação  
 A configuração do elemento de associação é mais interessante no lado do cliente. Você pode usar a configuração para especificar os critérios de localização usados para descobrir serviços de um aplicativo cliente WCF.  O exemplo a seguir cria uma associação personalizada com o canal <xref:System.ServiceModel.Discovery.DiscoveryClient> e especifica os critérios de localização que incluem um tipo e um escopo. Além disso, ele especifica valores para as propriedades <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> e <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A>.  
  
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
  
 Essa configuração de associação personalizada deve ser referenciada por um ponto de extremidade do cliente:  
  
```xml  
<client>  
      <endpoint address="http://schemas.microsoft.com/discovery/dynamic"  
                binding="customBinding"  
                bindingConfiguration="discoBindingConfiguration"  
                contract="IHelloWorldService" />  
    </client>  
```  
  
 Para obter mais informações sobre critérios de localização [, consulte descoberta e FindCriteria](../../../../docs/framework/wcf/feature-details/discovery-find-and-findcriteria.md). Para obter mais informações sobre elementos de associação e descoberta, consulte [visão geral da descoberta do WCF](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)  
  
## <a name="standard-endpoint-configuration"></a>Configuração de ponto de extremidade padrão  
 Os pontos de extremidade padrão são pontos de extremidade predefinidos que têm valores padrão para uma ou mais Propriedades (endereço, associação ou contrato) ou um ou mais valores de propriedade que não podem ser alterados. O .NET 4 é fornecido com 3 pontos de extremidade padrão relacionados à descoberta: <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> e <xref:System.ServiceModel.Discovery.DynamicEndpoint>.  O <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> é um ponto de extremidade padrão pré-configurado para operações de descoberta em uma associação de multicast UDP. O <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> é um ponto de extremidade padrão que é pré-configurado para enviar mensagens de anúncio por uma associação UDP. O <xref:System.ServiceModel.Discovery.DynamicEndpoint> é um ponto de extremidade padrão que usa a descoberta para localizar o endereço do ponto de extremidade de um serviço descoberto dinamicamente em tempo de execução.  As associações padrão são especificadas com um elemento < `endpoint` > que contém o atributo Kind que especificou o tipo de ponto de extremidade padrão a ser adicionado. O exemplo a seguir mostra como adicionar um <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> e um <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>.  
  
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
  
 Os pontos de extremidade padrão são configurados em um elemento < `standardEndpoints` >. O exemplo a seguir mostra como configurar o <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> e o <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>.  
  
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
  
 Depois de adicionar a configuração de ponto de extremidade padrão, faça referência à configuração no elemento < `endpoint` > para cada ponto de extremidade, conforme mostrado no exemplo a seguir.  
  
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
  
 Ao contrário dos outros pontos de extremidade padrão usados na descoberta, você especifica uma associação e um contrato para <xref:System.ServiceModel.Discovery.DynamicEndpoint>. O exemplo a seguir mostra como adicionar e configurar um <xref:System.ServiceModel.Discovery.DynamicEndpoint>.  
  
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
  
 Para obter mais informações sobre pontos de extremidade padrão, consulte [pontos de extremidade padrão](standard-endpoints.md).
