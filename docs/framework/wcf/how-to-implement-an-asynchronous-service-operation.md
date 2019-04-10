---
title: 'Como: implementar uma operação de serviço assíncrona'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4e5d2ea5-d8f8-4712-bd18-ea3c5461702c
ms.openlocfilehash: 603ee57475b3e7b1af607d49050e3276fd3082d8
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59298650"
---
# <a name="how-to-implement-an-asynchronous-service-operation"></a>Como: implementar uma operação de serviço assíncrona
Em aplicativos do Windows Communication Foundation (WCF), uma operação de serviço pode ser implementada forma assíncrona ou síncrona sem ditando ao cliente como chamá-lo. Por exemplo, operações de serviço assíncronas podem ser chamadas de forma síncrona e operações de serviço síncronas podem ser chamadas de forma assíncrona. Para obter um exemplo que mostra como chamar uma operação de forma assíncrona em um aplicativo cliente, consulte [como: Chamar operações de serviço de forma assíncrona](../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md). Para obter mais informações sobre operações síncronas e assíncronas, consulte [Criando contratos de serviço](../../../docs/framework/wcf/designing-service-contracts.md) e [síncrona e operações assíncronas](../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md). Este tópico descreve a estrutura básica de uma operação de serviço assíncrona, o código não está completo. Para obter um exemplo completo de cliente e o serviço, consulte [Asynchronous](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms751505(v=vs.100)).  
  
### <a name="implement-a-service-operation-asynchronously"></a>Implementar uma operação de serviço de forma assíncrona  
  
1. No seu contrato de serviço, declare um par de métodos assíncronos acordo com as diretrizes de design assíncrono do .NET. O `Begin` método usa um parâmetro, um objeto de retorno de chamada e um objeto de estado e retorna um <xref:System.IAsyncResult?displayProperty=nameWithType> e encontrar uma correspondência `End` método que usa um <xref:System.IAsyncResult?displayProperty=nameWithType> e retorna o valor de retorno. Para obter mais informações sobre as chamadas assíncronas, consulte [padrões de Design de programação assíncrona](https://go.microsoft.com/fwlink/?LinkId=248221).  
  
2. Marca o `Begin` método o par de método assíncrono com o <xref:System.ServiceModel.OperationContractAttribute?displayProperty=nameWithType> de atributo e definir o <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A?displayProperty=nameWithType> propriedade `true`. Por exemplo, o código a seguir executa as etapas 1 e 2.  
  
     [!code-csharp[C_SyncAsyncClient#6](../../../samples/snippets/csharp/VS_Snippets_CFX/c_syncasyncclient/cs/services.cs#6)]
     [!code-vb[C_SyncAsyncClient#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_syncasyncclient/vb/services.vb#6)]  
  
3. Implementar o `Begin/End` par de métodos em sua classe de serviço de acordo com as diretrizes de design assíncrono. Por exemplo, o exemplo de código a seguir mostra uma implementação em que uma cadeia de caracteres é gravada no console em ambos os `Begin` e `End` partes da operação assíncrona de serviço e o valor de retorno a `End` operação é retornado ao cliente. No exemplo de código completo, consulte a seção de exemplo.  
  
     [!code-csharp[C_SyncAsyncClient#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_syncasyncclient/cs/services.cs#3)]
     [!code-vb[C_SyncAsyncClient#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_syncasyncclient/vb/services.vb#3)]  
  
## <a name="example"></a>Exemplo  
 Os exemplos de código a seguir mostram:  
  
1. Uma interface de contrato de serviço com:  
  
    1.  Um síncrono `SampleMethod` operação.  
  
    2.  Assíncrona `BeginSampleMethod` operação.  
  
    3.  Assíncrona `BeginServiceAsyncMethod` / `EndServiceAsyncMethod` par da operação.  
  
2. Uma implementação de serviço usando um <xref:System.IAsyncResult?displayProperty=nameWithType> objeto.  
  
 [!code-csharp[C_SyncAsyncClient#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_syncasyncclient/cs/services.cs#1)]
 [!code-vb[C_SyncAsyncClient#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_syncasyncclient/vb/services.vb#1)]  
  
## <a name="see-also"></a>Consulte também

- [Criando contratos de serviço](../../../docs/framework/wcf/designing-service-contracts.md)
- [Operações síncronas e assíncronas](../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md)
