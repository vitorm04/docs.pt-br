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
ms.openlocfilehash: c2f4a0787f6027d7f57891d4e219758c4a7054ff
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54145842"
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
  <tracking>
  </tracking>
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
|[\<associações >](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|Esta seção contém uma coleção de associações padrão e personalizadas. Cada entrada é identificada por seu exclusivo `name`. Serviços usam associações vinculando-as usando o `name`.|  
|[\<cliente >](../../../../../docs/framework/configure-apps/file-schema/wcf/client.md)|Esta seção contém uma lista de pontos de extremidade de que um cliente usa para se conectar a um serviço.|  
|[\<comContracts>](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontracts.md)|Esta seção define os contratos COM habilitado para a interoperabilidade do WCF e do COM.|  
|[\<commonBehaviors >](../../../../../docs/framework/configure-apps/file-schema/wcf/commonbehaviors.md)|Esta seção só pode ser definida no arquivo Machine. config. Ele define duas coleções filhas nomeadas `endpointBehaviors` e `serviceBehaviors`.  Cada coleção define elementos de comportamento consumidos por todos os pontos de extremidade do WCF e serviços no computador, respectivamente.  Se um comportamento é definido em ambos `<commonBehaviors>` e `<behaviors>` seções, o comportamento no \<comportamentos > seção é dada preferência.|  
|[\<diagnóstico >](../../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md)|Esta seção contém as configurações para os recursos de diagnóstico do WCF. O usuário pode habilitar/desabilitar o rastreamento, contadores de desempenho e o provedor WMI e pode adicionar filtros de mensagem personalizada.|  
|[\<Extensões >](../../../../../docs/framework/configure-apps/file-schema/wcf/extensions-section.md)|Esta seção contém uma coleção de extensões, que permitem que o usuário crie associações definidas pelo usuário, comportamentos e outros aspectos de extensões.|  
|[\<protocolMapping >](../../../../../docs/framework/configure-apps/file-schema/wcf/protocolmapping.md)|Esta seção define um conjunto padrão de mapeamento de protocolo entre esquemas de protocolo de transporte (por exemplo, http, NET. TCP, NET. pipe, etc.) e associações do WCF.|  
|[\<roteamento >](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|Esta seção define um conjunto de filtros de roteamento, que determinam o tipo do Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> a ser usada ao avaliar mensagens recebidas, bem como roteamento de tabelas que definem os pontos de extremidade de destino para enviar mensagens para quando um corresponde ao filtro.|  
|[\<serviceHostingEnvironment >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)|Esta seção define que tipo de serviço do ambiente de hospedagem cria uma instância para um transporte particular. Se esta seção está vazia, o tipo padrão é usado.|  
|[\<Serviços >](../../../../../docs/framework/configure-apps/file-schema/wcf/services.md)|A seção contém uma coleção de serviços. Para cada serviço definido no assembly, esse elemento contém um `service` elemento que especifica configurações para o serviço.|  
|[\<standardEndpoints >](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|Esta seção define uma coleção de pontos de extremidade padrão que são pontos de extremidade pré-configurados reutilizáveis. Um ponto de extremidade padrão terá um ou mais do endereço, associação e atributos de contrato definido como um valor fixo. Por exemplo, o ponto de extremidade de descoberta o contrato é fixo. Você também pode usar pontos de extremidade padrão para estender o ponto de extremidade de serviço com novas propriedades semelhantes à definição de ligações personalizadas.|
|[\<Acompanhamento >](../../../../../docs/framework/configure-apps/file-schema/wcf/tracking-of-wcf.md)|Esta seção define as configurações de rastreamento para um serviço de fluxo de trabalho.|

### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|\<configuration>|O elemento raiz para todos os elementos de configuração em um arquivo de configuração do .NET.|  
  
## <a name="remarks"></a>Comentários  
 WCF não adiciona elementos para as seções de configuração de outros produtos.  
  
 Os serviços do WCF são definidos na `services` seção do arquivo de configuração. Um assembly pode conter qualquer número de serviços. Cada serviço tem seu próprio `service` seção de configuração. A seção e seu conteúdo definem o contrato de serviço, o comportamento e os pontos de extremidade do serviço em questão.  
  
 Somente o de um serviço `name` atributo é necessário.  Por padrão, o nome do serviço descreve o tipo CLR subjacente usado para implementar um serviço; No entanto, você pode alterar a propriedade ConfigurationName em um <xref:System.ServiceModel.ServiceContractAttribute> para substituir o requisito de tipo CLR.  
  
 O atributo `behaviorConfiguration` é opcional. Ele identifica o comportamento de serviço usado por um serviço. O comportamento especificado por este atributo deve vincular a um comportamento de serviço definido no escopo do mesmo arquivo de configuração (ou seja, o mesmo arquivo ou um arquivo pai).  
  
 Cada serviço expõe um ou mais pontos de extremidade definido em um `endpoint` elemento. Cada ponto de extremidade tem seu próprio endereço e associação. Todas as ligações usadas no arquivo de configuração devem ser definidas no escopo do arquivo.  
  
 Associações são vinculadas aos pontos de extremidade por meio da combinação dos atributos `name` e `bindingConfiguration`. O `binding` atributo define em qual seção a associação é definida. O `bindingConfiguration` atributo define qual associação configurada dentro da seção de associação é usada. Uma seção de associação pode definir várias associações configuradas.  
  
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
    <diagnostics wmiProviderEnabled="false"
                 performanceCountersEnabled="false"
                 tracingEnabled="false">
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
