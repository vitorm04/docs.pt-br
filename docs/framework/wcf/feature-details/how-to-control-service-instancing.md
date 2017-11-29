---
title: "Como controlar instanciação de serviço"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: e0b12b34-8004-443a-a46d-83a5c00f2601
caps.latest.revision: "19"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 58393f6ed3f14e65b1732c8ec8f90c109be0894a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-control-service-instancing"></a>Como controlar instanciação de serviço
Definir o modo de instância de um serviço permite que você especifique quando um <xref:System.ServiceModel.InstanceContext?displayProperty=nameWithType> (e seu objeto de serviço definido pelo usuário associado) é criado. Consulte o <xref:System.ServiceModel.InstanceContextMode> enumeração para os modos possíveis. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]comportamentos, consulte [Configurando e estendendo o tempo de execução com comportamentos](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md). Para obter exemplos de funcionamento, consulte [comportamentos](../../../../docs/framework/wcf/samples/behaviors.md).  
  
### <a name="to-control-the-service-instance-lifetime-using-code"></a>Para controlar o tempo de vida de instância de serviço usando código  
  
1.  Aplicar o <xref:System.ServiceModel.ServiceBehaviorAttribute> para a classe de serviço.  
  
2.  Definir o <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> propriedade com um dos seguintes valores: <xref:System.ServiceModel.InstanceContextMode.PerCall>, <xref:System.ServiceModel.InstanceContextMode.PerSession>, ou <xref:System.ServiceModel.InstanceContextMode.Single>.  
  
     [!code-csharp[C_ControlServiceInstancing#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_controlserviceinstancing/cs/source.cs#1)]
     [!code-vb[C_ControlServiceInstancing#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_controlserviceinstancing/vb/source.vb#1)]  
  
## <a name="example"></a>Exemplo  
 O seguinte exemplo de código define o <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> propriedade o <xref:System.ServiceModel.ServiceBehaviorAttribute> atributo <xref:System.ServiceModel.InstanceContextMode.PerCall>.  
  
 [!code-csharp[c_ControlServiceInstancing#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_controlserviceinstancing/cs/source.cs#2)]
 [!code-vb[c_ControlServiceInstancing#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_controlserviceinstancing/vb/source.vb#2)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.ServiceBehaviorAttribute>  
 <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A>  
 <xref:System.ServiceModel.InstanceContextMode>  
 [Serviço: Exemplos de comportamentos](http://msdn.microsoft.com/en-us/4e3c6513-a7ff-4b35-8dcf-b5506c6f39a7)
