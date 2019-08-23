---
title: Configuração simplificada
ms.date: 03/30/2017
ms.assetid: dcbe1f84-437c-495f-9324-2bc09fd79ea9
ms.openlocfilehash: 5aaca8ae8c456e2377326ee2e9e22c3dcf6a21a7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923005"
---
# <a name="simplified-configuration"></a>Configuração simplificada
Configurar os serviços Windows Communication Foundation (WCF) pode ser uma tarefa complexa. Há muitas opções diferentes e nem sempre é fácil determinar quais configurações são necessárias. Embora os arquivos de configuração aumentem a flexibilidade dos serviços WCF, eles também são a fonte de muitos problemas difíceis de encontrar. [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)]resolve esses problemas e fornece uma maneira de reduzir o tamanho e a complexidade da configuração de serviço.  
  
## <a name="simplified-configuration"></a>Configuração simplificada  
 Nos arquivos de configuração do serviço WCF,`system.serviceModel`a seção < > contém`service`um elemento < > para cada serviço hospedado. O elemento`service`< > contém uma coleção de elementos`endpoint`de > < que especificam os pontos de extremidade expostos para cada serviço e, opcionalmente, um conjunto de comportamentos de serviço. O <`endpoint`> elementos especificam o endereço, a associação e o contrato expostos pelo ponto de extremidade e, opcionalmente, associando os comportamentos de configuração e ponto de extremidade. A seção`system.serviceModel`< > também contém um elemento`behaviors`< > que permite especificar comportamentos de serviço ou ponto de extremidade. O exemplo a seguir mostra a`system.serviceModel`< > seção de um arquivo de configuração.  
  
```  
<system.serviceModel>  
  <behaviors>  
    <serviceBehaviors>  
      <behavior name="MyServiceBehavior">  
        <serviceMetadata httpGetEnabled="true">  
        <serviceDebug includeExceptionDetailInFaults="false">  
      </behavior>  
    </serviceBehaviors>  
  </behaviors>  
  <bindings>  
   <basicHttpBinding>  
      <binding name=MyBindingConfig"  
               maxBufferSize="100"  
               maxReceiveBufferSize="100" />  
   </basicHttpBinding>  
   </bindings>   <services>  
    <service behaviorConfiguration="MyServiceBehavior"  
             name="MyService">  
      <endpoint address=""  
                binding="basicHttpBinding"  
                contract="ICalculator"  
                bindingConfiguration="MyBindingConfig" />  
      <endpoint address="mex"  
                binding="mexHttpBinding"  
                contract="IMetadataExchange"/>  
    </service>  
  </services>  
</system.serviceModel>  
```  
  
 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]torna a configuração de um serviço WCF mais fácil, removendo o`service`requisito para o elemento < >. Se você não adicionar uma seção <`service`> ou adicionar pontos de extremidade em uma seção <`service`> e o serviço não definir nenhum ponto de extremidade de forma programática, um conjunto de pontos de extremidade padrão será adicionado automaticamente ao seu serviço, um para cada endereço base de serviço e para cada contrato implementado pelo seu serviço. Em cada uma dessas extremidades, o endereço do ponto de extremidade corresponde ao endereço base, a associação é determinada pelo esquema de endereço base e o contrato é o que é implementado pelo seu serviço. Se você não precisar especificar pontos de extremidade ou comportamentos de serviço ou fazer alterações de configuração de associação, não será necessário especificar um arquivo de configuração de serviço. Se um serviço implementar dois contratos e o host habilitar transportes HTTP e TCP, o host de serviço criará quatro pontos de extremidade padrão, um para cada contrato usando cada transporte. Para criar pontos de extremidade padrão, o host de serviço deve saber quais associações usar. Essas configurações são especificadas em uma seção`protocolMappings`< > na seção <`system.serviceModel`>. A seção`protocolMappings`< > contém uma lista de esquemas de protocolo de transporte mapeados para tipos de associação. O host de serviço usa os endereços base passados para ele para determinar qual associação usar. O exemplo a seguir usa o`protocolMappings`elemento < >.  
  
> [!WARNING]
>  Alterar os elementos de configuração padrão, como associações ou comportamentos, pode afetar os serviços definidos em níveis inferiores da hierarquia de configuração, pois eles podem estar usando essas associações e comportamentos padrão. Assim, quem altera as associações e os comportamentos padrão precisa estar ciente de que essas alterações podem afetar outros serviços na hierarquia.  
  
> [!NOTE]
> Os serviços hospedados em Serviços de Informações da Internet (IIS) ou serviço de ativação de processos do Windows (WAS) usam o diretório virtual como seu endereço base.  
  
```xml  
<protocolMapping>  
  <add scheme="http"     binding="basicHttpBinding" bindingConfiguration="MyBindingConfiguration"/>  
  <add scheme="net.tcp"  binding="netTcpBinding"/>  
  <add scheme="net.pipe" binding="netNamedPipeBinding"/>  
  <add scheme="net.msmq" binding="netMSMQBinding"/>  
</protocolMapping>  
```  
  
 No exemplo anterior, um ponto de extremidade com um endereço base que começa com o esquema "http" usa <xref:System.ServiceModel.BasicHttpBinding>o. Um ponto de extremidade com um endereço base que começa com o esquema "net. TCP" <xref:System.ServiceModel.NetTcpBinding>usa o. Você pode substituir as configurações em um arquivo app. config ou Web. config local.  
  
 Cada elemento dentro da seção`protocolMappings`< > deve especificar um esquema e uma associação. Opcionalmente, ele pode especificar `bindingConfiguration` um atributo que especifica uma configuração de associação dentro`bindings`da seção < > do arquivo de configuração. Se não `bindingConfiguration` for especificado, a configuração de associação anônima do tipo de associação apropriado será usada.  
  
 Os comportamentos de serviço são configurados para os pontos de extremidade padrão`behavior`usando seções < anônimas > nas seções <`serviceBehaviors`>. Quaisquer <`behavior`> elementos sem nome dentro de <`serviceBehaviors`> são usados para configurar comportamentos de serviço. Por exemplo, o arquivo de configuração a seguir habilita a publicação de metadados de serviço para todos os serviços no host.  
  
```xml  
<system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceMetadata httpGetEnabled="True"/>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>    <!-- No <service> tag is necessary. Default endpoints are added to the service -->  
    <!-- The service behavior with name="" is picked up by the service -->  
 </system.serviceModel>  
```  
  
 Os comportamentos de ponto de extremidade são configurados usando seções`serviceBehaviors`<`behavior`anônimas > dentro das seções < >.  
  
 O exemplo a seguir é um arquivo de configuração equivalente ao do início deste tópico que usa o modelo de configuração simplificado.  
  
```xml  
<system.serviceModel>
    <behaviors>
      <serviceBehaviors>
        <behavior>
          <serviceMetadata httpGetEnabled="true" />
          <serviceDebug includeExceptionDetailInFaults="false" />
        </behavior>
      </serviceBehaviors>
    </behaviors>
    <bindings>
       <basicHttpBinding>
          <binding maxBufferSize="100"
                   maxReceiveBufferSize="100" />
       </basicHttpBinding>
    </bindings>
    <!-- No <service> tag is necessary. Default endpoints will be added to the service -->
    <!-- The service behavior with name="" will be picked up by the service -->
    <protocolMapping>
      <add scheme="http" binding="basicHttpBinding" />
  </protocolMapping>
  </system.serviceModel>
```  
  
> [!IMPORTANT]
> Esse recurso está relacionado somente à configuração do serviço WCF, não à configuração do cliente. Na maioria das vezes, a configuração do cliente WCF será gerada por uma ferramenta como SvcUtil. exe ou adicionando uma referência de serviço do Visual Studio. Se você estiver configurando manualmente um cliente WCF, precisará adicionar \<um elemento cliente > à configuração e especificar os pontos de extremidade que deseja chamar.  
  
## <a name="see-also"></a>Consulte também

- [Configurando serviços usando arquivos de configuração](../../../docs/framework/wcf/configuring-services-using-configuration-files.md)
- [Configurando associações para serviços](../../../docs/framework/wcf/configuring-bindings-for-wcf-services.md)
- [Configurando associações fornecidas pelo sistema](../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [Configurando serviços](../../../docs/framework/wcf/configuring-services.md)
- [Configurando serviços WCF](configuring-services.md)
- [Configurando serviços do WCF em código](../../../docs/framework/wcf/configuring-wcf-services-in-code.md)
