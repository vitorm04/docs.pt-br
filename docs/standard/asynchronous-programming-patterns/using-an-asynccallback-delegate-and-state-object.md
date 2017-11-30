---
title: Usando um delegado AsyncCallback e um objeto de estado
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
- asynchronous programming, delegates
- AsyncCallback delegate, samples
- asynchronous programming, state objects
- IAsyncResult interface, samples
ms.assetid: e3e5475d-c5e9-43f0-928e-d18df8ca1f1d
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e8793a78289e9b58407038f41cc9d403ff9f9940
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="using-an-asynccallback-delegate-and-state-object"></a>Usando um delegado AsyncCallback e um objeto de estado
Quando você usa um <xref:System.AsyncCallback> delegar para processar os resultados da operação assíncrona em um thread separado, você pode usar um objeto de estado para transmitir informações entre os retornos de chamada e recuperar o resultado final. Este tópico demonstra essa prática expandindo o exemplo [usando um delegado AsyncCallback para finalizar uma operação assíncrona](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir demonstra como usar métodos assíncronos no <xref:System.Net.Dns> classe para recuperar informações do sistema de nome de domínio (DNS) de computadores especificado pelo usuário. Este exemplo define e usa o `HostRequest` classe para armazenar informações de estado. Um `HostRequest` objeto é criado para cada nome de computador inserido pelo usuário. Este objeto é passado para o <xref:System.Net.Dns.BeginGetHostByName%2A> método. O `ProcessDnsInformation` método é chamado sempre que uma solicitação é concluída. O `HostRequest` objeto é recuperado usando o <xref:System.IAsyncResult.AsyncState%2A> propriedade. O `ProcessDnsInformation` método usa o `HostRequest` objeto para armazenar o <xref:System.Net.IPHostEntry> retornado pela solicitação ou um <xref:System.Net.Sockets.SocketException> gerada pela solicitação. Quando todas as solicitações estiverem concluídas, o aplicativo itera através de `HostRequest` objetos e exibe as informações de DNS ou <xref:System.Net.Sockets.SocketException> mensagem de erro.  
  
 [!code-csharp[AsyncDesignPattern#5](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/AsyncDelegateWithStateObject.cs#5)]
 [!code-vb[AsyncDesignPattern#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/AsyncDelegateWithStateObject.vb#5)]  
  
## <a name="see-also"></a>Consulte também  
 [EAP (Padrão Assíncrono baseado em Evento)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 [Visão Geral do Padrão Assíncrono Baseado em Evento](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)  
 [Usando um representante AsyncCallback para finalizar uma operação assíncrona](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md)
