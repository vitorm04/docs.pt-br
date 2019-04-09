---
title: 'Como: declarar falhas em contratos de serviço'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e8da98e7-d22f-4f60-ac82-3fb0928a353f
ms.openlocfilehash: 90abb29550ce7e027244b220f30e9fe46e282ff3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59129487"
---
# <a name="how-to-declare-faults-in-service-contracts"></a>Como: declarar falhas em contratos de serviço
No código gerenciado, as exceções são geradas quando ocorrem condições de erro. Em aplicativos do Windows Communication Foundation (WCF), no entanto, os contratos de serviço especificam quais informações de erro serão retornadas aos clientes por meio da declaração de falhas de SOAP no contrato de serviço. Para obter uma visão geral da relação entre exceções e falhas, consulte [especificação e tratamento de falhas em contratos e serviços](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).  
  
### <a name="create-a-service-contract-that-specifies-a-soap-fault"></a>Criar um contrato de serviço que especifica uma falha de SOAP  
  
1.  Crie um contrato de serviço que contém pelo menos uma operação. Para obter um exemplo, consulte [ Definir um contrato de serviço](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md).  
  
2.  Selecione uma operação que pode especificar uma condição de erro sobre o qual os clientes podem esperar ser notificado. Para decidir quais condições de erro justificam retornar falhas de SOAP aos clientes, consulte [especificação e tratamento de falhas em contratos e serviços](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).  
  
3.  Aplicar um <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType> para a operação selecionada e a passagem de uma falha serializável de tipo para o construtor. Para obter detalhes sobre como criar e usar tipos serializáveis, consulte [especificando a transferência de dados em contratos de serviço](../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md). O exemplo a seguir mostra como especificar que o `SampleMethod` operação pode resultar em um `GreetingFault`.  
  
     [!code-csharp[FaultContractAttribute#4](../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/services.cs#4)]
     [!code-vb[FaultContractAttribute#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/services.vb#4)]  
  
4.  Repita as etapas 2 e 3 para todas as operações no contrato que se comunicam as condições de erro para os clientes.  
  
## <a name="implementing-an-operation-to-return-a-specified-soap-fault"></a>Implementando uma operação para retornar uma falha SOAP especificada  
 Depois que uma operação especificou que uma falha SOAP específica pode ser retornada (como no procedimento anterior) para se comunicar uma condição de erro para um aplicativo de chamada, a próxima etapa é implementar essa especificação.  
  
#### <a name="throw-the-specified-soap-fault-in-the-operation"></a>Gerar a falha SOAP especificada na operação  
  
1.  Quando um <xref:System.ServiceModel.FaultContractAttribute>-a condição de erro especificada ocorre em uma operação lançar uma nova <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType> onde a falha SOAP especificada é o parâmetro de tipo. O exemplo a seguir mostra como gerar o `GreetingFault` no `SampleMethod` mostrado no procedimento anterior e na seção de código a seguir.  
  
     [!code-csharp[FaultContractAttribute#5](../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/services.cs#5)]
     [!code-vb[FaultContractAttribute#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/services.vb#5)]  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir mostra uma implementação de uma única operação que especifica um `GreetingFault` para o `SampleMethod` operação.  
  
 [!code-csharp[FaultContractAttribute#1](../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/services.cs#1)]
 [!code-vb[FaultContractAttribute#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/services.vb#1)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType>
