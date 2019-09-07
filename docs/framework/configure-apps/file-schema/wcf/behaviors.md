---
title: <behaviors>
ms.date: 03/30/2017
ms.assetid: 0e5da4e6-1aa5-466c-924e-f10efee57f0b
ms.openlocfilehash: a87966f643fe46d0ef69f843dc306151ca7c18bb
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400590"
---
# <a name="behaviors"></a>\<comportamentos >
Esse elemento define duas coleções filho chamadas `endpointBehaviors` e `serviceBehaviors`.  Cada coleção define elementos de comportamento consumidos por pontos de extremidade e serviços, respectivamente. Cada elemento do comportamento é identificado por seu exclusivo `name` atributo. A partir do, não é necessário que as associações e os comportamentos tenham um nome. [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)] Para obter mais informações sobre configurações padrão e associações e comportamentos do sem nome, consulte [configuração simplificada](../../../wcf/simplified-configuration.md) e [configuração simplificada para serviços WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<comportamentos >**  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<behaviors>
  <serviceBehaviors>
  </serviceBehaviors>
  <endpointBehaviors>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
 Nenhum  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<endpointBehaviors>](endpointbehaviors.md)|Esta seção de configuração representa todos os comportamentos definidos para um ponto de extremidade específico.|  
|[\<serviceBehaviors>](servicebehaviors.md)|Esta seção de configuração representa todos os comportamentos definidos para um serviço específico.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<system.serviceModel>](system-servicemodel.md)|O elemento raiz de todos os elementos de configuração de Windows Communication Foundation (WCF).|  
  
## <a name="remarks"></a>Comentários  
 Você pode usar o `<remove>` elemento para remover um comportamento específico da coleção. Para fazer isso, basta fornecer o nome do comportamento a ser removido no `name` atributo `<remove>` do elemento.  Você também pode usar o `<clear>` elemento para garantir que uma coleção de comportamentos comece vazia limpando todo o conteúdo da coleção.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Configuration.BehaviorsSection>
- <xref:System.ServiceModel.Configuration.EndpointBehaviorElementCollection>
- <xref:System.ServiceModel.Configuration.EndpointBehaviorElement>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElement>
- [Configurando e estendendo o tempo de execução com comportamentos](../../../wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
- [Configurando comportamentos do cliente](../../../wcf/configuring-client-behaviors.md)
- [Especificando o comportamento em tempo de execução do cliente](../../../wcf/specifying-client-run-time-behavior.md)
- [Especificando o comportamento em tempo de execução do serviço](../../../wcf/specifying-service-run-time-behavior.md)
- [Comportamentos de segurança](../../../wcf/feature-details/security-behaviors-in-wcf.md)
