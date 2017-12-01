---
title: "Chamando métodos síncronos de forma assíncrona"
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
- cpp
helpviewer_keywords:
- asynchronous programming, delegates
- asynchronous delegates
- AsyncWaitHandle property
- callback methods
- calling synchronous methods in asynchronous manner
- WaitHandle class, code examples
- asynchronous programming, status polling
- polling asynchronous operation status
- delegates [.NET Framework], asynchronous
- synchronous calling in asynchronous manner
- waiting for asynchronous calls
- status information [.NET Framework], asynchronous operations
ms.assetid: 41972034-92ed-450a-9664-ab93fcc6f1fb
caps.latest.revision: "24"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 965e5928c03ae573eacba98a7596f55b56aaba26
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="calling-synchronous-methods-asynchronously"></a>Chamando métodos síncronos de forma assíncrona
O .NET Framework permite que você chamar qualquer método de forma assíncrona. Para fazer isso, você define um delegado com a mesma assinatura do método que você deseja chamar; o common language runtime automaticamente define `BeginInvoke` e `EndInvoke` métodos para este delegado, com as assinaturas apropriadas.  
  
> [!NOTE]
>  Chamadas assíncrono delegado, especificamente o `BeginInvoke` e `EndInvoke` métodos não têm suporte no .NET Compact Framework.  
  
 O `BeginInvoke` método inicia a chamada assíncrona. Ele tem os mesmos parâmetros que o método que você deseja executar de forma assíncrona, além de dois parâmetros opcionais adicionais. O primeiro parâmetro é um <xref:System.AsyncCallback> delegado que faz referência a um método a ser chamado quando a chamada assíncrona é concluída. O segundo parâmetro é um objeto definido pelo usuário que passa informações para o método de retorno de chamada. `BeginInvoke`retorna imediatamente e não espera para concluir a chamada assíncrona. `BeginInvoke`Retorna um <xref:System.IAsyncResult>, que pode ser usado para monitorar o andamento da chamada assíncrona.  
  
 O `EndInvoke` método recupera os resultados da chamada assíncrona. Ele pode ser chamado a qualquer momento após `BeginInvoke`. Se a chamada assíncrona não for concluída, `EndInvoke` bloqueia o thread de chamada até que ela seja concluída. Os parâmetros de `EndInvoke` incluem o `out` e `ref` parâmetros (`<Out>` `ByRef` e `ByRef` no Visual Basic) do método que você deseja executar de forma assíncrona, mais o <xref:System.IAsyncResult> retornado por `BeginInvoke`.  
  
> [!NOTE]
>  Recurso IntelliSense no [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] exibe os parâmetros de `BeginInvoke` e `EndInvoke`. Se você não estiver usando o Visual Studio ou uma ferramenta semelhante, ou se você estiver usando c# com [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)], consulte [modelo de programação assíncrona (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md) para obter uma descrição dos parâmetros definidos para esses métodos.  
  
 Os exemplos de código neste tópico demonstram quatro formas comuns de usar `BeginInvoke` e `EndInvoke` para fazer chamadas assíncronas. Depois de chamar `BeginInvoke` pode fazer o seguinte:  
  
-   Alguns trabalhar e, em seguida, chame `EndInvoke` para bloquear até que a chamada é concluída.  
  
-   Obter um <xref:System.Threading.WaitHandle> usando o <xref:System.IAsyncResult.AsyncWaitHandle%2A?displayProperty=nameWithType> propriedade, use seu <xref:System.Threading.WaitHandle.WaitOne%2A> método para impedir a execução até que o <xref:System.Threading.WaitHandle> é sinalizado e, em seguida, chame `EndInvoke`.  
  
-   Sondagem de <xref:System.IAsyncResult> retornado por `BeginInvoke` para determinar quando a chamada assíncrona é concluída e, em seguida, chame `EndInvoke`.  
  
-   Transmitir um delegado para um método de retorno de chamada para `BeginInvoke`. O método é executado em um <xref:System.Threading.ThreadPool> thread quando a chamada assíncrona é concluída. As chamadas de método de retorno de chamada `EndInvoke`.  
  
> [!IMPORTANT]
>  Não importa qual técnica de você usar, sempre chamar `EndInvoke` para completar a chamada assíncrona.  
  
## <a name="defining-the-test-method-and-asynchronous-delegate"></a>Definir o método de teste e o representante assíncrono  
 Os exemplos de código a seguirem demonstram várias maneiras de chamar o mesmo método de execução longa, `TestMethod`, de forma assíncrona. O `TestMethod` método exibe uma mensagem de console para mostrar que ele começou a processar, dormem por alguns segundos e, em seguida, termina. `TestMethod`tem um `out` parâmetro para demonstrar a maneira como esses parâmetros são adicionados às assinaturas dos `BeginInvoke` e `EndInvoke`. Você pode manipular `ref` parâmetros da mesma forma.  
  
 O exemplo de código a seguir mostra a definição de `TestMethod` e o representante chamado `AsyncMethodCaller` que pode ser usado para chamar `TestMethod` assincronamente. Para compilar os exemplos de código, você deve incluir as definições de `TestMethod` e `AsyncMethodCaller` delegate.  
  
 [!code-cpp[AsyncDelegateExamples#1](../../../samples/snippets/cpp/VS_Snippets_CLR/AsyncDelegateExamples/cpp/TestMethod.cpp#1)]
 [!code-csharp[AsyncDelegateExamples#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDelegateExamples/CS/TestMethod.cs#1)]
 [!code-vb[AsyncDelegateExamples#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDelegateExamples/VB/TestMethod.vb#1)]  
  
## <a name="waiting-for-an-asynchronous-call-with-endinvoke"></a>Esperando por uma chamada assíncrona com EndInvoke  
 É a maneira mais simples de executar um método de forma assíncrona iniciar a execução do método chamando o delegado `BeginInvoke` método, algumas trabalhar no thread principal e, em seguida, chamar o delegado `EndInvoke` método. `EndInvoke`podem bloquear o thread de chamada porque ela não retorna até que a chamada assíncrona é concluída. Essa é uma técnica válida para usar com operações de arquivo ou de rede.  
  
> [!IMPORTANT]
>  Como `EndInvoke` podem bloquear, você nunca deve chamá-lo de threads que a interface do usuário do serviço.  
  
 [!code-cpp[AsyncDelegateExamples#2](../../../samples/snippets/cpp/VS_Snippets_CLR/AsyncDelegateExamples/cpp/EndInvoke.cpp#2)]
 [!code-csharp[AsyncDelegateExamples#2](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDelegateExamples/CS/EndInvoke.cs#2)]
 [!code-vb[AsyncDelegateExamples#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDelegateExamples/VB/EndInvoke.vb#2)]  
  
## <a name="waiting-for-an-asynchronous-call-with-waithandle"></a>Esperando por uma chamada assíncrona com WaitHandle  
 Você pode obter um <xref:System.Threading.WaitHandle> usando o <xref:System.IAsyncResult.AsyncWaitHandle%2A> propriedade o <xref:System.IAsyncResult> retornado por `BeginInvoke`. O <xref:System.Threading.WaitHandle> é sinalizado quando a chamada assíncrona é concluída, e você pode esperar para que ele ao chamar o <xref:System.Threading.WaitHandle.WaitOne%2A> método.  
  
 Se você usar um <xref:System.Threading.WaitHandle>, você pode executar processamento adicional antes ou depois que a chamada assíncrona é concluída, mas antes de chamar `EndInvoke` para recuperar os resultados.  
  
> [!NOTE]
>  O identificador de espera não é fechado automaticamente quando você chama `EndInvoke`. Se você liberar todas as referências para o identificador de espera, recursos de sistema são liberados quando a coleta de lixo recupera o identificador de espera. Para liberar os recursos do sistema, assim que terminar de usar o identificador de espera, descarte-lo chamando o <xref:System.Threading.WaitHandle.Close%2A?displayProperty=nameWithType> método. Coleta de lixo funciona com mais eficiência quando objetos descartáveis explicitamente são descartados.  
  
 [!code-cpp[AsyncDelegateExamples#3](../../../samples/snippets/cpp/VS_Snippets_CLR/AsyncDelegateExamples/cpp/waithandle.cpp#3)]
 [!code-csharp[AsyncDelegateExamples#3](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDelegateExamples/CS/waithandle.cs#3)]
 [!code-vb[AsyncDelegateExamples#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDelegateExamples/VB/WaitHandle.vb#3)]  
  
## <a name="polling-for-asynchronous-call-completion"></a>Sondagem de conclusão de chamada assíncrona  
 Você pode usar o <xref:System.IAsyncResult.IsCompleted%2A> propriedade o <xref:System.IAsyncResult> retornado por `BeginInvoke` para descobrir quando a chamada assíncrona é concluída. Você pode fazer isso ao fazer a chamada assíncrona de um thread que a interface do usuário de serviços. Sondagem para conclusão permite que o thread de chamada continuar a executar quando a chamada assíncrona é executado em um <xref:System.Threading.ThreadPool> thread.  
  
 [!code-cpp[AsyncDelegateExamples#4](../../../samples/snippets/cpp/VS_Snippets_CLR/AsyncDelegateExamples/cpp/polling.cpp#4)]
 [!code-csharp[AsyncDelegateExamples#4](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDelegateExamples/CS/polling.cs#4)]
 [!code-vb[AsyncDelegateExamples#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDelegateExamples/VB/polling.vb#4)]  
  
## <a name="executing-a-callback-method-when-an-asynchronous-call-completes"></a>Executar um método de retorno de chamada quando uma chamada assíncrona é concluída  
 Se o thread que inicia a chamada assíncrona não precisa ser o thread que processa os resultados, você pode executar um método de retorno de chamada quando a chamada é concluída. O método de retorno de chamada é executado em um <xref:System.Threading.ThreadPool> thread.  
  
 Para usar um método de retorno de chamada, você deve passar `BeginInvoke` um <xref:System.AsyncCallback> delegado que representa o método de retorno de chamada. Você também pode passar um objeto que contém as informações a serem usadas pelo método de retorno de chamada. O método de retorno de chamada, você pode converter o <xref:System.IAsyncResult>, que é o único parâmetro do método de retorno de chamada, um <xref:System.Runtime.Remoting.Messaging.AsyncResult> objeto. Você pode usar o <xref:System.Runtime.Remoting.Messaging.AsyncResult.AsyncDelegate%2A?displayProperty=nameWithType> propriedade para obter o delegado que foi usado para iniciar a chamada para que você possa chamar `EndInvoke`.  
  
 Observações sobre o exemplo:  
  
-   O `threadId` parâmetro `TestMethod` é um `out` parâmetro ([`<Out>` `ByRef` no Visual Basic), portanto, sua entrada valor nunca é usado pelo `TestMethod`. Uma variável fictícia é passada para o `BeginInvoke` chamar. Se o `threadId` parâmetro foram um `ref` parâmetro (`ByRef` no Visual Basic), a variável precisa ser um campo de nível de classe para que ele pode ser passado para ambos os `BeginInvoke` e `EndInvoke`.  
  
-   As informações de estado que são passadas para `BeginInvoke` é uma cadeia de caracteres de formato, que usa o método de retorno de chamada para formatar uma mensagem de saída. Porque ele é passado como tipo <xref:System.Object>, as informações de estado devem ser convertidas para o tipo correto antes de ser usada.  
  
-   O retorno de chamada é feito em um <xref:System.Threading.ThreadPool> thread. <xref:System.Threading.ThreadPool>threads são threads em segundo plano, o que não mantém o aplicativo em execução se o thread principal terminar, portanto o thread principal do exemplo tem no estado de suspensão tempo suficiente para o retorno de chamada concluir.  
  
 [!code-cpp[AsyncDelegateExamples#5](../../../samples/snippets/cpp/VS_Snippets_CLR/AsyncDelegateExamples/cpp/callback.cpp#5)]
 [!code-csharp[AsyncDelegateExamples#5](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDelegateExamples/CS/callback.cs#5)]
 [!code-vb[AsyncDelegateExamples#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDelegateExamples/VB/callback.vb#5)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Delegate>  
 [EAP (Padrão Assíncrono baseado em Evento)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
