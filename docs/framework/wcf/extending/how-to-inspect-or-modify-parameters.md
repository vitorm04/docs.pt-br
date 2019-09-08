---
title: 'Como: inspecionar ou modificar parâmetros'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ab6c0ac7-aac4-45ba-93d6-a0e9afd1756f
ms.openlocfilehash: b4a673f97f06e8d489d9acc85d84e1ecea4656e4
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795592"
---
# <a name="how-to-inspect-or-modify-parameters"></a>Como: inspecionar ou modificar parâmetros
Você pode inspecionar ou modificar as mensagens de entrada ou saída para uma única operação em um objeto de cliente Windows Communication Foundation (WCF) ou em um serviço WCF <xref:System.ServiceModel.Dispatcher.IParameterInspector?displayProperty=nameWithType> implementando a interface e inserindo-a no tempo de execução do cliente ou do serviço. Normalmente, um comportamento de operação é usado para adicionar inspetores de parâmetro para uma única operação; outros comportamentos podem ser usados para fornecer acesso fácil ao tempo de execução em um escopo maior. Para obter mais informações, consulte Estendendo [clientes](extending-clients.md) e [estendendo expatchers](extending-dispatchers.md).  
  
### <a name="inspecting-or-modifying-parameters"></a>Inspecionando ou modificando parâmetros  
  
1. Implementar a interface <xref:System.ServiceModel.Dispatcher.IParameterInspector?displayProperty=nameWithType>.  
  
2. Implemente <xref:System.ServiceModel.Description.IOperationBehavior?displayProperty=nameWithType>um <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType> , ou<xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> (dependendo do escopo necessário) para adicionar seu inspetor de parâmetro às propriedades <xref:System.ServiceModel.Dispatcher.ClientOperation.ParameterInspectors%2A?displayProperty=nameWithType> ou <xref:System.ServiceModel.Dispatcher.DispatchOperation.ParameterInspectors%2A?displayProperty=nameWithType> .  
  
3. Insira seu comportamento antes de chamar <xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=nameWithType> ou o <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> método no <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>. Para obter detalhes, consulte [Configurando e estendendo o tempo de execução com comportamentos](configuring-and-extending-the-runtime-with-behaviors.md).  
  
## <a name="example"></a>Exemplo  
 Os exemplos de código a seguir mostram, em ordem:  
  
- Uma implementação de Inspetor de parâmetro.  
  
- A implementação de comportamento que insere o Inspetor de parâmetro <xref:System.ServiceModel.Description.IOperationBehavior?displayProperty=nameWithType>usando <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>um, e <xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType>um.  
  
- Um arquivo de configuração que carrega e executa o comportamento do ponto de extremidade em um aplicativo cliente para inserir o Inspetor de parâmetro no cliente.  
  
 [!code-csharp[Interceptors#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/interceptors.cs#4)]
 [!code-vb[Interceptors#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/interceptors.vb#4)]  
  
 [!code-csharp[Interceptors#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/insertingbehaviors.cs#5)]
 [!code-vb[Interceptors#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/insertingbehaviors.vb#5)]  
  
 [!code-xml[Interceptors#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/client.exe.config#3)]  
  
## <a name="see-also"></a>Consulte também

- [Configurando e estendendo o tempo de execução com comportamentos](configuring-and-extending-the-runtime-with-behaviors.md)
