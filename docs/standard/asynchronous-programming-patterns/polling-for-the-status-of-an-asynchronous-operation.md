---
title: Sondando o status de uma operação assíncrona
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- asynchronous programming, status polling
- polling asynchronous operation status
- status information [.NET Framework], asynchronous operations
ms.assetid: b541af31-dacb-4e20-8847-1b1ff7c35363
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e1bf2b2c4fdacda2b44498ab8e1c98c8fa9c6d5c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33567387"
---
# <a name="polling-for-the-status-of-an-asynchronous-operation"></a>Sondando o status de uma operação assíncrona
Os aplicativos que podem executar outras tarefas enquanto aguardam os resultados de uma operação assíncrona não devem bloquear a espera até que a operação seja concluída. Use uma das opções a seguir para continuar a execução das instruções ao aguardar a conclusão de uma operação assíncrona:  
  
-   Use a propriedade <xref:System.IAsyncResult.IsCompleted%2A> do <xref:System.IAsyncResult> retornado do método **Begin***OperationName* da operação assíncrona para determinar se a operação foi concluída. Essa abordagem é conhecida como sondagem e será demonstrada neste tópico.  
  
-   Use um representante do <xref:System.AsyncCallback> para processar os resultados da operação assíncrona em um thread separado. Veja um exemplo que demonstra essa abordagem em [Usar um representante AsyncCallback para finalizar uma operação assíncrona](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir demonstra como usar métodos assíncronos na classe <xref:System.Net.Dns> para recuperar informações do Sistema de Nomes de Domínio de computadores especificados pelo usuário. Este exemplo inicia a operação assíncrona e, em seguida, imprime pontos (".") no console até que a operação seja concluída. Observe que **nulo** (**Nada** no Visual Basic) é passado para os parâmetros <xref:System.Net.Dns.BeginGetHostByName%2A><xref:System.AsyncCallback> e <xref:System.Object> porque esses argumentos não são necessários quando se usa essa abordagem.  
  
 [!code-csharp[AsyncDesignPattern#3](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/Async_Poll.cs#3)]
 [!code-vb[AsyncDesignPattern#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/Async_Poll.vb#3)]  
  
## <a name="see-also"></a>Consulte também  
 [EAP (Padrão Assíncrono baseado em Evento)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 [Visão Geral do Padrão Assíncrono Baseado em Evento](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
