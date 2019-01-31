---
title: <binding>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 666183d6-4d1f-45c7-ac64-bdf93ee8f36f
ms.openlocfilehash: fb51eb1962603439b89a203eb668dfb543049170
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55271467"
---
# <a name="binding"></a>\<binding>
Você pode usar o `binding` predefinidos de elemento para configurar diferentes tipos de associações fornecidas pelo Windows Communication Foundation (WCF).  
  
## <a name="system-provided-binding"></a>Associação fornecida pelo sistema  
 Associações fornecidas pelo sistema ocultam a complexidade da pilha de mensagens do WCF. Aplicativos que usam associações fornecidas pelo sistema não exigem controle total sobre a pilha. Os atributos expostos em cada associação fornecida pelo sistema são aqueles mais apropriada para o cenário de uso, os endereços de associação.  
  
 A seção de configuração para cada associação fornecida pelo sistema pode definir várias configurações usadas para configurar a associação. Cada configuração é identificada por um nome exclusivo.  
  
 Não é possível adicionar elementos ou atributos para uma associação fornecida pelo sistema. Para fazer isso, você deve implementar uma ligação personalizada, conforme descrito na seção "Associação personalizada" deste tópico. É possível definir uma ligação personalizada que imita um fornecido pelo sistema de associação perfeitamente e adiciona algumas configurações que o aplicativo de usuário deseja ter controle sobre.  
  
## <a name="custom-binding"></a>Associação personalizado  
 Associações personalizadas fornecem controle total sobre a pilha de mensagens do WCF. Uma associação individual define a pilha de mensagem, especificando os elementos de configuração para os elementos da pilha na ordem em que aparecem na pilha. Cada elemento define e configura um elemento da pilha. Deve haver apenas um `transport` elemento em cada associação personalizada. Sem esse elemento, a pilha de mensagens está incompleta.  
  
 A ordem na qual os elementos aparecem na pilha é importante, porque ele é a ordem na qual as operações são aplicadas à mensagem. A ordem recomendada de elementos da pilha é o seguinte:  
  
1.  Transações (opcionais)  
  
2.  (Opcional) de mensagens confiáveis  
  
3.  Segurança (opcional)  
  
4.  Codificador  
  
5.  Transporte  
  
 Associações personalizadas são identificadas por seus `name` atributo.  
  
## <a name="see-also"></a>Consulte também
- <xref:System.ServiceModel.Configuration.BindingsSection>
- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- [Associações](../../../docs/framework/wcf/bindings.md)
- [Associações personalizadas](../../../docs/framework/wcf/extending/custom-bindings.md)
- [\<customBinding>](../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
