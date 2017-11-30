---
title: "Usando um delegado AsyncCallback para finalizar uma operação assíncrona"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ending asynchronous operations
- asynchronous programming, ending operations
- AsyncCallback delegate
- stopping asynchronous operations
ms.assetid: 9d97206c-8917-406c-8961-7d0909d84eeb
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: bbe170588776daa97fec4c736d4b1bdd871de518
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="using-an-asynccallback-delegate-to-end-an-asynchronous-operation"></a>Usando um delegado AsyncCallback para finalizar uma operação assíncrona
Aplicativos que podem executar outras tarefas enquanto aguarda os resultados de uma operação assíncrona não devem bloquear a esperar até que a operação for concluída. Use uma das opções a seguir para continuar a execução de instruções enquanto aguarda uma operação assíncrona concluir:  
  
-   Use um <xref:System.AsyncCallback> delegado para processar os resultados da operação assíncrona em um thread separado. Essa abordagem é demonstrada neste tópico.  
  
-   Use o <xref:System.IAsyncResult.IsCompleted%2A> propriedade o <xref:System.IAsyncResult> retornado da operação assíncrona **começar** *OperationName* método para determinar se a operação foi concluída. Para obter um exemplo que demonstra essa abordagem, consulte [sondagem do status de uma operação assíncrona](../../../docs/standard/asynchronous-programming-patterns/polling-for-the-status-of-an-asynchronous-operation.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir demonstra como usar métodos assíncronos no <xref:System.Net.Dns> classe para recuperar informações do sistema de nome de domínio (DNS) de computadores especificado pelo usuário. Este exemplo cria um <xref:System.AsyncCallback> representante que referencia o `ProcessDnsInformation` método. Esse método é chamado uma vez para cada solicitação assíncrona para obter informações de DNS.  
  
 Observe que o host especificado pelo usuário é passado para o <xref:System.Net.Dns.BeginGetHostByName%2A> <xref:System.Object> parâmetro. Para obter um exemplo que demonstra a definição e uso de um objeto de estado mais complexo, consulte [usando um delegado AsyncCallback e um objeto de estado](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-and-state-object.md).  
  
 [!code-csharp[AsyncDesignPattern#4](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/AsyncDelegateNoStateObject.cs#4)]
 [!code-vb[AsyncDesignPattern#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/AsyncDelegateNoState.vb#4)]  
  
## <a name="see-also"></a>Consulte também  
 [EAP (Padrão Assíncrono baseado em Evento)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 [Visão Geral do Padrão Assíncrono Baseado em Evento](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)  
 [Chamando métodos assíncronos usando IAsyncResult](../../../docs/standard/asynchronous-programming-patterns/calling-asynchronous-methods-using-iasyncresult.md)  
 [Usando um representante AsyncCallback e um objeto de estado](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-and-state-object.md)
