---
title: Como implementar uma operação de serviço assíncrona
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4e5d2ea5-d8f8-4712-bd18-ea3c5461702c
ms.openlocfilehash: b706ec49db123f33b3fc1ab0f420ed9a47e32f67
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320948"
---
# <a name="how-to-implement-an-asynchronous-service-operation"></a>Como implementar uma operação de serviço assíncrona
Em aplicativos Windows Communication Foundation (WCF), uma operação de serviço pode ser implementada de forma assíncrona ou síncrona, sem ditar ao cliente como chamá-lo. Por exemplo, as operações de serviço assíncronas podem ser chamadas de forma síncrona e as operações de serviço síncronas podem ser chamadas assincronamente. Para obter um exemplo que mostra como chamar uma operação de forma assíncrona em um aplicativo cliente, consulte [como: chamar operações de serviço de forma assíncrona](./feature-details/how-to-call-wcf-service-operations-asynchronously.md). Para obter mais informações sobre operações síncronas e assíncronas, consulte [Criando contratos de serviço](designing-service-contracts.md) e operações síncronas [e assíncronas](synchronous-and-asynchronous-operations.md). Este tópico descreve a estrutura básica de uma operação de serviço assíncrona, o código não está completo. Para obter um exemplo completo dos lados do serviço e do cliente, consulte [assíncrono](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms751505(v=vs.100)).  
  
### <a name="implement-a-service-operation-asynchronously"></a>Implementar uma operação de serviço de forma assíncrona  
  
1. Em seu contrato de serviço, declare um par de métodos assíncronos de acordo com as diretrizes de design assíncrono do .NET. O método `Begin` usa um parâmetro, um objeto de retorno de chamada e um objeto de estado e retorna um <xref:System.IAsyncResult?displayProperty=nameWithType> e um método `End` correspondente que usa um <xref:System.IAsyncResult?displayProperty=nameWithType> e retorna o valor de retorno. Para obter mais informações sobre chamadas assíncronas, consulte [padrões de design de programação assíncrona](https://go.microsoft.com/fwlink/?LinkId=248221).  
  
2. Marque o método `Begin` do par método assíncrono com o atributo <xref:System.ServiceModel.OperationContractAttribute?displayProperty=nameWithType> e defina a propriedade <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A?displayProperty=nameWithType> como `true`. Por exemplo, o código a seguir executa as etapas 1 e 2.  
  
     [!code-csharp[C_SyncAsyncClient#6](../../../samples/snippets/csharp/VS_Snippets_CFX/c_syncasyncclient/cs/services.cs#6)]
     [!code-vb[C_SyncAsyncClient#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_syncasyncclient/vb/services.vb#6)]  
  
3. Implemente o par de método `Begin/End` em sua classe de serviço de acordo com as diretrizes de design assíncronas. Por exemplo, o exemplo de código a seguir mostra uma implementação na qual uma cadeia de caracteres é gravada no console do nas partes `Begin` e `End` da operação de serviço assíncrona e o valor de retorno da operação de `End` é retornado ao cliente. Para obter o exemplo de código completo, consulte a seção de exemplo.  
  
     [!code-csharp[C_SyncAsyncClient#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_syncasyncclient/cs/services.cs#3)]
     [!code-vb[C_SyncAsyncClient#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_syncasyncclient/vb/services.vb#3)]  
  
## <a name="example"></a>{1&gt;Exemplo&lt;1}  
 Os exemplos de código a seguir mostram:  
  
1. Uma interface de contrato de serviço com:  
  
    1. Uma operação de `SampleMethod` síncrona.  
  
    2. Uma operação de `BeginSampleMethod` assíncrona.  
  
    3. Um par de operações `BeginServiceAsyncMethod`/`EndServiceAsyncMethod` assíncrona.  
  
2. Uma implementação de serviço usando um objeto <xref:System.IAsyncResult?displayProperty=nameWithType>.  
  
 [!code-csharp[C_SyncAsyncClient#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_syncasyncclient/cs/services.cs#1)]
 [!code-vb[C_SyncAsyncClient#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_syncasyncclient/vb/services.vb#1)]  
  
## <a name="see-also"></a>Consulte também

- [Criando contratos de serviço](designing-service-contracts.md)
- [Operações síncronas e assíncronas](synchronous-and-asynchronous-operations.md)
