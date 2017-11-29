---
title: "Como declarar falhas em contratos de serviço"
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
ms.assetid: e8da98e7-d22f-4f60-ac82-3fb0928a353f
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1ebfe56a0e073534840ce81eebb64ce3f5db48a1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-declare-faults-in-service-contracts"></a>Como declarar falhas em contratos de serviço
No código gerenciado, as exceções são geradas quando ocorrem condições de erro. Em [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] aplicativos, no entanto, os contratos de serviço especificar quais informações de erro são retornadas aos clientes declarando falhas de SOAP no contrato de serviço. Para obter uma visão geral da relação entre exceções e falhas, consulte [especificando e tratamento de falhas em contratos e serviços](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).  
  
### <a name="create-a-service-contract-that-specifies-a-soap-fault"></a>Crie um contrato de serviço que especifica uma falha de SOAP  
  
1.  Crie um contrato de serviço que contém pelo menos uma operação. Para obter um exemplo, consulte [como: definir um contrato de serviço](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md).  
  
2.  Selecione uma operação que pode especificar uma condição de erro sobre os quais os clientes podem esperar ser notificado. Para decidir quais condições de erro justificam retornando falhas de SOAP para os clientes, consulte [especificando e tratamento de falhas em contratos e serviços](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).  
  
3.  Aplicar um <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType> para a operação selecionada e digite uma falha serializável de passagem para o construtor. Para obter detalhes sobre como criar e usar tipos serializáveis, consulte [especificando a transferência de dados em contratos de serviço](../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md). O exemplo a seguir mostra como especificar que o `SampleMethod` operação pode resultar em um `GreetingFault`.  
  
     [!code-csharp[FaultContractAttribute#4](../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/services.cs#4)]
     [!code-vb[FaultContractAttribute#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/services.vb#4)]  
  
4.  Repita as etapas 2 e 3 para todas as operações no contrato que se comunicam condições de erro para os clientes.  
  
## <a name="implementing-an-operation-to-return-a-specified-soap-fault"></a>Implementação de uma operação para retornar uma falha de SOAP especificada  
 Depois que uma operação especificou que uma falha SOAP específica pode ser retornada (como o procedimento anterior) para comunicar-se uma condição de erro para um aplicativo de chamada, a próxima etapa é implementar essa especificação.  
  
#### <a name="throw-the-specified-soap-fault-in-the-operation"></a>Lançar a falha SOAP especificada na operação  
  
1.  Quando um <xref:System.ServiceModel.FaultContractAttribute>-condição de erro especificado ocorre em uma operação, gerar um novo <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType> onde a falha SOAP especificada é o parâmetro de tipo. O exemplo a seguir mostra como gerar o `GreetingFault` no `SampleMethod` mostrado no procedimento anterior e, na seção de código a seguir.  
  
     [!code-csharp[FaultContractAttribute#5](../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/services.cs#5)]
     [!code-vb[FaultContractAttribute#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/services.vb#5)]  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir mostra uma implementação de uma única operação que especifica um `GreetingFault` para o `SampleMethod` operação.  
  
 [!code-csharp[FaultContractAttribute#1](../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/services.cs#1)]
 [!code-vb[FaultContractAttribute#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/services.vb#1)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType>  
 <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType>
