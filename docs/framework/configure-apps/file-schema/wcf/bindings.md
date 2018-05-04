---
title: '&lt;Associações&gt;'
ms.date: 03/30/2017
ms.assetid: b62cd369-5409-4030-8490-9759a462dd3a
ms.openlocfilehash: 76ebd7c317bf5f0aa1ec02d4014235df232314f0
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="ltbindingsgt"></a>&lt;Associações&gt;
Esta seção contém uma coleção de associações padrão e personalizadas. Cada entrada é um `binding` elemento que pode ser identificado pelo seu exclusivo `name`. Serviços usar associações vinculando-as usando o `name`. Começando com [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], associações e comportamentos não precisam ter um nome. Para obter mais informações sobre a configuração padrão e associações de nomes e comportamentos, consulte [configuração simplificada](../../../../../docs/framework/wcf/simplified-configuration.md) e [configuração simplificada para serviços WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
## <a name="system-provided-binding"></a>Associação fornecida pelo sistema  
 Associações fornecidas pelo sistema ocultam a complexidade da pilha de mensagens do WCF. Aplicativos usando associações fornecidas pelo sistema não necessitam de controle total sobre a pilha. Os atributos expostos em cada associação fornecida pelo sistema são as mais apropriada para o cenário de uso, os endereços de associação.  
  
 A seção de configuração para cada associação fornecida pelo sistema pode definir várias configurações usadas para configurar a associação. Cada configuração é identificada por um nome exclusivo.  
  
 Não é possível adicionar elementos ou atributos em uma associação fornecida pelo sistema. Para fazer isso, você deve implementar uma associação personalizada, conforme descrito na seção "Associação personalizada" deste tópico. É possível definir uma associação personalizada que simule um fornecido pelo sistema de associação perfeitamente e adiciona algumas configurações de que aplicativo do usuário deseja ter controle sobre.  
  
 Para obter uma lista de associações fornecidas pelo sistema, consulte [System-Provided associações](../../../../../docs/framework/wcf/system-provided-bindings.md).  
  
## <a name="custom-binding"></a>Associação personalizado  
 Associações personalizadas fornecem controle total sobre a pilha de mensagens do WCF. Uma associação individual define a pilha de mensagem, especificando os elementos de configuração para os elementos da pilha na ordem em que aparecem na pilha. Cada elemento define e configura um elemento da pilha. Deve haver apenas um `transport` elemento em cada associação personalizada. Sem esse elemento, a pilha de mensagens está incompleta.  
  
 A ordem na qual os elementos aparecem na pilha é importante, porque é a ordem na qual as operações são aplicadas à mensagem. A ordem exigida de elementos da pilha é o seguinte:  
  
1.  Transações (opcionais)  
  
2.  Confiável de mensagens (opcional)  
  
3.  Segurança (opcional)  
  
4.  Codificador  
  
5.  Transporte  
  
 Associações personalizadas são identificadas por seus `name` atributo. Para obter mais informações sobre associações personalizadas, consulte [associações personalizadas](../../../../../docs/framework/wcf/extending/custom-bindings.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Configuration.BindingsSection>  
 <xref:System.ServiceModel.Channels.Binding>  
 <xref:System.ServiceModel.Channels.BindingElement>  
 [Associações](../../../../../docs/framework/wcf/bindings.md)  
 [Associações personalizadas](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<customBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [\<associação >](../../../../../docs/framework/misc/binding.md)
