---
title: Configurando a descoberta em um arquivo de configuração
ms.date: 03/30/2017
ms.assetid: b9884c11-8011-4763-bc2c-c526b80175d0
ms.openlocfilehash: 934b04b51b9954cf943f57f33250951048e5671b
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81464213"
---
# <a name="configuring-discovery-in-a-configuration-file"></a>Configurando a descoberta em um arquivo de configuração
Existem quatro grandes grupos de configurações usadas na descoberta. Este tópico descreverá brevemente cada um e mostrará exemplos de como configurá-los. Na sequência de cada seção haverá um link para uma documentação mais detalhada sobre cada área.  
  
## <a name="behavior-configuration"></a>Configuração de comportamento  
 A Discovery usa comportamentos de serviço e comportamentos de ponto final. O <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> comportamento permite a descoberta de todos os pontos finais de um serviço e permite especificar pontos finais de anúncio.  O exemplo a seguir <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> mostra como adicionar e especificar um ponto final de anúncio.  
  
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
</behaviors>  
```  
  
 Depois de especificar o comportamento, `service` faça referência a um elemento> <, conforme mostrado na amostra a seguir.  
  
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
    </services>  
</system.serviceModel>  
```  
  
 Para que um serviço seja descoberto, você também deve adicionar um ponto <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> final de descoberta, o exemplo acima adiciona um ponto final padrão.  
  
 Ao adicionar pontos finais de anúncio, você também deve `services` adicionar um serviço de ouvinte de anúncio ao elemento> <como mostrado no exemplo a seguir.  
  
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
</services>
```  
  
 O <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> comportamento é usado para ativar ou desativar a descoberta de um ponto final específico.  O exemplo a seguir configura um serviço com dois pontos finais de aplicativo, um com a detecção ativada e outro com a detecção desativada. Para cada ponto <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> final é adicionado um comportamento.  
  
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
</system.serviceModel>  
```  
  
 O <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> comportamento também pode ser usado para adicionar metadados personalizados aos metadados de ponto final retornados pelo serviço. O exemplo a seguir mostra como fazer isso.  
  
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
  
 O <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> comportamento também pode ser usado para adicionar escopos e tipos que os clientes usam para procurar serviços. O exemplo a seguir mostra como fazer isso em um arquivo de configuração do lado do cliente.  
  
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
  
 Para obter <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> mais <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> informações e consulte [o WCF Discovery Overview](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md).  
  
## <a name="binding-element-configuration"></a>Configuração do elemento de vinculação  
 A configuração do elemento de ligação é mais interessante no lado do cliente. Você pode usar a configuração para especificar os critérios de encontrar usados para descobrir serviços a partir de um aplicativo cliente WCF.  O exemplo a seguir cria <xref:System.ServiceModel.Discovery.DiscoveryClient> uma vinculação personalizada com o canal e especifica critérios de encontrar que incluam um tipo e escopo. Além disso, especifica valores para as <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> propriedades. <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A>  
  
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
   </customBinding>
</bindings>  
```  
  
 Esta configuração de vinculação personalizada deve ser referenciada por um ponto final do cliente:  
  
```xml  
<client>  
      <endpoint address="http://schemas.microsoft.com/discovery/dynamic"  
                binding="customBinding"  
                bindingConfiguration="discoBindingConfiguration"  
                contract="IHelloWorldService" />  
</client>  
```  
  
 Para obter mais informações sobre os critérios de encontrar, consulte [Discovery Find e FindCriteria](../../../../docs/framework/wcf/feature-details/discovery-find-and-findcriteria.md). Para obter mais informações sobre elementos de descoberta e vinculação, consulte o [WCF Discovery Overview](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)  
  
## <a name="standard-endpoint-configuration"></a>Configuração padrão do ponto final  
 Os pontos finais padrão são pontos finais predefinidos que têm valores padrão para uma ou mais propriedades (endereço, vinculação ou contrato) ou um ou mais valores de propriedade que não podem ser alterar. .NET 4 navios com 3 <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>pontos <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>finais <xref:System.ServiceModel.Discovery.DynamicEndpoint>padrão relacionados à descoberta: , e .  O <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> é um ponto final padrão pré-configurado para operações de detecção sobre uma vinculação multicast UDP. O <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> é um ponto final padrão que está pré-configurado para enviar mensagens de anúncio por uma vinculação UDP. O <xref:System.ServiceModel.Discovery.DynamicEndpoint> é um ponto final padrão que usa a descoberta para encontrar o endereço de ponto final de um serviço descoberto dinamicamente em tempo de execução.  As vinculações padrão são `endpoint` especificadas com um elemento> <que contém atributo tipo que especificava o tipo de ponto final padrão a ser adicionado. O exemplo a seguir <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> mostra <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>como adicionar a e a .  
  
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
  
 Os pontos finais padrão são `standardEndpoints` configurados em um elemento> <. O exemplo a seguir mostra <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> como <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>configurar o e o .  
  
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
</standardEndpoints>
```  
  
 Depois de adicionar a configuração padrão do ponto `endpoint` final, consulte a configuração no elemento <> para cada ponto final, conforme mostrado na amostra a seguir.  
  
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
  
 Ao contrário dos outros pontos finais padrão usados <xref:System.ServiceModel.Discovery.DynamicEndpoint>na descoberta, você especifica uma vinculação e contrato para . O exemplo a seguir mostra como <xref:System.ServiceModel.Discovery.DynamicEndpoint>adicionar e configurar um .  
  
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
  
 Para obter mais informações sobre pontos finais padrão, consulte [Standard Endpoints](standard-endpoints.md).
