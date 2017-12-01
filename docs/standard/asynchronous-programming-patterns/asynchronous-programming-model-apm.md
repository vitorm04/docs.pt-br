---
title: "Modelo de programação assíncrona (APM)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ending asynchronous operations
- starting asynchronous operations
- beginning asynchronous operations
- asynchronous programming, ending operations
- asynchronous programming
- stopping asynchronous operations
- asynchronous programming, beginning operations
ms.assetid: c9b3501e-6bc6-40f9-8efd-4b6d9e39ccf0
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b31383f8972ecf345366f90460d88b6be21eab99
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="asynchronous-programming-model-apm"></a>Modelo de programação assíncrona (APM)
Uma operação assíncrona que utiliza o <xref:System.IAsyncResult> padrão de design é implementado como dois métodos chamados **começar** *OperationName* e **final**  *OperationName* que começam e terminam a operação assíncrona *OperationName* respectivamente. Por exemplo, o <xref:System.IO.FileStream> classe fornece a <xref:System.IO.FileStream.BeginRead%2A> e <xref:System.IO.FileStream.EndRead%2A> métodos para ler os bytes de um arquivo de forma assíncrona. Esses métodos de implementam a versão assíncrona do <xref:System.IO.FileStream.Read%2A> método.  
  
> [!NOTE]
>  Começando com o .NET Framework 4, a biblioteca paralela de tarefas fornece um novo modelo de programação assíncrona e paralela. Para obter mais informações, consulte [tarefa TPL (biblioteca paralela)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md) e [padrão assíncrono baseado em tarefa (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)).  
  
 Depois de chamar **começar** *OperationName*, um aplicativo pode continuar a executar as instruções no thread de chamada, enquanto a operação assíncrona ocorre em um thread diferente. Cada chamada para **começar** *OperationName*, o aplicativo também deve chamar **final** *OperationName* para obter os resultados das operação.  
  
## <a name="beginning-an-asynchronous-operation"></a>A partir de uma operação assíncrona  
 O **começar** *OperationName* método inicia a operação assíncrona *OperationName* e retorna um objeto que implementa o <xref:System.IAsyncResult> interface. <xref:System.IAsyncResult>objetos armazenam informações sobre uma operação assíncrona. A tabela a seguir mostra informações sobre uma operação assíncrona.  
  
|Membro|Descrição|  
|------------|-----------------|  
|<xref:System.IAsyncResult.AsyncState%2A>|Um objeto específico do aplicativo opcional que contém informações sobre a operação assíncrona.|  
|<xref:System.IAsyncResult.AsyncWaitHandle%2A>|Um <xref:System.Threading.WaitHandle> que pode ser usado para bloquear a execução do aplicativo até que a operação assíncrona é concluída.|  
|<xref:System.IAsyncResult.CompletedSynchronously%2A>|Um valor que indica se a operação assíncrona foi concluída no thread usado para chamar **começar** *OperationName* em vez de concluir em uma separada <xref:System.Threading.ThreadPool> thread.|  
|<xref:System.IAsyncResult.IsCompleted%2A>|Um valor que indica se a operação assíncrona foi concluída.|  
  
 Um **começar** *OperationName* método usa qualquer declarados na assinatura da versão síncrona do método de parâmetros que são passados por valor ou por referência. Quaisquer parâmetros de saída não são parte do **começar** *OperationName* assinatura do método. O **começar** *OperationName* assinatura do método também inclui dois parâmetros adicionais. O primeiro deles define uma <xref:System.AsyncCallback> delegado que faz referência a um método que é chamado quando a operação assíncrona for concluída. O chamador pode especificar `null` (`Nothing` no Visual Basic) se não desejar um método chamado quando a operação for concluída. O segundo parâmetro adicional é um objeto definido pelo usuário. Esse objeto pode ser usado para passar informações de estado específico do aplicativo para o método invocado quando a operação assíncrona é concluída. Se um **começar** *OperationName* método usa parâmetros específicos de operação adicionais, como uma matriz de bytes para armazenar os bytes lidos de um arquivo, o <xref:System.AsyncCallback> e o objeto de estado do aplicativo são as últimas parâmetros de **começar** *OperationName* assinatura do método.  
  
 **Iniciar** *OperationName* retorna o controle para o thread de chamada imediatamente. Se o **começar** *OperationName* método lança exceções, as exceções são lançadas antes da operação assíncrona é iniciada. Se o **começar** *OperationName* método lança exceções, o método de retorno de chamada não é invocado.  
  
## <a name="ending-an-asynchronous-operation"></a>Finalizando uma operação assíncrona  
 O **final** *OperationName* método termina a operação assíncrona *OperationName*. O valor de retorno de **final** *OperationName* método é do mesmo tipo retornado pela sua contraparte síncrona e é específico para a operação assíncrona. Por exemplo, o <xref:System.IO.FileStream.EndRead%2A> método retorna o número de bytes lidos de um <xref:System.IO.FileStream> e o <xref:System.Net.Dns.EndGetHostByName%2A> método retorna um <xref:System.Net.IPHostEntry> objeto que contém informações sobre um computador host. O **final** *OperationName* método usa qualquer ou parâmetros ref é declarada na assinatura da versão síncrona do método. Além dos parâmetros do método síncrono, o **final** *OperationName* método também inclui um <xref:System.IAsyncResult> parâmetro. Os chamadores devem passar a instância retornada pela chamada correspondente para **começar** *OperationName*.  
  
 Se a operação assíncrona representados pelo <xref:System.IAsyncResult> objeto não foi concluída quando **final** *OperationName* é chamado, **final**  *OperationName* bloqueia o thread de chamada até que a operação assíncrona é concluída. Exceções geradas pela operação assíncrona são geradas do **final** *OperationName* método. O efeito da chamada a **final** *OperationName* método várias vezes com o mesmo <xref:System.IAsyncResult> não está definido. Da mesma forma, ao chamar o **final** *OperationName* método com um <xref:System.IAsyncResult> que não retornou de Begin relacionado método também não está definido.  
  
> [!NOTE]
>  Para qualquer um dos cenários indefinidos, implementadores considere gerar <xref:System.InvalidOperationException>.  
  
> [!NOTE]
>  Os implementadores de padrão de design devem notificar o chamador que a operação assíncrona é concluída, definindo <xref:System.IAsyncResult.IsCompleted%2A> como true, chamar o método de retorno de chamada assíncrono (se tiver sido especificado) e a sinalização de <xref:System.IAsyncResult.AsyncWaitHandle%2A>.  
  
 Os desenvolvedores de aplicativos tem várias opções de design para acessar os resultados da operação assíncrona. A opção correta depende se o aplicativo tem instruções que podem ser executados enquanto a operação é concluída. Se um aplicativo não pode executar qualquer trabalho adicional até que ele recebe os resultados da operação assíncrona, o aplicativo deve bloquear até que os resultados estão disponíveis. Para bloquear até que uma operação assíncrona é concluída, você pode usar uma das seguintes abordagens:  
  
-   Chamar **final** *OperationName* do thread de principal do aplicativo, bloqueando a execução do aplicativo até que a operação for concluída. Para obter um exemplo que ilustra essa técnica, consulte [bloqueando a execução de aplicativos por finalizando uma operação assíncrona](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-by-ending-an-async-operation.md).  
  
-   Use o <xref:System.IAsyncResult.AsyncWaitHandle%2A> para impedir a execução de aplicativo até que uma ou mais operações sejam concluídas. Para obter um exemplo que ilustra essa técnica, consulte [bloqueando a execução de aplicativo com um AsyncWaitHandle](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-using-an-asyncwaithandle.md).  
  
 Aplicativos que não é necessário bloquear enquanto a operação assíncrona é concluída podem usar uma das seguintes abordagens:  
  
-   Sondagem de status de conclusão da operação, verificando o <xref:System.IAsyncResult.IsCompleted%2A> propriedade periodicamente e chamar **final** *OperationName* quando a operação for concluída. Para obter um exemplo que ilustra essa técnica, consulte [sondagem do status de uma operação assíncrona](../../../docs/standard/asynchronous-programming-patterns/polling-for-the-status-of-an-asynchronous-operation.md).  
  
-   Use um <xref:System.AsyncCallback> delegado para especificar um método a ser invocado quando a operação for concluída. Para obter um exemplo que ilustra essa técnica, consulte [usando um delegado AsyncCallback para finalizar uma operação assíncrona](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).  
  
## <a name="see-also"></a>Consulte também  
 [EAP (Padrão Assíncrono baseado em Evento)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 [Chamando métodos síncronos de forma assíncrona](../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)  
 [Usando um representante AsyncCallback e um objeto de estado](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-and-state-object.md)
