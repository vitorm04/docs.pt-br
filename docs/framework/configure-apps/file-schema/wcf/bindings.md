---
title: <bindings>
ms.date: 01/22/2018
ms.assetid: b62cd369-5409-4030-8490-9759a462dd3a
ms.openlocfilehash: 479941593b1abefe637525703140b02917c6692b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59316785"
---
# <a name="bindings"></a>\<bindings>

Você pode usar o `bindings` elemento para configurar uma coleção de associações padrão e personalizadas para o Windows Communication Foundation (WCF). Cada entrada é uma `binding` elemento que pode ser identificado por seu exclusivo `name`. Serviços usam associações vinculando-as usando o `name`. Começando com [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], associações e comportamentos não precisam ter um nome. Para obter mais informações sobre a configuração padrão e sem nome associações e comportamentos, consulte [configuração simplificado](../../../../../docs/framework/wcf/simplified-configuration.md) e [configuração simplificada para serviços WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
## <a name="system-provided-bindings"></a>Associações fornecidas pelo sistema
 
 Associações fornecidas pelo sistema ocultam a complexidade da pilha de mensagens do WCF. Aplicativos que usam associações fornecidas pelo sistema não exigem controle total sobre a pilha. Os atributos expostos em cada associação fornecida pelo sistema são aqueles mais apropriada para o cenário de uso, os endereços de associação.  
  
 A seção de configuração para cada associação fornecida pelo sistema pode definir várias configurações usadas para configurar a associação. Cada configuração é identificada por um nome exclusivo.  
  
 Não é possível adicionar elementos ou atributos para uma associação fornecida pelo sistema. Para fazer isso, você deve implementar uma ligação personalizada conforme descrito na [ligações personalizadas](#custom-bindings) seção. É possível definir uma ligação personalizada que imita um fornecido pelo sistema de associação perfeitamente e adiciona algumas configurações que o aplicativo de usuário deseja ter controle sobre.  
  
 Para obter uma lista das associações fornecidas pelo sistema, consulte [System-Provided associações](../../../../../docs/framework/wcf/system-provided-bindings.md).  
  
## <a name="custom-bindings"></a>Associações personalizadas

 Associações personalizadas fornecem controle total sobre a pilha de mensagens do WCF. Uma associação individual define a pilha de mensagem, especificando os elementos de configuração para os elementos da pilha na ordem em que aparecem na pilha. Cada elemento define e configura um elemento da pilha. Deve haver apenas um `transport` elemento em cada associação personalizada. Sem esse elemento, a pilha de mensagens está incompleta.  
  
 A ordem na qual os elementos aparecem na pilha é importante, porque ele é a ordem na qual as operações são aplicadas à mensagem. A ordem exigida dos elementos da pilha é o seguinte:  
  
1. Transações (opcionais)  
  
2. (Opcional) de mensagens confiáveis  
  
3. Segurança (opcional)  
  
4. Codificador  
  
5. Transporte  
  
 Associações personalizadas são identificadas por seus `name` atributo. Para obter mais informações sobre ligações personalizadas, consulte [ligações personalizadas](../../../../../docs/framework/wcf/extending/custom-bindings.md).  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Configuration.BindingsSection?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.Binding?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType>  
- [Associações](../../../../../docs/framework/wcf/bindings.md)  
- [Associações personalizadas](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
- [\<customBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
- [\<binding>](../../../../../docs/framework/misc/binding.md)
