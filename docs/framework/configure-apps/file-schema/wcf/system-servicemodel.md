---
title: '&lt;System. ServiceModel&gt;'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.ServiceModel
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.ServiceModel
helpviewer_keywords:
- <system.serviceModel> element
- system.serviceModel element
ms.assetid: 78519531-ad7a-40d3-b3e7-42f1103d8854
ms.openlocfilehash: 0ce459b5b3d739770353d9913f30c6feaceabfd8
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="ltsystemservicemodelgt"></a>&lt;System. ServiceModel&gt;
Esta seção de configuração contém todos os elementos de configuração de ServiceModel do Windows Communication Foundation (WCF).  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<system.serviceModel>  
  <behaviors>  
  </behaviors>  
  <bindings>  
  </bindings>  
  <client>  
  </client>  
  <comContracts>  
  </comContracts>  
  <commonBehaviors>  
  </commonBehaviors>  
  <diagnostics>  
  </diagnostics>  
  <extensions>  
  </extensions>
  <protocolMapping>
  </protocolMapping>
  <routing>
  </routing>  
  <serviceHostingEnvironment>  
  </serviceHostingEnvironment>  
  <services>  
  </services>
  <standardEndpoints>  
  </standardEndpoints>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
 Nenhum  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<comportamentos >](../../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)|Esta seção define duas coleções filhas nomeadas `endpointBehaviors` e `serviceBehaviors`.  Cada coleção define elementos de comportamento consumidos pelos pontos de extremidade e serviços, respectivamente. Cada elemento do comportamento é identificado por seu exclusivo `name` atributo.|  
|[\<associações >](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|Esta seção contém uma coleção de associações padrão e personalizadas. Cada entrada é identificada pelo seu exclusivo `name`. Serviços usar associações vinculando-as usando o `name`.|  
|[\<cliente >](../../../../../docs/framework/configure-apps/file-schema/wcf/client.md)|Esta seção contém uma lista de pontos de extremidade de que um cliente usa para se conectar a um serviço.|  
|[\<comContracts>](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontracts.md)|Esta seção define os contratos COM habilitado para interoperabilidade COM e o WCF.|  
|[\<commonBehaviors >](../../../../../docs/framework/configure-apps/file-schema/wcf/commonbehaviors.md)|Esta seção só pode ser definida no arquivo Machine. config. Ele define duas coleções filhas nomeadas `endpointBehaviors` e `serviceBehaviors`.  Cada coleção define elementos de comportamento consumidos por todos os [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] pontos de extremidade e serviços no computador respectivamente.  Se um comportamento é definido em `<commonBehaviors>` e `<behaviors>` seções, o comportamento de \<comportamentos > seção tem preferência.|  
|[\<Extensões >](../../../../../docs/framework/configure-apps/file-schema/wcf/extensions-section.md)|Esta seção contém uma coleção de extensões, que permitem que o usuário crie associações definidas pelo usuário, comportamentos e outros aspectos de extensões.|  
|[\<diagnóstico >](../../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md)|Esta seção contém as configurações para os recursos de diagnóstico do WCF. O usuário pode ativar/desativar o rastreamento, contadores de desempenho e o provedor WMI e pode adicionar filtros de mensagem personalizada.|  
|[\<protocolMapping >](../../../../../docs/framework/configure-apps/file-schema/wcf/protocolmapping.md)|Esta seção define um conjunto de mapeamento de padrão de protocolo entre esquemas de protocolo de transporte (por exemplo, http, net.tcp, NET. pipe, etc.) e as associações do WCF.|  
|[\<roteamento >](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|Esta seção define um conjunto de filtros de roteamento, que determinam o tipo do Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> a ser usada ao avaliar mensagens recebidas, bem como o roteamento de tabelas que definem os pontos de extremidade de destino para enviar mensagens quando um corresponde ao filtro.|  
|[\<serviceHostingEnvironment >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)|Esta seção define o tipo de serviço instancia do ambiente de hospedagem para um determinado transporte. Se esta seção está vazia, o tipo padrão será usado.|  
|[\<Serviços >](../../../../../docs/framework/configure-apps/file-schema/wcf/services.md)|A seção contém uma coleção de serviços. Para cada serviço definido no assembly, esse elemento contém um `service` elemento para especificar configurações para o serviço.|  
|[\<standardEndpoints >](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|Esta seção define uma coleção de pontos de extremidade padrão, que são pontos de extremidade pré-configurados reutilizáveis. Um ponto de extremidade padrão terá um ou mais do endereço, associação e os atributos do contrato definido como um valor fixo. Por exemplo, no ponto de extremidade de descoberta do contrato é fixo. Você também pode usar pontos de extremidade padrão para estender o ponto de extremidade de serviço com novas propriedades semelhantes para definir associações personalizadas.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|\<configuration>|O elemento raiz para todos os elementos de configuração em um arquivo de configuração do .NET.|  
  
## <a name="remarks"></a>Comentários  
 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] Não adicione elementos para as seções de configuração de outros produtos.  
  
 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] os serviços são definidos no `services` seção do arquivo de configuração. Um assembly pode conter qualquer número de serviços. Cada serviço tem seu próprio `service` seção de configuração. A seção e seu conteúdo definem o contrato de serviço, o comportamento e os pontos de extremidade do serviço em questão.  
  
 Do somente um serviço `name` atributo é necessário.  Por padrão, o nome do serviço descreve o tipo CLR subjacente usado para implementar um serviço; No entanto, você pode alterar a propriedade ConfigurationName em um <xref:System.ServiceModel.ServiceContractAttribute> para substituir o requisito de tipo CLR.  
  
 O atributo `behaviorConfiguration` é opcional. Ele identifica o comportamento de serviço usado por um serviço. O comportamento especificado por esse atributo deve vincular a um comportamento de serviço definido no escopo do mesmo arquivo de configuração (ou seja, o mesmo arquivo ou um arquivo pai).  
  
 Cada serviço expõe um ou mais pontos de extremidade definidos em um `endpoint` elemento. Cada ponto de extremidade tem seu próprio endereço e associação. Todas as associações usadas no arquivo de configuração devem ser definidas no escopo do arquivo.  
  
 Associações são vinculadas aos pontos de extremidade pela combinação dos atributos `name` e `bindingConfiguration`. O `binding` atributo define na seção a associação está definida. O `bindingConfiguration` atributo define qual associação configurada na seção de associação é usada. Uma seção de associação pode definir várias associações configuradas.  
  
## <a name="example"></a>Exemplo  
 Este é um exemplo de um arquivo de configuração do WCF.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
    <system.serviceModel>  
        <behaviors>  
           <!-- List of Behaviors -->  
        </behaviors>  
        <client>  
           <!-- List of Endpoints -->  
        </client>  
        <diagnostics wmiProviderEnabled="false" performanceCountersEnabled="false" tracingEnabled="false">  
        </diagnostics>  
        <serviceHostingEnvironment>  
           <!-- List of entries -->  
        </serviceHostingEnvironment>  
        <comContracts>  
           <!-- List of COM+ Contracts -->  
        </comContracts>          
        <services>  
           <!-- List of Services -->  
        </services>  
        <bindings>  
           <!-- List of Bindings -->  
        </bindings>  
    </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Configuration.ServiceModelSectionGroup>
