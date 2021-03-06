---
title: Interoperabilidade com outros tipos e padrões assíncronos
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- asynchronous design patterns, .NET
- TAP, .NET support for
- Task-based Asynchronous Pattern, .NET support for
- .NET, asynchronous design patterns
ms.assetid: f120a5d9-933b-4d1d-acb6-f034a57c3749
ms.openlocfilehash: 5ad49c70aaa69d8a4f830851b80b6a4839388b0f
ms.sourcegitcommit: 4a938327bad8b2e20cabd0f46a9dc50882596f13
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/28/2020
ms.locfileid: "92888744"
---
# <a name="interop-with-other-asynchronous-patterns-and-types"></a>Interoperabilidade com outros tipos e padrões assíncronos

Um breve histórico dos padrões assíncronos no .NET:

- .NET Framework 1,0 introduziu o <xref:System.IAsyncResult> padrão, também conhecido como o [modelo de programação assíncrona (APM)](asynchronous-programming-model-apm.md)ou o `Begin/End` padrão.
- .NET Framework 2,0 adicionou o [padrão assíncrono baseado em evento (EAP)](event-based-asynchronous-pattern-eap.md).
- O .NET Framework 4 introduziu o [padrão assíncrono baseado em tarefa (TAP)](task-based-asynchronous-pattern-tap.md), que substitui o APM e o EAP e fornece a capacidade de criar facilmente rotinas de migração a partir dos padrões anteriores.
  
## <a name="tasks-and-the-asynchronous-programming-model-apm"></a>Tarefas e APM (Modelo Assíncrono de Programação)

### <a name="from-apm-to-tap"></a>De APM para TAP  
 Como o padrão do [modelo de programação assíncrona (APM)](asynchronous-programming-model-apm.md) é estruturado, é muito fácil criar um wrapper para expor uma implementação de APM como uma implementação de toque. O .NET Framework 4 e versões posteriores incluem rotinas auxiliares na forma de <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A> sobrecargas de método para fornecer essa tradução.  
  
 Considere a classe <xref:System.IO.Stream> e seus métodos <xref:System.IO.Stream.BeginRead%2A> e <xref:System.IO.Stream.EndRead%2A>, que representam a contrapartida do APM para o método síncrono <xref:System.IO.Stream.Read%2A>:  
  
 [!code-csharp[Conceptual.AsyncInterop#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Stream1.cs#1)]
 [!code-vb[Conceptual.AsyncInterop#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/stream1.vb#1)]  
[!code-csharp[Conceptual.AsyncInterop#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Stream1.cs#2)]
[!code-vb[Conceptual.AsyncInterop#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/stream1.vb#2)]  
[!code-csharp[Conceptual.AsyncInterop#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Stream1.cs#3)]
[!code-vb[Conceptual.AsyncInterop#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/stream1.vb#3)]  
  
 Você pode usar o método <xref:System.Threading.Tasks.TaskFactory%601.FromAsync%2A?displayProperty=nameWithType> para implementar um wrapper do TAP para essa operação da seguinte maneira:  
  
 [!code-csharp[Conceptual.AsyncInterop#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wrap1.cs#4)]
 [!code-vb[Conceptual.AsyncInterop#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wrap1.vb#4)]  
  
 Essa implementação é semelhante ao seguinte:  
  
 [!code-csharp[Conceptual.AsyncInterop#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wrap2.cs#5)]
 [!code-vb[Conceptual.AsyncInterop#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wrap2.vb#5)]  
  
### <a name="from-tap-to-apm"></a>De TAP para APM  
 Se a infraestrutura existente esperar o padrão APM, convém também pegar uma implementação do TAP e usá-la onde uma implementação do APM é esperada.  Como as tarefas podem ser compostas e a classe <xref:System.Threading.Tasks.Task> implementa o <xref:System.IAsyncResult>, você pode usar uma função auxiliar simples para fazer isso. O código a seguir usa uma extensão da classe <xref:System.Threading.Tasks.Task%601>, mas você pode usar uma função quase idêntica para tarefas não genéricas.  
  
 [!code-csharp[Conceptual.AsyncInterop#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM1.cs#6)]
 [!code-vb[Conceptual.AsyncInterop#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM1.vb#6)]  
  
 Agora, considere um caso onde você tem a seguinte implementação do TAP:  
  
 [!code-csharp[Conceptual.AsyncInterop#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#7)]
 [!code-vb[Conceptual.AsyncInterop#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#7)]  
  
 e você deseja oferecer essa implementação do APM:  
  
 [!code-csharp[Conceptual.AsyncInterop#8](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#8)]
 [!code-vb[Conceptual.AsyncInterop#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#8)]  
[!code-csharp[Conceptual.AsyncInterop#9](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#9)]
[!code-vb[Conceptual.AsyncInterop#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#9)]  
  
 O exemplo a seguir demonstra uma migração para APM:  
  
 [!code-csharp[Conceptual.AsyncInterop#10](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#10)]
 [!code-vb[Conceptual.AsyncInterop#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#10)]  
  
## <a name="tasks-and-the-event-based-asynchronous-pattern-eap"></a>Tarefas e o EAP (Padrão assíncrono baseado em evento)  
 Dispor uma implementação do [EAP (Padrão assíncrono baseado em evento)](event-based-asynchronous-pattern-eap.md) é mais envolvente do que dispor um padrão do APM porque o padrão EAP possui mais variações e menos estrutura do que o padrão APM.  Para demonstrar, o código a seguir se dispõe ao redor do método `DownloadStringAsync`.  `DownloadStringAsync` aceita um URI, gera o evento `DownloadProgressChanged` durante o download para oferecer várias estatísticas sobre o andamento e, quando tiver terminado, gera o evento `DownloadStringCompleted`.  O resultado final é uma cadeia de caracteres que contém o conteúdo da página no URI especificado.  
  
 [!code-csharp[Conceptual.AsyncInterop#11](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/EAP1.cs#11)]
 [!code-vb[Conceptual.AsyncInterop#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/EAP1.vb#11)]  
  
## <a name="tasks-and-wait-handles"></a>Tarefas e identificadores de espera  
  
### <a name="from-wait-handles-to-tap"></a>De Identificadores de espera para TAP  
 Embora os identificadores de espera não implementem um padrão assíncrono, os desenvolvedores avançados podem usar a classe <xref:System.Threading.WaitHandle> e o método <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A?displayProperty=nameWithType> em notificações assíncronas quando um identificador de espera estiver definido.  Você pode dispor o método <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A> para habilitar uma alternativa baseada em tarefa para qualquer espera síncrona em um identificador de espera:  
  
 [!code-csharp[Conceptual.AsyncInterop#12](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wait1.cs#12)]
 [!code-vb[Conceptual.AsyncInterop#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wait1.vb#12)]  
  
 Com esse método, você pode usar implementações <xref:System.Threading.WaitHandle> existentes em métodos assíncronos.  Por exemplo, se quiser limitar o número de operações assíncronas que são executadas em um determinado momento, você pode utilizar um semáforo (um objeto <xref:System.Threading.SemaphoreSlim?displayProperty=nameWithType>).  Você pode limitar a *N* o número de operações que são executadas simultaneamente inicializando a contagem do semáforo como *N* , aguardando o semáforo sempre que você desejar executar uma operação e liberando o semáforo quando terminar com uma operação:  
  
 [!code-csharp[Conceptual.AsyncInterop#13](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Semaphore1.cs#13)]
 [!code-vb[Conceptual.AsyncInterop#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Semaphore1.vb#13)]  
  
 Você também pode criar um semáforo assíncrono que não depende de identificadores de espera e só trabalha com tarefas. Para fazer isso, você pode usar técnicas, como aquelas discutidas em [Consumir o Padrão assíncrono baseado em tarefa](consuming-the-task-based-asynchronous-pattern.md), para criar estruturas de dados em cima de <xref:System.Threading.Tasks.Task>.  
  
### <a name="from-tap-to-wait-handles"></a>De TAP para Identificadores de espera  
 Conforme mencionado anteriormente, a classe <xref:System.Threading.Tasks.Task> implementa o <xref:System.IAsyncResult> e essa implementação expõe uma propriedade <xref:System.Threading.Tasks.Task.System%23IAsyncResult%23AsyncWaitHandle%2A> que retorna um identificador de espera que será definido quando <xref:System.Threading.Tasks.Task> for concluído.  Você pode obter um <xref:System.Threading.WaitHandle> para um <xref:System.Threading.Tasks.Task> da seguinte maneira:  
  
 [!code-csharp[Conceptual.AsyncInterop#14](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wait1.cs#14)]
 [!code-vb[Conceptual.AsyncInterop#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wait1.vb#14)]  
  
## <a name="see-also"></a>Veja também

- [Padrão assíncrono baseado em tarefa (TAP)](task-based-asynchronous-pattern-tap.md)
- [Implementando o padrão assíncrono baseado em tarefa](implementing-the-task-based-asynchronous-pattern.md)
- [Consumindo o padrão assíncrono baseado em tarefa](consuming-the-task-based-asynchronous-pattern.md)
