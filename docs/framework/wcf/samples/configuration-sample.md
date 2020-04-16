---
title: Exemplo de configuração
ms.date: 03/30/2017
ms.assetid: 75515b4a-8d70-44c8-99e0-7423df41380e
ms.openlocfilehash: 52747e6d964022d5028b0edb91dc8bc0ac0e82bc
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463964"
---
# <a name="configuration-sample"></a>Exemplo de configuração
Esta amostra demonstra o uso de um arquivo de configuração para tornar um serviço desvendado.  
  
> [!NOTE]
> Esta amostra implementa a descoberta na configuração. Para obter uma amostra que implemente a descoberta em código, consulte [Basic](../../../../docs/framework/wcf/samples/basic-sample.md).  
  
> [!IMPORTANT]
> Os exemplos podem mais ser instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation). Este exemplo está localizado no seguinte diretório.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\Configuration`  
  
## <a name="service-configuration"></a>Configuração de Serviço  
 O arquivo de configuração nesta amostra demonstra dois recursos:  
  
- Tornando o serviço descubro acima de um padrão. <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>  
  
- Ajustando as informações relacionadas à descoberta para o ponto final do aplicativo do serviço e ajustando algumas das configurações relacionadas à descoberta no ponto final padrão.  
  
 Para habilitar a detecção, algumas alterações devem ser feitas no arquivo de configuração do aplicativo para o serviço:  
  
- Um ponto final de descoberta `<service>` deve ser adicionado ao elemento. Este é <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> um ponto final padrão. Este é um ponto final do sistema que o tempo de execução associa ao serviço de descoberta. O serviço de descoberta ouve mensagens neste ponto final.  
  
- Um `<serviceDiscovery>` comportamento é `<serviceBehaviors>` adicionado à seção. Isso permite que o serviço seja descoberto em tempo de execução e `Probe` `Resolve` usa o ponto final de descoberta mencionado anteriormente para ouvir a descoberta e as mensagens. Com essas duas adições, o serviço é descoberto no ponto final de descoberta especificado.  
  
 O seguinte trecho de configuração mostra um serviço com um ponto final de aplicativo e um ponto final de descoberta definido:  
  
```xml
<services>  
        <service name="Microsoft.Samples.Discovery.CalculatorService"  
                 behaviorConfiguration="calculatorServiceBehavior">  
          <endpoint address=""  
                    binding="wsHttpBinding"  
                    contract="Microsoft.Samples.Discovery.ICalculatorService"  
                    behaviorConfiguration="endpointBehaviorConfiguration" />  
          <endpoint name="udpDiscovery"
                    kind="udpDiscoveryEndpoint"
                endpointConfiguration="adhocDiscoveryEndpointConfiguration"/>        </service>  
      </services>  
```  
  
 Para aproveitar os anúncios, você precisará adicionar um ponto final de anúncio. Para fazer isso, modifique o arquivo de configuração conforme mostrado no código a seguir.  
  
```xml  
<serviceDiscovery>  
            <announcementEndpoints>  
              <endpoint kind="udpAnnouncementEndpoint"/>  
            </announcementEndpoints>  
          </serviceDiscovery>  
```  
  
 Adicionar um ponto final de anúncio ao comportamento do serviço de descoberta cria um cliente de anúncio padrão para o serviço. Isso garante que o serviço enviará um comunicado online e offline quando o serviço for aberto e fechado, respectivamente.  
  
 Este arquivo de configuração vai além apenas dessas etapas simples, modificando comportamentos adicionais. É possível controlar informações relacionadas à descoberta usando pontos finais específicos. Ou seja, um usuário pode controlar se um ponto final pode ser <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior.Scopes%2A> descoberto e o usuário também pode marcar esse ponto final com metadados XML personalizados. Para fazer isso, o `behaviorConfiguration` usuário deve adicionar uma propriedade ao ponto final do aplicativo. Neste caso, a seguinte propriedade é adicionada ao ponto final do aplicativo.  
  
`behaviorConfiguration="endpointBehaviorConfiguration"`  
  
 Agora, através do elemento de configuração de comportamento, você pode controlar atributos relacionados à descoberta. Neste caso, dois escopos são adicionados ao ponto final do aplicativo.  
  
```xml  
<endpointBehaviors>  
          <behavior name="endpointBehaviorConfiguration">  
            <endpointDiscovery>  
              <scopes>  
                <add scope="http://www.example.com/calculator"/>  
                <add scope="ldap:///ou=engineering,o=examplecom,c=us"/>  
              </scopes>  
            </endpointDiscovery>  
  
          </behavior>
        </endpointBehaviors>  
```  
  
 Para obter mais informações sobre escopos, consulte [Discovery Find e FindCriteria](../../../../docs/framework/wcf/feature-details/discovery-find-and-findcriteria.md).  
  
 Você também pode controlar detalhes específicos do ponto final da descoberta. Isso é feito <xref:System.ServiceModel.Configuration.StandardEndpointsSection>através do . Nesta amostra, a versão do protocolo usado é `maxResponseDelay` modificada, bem como a adição de um atributo como mostrado no exemplo de código a seguir.  
  
```xml  
<standardEndpoints>  
   <udpDiscoveryEndpoint>  
      <standardEndpoint name="adhocDiscoveryEndpointConfiguration" discoveryVersion="WSDiscovery11" maxResponseDelay="00:00:00.600" />
   </udpDiscoveryEndpoint>  
</standardEndpoints>  
```  
  
 A seguir está o arquivo de configuração completa usado neste exemplo:  
  
```xml  
<configuration>  
    <system.serviceModel>  
  
      <services>  
        <service name="Microsoft.Samples.Discovery.CalculatorService"  
                 behaviorConfiguration="calculatorServiceBehavior">  
          <endpoint address=""  
                    binding="wsHttpBinding"  
                    contract="Microsoft.Samples.Discovery.ICalculatorService"  
                    behaviorConfiguration="endpointBehaviorConfiguration" />  
         <!-- Define the discovery endpoint -->
<endpoint name="udpDiscovery" kind="udpDiscoveryEndpoint" endpointConfiguration="adhocDiscoveryEndpointConfiguration"/>        </service>  
      </services>  
  
      <behaviors>  
  
        <serviceBehaviors>  
          <behavior name="calculatorServiceBehavior">  
  
            <!-- Add an announcement endpoint -->  
            <serviceDiscovery>  
              <announcementEndpoints>  
                <endpoint kind="udpAnnouncementEndpoint"/>  
              </announcementEndpoints>  
            </serviceDiscovery>  
          </behavior>  
        </serviceBehaviors>  
  
        <endpointBehaviors>  
          <behavior name="endpointBehaviorConfiguration">  
            <!-- Add scopes used to identify the service -->  
            <endpointDiscovery>  
              <scopes>  
                <add scope="http://www.example.com/calculator"/>  
                <add scope="ldap:///ou=engineering,o=examplecom,c=us"/>  
              </scopes>  
            </endpointDiscovery>  
  
          </behavior>
        </endpointBehaviors>  
  
      </behaviors>  
  
      <standardEndpoints>  
        <udpDiscoveryEndpoint>  
         <!-- Configure the UDP discovery endpoint -->  
          <standardEndpoint name="adhocDiscoveryEndpointConfiguration" discoveryVersion="WSDiscovery11" maxResponseDelay="00:00:00.600" />
        </udpDiscoveryEndpoint>  
      </standardEndpoints>  
  
    </system.serviceModel>  
</configuration>  
```  
  
## <a name="client-configuration"></a>Configuração do cliente  
 No arquivo de configuração do `standardEndpoint` aplicativo `dynamicEndpoint` para o cliente, um tipo é usado para utilizar a descoberta como mostrado no trecho de configuração a seguir.  
  
```xml  
<client>  
   <!--  Create an endpoint, make kind="dynamicEndpoint" and use the endpointConfiguration to change settings of DynamicEndpoint -->  
   <endpoint name="calculatorEndpoint"  
             binding="wsHttpBinding"  
             contract="ICalculatorService"  
             kind ="dynamicEndpoint"  
             endpointConfiguration="dynamicEndpointConfiguration">  
   </endpoint>  
</client>  
```  
  
 Quando um cliente `dynamicEndpoint`está usando um , o tempo de execução executa a descoberta automaticamente. Várias configurações são usadas durante a `discoveryClientSettings` descoberta, como as definidas na seção, que especifica o tipo de ponto final de descoberta a ser usado:  
  
```xml  
<endpoint kind="udpDiscoveryEndpoint" endpointConfiguration="adhocDiscoveryEndpointConfiguration" />  
```  
  
 Os critérios de busca utilizados para a busca de serviços:  
  
```xml  
<!-- Add Scopes, ScopeMatchBy, Extensions and termination criteria in FindCriteria -->  
<findCriteria scopeMatchBy="http://schemas.microsoft.com/ws/2008/06/discovery/rfc" duration="00:00:10" maxResults="1">  
   <scopes>  
      <add scope="http://www.microsoft.com/building42/floor1"/>  
   </scopes>  
   <!-- These extensions are sent from the client to the service as part of the probe message -->  
   <extensions>  
      <CustomMetadata>This is custom metadata that is sent to the service along with the client's find request.</CustomMetadata>  
   </extensions>  
</findCriteria>  
```  
  
 Esta amostra estende esse recurso <xref:System.ServiceModel.Discovery.FindCriteria> e modifica o usado pelo cliente, `updDiscoveryEndpoint` bem como algumas propriedades do padrão usado para descoberta. Os <xref:System.ServiceModel.Discovery.FindCriteria> são modificados para usar `scopeMatchBy` um escopo e um algoritmo específico, bem como critérios de terminação personalizados. Além disso, a amostra também mostra como um `Probe` cliente pode enviar elementos XML usando mensagens. Por fim, algumas alterações <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>são feitas no , como a versão do protocolo usado e configurações específicas de UDP, como mostrado no arquivo de configuração a seguir.  
  
```xml  
<udpDiscoveryEndpoint>
        <!-- Specify the discovery protocol version and UDP transport settings. -->
        <standardEndpoint name="adhocDiscoveryEndpointConfiguration" discoveryVersion="WSDiscovery11">  
          <transportSettings duplicateMessageHistoryLength="2048"  
                             maxPendingMessageCount="5"  
                             maxReceivedMessageSize="8192"  
                             maxBufferPoolSize="262144"/>  
        </standardEndpoint>
      </udpDiscoveryEndpoint>  
```  
  
 A seguir está a configuração completa do cliente usada na amostra.  
  
```xml  
<configuration>  
  <system.serviceModel>  
  
    <client>  
      <!--  Create an endpoint, make kind="dynamicEndpoint" and use the endpointConfiguration to change settings of DynamicEndpoint -->  
      <endpoint name="calculatorEndpoint"  
                binding="wsHttpBinding"  
                contract="ICalculatorService"  
                kind ="dynamicEndpoint"  
                endpointConfiguration="dynamicEndpointConfiguration">  
      </endpoint>  
    </client>  
  
    <standardEndpoints>  
  
      <dynamicEndpoint>
        <standardEndpoint name="dynamicEndpointConfiguration">  
          <discoveryClientSettings>  
            <!-- Controls where the discovery happens. In this case, Probe message is sent over UdpDiscoveryEndpoint. -->  
            <endpoint kind="udpDiscoveryEndpoint" endpointConfiguration="adhocDiscoveryEndpointConfiguration" />  
  
            <!-- Add Scopes, ScopeMatchBy, Extensions and termination criteria in FindCriteria -->  
            <findCriteria scopeMatchBy="http://schemas.microsoft.com/ws/2008/06/discovery/rfc" duration="00:00:10" maxResults="1">  
              <scopes>  
                <add scope="http://www.microsoft.com/building42/floor1"/>  
              </scopes>  
              <!-- These extensions are sent from the client to the service as part of the probe message -->  
              <extensions>  
                <CustomMetadata>This is custom metadata that is sent to the service along with the client's find request.</CustomMetadata>  
              </extensions>  
            </findCriteria>  
          </discoveryClientSettings>  
        </standardEndpoint>
      </dynamicEndpoint>  
  
      <udpDiscoveryEndpoint>
        <!-- Specify the discovery protocol version and UDP transport settings. -->
        <standardEndpoint name="adhocDiscoveryEndpointConfiguration" discoveryVersion="WSDiscovery11">  
          <transportSettings duplicateMessageHistoryLength="2048"  
                             maxPendingMessageCount="5"  
                             maxReceivedMessageSize="8192"  
                             maxBufferPoolSize="262144"/>  
        </standardEndpoint>
      </udpDiscoveryEndpoint>  
  
    </standardEndpoints>  
  
  </system.serviceModel>
</configuration>
```  
  
#### <a name="to-use-this-sample"></a>Para usar este exemplo  
  
1. Esta amostra usa pontos finais HTTP e, para executar esta amostra, devem ser adicionadas ACLs url adequadas. Para obter mais informações, consulte [Configuração HTTP e HTTPS](../feature-details/configuring-http-and-https.md). A execução do seguinte comando em um privilégio elevado deve adicionar as ACLs apropriadas. Você pode querer substituir seu Domínio e Nome de Usuário pelos seguintes argumentos se o comando não funcionar como está. `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`  
  
2. Compile a solução.  
  
3. Execute o executável de serviço a partir do diretório de compilação.  
  
4. Execute o cliente executável. Observe que o cliente é capaz de localizar o serviço.  
