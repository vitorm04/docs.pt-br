---
title: "Como implementar uma operação de serviço assíncrona"
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
ms.assetid: 4e5d2ea5-d8f8-4712-bd18-ea3c5461702c
caps.latest.revision: "14"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 65cd45a2510aa43c3f0c58a7cbf78c13e47d821e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-implement-an-asynchronous-service-operation"></a>Como implementar uma operação de serviço assíncrona
Em [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] aplicativos, uma operação de serviço podem ser implementados assíncrona ou síncrona sem ditando ao cliente como chamá-lo. Por exemplo, operações de serviço assíncrona podem chamar sincronamente e operações de serviço síncronas podem ser chamadas de forma assíncrona. Para obter um exemplo que mostra como chamar uma operação assíncrona em um aplicativo cliente, consulte [como: chamar operações de serviço assíncrona](../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md). [!INCLUDE[crabout](../../../includes/crabout-md.md)]operações síncronas e assíncronas, consulte [criar contratos de serviço](../../../docs/framework/wcf/designing-service-contracts.md) e [síncrona e operações assíncronas](../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md). Este tópico descreve a estrutura básica de uma operação de serviço assíncrona, o código não está completo. Para um exemplo completo de cliente e serviço consulte [assíncrona](http://msdn.microsoft.com/en-us/833db946-f511-4f64-a26f-2759a11217c7).  
  
### <a name="implement-a-service-operation-asynchronously"></a>Implementar uma operação de serviço de forma assíncrona  
  
1.  No seu contrato de serviço, declare um par de método assíncrono, de acordo com as diretrizes de design assíncronos .NET. O `Begin` método utiliza um parâmetro, um objeto de retorno de chamada e um objeto de estado e retorna um <xref:System.IAsyncResult?displayProperty=nameWithType> uma correspondência e `End` método que utiliza um <xref:System.IAsyncResult?displayProperty=nameWithType> e retorna o valor de retorno. Para obter mais informações sobre as chamadas assíncronas, consulte [padrões de Design de programação assíncrona](http://go.microsoft.com/fwlink/?LinkId=248221).  
  
2.  Marca o `Begin` método do par de método assíncrono com o <xref:System.ServiceModel.OperationContractAttribute?displayProperty=nameWithType> de atributo e definir o <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A?displayProperty=nameWithType> propriedade `true`. Por exemplo, o código a seguir executa as etapas 1 e 2.  
  
     [!code-csharp[C_SyncAsyncClient#6](../../../samples/snippets/csharp/VS_Snippets_CFX/c_syncasyncclient/cs/services.cs#6)]
     [!code-vb[C_SyncAsyncClient#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_syncasyncclient/vb/services.vb#6)]  
  
3.  Implementar o `Begin/End` par de métodos em sua classe de serviço de acordo com as diretrizes de design assíncronos. Por exemplo, o exemplo de código a seguir mostra uma implementação na qual uma cadeia de caracteres é gravada no console em ambos o `Begin` e `End` partes da operação de serviço assíncrona e o valor de retorno a `End` operação retornado ao cliente. Para o exemplo de código completo, consulte a seção de exemplo.  
  
     [!code-csharp[C_SyncAsyncClient#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_syncasyncclient/cs/services.cs#3)]
     [!code-vb[C_SyncAsyncClient#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_syncasyncclient/vb/services.vb#3)]  
  
## <a name="example"></a>Exemplo  
 Os exemplos de código a seguir mostram:  
  
1.  Uma interface de contrato de serviço com:  
  
    1.  Um síncrono `SampleMethod` operação.  
  
    2.  Assíncrona `BeginSampleMethod` operação.  
  
    3.  Assíncrona `BeginServiceAsyncMethod` / `EndServiceAsyncMethod` par de operação.  
  
2.  Uma implementação de serviço usando um <xref:System.IAsyncResult?displayProperty=nameWithType> objeto.  
  
 [!code-csharp[C_SyncAsyncClient#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_syncasyncclient/cs/services.cs#1)]
 [!code-vb[C_SyncAsyncClient#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_syncasyncclient/vb/services.vb#1)]  
  
## <a name="see-also"></a>Consulte também  
 [Designing Service Contracts](../../../docs/framework/wcf/designing-service-contracts.md) (Criando contratos de serviço)  
 [Operações síncronas e assíncronas](../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md)
