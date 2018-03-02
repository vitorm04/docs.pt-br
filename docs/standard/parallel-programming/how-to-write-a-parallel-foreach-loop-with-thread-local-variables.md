---
title: "Como escrever um loop Parallel.ForEach com variáveis locais de thread"
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
- parallel foreach loop, how to use local state
ms.assetid: 24b10041-b30b-45cb-aa65-66cf568ca76d
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 4c65edd8959cbf5f83e3353770f71cad130953d1
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-write-a-parallelforeach-loop-with-thread-local-variables"></a>Como escrever um loop Parallel.ForEach com variáveis locais de thread
O exemplo a seguir mostra como gravar um método <xref:System.Threading.Tasks.Parallel.ForEach%2A> que usa variáveis de thread local. Quando um loop <xref:System.Threading.Tasks.Parallel.ForEach%2A> é executado, ele divide a coleção de origem em diversas partições. Cada partição tem sua própria cópia da variável de "thread local". O termo "thread local" não é muito preciso por que, em alguns casos, duas partições podem executar no mesmo thread.  
  
 O código e os parâmetros desse exemplo parecem com o método <xref:System.Threading.Tasks.Parallel.For%2A> correspondente. Para saber mais, confira [Como escrever um loop Parallel.For com variáveis locais de thread](../../../docs/standard/parallel-programming/how-to-write-a-parallel-for-loop-with-thread-local-variables.md).  
  
 Para usar uma variável de thread local em um loop <xref:System.Threading.Tasks.Parallel.ForEach%2A>, você deve chamar uma das sobrecargas de método que usa dois parâmetros de tipos. O primeiro parâmetro de tipo, `TSource`, especifica o tipo do elemento de origem. Já o segundo, `TLocal`, especifica o tipo da variável de thread local.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir chama a sobrecarga <xref:System.Threading.Tasks.Parallel.ForEach%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%601%7D%2CSystem.Func%7B%60%600%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%601%2C%60%601%7D%2CSystem.Action%7B%60%601%7D%29?displayProperty=nameWithType> para calcular a soma de uma matriz com um milhão de elementos. Essa sobrecarga tem quatro parâmetros:  
  
-   `source`, que é a fonte de dados. Ela deve implementar <xref:System.Collections.Generic.IEnumerable%601>. A fonte de dados do nosso exemplo é um objeto `IEnumerable<Int32>` membro de um milhão retornado pelo método <xref:System.Linq.Enumerable.Range%2A?displayProperty=nameWithType>.  
  
-   `localInit`, ou a função que inicia a variável de thread local. Essa função é chamada uma vez para cada partição onde a operação <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> é executada. Nosso exemplo inicia a variável de thread local como zero.  
  
-   `body`, um <xref:System.Func%604> que é invocado pelo loop paralelo em cada iteração do loop. Sua assinatura é `Func\<TSource, ParallelLoopState, TLocal, TLocal>`. Você fornece o código para o representante e o loop passa pelos parâmetros de entrada, que são:  
  
    -   O elemento atual de <xref:System.Collections.Generic.IEnumerable%601>.  
  
    -   Uma variável <xref:System.Threading.Tasks.ParallelLoopState> que pode ser usada no código do representante para avaliar o estado do loop.  
  
    -   A variável de thread local.  
  
     Seu representante retorna a variável de thread local, que é apresentada para a próxima iteração do loop que executa nessa partição específica. Cada partição do loop mantém uma instância separada dessa variável.  
  
     Nesse exemplo, o representante adiciona o valor de cada inteiro à variável de thread local, que mantém um total de valores dos elementos inteiros dessa partição em execução.  
  
-   `localFinally`, um representante `Action<TLocal>` que o <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> invoca quando são concluídas as operações de loop de cada partição. O método <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> passa o valor final da variável de thread local desse thread (ou partição de loop) para seu representante `Action<TLocal>`, e você fornece o código que executa a ação necessária para combinar o resultado dessa partição aos resultados de outras partições. Esse representante pode ser invocado ao mesmo tempo por diversas tarefas. Por isso, o exemplo usa o método <xref:System.Threading.Interlocked.Add%28System.Int32%40%2CSystem.Int32%29?displayProperty=nameWithType> para sincronizar o acesso à variável `total`. Como o tipo de representante é um <xref:System.Action%601>, não há valor retornado.  
  
 [!code-csharp[TPL_Parallel#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/foreachthreadlocal.cs#04)]
 [!code-vb[TPL_Parallel#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/foreachthreadlocal.vb#04)]  
  
## <a name="see-also"></a>Consulte também  
 [Paralelismo de dados](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)  
 [Como escrever um loop Parallel.For com variáveis locais de thread](../../../docs/standard/parallel-programming/how-to-write-a-parallel-for-loop-with-thread-local-variables.md)  
 [Expressões lambda em PLINQ e TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
