---
title: Pooling de threads (C#)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 98ae68c1-ace8-44b9-9317-8920ac9ef2b6
caps.latest.revision: "5"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 09dd597e8ac7a6b336f71891ccc89984ea659614
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="thread-pooling-c"></a>Pooling de threads (C#)
Um *pool de threads* é uma coleção de threads que pode ser usada para executar várias tarefas em segundo plano. (Consulte [Threading (C#)](../../../../csharp/programming-guide/concepts/threading/index.md) para obter informações gerais.) Isso deixa o thread primário livre para executar outras tarefas de forma assíncrona.  
  
 Os pools de threads geralmente são empregados em aplicativos de servidor. Cada solicitação de entrada é atribuída a um thread do pool de threads para que a solicitação possa ser processada de forma assíncrona, sem prender o thread primário ou atrasar o processamento das solicitações subsequentes.  
  
 Depois que um thread do pool conclui sua tarefa, ele é retornado para uma fila de segmentos em espera, no qual ele pode ser reutilizado. Essa reutilização permite que os aplicativos evitem o custo de criação de um novo thread para cada tarefa.  
  
 Os pools de threads geralmente têm um número máximo de threads. Se todos os threads estiverem ocupados, as tarefas adicionais serão colocadas na fila até que possam ser atendidas conforme threads se tornam disponíveis.  
  
 Você pode implementar seu próprio pool de threads, mas é mais fácil de usar o pool de threads fornecido pelo .NET Framework por meio da classe <xref:System.Threading.ThreadPool>.  
  
 Com o pooling de threads, você chama o método <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=nameWithType> com um delegado para o procedimento que deseja executar e o C# cria o thread e executa o procedimento.  
  
## <a name="thread-pooling-example"></a>Exemplo de pooling de threads  
 O exemplo a seguir mostra como você pode usar o pooling de threads para iniciar várias tarefas.  
  
```csharp  
public void DoWork()  
{  
    // Queue a task.  
    System.Threading.ThreadPool.QueueUserWorkItem(  
        new System.Threading.WaitCallback(SomeLongTask));  
    // Queue another task.  
    System.Threading.ThreadPool.QueueUserWorkItem(  
        new System.Threading.WaitCallback(AnotherLongTask));  
}  
  
private void SomeLongTask(Object state)  
{  
    // Insert code to perform a long task.  
}  
  
private void AnotherLongTask(Object state)  
{  
    // Insert code to perform a long task.  
}  
```  
  
 Uma vantagem do pooling de threads é que você pode passar argumentos em um objeto de estado para o procedimento da tarefa. Se o procedimento que você está chamando exigir mais de um argumento, você pode converter uma estrutura ou uma instância de uma classe em um tipo de dados `Object`.  
  
## <a name="thread-pool-parameters-and-return-values"></a>Parâmetros do pool de threads e valores retornados  
 Os valores retornados de um thread do pool de threads não são simples. A forma padrão de retornar valores de uma chamada de função não é permitida porque os procedimentos `Sub` são o único tipo de procedimento que pode ser colocado na fila para um pool de thread. Uma maneira de você fornecer parâmetros e valores retornados é encapsular os parâmetros, valores retornados e métodos em uma classe wrapper conforme descrito em [Parâmetros e valores de retorno para procedimentos multithreaded (C#)](../../../../csharp/programming-guide/concepts/threading/parameters-and-return-values-for-multithreaded-procedures.md).  
  
 Um modo mais fácil de fornecer parâmetros e retornar valores é usando a variável de objeto de estado `ByVal` do método <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A>. Se você usar essa variável para passar uma referência para uma instância de uma classe, os membros da instância poderão ser modificados pelo thread do pool de threads e usados como valores retornados.  
  
 Inicialmente pode não ser óbvio que você pode modificar um objeto referenciado por uma variável passada por valor. Você pode fazer isso porque somente a referência de objeto é passada por valor. Quando você faz alterações em membros do objeto referenciado pela referência de objeto, as alterações se aplicam à instância de classe real.  
  
 As estruturas não podem ser usadas para retornar valores dentro de objetos de estado. Como estruturas são tipos de valor, as alterações que o processo assíncrono faz não alteram os membros da estrutura original. Use estruturas para fornecer parâmetros quando valores de retorno não são necessários.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A>  
 <xref:System.Threading>  
 <xref:System.Threading.ThreadPool>  
 [Como usar um pool de thread (C#)](../../../../csharp/programming-guide/concepts/threading/how-to-use-a-thread-pool.md)  
 [Threading (C#)](../../../../csharp/programming-guide/concepts/threading/index.md)  
 [Aplicativos com multithread (C#)](../../../../csharp/programming-guide/concepts/threading/multithreaded-applications.md)  
 [Sincronização de thread (C#)](../../../../csharp/programming-guide/concepts/threading/thread-synchronization.md)
