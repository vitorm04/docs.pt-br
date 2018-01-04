---
title: "Como inspecionar e modificar mensagens do serviço"
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
ms.assetid: 9c5b1cc7-84f3-45f8-9226-d59c278e8c42
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 64d9ccf97533be6be0da5d1e23763e8174aead3c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-inspect-and-modify-messages-on-the-service"></a>Como inspecionar e modificar mensagens do serviço
Você pode inspecionar ou modificar as mensagens de entrada ou saídas em uma [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] cliente implementando um <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType> e inseri-lo no tempo de execução do serviço. Para obter mais informações, consulte [estendendo Dispatchers](../../../../docs/framework/wcf/extending/extending-dispatchers.md). O recurso equivalente do serviço é o <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>.  
  
### <a name="to-inspect-or-modify-messages"></a>Para inspecionar ou modificar as mensagens  
  
1.  Implementar a interface <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType>.  
  
2.  Implementar um <xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>, ou <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> interface de acordo com o escopo no qual você deseja inserir facilmente o Inspetor de mensagens do serviço.  
  
3.  Insira seu comportamento antes de chamar o <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> método o <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType>. Para obter detalhes, consulte [Configurando e estendendo o tempo de execução com comportamentos](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).  
  
## <a name="example"></a>Exemplo  
 Os exemplos de código a seguir mostram, em ordem:  
  
-   Uma implementação de Inspetor de serviço.  
  
-   Um comportamento de serviço que insere o Inspetor.  
  
-   Um arquivo de configuração que carrega e executa o comportamento em um aplicativo de serviço.  
  
 [!code-csharp[Interceptors#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/interceptors.cs#7)]
 [!code-vb[Interceptors#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/interceptors.vb#7)]  
  
 [!code-csharp[Interceptors#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/insertingbehaviors.cs#8)]
 [!code-vb[Interceptors#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/insertingbehaviors.vb#8)]  
  
 [!code-xml[Interceptors#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/hostapplication.exe.config#9)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>  
 <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType>  
 [Configurando e estendendo o tempo de execução com comportamentos](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
