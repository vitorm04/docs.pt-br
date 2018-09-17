---
title: Modelo de programação assíncrona (APM)
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- ending asynchronous operations
- starting asynchronous operations
- beginning asynchronous operations
- asynchronous programming, ending operations
- asynchronous programming
- stopping asynchronous operations
- asynchronous programming, beginning operations
ms.assetid: c9b3501e-6bc6-40f9-8efd-4b6d9e39ccf0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5cd2fa6219f39a8506d865d85e1ce5f84d22a92f
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45698364"
---
# <a name="asynchronous-programming-model-apm"></a>Modelo de programação assíncrona (APM)
Uma operação assíncrona que usa o padrão de design <xref:System.IAsyncResult> é implementada como dois métodos chamados **Begin***OperationName* e **End***OperationName* que começam e terminam a operação assíncrona *OperationName*, respectivamente. Por exemplo, a classe <xref:System.IO.FileStream> fornece os métodos <xref:System.IO.FileStream.BeginRead%2A> e <xref:System.IO.FileStream.EndRead%2A> para ler os bytes de um arquivo de forma assíncrona. Esses métodos implementam a versão assíncrona do método <xref:System.IO.FileStream.Read%2A>.  
  
> [!NOTE]
>  A partir do .NET Framework 4, a Biblioteca de Paralelismo de Tarefas fornece um novo modelo de programação paralela e assíncrona. Para saber mais, confira [Biblioteca de Paralelismo de Tarefas (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md) e [Padrão Assíncrono Baseado em Tarefa (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md).  
  
 Depois de chamar **Begin***OperationName*, um aplicativo pode continuar executando as instruções no thread de chamada, enquanto a operação assíncrona ocorre em outro thread. Para cada chamada a **Begin***OperationName*, o aplicativo também deve chamar **End***OperationName* para obter os resultados da operação.  
  
## <a name="beginning-an-asynchronous-operation"></a>Começando uma operação assíncrona  
 O método **Begin***OperationName* inicia a operação assíncrona *OperationName* e retorna um objeto que implementa a interface <xref:System.IAsyncResult>. Os objetos <xref:System.IAsyncResult> armazenam as informações sobre uma operação assíncrona. A tabela a seguir mostra informações sobre uma operação assíncrona.  
  
|Membro|Descrição|  
|------------|-----------------|  
|<xref:System.IAsyncResult.AsyncState%2A>|Um objeto específico do aplicativo opcional que contém informações sobre a operação assíncrona.|  
|<xref:System.IAsyncResult.AsyncWaitHandle%2A>|Um <xref:System.Threading.WaitHandle> que pode ser usado para bloquear a execução do aplicativo até que a operação assíncrona seja concluída.|  
|<xref:System.IAsyncResult.CompletedSynchronously%2A>|Um valor que indica se a operação assíncrona foi concluída no thread usado para chamar **Begin***OperationName*, em vez de concluir em um thread <xref:System.Threading.ThreadPool> separado.|  
|<xref:System.IAsyncResult.IsCompleted%2A>|Um valor que indica se a operação assíncrona foi concluída.|  
  
 Um método **Begin***OperationName* usa os parâmetros declarados na assinatura da versão síncrona do método que são passados por valor ou por referência. Os parâmetros de saída não fazem parte da assinatura do método **Begin***OperationName*. A assinatura do método **Begin***OperationName* também inclui dois parâmetros adicionais. O primeiro deles define um delegado <xref:System.AsyncCallback> que faz referência a um método que é chamado quando a operação assíncrona é concluída. O chamador pode especificar `null` (`Nothing` no Visual Basic) se não desejar um método chamado quando a operação for concluída. O segundo parâmetro adicional é um objeto definido pelo usuário. Esse objeto pode ser usado para passar informações de estado específico do aplicativo para o método invocado quando a operação assíncrona é concluída. Se um método **Begin***OperationName* usa parâmetros adicionais específicos a uma operação, como uma matriz de bytes para armazenar os bytes lidos de um arquivo, o <xref:System.AsyncCallback> e o objeto de estado do aplicativo são os últimos parâmetros da assinatura do método **Begin***OperationName*.  
  
 **Begin***OperationName* retorna o controle para o thread de chamada imediatamente. Se o método **Begin***OperationName* gera exceções, as exceções são geradas antes de a operação assíncrona ser iniciada. Se o método **Begin***OperationName* gera exceções, o método de retorno de chamada não é invocado.  
  
## <a name="ending-an-asynchronous-operation"></a>Encerrando uma operação assíncrona  
 O método **End***OperationName* termina a operação assíncrona *OperationName*. O valor retornado do método **End***OperationName* é do mesmo tipo retornado pelo seu equivalente síncrono e é específico à operação assíncrona. Por exemplo, o método <xref:System.IO.FileStream.EndRead%2A> retorna o número de bytes lidos de um <xref:System.IO.FileStream> e o método <xref:System.Net.Dns.EndGetHostByName%2A> retorna um objeto <xref:System.Net.IPHostEntry> que contém informações sobre um computador host. O método **End***OperationName* usa os parâmetros de saída ou referência declarados na assinatura da versão síncrona do método. Além dos parâmetros do método síncrono, o método **End***OperationName* também inclui um parâmetro <xref:System.IAsyncResult>. Os chamadores precisam passar a instância retornada pela chamada correspondente para **Begin***OperationName*.  
  
 Se a operação assíncrona representada pelo objeto <xref:System.IAsyncResult> não tiver sido concluída quando **End***OperationName* for chamado, **End***OperationName* bloqueará o thread de chamada até que a operação assíncrona seja concluída. As exceções geradas pela operação assíncrona são geradas do método **End***OperationName*. O efeito da chamada ao método **End***OperationName* várias vezes com o mesmo <xref:System.IAsyncResult> não está definido. Da mesma forma, a chamada ao método **End***OperationName* com um <xref:System.IAsyncResult> que não foi retornado pelo método Begin relacionado também não está definido.  
  
> [!NOTE]
>  Para qualquer um dos cenários indefinidos, os implementadores devem considerar a geração de <xref:System.InvalidOperationException>.  
  
> [!NOTE]
>  Os implementadores deste padrão de design devem notificar o chamador de que a operação assíncrona está concluída, definindo <xref:System.IAsyncResult.IsCompleted%2A> como true, chamando o método de retorno de chamada assíncrono (se tiver sido especificado) e sinalizando o <xref:System.IAsyncResult.AsyncWaitHandle%2A>.  
  
 Os desenvolvedores de aplicativos tem várias opções de design para acessar os resultados da operação assíncrona. A opção correta depende se o aplicativo tem instruções que podem ser executadas enquanto a operação é concluída. Se um aplicativo não puder executar trabalho adicional até que ele receba os resultados da operação assíncrona, o aplicativo deverá ser bloqueado até que os resultados estejam disponíveis. Para bloquear até que uma operação assíncrona seja concluída, você poderá usar uma das seguintes abordagens:  
  
-   Chame **End***OperationName* do thread principal do aplicativo, bloqueando a execução do aplicativo até que a operação seja concluída. Veja um exemplo que ilustra essa técnica em [Bloqueando a execução de um aplicativo encerrando uma operação assíncrona](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-by-ending-an-async-operation.md).  
  
-   Use o <xref:System.IAsyncResult.AsyncWaitHandle%2A> para impedir a execução do aplicativo até que uma ou mais operações sejam concluídas. Veja um exemplo que ilustra essa técnica em [Bloqueando a execução de um aplicativo com um AsyncWaitHandle](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-using-an-asyncwaithandle.md).  
  
 Os aplicativos que não precisarem ser bloqueados enquanto a operação assíncrona é concluída podem usar uma das seguintes abordagens:  
  
-   Sonde o status de conclusão da operação verificando a propriedade <xref:System.IAsyncResult.IsCompleted%2A> periodicamente e chamando **End***OperationName* quando a operação for concluída. Veja um exemplo que ilustra essa técnica em [Sondagem do status de uma operação assíncrona](../../../docs/standard/asynchronous-programming-patterns/polling-for-the-status-of-an-asynchronous-operation.md).  
  
-   Use um delegado <xref:System.AsyncCallback> para especificar um método a ser invocado quando a operação for concluída. Veja um exemplo que ilustra essa técnica em [Usar um representante AsyncCallback para finalizar uma operação assíncrona](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).  
  
## <a name="see-also"></a>Consulte também

- [EAP (Padrão Assíncrono baseado em Evento)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
- [Chamando métodos síncronos de forma assíncrona](../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)  
- [Usando um representante AsyncCallback e um objeto de estado](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-and-state-object.md)
