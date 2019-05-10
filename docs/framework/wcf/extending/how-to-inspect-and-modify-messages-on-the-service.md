---
title: 'Como: inspecionar e modificar mensagens do serviço'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9c5b1cc7-84f3-45f8-9226-d59c278e8c42
ms.openlocfilehash: 17ec1d974332b38bed9c00d57bdacba708d0e64f
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64606357"
---
# <a name="how-to-inspect-and-modify-messages-on-the-service"></a>Como: inspecionar e modificar mensagens do serviço
Você pode inspecionar ou modificar as mensagens de entrada ou saídas em um cliente do Windows Communication Foundation (WCF), Implementando um <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType> e inseri-lo no tempo de execução do serviço. Para obter mais informações, consulte [estendendo Dispatchers](../../../../docs/framework/wcf/extending/extending-dispatchers.md). O recurso equivalente no serviço é o <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>.  
  
### <a name="to-inspect-or-modify-messages"></a>Para inspecionar ou modificar as mensagens  
  
1. Implementar a interface <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType>.  
  
2. Implementar uma <xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>, ou <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> interface dependendo do escopo no qual você deseja inserir facilmente o Inspetor de mensagens do serviço.  
  
3. Inserir seu comportamento antes de chamar o <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> método no <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType>. Para obter detalhes, consulte [Configurando e estendendo o tempo de execução com comportamentos](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).  
  
## <a name="example"></a>Exemplo  
 Os exemplos de código a seguir mostram, na ordem:  
  
- Uma implementação de Inspetor de serviço.  
  
- Um comportamento de serviço que insere o Inspetor.  
  
- Um arquivo de configuração que carrega e executa o comportamento em um aplicativo de serviço.  
  
 [!code-csharp[Interceptors#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/interceptors.cs#7)]
 [!code-vb[Interceptors#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/interceptors.vb#7)]  
  
 [!code-csharp[Interceptors#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/insertingbehaviors.cs#8)]
 [!code-vb[Interceptors#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/insertingbehaviors.vb#8)]  
  
 [!code-xml[Interceptors#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/hostapplication.exe.config#9)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType>
- [Configurando e estendendo o tempo de execução com comportamentos](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
