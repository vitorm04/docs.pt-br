---
title: "Interoperabilidade com outros tipos e padrões assíncronos"
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
- .NET Framework, and TAP
- asynchronous design patterns, .NET Framework
- TAP, .NET Framework support for
- Task-based Asynchronous Pattern, .NET Framework support for
- .NET Framework, asynchronous design patterns
ms.assetid: f120a5d9-933b-4d1d-acb6-f034a57c3749
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2e30b562b4795717df526c143df96607686a7582
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="interop-with-other-asynchronous-patterns-and-types"></a>Interoperabilidade com outros tipos e padrões assíncronos
O .NET Framework 1.0 introduziu o <xref:System.IAsyncResult> padrão, também conhecido como o [modelo de programação assíncrona (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md), ou o `Begin/End` padrão.  O .NET Framework 2.0 adicionado o [padrão assíncrono baseado em evento (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md).  Começando com o .NET Framework 4, o [padrão assíncrono baseado em tarefa (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) substitui o APM e EAP, mas oferece a capacidade de criar facilmente as rotinas de migração dos padrões anteriores.  
  
 Neste tópico:  
  
-   [Tarefas e APM](#APM) ([do APM para toque](#ApmToTap) ou [de toque para APM](#TapToApm))  
  
-   [Tarefas e EAP](#EAP)  
  
-   [Tarefas e identificadores de espera](#WaitHandles) ([de identificadores de espera para toque](#WHToTap) ou [de toque para identificadores de espera](#TapToWH))  
  
<a name="APM"></a>   
## <a name="tasks-and-the-asynchronous-programming-model-apm"></a>Tarefas e o modelo de programação assíncrona (APM)  
  
<a name="ApmToTap"></a>   
### <a name="from-apm-to-tap"></a>Do APM para toque  
 Porque o [modelo de programação assíncrona (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md) padrão é muito estruturado, é muito fácil criar um wrapper para expor uma implementação de APM como uma implementação de toque. Na verdade, o .NET Framework, começando com [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], inclui rotinas auxiliares na forma de <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A> sobrecargas do método para fornecer essa conversão.  
  
 Considere o <xref:System.IO.Stream> classe e seu <xref:System.IO.Stream.BeginRead%2A> e <xref:System.IO.Stream.EndRead%2A> métodos, que representam a contraparte APM para o síncrona <xref:System.IO.Stream.Read%2A> método:  
  
 [!code-csharp[Conceptual.AsyncInterop#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Stream1.cs#1)]
 [!code-vb[Conceptual.AsyncInterop#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/stream1.vb#1)]  
[!code-csharp[Conceptual.AsyncInterop#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Stream1.cs#2)]
[!code-vb[Conceptual.AsyncInterop#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/stream1.vb#2)]  
[!code-csharp[Conceptual.AsyncInterop#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Stream1.cs#3)]
[!code-vb[Conceptual.AsyncInterop#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/stream1.vb#3)]  
  
 Você pode usar o <xref:System.Threading.Tasks.TaskFactory%601.FromAsync%2A?displayProperty=nameWithType> método para implementar um wrapper de toque para essa operação da seguinte maneira:  
  
 [!code-csharp[Conceptual.AsyncInterop#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wrap1.cs#4)]
 [!code-vb[Conceptual.AsyncInterop#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wrap1.vb#4)]  
  
 Essa implementação é semelhante ao seguinte:  
  
 [!code-csharp[Conceptual.AsyncInterop#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wrap2.cs#5)]
 [!code-vb[Conceptual.AsyncInterop#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wrap2.vb#5)]  
  
<a name="TapToApm"></a>   
### <a name="from-tap-to-apm"></a>De toque para APM  
 Se sua infraestrutura existente espera o padrão do APM, você também vai querer levar uma implementação de toque e usá-lo em uma implementação de APM é esperada.  Como as tarefas podem ser compostas e <xref:System.Threading.Tasks.Task> classe implementa <xref:System.IAsyncResult>, você pode usar uma função auxiliar simples para fazer isso. O código a seguir usa uma extensão de <xref:System.Threading.Tasks.Task%601> classe, mas você pode usar uma função de quase idêntica para tarefas não genérico.  
  
 [!code-csharp[Conceptual.AsyncInterop#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM1.cs#6)]
 [!code-vb[Conceptual.AsyncInterop#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM1.vb#6)]  
  
 Agora, considere um caso em que a implementação de toque a seguir:  
  
 [!code-csharp[Conceptual.AsyncInterop#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#7)]
 [!code-vb[Conceptual.AsyncInterop#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#7)]  
  
 e você deseja fornecer essa implementação de APM:  
  
 [!code-csharp[Conceptual.AsyncInterop#8](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#8)]
 [!code-vb[Conceptual.AsyncInterop#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#8)]  
[!code-csharp[Conceptual.AsyncInterop#9](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#9)]
[!code-vb[Conceptual.AsyncInterop#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#9)]  
  
 O exemplo a seguir demonstra uma migração para o APM:  
  
 [!code-csharp[Conceptual.AsyncInterop#10](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#10)]
 [!code-vb[Conceptual.AsyncInterop#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#10)]  
  
<a name="EAP"></a>   
## <a name="tasks-and-the-event-based-asynchronous-pattern-eap"></a>Tarefas e o padrão assíncrono baseado em evento (EAP)  
 Quebra automática de um [padrão assíncrono baseado em evento (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md) implementação é mais envolvida que quebra automática de um padrão APM, porque o padrão EAP possui uma variação mais e menos estrutura que o padrão do APM.  Para demonstrar, o código a seguir encapsula o `DownloadStringAsync` método.  `DownloadStringAsync`aceita um URI, dispara o `DownloadProgressChanged` eventos durante o download para relatar várias estatísticas em andamento e gera o `DownloadStringCompleted` eventos quando tiver terminado.  O resultado final é uma cadeia de caracteres que contém o conteúdo da página no URI especificado.  
  
 [!code-csharp[Conceptual.AsyncInterop#11](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/EAP1.cs#11)]
 [!code-vb[Conceptual.AsyncInterop#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/EAP1.vb#11)]  
  
<a name="WaitHandles"></a>   
## <a name="tasks-and-wait-handles"></a>Tarefas e identificadores de espera  
  
<a name="WHToTap"></a>   
### <a name="from-wait-handles-to-tap"></a>De identificadores de espera para toque  
 Embora os identificadores de espera não implementam um padrão assíncrono, os desenvolvedores avançados podem usar o <xref:System.Threading.WaitHandle> classe e o <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A?displayProperty=nameWithType> método para notificações assíncronas quando um identificador de espera é definido.  Você pode encapsular a <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A> método para habilitar uma alternativa baseada em tarefa para qualquer espera síncrona em um identificador de espera:  
  
 [!code-csharp[Conceptual.AsyncInterop#12](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wait1.cs#12)]
 [!code-vb[Conceptual.AsyncInterop#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wait1.vb#12)]  
  
 Com esse método, você pode usar existente <xref:System.Threading.WaitHandle> implementações de métodos assíncronos.  Por exemplo, se você deseja limitar o número de operações assíncronas que são executados em um determinado momento, você pode utilizar um semáforo (um <xref:System.Threading.SemaphoreSlim?displayProperty=nameWithType> objeto).  Você pode acelerar a *N* o número de operações executadas simultaneamente por inicializar a contagem do sinal para *N*, esperando o semáforo sempre que quiser executar uma operação e liberar o semáforo quando terminar com uma operação:  
  
 [!code-csharp[Conceptual.AsyncInterop#13](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Semaphore1.cs#13)]
 [!code-vb[Conceptual.AsyncInterop#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Semaphore1.vb#13)]  
  
 Você também pode criar um semáforo assíncrono que não depende de identificadores de espera e trabalha completamente com tarefas. Para fazer isso, você pode usar técnicas como discutido [consumindo o padrão assíncrono baseado em tarefa](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md) para a criação de estruturas de dados na parte superior do <xref:System.Threading.Tasks.Task>.  
  
<a name="TapToWH"></a>   
### <a name="from-tap-to-wait-handles"></a>De toque para identificadores de espera  
 Como mencionado anteriormente, o <xref:System.Threading.Tasks.Task> classe implementa <xref:System.IAsyncResult>, e que a implementação expõe um <xref:System.Threading.Tasks.Task.System%23IAsyncResult%23AsyncWaitHandle%2A> propriedade que retorna um identificador de espera será definido quando o <xref:System.Threading.Tasks.Task> é concluída.  Você pode obter um <xref:System.Threading.WaitHandle> para um <xref:System.Threading.Tasks.Task> da seguinte maneira:  
  
 [!code-csharp[Conceptual.AsyncInterop#14](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wait1.cs#14)]
 [!code-vb[Conceptual.AsyncInterop#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wait1.vb#14)]  
  
## <a name="see-also"></a>Consulte também  
 [TAP (Padrão Assíncrono Baseado em Tarefa)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)  
 [Implementando o padrão assíncrono baseado em tarefa](../../../docs/standard/asynchronous-programming-patterns/implementing-the-task-based-asynchronous-pattern.md)  
 [Consumindo o padrão assíncrono baseado em tarefa](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md)
