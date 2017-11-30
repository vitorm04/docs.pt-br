---
title: "Sondando o status de uma operação assíncrona"
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
- asynchronous programming, status polling
- polling asynchronous operation status
- status information [.NET Framework], asynchronous operations
ms.assetid: b541af31-dacb-4e20-8847-1b1ff7c35363
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e1f7f74a8b38c06f6a042d55c0def76ddfc5da77
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="polling-for-the-status-of-an-asynchronous-operation"></a>Sondando o status de uma operação assíncrona
Aplicativos que podem executar outras tarefas enquanto aguarda os resultados de uma operação assíncrona não devem bloquear a esperar até que a operação for concluída. Use uma das opções a seguir para continuar a execução de instruções enquanto aguarda uma operação assíncrona concluir:  
  
-   Use o <xref:System.IAsyncResult.IsCompleted%2A> propriedade o <xref:System.IAsyncResult> retornado da operação assíncrona **começar** *OperationName* método para determinar se a operação foi concluída. Essa abordagem é conhecida como sondagem e demonstrada neste tópico.  
  
-   Use um <xref:System.AsyncCallback> delegado para processar os resultados da operação assíncrona em um thread separado. Para obter um exemplo que demonstra essa abordagem, consulte [usando um delegado AsyncCallback para finalizar uma operação assíncrona](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir demonstra como usar métodos assíncronos no <xref:System.Net.Dns> classe para recuperar informações do sistema de nomes de domínio para um computador especificado pelo usuário. Este exemplo inicia a operação assíncrona e, em seguida, imprime períodos (".") no console até que a operação seja concluída. Observe que **nulo** (**nada** no Visual Basic) é passada o <xref:System.Net.Dns.BeginGetHostByName%2A> <xref:System.AsyncCallback> e <xref:System.Object> parâmetros porque esses argumentos não são necessários ao usar essa abordagem.  
  
 [!code-csharp[AsyncDesignPattern#3](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/Async_Poll.cs#3)]
 [!code-vb[AsyncDesignPattern#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/Async_Poll.vb#3)]  
  
## <a name="see-also"></a>Consulte também  
 [EAP (Padrão Assíncrono baseado em Evento)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 [Visão Geral do Padrão Assíncrono Baseado em Evento](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
