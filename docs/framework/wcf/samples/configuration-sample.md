---
title: Exemplo de configuração
ms.date: 03/30/2017
ms.assetid: 75515b4a-8d70-44c8-99e0-7423df41380e
ms.openlocfilehash: b999c84fc6fd4d1a367b4e1476de8376858008a2
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58814387"
---
# <a name="configuration-sample"></a>Exemplo de configuração
Este exemplo demonstra o uso de um arquivo de configuração para tornar um serviço detectável.  
  
> [!NOTE]
>  Este exemplo implementa descoberta na configuração. Para obter um exemplo que implementa a descoberta no código, consulte [básica](../../../../docs/framework/wcf/samples/basic-sample.md).  
  
> [!IMPORTANT]
>  Os exemplos podem mais ser instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\Configuration`  
  
## <a name="service-configuration"></a>Configuração de Serviço  
 O arquivo de configuração neste exemplo demonstra dois recursos:  
  
-   Tornando o serviço podem ser descobertos ao longo de um padrão <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>.  
  
-   Ajustando informações relacionadas a descoberta para o serviço ponto de extremidade do aplicativo e ajustar algumas das configurações relacionadas à descoberta no ponto de extremidade padrão.  
  
 Para habilitar a descoberta, algumas alterações devem ser feitas no arquivo de configuração do aplicativo para o serviço:  
  
-   Um ponto de extremidade de descoberta deve ser adicionado para o `<service>` elemento. Este é um padrão <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> ponto de extremidade. Esse é um ponto de extremidade do sistema que o tempo de execução associa com o serviço de descoberta. O serviço de descoberta escuta as mensagens nesse ponto de extremidade.  
  
-   Um `<serviceDiscovery>` comportamento é adicionado para o `<serviceBehaviors>` seção. Isso permite que o serviço seja descoberto em tempo de execução e usa o ponto de extremidade de descoberta mencionado anteriormente para ouvir de descoberta `Probe` e `Resolve` mensagens. Com essas duas adições, o serviço é detectável no ponto de extremidade de descoberta especificado.  
  
 O trecho de configuração a seguir mostra um serviço com um ponto de extremidade do aplicativo e um ponto de extremidade de descoberta definido:  
  
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
  
 Para tirar proveito dos anúncios, você precisará adicionar um ponto de extremidade de comunicado. Para fazer isso, modifique o arquivo de configuração, conforme mostrado no código a seguir.  
  
```xml  
<serviceDiscovery>  
            <announcementEndpoints>  
              <endpoint kind="udpAnnouncementEndpoint"/>  
            </announcementEndpoints>  
          </serviceDiscovery>  
```  
  
 Adicionar um ponto de extremidade de comunicado para o comportamento de serviço de descoberta cria um cliente de anúncio padrão para o serviço. Isso garante que o serviço enviará um comunicado online e offline quando o serviço é aberto e fechado, respectivamente.  
  
 Esse arquivo de configuração vai além apenas essas etapas simples, modificando comportamentos adicionais. É possível controlar informações relacionadas à descoberta por meio de pontos de extremidade específicos. Ou seja, um usuário pode controlar se um ponto de extremidade pode ser descoberto e o usuário também pode marcar o ponto de extremidade com <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior.Scopes%2A> e metadados XML personalizados. Para fazer isso, o usuário deve adicionar um `behaviorConfiguration` propriedade para o ponto de extremidade do aplicativo. Nesse caso, a propriedade a seguir é adicionada para o ponto de extremidade do aplicativo.  
  
```  
behaviorConfiguration="endpointBehaviorConfiguration"  
```  
  
 Agora, por meio do elemento de configuração de comportamento, você pode controlar atributos relacionados à descoberta. Nesse caso, os dois escopos são adicionados para o ponto de extremidade do aplicativo.  
  
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
  
 Para obter mais informações sobre escopos, consulte [FindCriteria e descoberta localizar](../../../../docs/framework/wcf/feature-details/discovery-find-and-findcriteria.md).  
  
 Você também pode controlar os detalhes específicos do ponto de extremidade de descoberta. Isso é feito por meio de <xref:System.ServiceModel.Configuration.StandardEndpointsSection>. Neste exemplo, a versão do protocolo usado é modificada, bem como adicionar um `maxResponseDelay` atributo conforme mostrado no exemplo de código a seguir.  
  
```xml  
<standardEndpoints>  
   <udpDiscoveryEndpoint>  
      <standardEndpoint name="adhocDiscoveryEndpointConfiguration" discoveryVersion="WSDiscovery11" maxResponseDelay="00:00:00.600" />    
   </udpDiscoveryEndpoint>  
</standardEndpoints>  
```  
  
 Este é o arquivo de configuração completo usado neste exemplo:  
  
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
 No arquivo de configuração do aplicativo para o cliente, uma `standardEndpoint` do tipo `dynamicEndpoint` é usado para utilizar descoberta, conforme mostrado no seguinte trecho de config.  
  
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
  
 Quando um cliente estiver usando um `dynamicEndpoint`, o tempo de execução executa a descoberta automaticamente. Várias configurações são usadas durante a descoberta, como aquelas definidas no `discoveryClientSettings` seção, que especifica o tipo de ponto de extremidade de descoberta para usar:  
  
```xml  
<endpoint kind="udpDiscoveryEndpoint" endpointConfiguration="adhocDiscoveryEndpointConfiguration" />  
```  
  
 Os critérios de localização usados para pesquisar serviços:  
  
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
  
 Este exemplo amplia esse recurso e modifica o <xref:System.ServiceModel.Discovery.FindCriteria> usado pelo cliente, bem como algumas propriedades do padrão `updDiscoveryEndpoint` usada para descoberta. O <xref:System.ServiceModel.Discovery.FindCriteria> são modificadas para usar um escopo e uma determinada `scopeMatchBy` algoritmo, bem como critérios de encerramento personalizada. Além disso, o exemplo também mostra como um cliente pode enviar os elementos XML usando `Probe` mensagens. Por fim, algumas alterações são feitas para o <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, como a versão do protocolo usado e as configurações de UDP específicas, conforme mostrado no seguinte arquivo de configuração.  
  
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
  
 A seguir está a configuração de cliente completa usada no exemplo.  
  
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
```  
  
#### <a name="to-use-this-sample"></a>Para usar este exemplo  
  
1.  Este exemplo usa pontos de extremidade HTTP e executar isso URL de exemplo, apropriado ACLs deve ser adicionado ver [Configuring HTTP and HTTPS](https://go.microsoft.com/fwlink/?LinkId=70353) para obter detalhes. Executando o seguinte comando para um nível de privilégio elevado deve adicionar as ACLs apropriado. Você talvez queira substituir seu domínio e nome de usuário para os argumentos a seguir, se o comando não funcionar como está. `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`  
  
2.  Compile a solução.  
  
3.  Execute o executável do serviço de diretório de compilação.  
  
4.  Execute o executável do cliente. Observe que o cliente é capaz de localizar o serviço.  
  
