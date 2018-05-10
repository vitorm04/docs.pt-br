---
title: Configuração simplificada
ms.date: 03/30/2017
ms.assetid: dcbe1f84-437c-495f-9324-2bc09fd79ea9
ms.openlocfilehash: 9f35a5f4fa4ae6be63bd75a24f58b56dd236ee9c
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2018
---
# <a name="simplified-configuration"></a>Configuração simplificada
Configurar serviços Windows Communication Foundation (WCF) pode ser uma tarefa complexa. Há muitas opções diferentes e nem sempre é fácil determinar quais configurações são necessárias. Enquanto os arquivos de configuração de aumentam a flexibilidade de serviços WCF, eles também serão a origem para muitos difíceis de encontrar problemas. [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] trata esses problemas e fornece uma maneira de reduzir o tamanho e a complexidade da configuração do serviço.  
  
## <a name="simplified-configuration"></a>Configuração simplificada  
 Nos arquivos de configuração do serviço WCF, o <`system.serviceModel`> seção contém um <`service`> elemento para cada serviço hospedado. O <`service`> elemento contém uma coleção de <`endpoint`> elementos que especificam os pontos de extremidade expostos para cada serviço e, opcionalmente, um conjunto de comportamentos de serviço. O <`endpoint`> elementos especificam o endereço, associação, e contrato expostos pelo ponto de extremidade e, opcionalmente, configuração de associação e os comportamentos de ponto de extremidade. O <`system.serviceModel`> seção também contém um <`behaviors`> elemento que permite que você especificar comportamentos de serviço ou o ponto de extremidade. A exemplo a seguir mostra o <`system.serviceModel`> seção de um arquivo de configuração.  
  
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
  
 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] torna a configuração de um serviço WCF mais fácil, removendo o requisito para o <`service`> elemento. Se você não adicionar um <`service`> seção ou adicionar pontos de extremidade em um <`service`> seção e o serviço não programaticamente define pontos de extremidade, em seguida, um conjunto de pontos de extremidade padrão são adicionados automaticamente ao seu serviço, um para cada endereço base do serviço e para cada contrato implementado pelo seu serviço. Em cada um desses pontos de extremidade, o endereço do ponto de extremidade corresponde ao endereço base, a associação é determinada pelo esquema de endereço de base e o contrato é a implementados pelo serviço. Se você não precisa especificar pontos de extremidade ou comportamentos de serviço ou faça as alterações de configuração de associação, você não precisa especificar um arquivo de configuração de serviço em todos os. Se um serviço implementa dois contratos e o host de transportes HTTP e TCP permite que o host de serviço cria quatro pontos de extremidade padrão, uma para cada contrato usando cada transporte. Para criar pontos de extremidade padrão que o host de serviço deve saber quais associações para usar. Essas configurações são especificadas em um <`protocolMappings`> seção dentro de <`system.serviceModel`> seção. O <`protocolMappings`> seção contém uma lista de esquemas de protocolo de transporte mapeados para tipos de vinculação. O host de serviço usa os endereços base passados a ele para determinar qual associação a ser usada. O exemplo a seguir usa o <`protocolMappings`> elemento.  
  
> [!WARNING]
>  Alterar elementos de configuração padrão, como associações ou comportamentos, pode afetar os serviços definidos em níveis inferiores da hierarquia de configuração, desde que estejam usando essas associações padrão e comportamentos. Portanto, quem altera associações padrão e comportamentos precisa estar ciente de que essas alterações podem afetar outros serviços na hierarquia.  
  
> [!NOTE]
>  Serviços hospedados em serviços de informações da Internet (IIS) ou o serviço de ativação de processos do Windows (WAS) usam o diretório virtual como seu endereço de base.  
  
```xml  
<protocolMapping>  
  <add scheme="http"     binding="basicHttpBinding" bindingConfiguration="MyBindingConfiguration"/>  
  <add scheme="net.tcp"  binding="netTcpBinding"/>  
  <add scheme="net.pipe" binding="netNamedPipeBinding"/>  
  <add scheme="net.msmq" binding="netMSMQBinding"/>  
</protocolMapping>  
```  
  
 No exemplo anterior, um ponto de extremidade com um endereço base que começa com o esquema "http" usa o <xref:System.ServiceModel.BasicHttpBinding>. Um ponto de extremidade com um endereço base que começa com o esquema de "NET" usa o <xref:System.ServiceModel.NetTcpBinding>. Você pode substituir as configurações em um arquivo App. config ou Web. config local.  
  
 Cada elemento dentro do <`protocolMappings`> seção deve especificar um esquema e uma associação. Opcionalmente, ele pode especificar um `bindingConfiguration` atributo que especifica uma configuração de associação dentro de <`bindings`> seção do arquivo de configuração. Se nenhum `bindingConfiguration` for especificado, a configuração de associação anônima do tipo de associação apropriado será usada.  
  
 Comportamentos de serviço são configurados para os pontos de extremidade padrão usando anônimo <`behavior`> seções dentro de <`serviceBehaviors`> seções. Qualquer sem nome <`behavior`> elementos <`serviceBehaviors`> são usados para configurar os comportamentos de serviço. Por exemplo, o arquivo de configuração a seguir habilita a publicação de metadados de serviço para todos os serviços dentro do host.  
  
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
  
 Comportamentos de ponto de extremidade são configurados usando anônimo <`behavior`> seções dentro de <`serviceBehaviors`> seções.  
  
 O exemplo a seguir é um arquivo de configuração equivalente no início deste tópico que usa o modelo de configuração simplificada.  
  
```xml  
<system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceMetadata httpGetEnabled="True"/>  
          <serviceDebug includeExceptionDetailInFaults="false"/>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>    <bindings>  
       <basicHttpBinding>  
          <binding maxBufferSize="100"  
                   maxReceiveBufferSize="100" />  
       </basicHttpBinding>  
    </bindings>    <!-- No <service> tag is necessary. Default endpoints will be added to the service -->  
    <!-- The service behavior with name="" will be picked up by the service -->  
    <protocolMapping>  
      <add scheme="http"     binding="basicHttpBinding" / </protocolMapping>  
  </system.serviceModel>  
```  
  
> [!IMPORTANT]
>  Esse recurso se relaciona apenas a configuração do serviço WCF, não a configuração de cliente. A maioria das vezes, a configuração de cliente do WCF será gerada por uma ferramenta como svcutil.exe ou adicionar uma referência de serviço do Visual Studio. Se você estiver configurando um cliente WCF manualmente, será necessário adicionar um \<cliente > elemento para a configuração e especifique quaisquer pontos de extremidade que você deseja chamar.  
  
## <a name="see-also"></a>Consulte também  
 [Configurando serviços usando arquivos de configuração](../../../docs/framework/wcf/configuring-services-using-configuration-files.md)  
 [Configurando associações para serviços](../../../docs/framework/wcf/configuring-bindings-for-wcf-services.md)  
 [Configurando associações fornecidas pelo sistema](../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Configurando serviços](../../../docs/framework/wcf/configuring-services.md)  
 [Configuring Windows Communication Foundation Applications](http://msdn.microsoft.com/library/13cb368e-88d4-4c61-8eed-2af0361c6d7a) (Configurando aplicativos do Windows Communication Foundation)  
 [Configurando serviços do WCF em código](../../../docs/framework/wcf/configuring-wcf-services-in-code.md)
