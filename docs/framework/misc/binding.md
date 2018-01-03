---
title: "&lt;associação&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 666183d6-4d1f-45c7-ac64-bdf93ee8f36f
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7b9e0c7e077a9f47de6df31b00f4df320b845150
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltbindinggt"></a>&lt;associação&gt;
Você pode usar o `binding` predefinidos de elemento para configurar diferentes tipos de associações fornecidas pelo Windows Communication Foundation (WCF).  
  
## <a name="system-provided-binding"></a>Associação fornecida pelo sistema  
 Associações fornecidas pelo sistema ocultam a complexidade da pilha de mensagens do WCF. Aplicativos usando associações fornecidas pelo sistema não necessitam de controle total sobre a pilha. Os atributos expostos em cada associação fornecida pelo sistema são as mais apropriada para o cenário de uso, os endereços de associação.  
  
 A seção de configuração para cada associação fornecida pelo sistema pode definir várias configurações usadas para configurar a associação. Cada configuração é identificada por um nome exclusivo.  
  
 Não é possível adicionar elementos ou atributos em uma associação fornecida pelo sistema. Para fazer isso, você deve implementar uma associação personalizada, conforme descrito na seção "Associação personalizada" deste tópico. É possível definir uma associação personalizada que simule um fornecido pelo sistema de associação perfeitamente e adiciona algumas configurações de que aplicativo do usuário deseja ter controle sobre.  
  
## <a name="custom-binding"></a>Associação personalizado  
 Associações personalizadas fornecem controle total sobre a pilha de mensagens do WCF. Uma associação individual define a pilha de mensagem, especificando os elementos de configuração para os elementos da pilha na ordem em que aparecem na pilha. Cada elemento define e configura um elemento da pilha. Deve haver apenas um `transport` elemento em cada associação personalizada. Sem esse elemento, a pilha de mensagens está incompleta.  
  
 A ordem na qual os elementos aparecem na pilha é importante, porque é a ordem na qual as operações são aplicadas à mensagem. A ordem recomendada de elementos da pilha é o seguinte:  
  
1.  Transações (opcionais)  
  
2.  Confiável de mensagens (opcional)  
  
3.  Segurança (opcional)  
  
4.  Codificador  
  
5.  Transporte  
  
 Associações personalizadas são identificadas por seus `name` atributo.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Configuration.BindingsSection>  
 <xref:System.ServiceModel.Channels.Binding>  
 <xref:System.ServiceModel.Channels.BindingElement>  
 [Associações](../../../docs/framework/wcf/bindings.md)  
 [Associações personalizadas](../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<customBinding >](../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
