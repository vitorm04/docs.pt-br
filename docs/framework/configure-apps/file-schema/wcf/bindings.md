---
title: <bindings>
ms.date: 01/22/2018
ms.assetid: b62cd369-5409-4030-8490-9759a462dd3a
ms.openlocfilehash: 1292bc38ce1e542086edac5539c1b29e619e2a32
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926381"
---
# <a name="bindings"></a>\<bindings>

Você pode usar o `bindings` elemento para configurar uma coleção de associações padrão e personalizadas para Windows Communication Foundation (WCF). Cada entrada é um `binding` elemento que pode ser identificado por seu exclusivo `name`. Os serviços usam associações vinculando-os usando `name`o. A partir do, não é necessário que as associações e os comportamentos tenham um nome. [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)] Para obter mais informações sobre configurações padrão e associações e comportamentos do sem nome, consulte [configuração simplificada](../../../wcf/simplified-configuration.md) e [configuração simplificada para serviços WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).  
  
## <a name="system-provided-bindings"></a>Associações fornecidas pelo sistema
 
 As associações fornecidas pelo sistema ocultam a complexidade da pilha de mensagens do WCF. Os aplicativos que usam associações fornecidas pelo sistema não exigem controle total sobre a pilha. Os atributos expostos em cada associação fornecida pelo sistema são os mais apropriados para o cenário de uso os endereços de associação.  
  
 A seção de configuração para cada associação fornecida pelo sistema pode definir várias configurações usadas para configurar a associação. Cada configuração é identificada por um nome exclusivo.  
  
 Não é possível adicionar elementos ou atributos a uma associação fornecida pelo sistema. Para fazer isso, você deve implementar uma associação personalizada, conforme descrito na seção [associações personalizadas](#custom-bindings) . É possível definir uma ligação personalizada que imita perfeitamente uma associação fornecida pelo sistema e adiciona algumas configurações para as quais o aplicativo do usuário deseja ter controle.  
  
 Para obter uma lista de associações fornecidas pelo sistema, consulte [associações fornecidas pelo sistema](../../../wcf/system-provided-bindings.md).  
  
## <a name="custom-bindings"></a>Associações personalizadas

 As associações personalizadas fornecem controle total sobre a pilha de mensagens do WCF. Uma associação individual define a pilha de mensagens especificando os elementos de configuração dos elementos de pilha na ordem em que aparecem na pilha. Cada elemento define e configura um elemento da pilha. Deve haver apenas `transport` um elemento em cada associação personalizada. Sem esse elemento, a pilha de mensagens está incompleta.  
  
 A ordem na qual os elementos aparecem na pilha é importante, pois é a ordem na qual as operações são aplicadas à mensagem. A ordem necessária dos elementos de pilha é a seguinte:  
  
1. Transações (opcional)  
  
2. Mensagens confiáveis (opcional)  
  
3. Segurança (opcional)  
  
4. Fita  
  
5. Porta  
  
 As associações personalizadas são identificadas por `name` seu atributo. Para obter mais informações sobre associações personalizadas, consulte [associações personalizadas](../../../wcf/extending/custom-bindings.md).  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Configuration.BindingsSection?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.Binding?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType>  
- [Associações](../../../wcf/bindings.md)  
- [Associações personalizadas](../../../wcf/extending/custom-bindings.md)  
- [\<customBinding>](custombinding.md)  
- [\<binding>](../../../misc/binding.md)
