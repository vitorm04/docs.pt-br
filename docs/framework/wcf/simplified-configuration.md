---
title: Configuração simplificada
ms.date: 03/30/2017
ms.assetid: dcbe1f84-437c-495f-9324-2bc09fd79ea9
ms.openlocfilehash: 4e316290c045b75896c61e36c1646440c18678e2
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249624"
---
# <a name="simplified-configuration"></a>Configuração simplificada
Configurar os serviços da Windows Communication Foundation (WCF) pode ser uma tarefa complexa. Existem muitas opções diferentes e nem sempre é fácil determinar quais configurações são necessárias. Embora os arquivos de configuração aumentem a flexibilidade dos serviços WCF, eles também são a fonte para muitos problemas difíceis de encontrar. [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)]resolve esses problemas e fornece uma maneira de reduzir o tamanho e a complexidade da configuração do serviço.  
  
## <a name="simplified-configuration"></a>Configuração simplificada  
 Nos arquivos de configuração `system.serviceModel` de serviço WCF, a seção> <contém um elemento <`service`> para cada serviço hospedado. O `service` elemento> <contém `endpoint` uma coleção de elementos <> que especificam os pontos finais expostos para cada serviço e, opcionalmente, um conjunto de comportamentos de serviço. Os `endpoint` elementos <> especificam o endereço, a vinculação e o contrato expostos pelo ponto final e, opcionalmente, vinculando comportamentos de configuração e ponto final. A `system.serviceModel` seção <> `behaviors` também contém um elemento> <que permite especificar comportamentos de serviço ou ponto final. O exemplo a `system.serviceModel` seguir mostra a seção> <de um arquivo de configuração.  
  
```xml  
<system.serviceModel>  
  <behaviors>  
    <serviceBehaviors>  
      <behavior name="MyServiceBehavior">  
        <serviceMetadata httpGetEnabled="true" />  
        <serviceDebug includeExceptionDetailInFaults="false" />  
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
  
 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]facilita a configuração de um serviço WCF `service` removendo o requisito para o <> elemento. Se você não adicionar `service` uma <> seção `service` ou adicionar quaisquer pontos finais em uma seção de> <e seu serviço não definir programáticamente quaisquer pontos finais, então um conjunto de pontos finais padrão são automaticamente adicionados ao seu serviço, um para cada endereço base de serviço e para cada contrato implementado pelo seu serviço. Em cada um desses pontos finais, o endereço de ponto final corresponde ao endereço base, a vinculação é determinada pelo esquema de endereço base e o contrato é o implementado pelo seu serviço. Se você não precisar especificar quaisquer pontos finais ou comportamentos de serviço ou fazer quaisquer alterações de configuração vinculantes, você não precisa especificar um arquivo de configuração de serviço. Se um serviço implementar dois contratos e o host habilitar tanto o TRANSPORTE HTTP quanto o TCP, o host de serviço criará quatro pontos finais padrão, um para cada contrato usando cada transporte. Para criar pontos finais padrão, o host de serviço deve saber quais vinculações usar. Essas configurações são especificadas `protocolMappings` em uma `system.serviceModel` seção de> <na seção <>. A `protocolMappings` seção <> contém uma lista de esquemas de protocolo de transporte mapeados para tipos de vinculação. O host de serviço usa os endereços base passados para ele para determinar qual vinculação usar. O exemplo a `protocolMappings` seguir usa o elemento> <.  
  
> [!WARNING]
> A alteração de elementos de configuração padrão, como vinculações ou comportamentos, pode afetar os serviços definidos em níveis mais baixos da hierarquia de configuração, uma vez que eles podem estar usando essas vinculações e comportamentos padrão. Assim, quem altera as vinculações e comportamentos padrão precisa estar ciente de que essas mudanças podem afetar outros serviços na hierarquia.  
  
> [!NOTE]
> Os serviços hospedados no Internet Information Services (IIS) ou no Windows Process Activation Service (WAS) usam o diretório virtual como endereço base.  
  
```xml  
<protocolMapping>  
  <add scheme="http"     binding="basicHttpBinding" bindingConfiguration="MyBindingConfiguration"/>  
  <add scheme="net.tcp"  binding="netTcpBinding"/>  
  <add scheme="net.pipe" binding="netNamedPipeBinding"/>  
  <add scheme="net.msmq" binding="netMSMQBinding"/>  
</protocolMapping>  
```  
  
 No exemplo anterior, um ponto final com um endereço base que <xref:System.ServiceModel.BasicHttpBinding>começa com o esquema "http" usa o . Um ponto final com um endereço base que começa com <xref:System.ServiceModel.NetTcpBinding>o esquema "net.tcp" usa o . Você pode substituir as configurações em um arquivo local App.config ou Web.config.  
  
 Cada elemento dentro `protocolMappings` da seção <> deve especificar um esquema e uma vinculação. Opcionalmente, ele `bindingConfiguration` pode especificar um atributo `bindings` que especifica uma configuração de vinculação dentro da seção <> do arquivo de configuração. Se `bindingConfiguration` não for especificado, a configuração de vinculação anônima do tipo de vinculação apropriada é usada.  
  
 Os comportamentos de serviço são configurados para `behavior` os pontos finais `serviceBehaviors` padrão usando seções de> de <anônimos nas seções <>. Quaisquer elementos `behavior` de> `serviceBehaviors` <não nomeados dentro de <> são usados para configurar comportamentos de serviço. Por exemplo, o arquivo de configuração a seguir permite a publicação de metadados de serviço para todos os serviços dentro do host.  
  
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
  
 Os comportamentos de ponto final são `behavior` configurados usando `serviceBehaviors` seções de> de <anônimos dentro de <seções>.  
  
 O exemplo a seguir é um arquivo de configuração equivalente ao do início deste tópico que usa o modelo de configuração simplificada.  
  
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
> Esse recurso diz respeito apenas à configuração do serviço WCF, não à configuração do cliente. Na maioria das vezes, a configuração do cliente WCF será gerada por uma ferramenta como svcutil.exe ou adicionando uma referência de serviço do Visual Studio. Se você estiver configurando manualmente um cliente WCF, você precisará adicionar um \<elemento de> cliente à configuração e especificar quaisquer pontos finais que você deseja chamar.  
  
## <a name="see-also"></a>Confira também

- [Configurando serviços usando arquivos de configuração](configuring-services-using-configuration-files.md)
- [Configurando associações para serviços](configuring-bindings-for-wcf-services.md)
- [Configurando associações fornecidas pelo sistema](./feature-details/configuring-system-provided-bindings.md)
- [Configurando serviços](configuring-services.md)
- [Configuração de serviços WCF](configuring-services.md)
- [Configurando serviços do WCF em código](configuring-wcf-services-in-code.md)
