---
title: Usando um delegado AsyncCallback e um objeto de estado
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- asynchronous programming, delegates
- AsyncCallback delegate, samples
- asynchronous programming, state objects
- IAsyncResult interface, samples
ms.assetid: e3e5475d-c5e9-43f0-928e-d18df8ca1f1d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 259f7de52dff04af043554382a5bad35355d9926
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33567231"
---
# <a name="using-an-asynccallback-delegate-and-state-object"></a>Usando um delegado AsyncCallback e um objeto de estado
Ao usar um representante <xref:System.AsyncCallback> para processar os resultados da operação assíncrona em um thread separado, você pode usar um objeto de estado para passar informações entre os retornos de chamada e recuperar um resultado final. Este tópico demonstra essa prática expandindo o exemplo em [Usando um representante AsyncCallback para finalizar uma operação assíncrona](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir demonstra como usar métodos assíncronos na classe <xref:System.Net.Dns> para recuperar informações do DNS (Sistema de Nomes de Domínio) de computadores especificados pelo usuário. Este exemplo define e usa a classe `HostRequest` para armazenar informações de estado. Um objeto `HostRequest` é criado para cada nome de computador inserido pelo usuário. Este objeto é passado para o método <xref:System.Net.Dns.BeginGetHostByName%2A>. O método `ProcessDnsInformation` é chamado sempre que uma solicitação é concluída. O objeto `HostRequest` é recuperado usando a propriedade <xref:System.IAsyncResult.AsyncState%2A>. O método `ProcessDnsInformation` usa o objeto `HostRequest` para armazenar o retornado <xref:System.Net.IPHostEntry> pela solicitação ou um <xref:System.Net.Sockets.SocketException> lançado pela solicitação. Quando todas as solicitações são concluídas, o aplicativo faz a iteração pelos objetos `HostRequest` e exibe as informações de DNS ou a mensagem de erro <xref:System.Net.Sockets.SocketException>.  
  
 [!code-csharp[AsyncDesignPattern#5](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/AsyncDelegateWithStateObject.cs#5)]
 [!code-vb[AsyncDesignPattern#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/AsyncDelegateWithStateObject.vb#5)]  
  
## <a name="see-also"></a>Consulte também  
 [EAP (Padrão Assíncrono baseado em Evento)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 [Visão Geral do Padrão Assíncrono Baseado em Evento](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)  
 [Usando um representante AsyncCallback para finalizar uma operação assíncrona](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md)
