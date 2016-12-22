---
title: "Thread Pooling (c#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
ms.assetid: 98ae68c1-ace8-44b9-9317-8920ac9ef2b6
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Thread Pooling (c#)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Um *pool de threads* é uma coleção de segmentos que podem ser usados para executar várias tarefas em segundo plano. \(Consulte [Threading \(c\#\)](../../../../visual-basic/reference/command-line-compiler/index.md) para obter mais informações.\) Isso deixa o thread primário livre para executar outras tarefas de forma assíncrona.  
  
 Pools de threads geralmente são empregados em aplicativos de servidor. Cada solicitação de entrada é atribuída a um thread do pool de threads, para que a solicitação pode ser processada de forma assíncrona, sem prender o thread primário ou atrasar o processamento das solicitações subseqüentes.  
  
 Depois que um thread do pool conclui sua tarefa, ele é retornado para uma fila de segmentos em espera, onde ele pode ser reutilizado. Essa reutilização permite que os aplicativos evitar o custo de criação de um novo thread para cada tarefa.  
  
 Pools de threads geralmente têm um número máximo de threads. Se todos os threads estiverem ocupados, tarefas adicionais são colocadas na fila até que possam ser atendidos conforme threads se tornam disponíveis.  
  
 Você pode implementar seu próprio pool de threads, mas é mais fácil de usar o pool de threads fornecido pelo .NET Framework por meio de <xref:System.Threading.ThreadPool> classe.  
  
 Com o pool de thread, você chama o <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=fullName> método com um representante para o procedimento que você deseja executar, e c\# cria o segmento e executa o procedimento.  
  
## Exemplo de pool de segmentos  
 O exemplo a seguir mostra como você pode usar o pool de segmentos para iniciar várias tarefas.  
  
```c#  
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
  
 Uma vantagem do pool de segmentos é que você pode passar argumentos em um objeto de estado para o procedimento de tarefas. Se o procedimento que você está chamando exigir mais de um argumento, você pode converter uma estrutura ou uma instância de uma classe em um `Object` tipo de dados.  
  
## Parâmetros do Pool de threads e valores de retorno  
 Retornar valores de um thread do pool de threads não é simples. A forma padrão de retornar valores de uma chamada de função não é permitida porque `Sub` procedimentos são os únicos tipos de procedimentos que podem ser colocados na fila para um pool de threads. Uma maneira de fornecer parâmetros e retornar valores é envolvendo os parâmetros, valores de retorno, e métodos em um classe wrapper conforme descrito em [Parâmetros e valores de retorno para procedimentos multithread \(c\#\)](../../../../csharp/programming-guide/concepts/threading/parameters-and-return-values-for-multithreaded-procedures.md).  
  
 É uma maneira mais fácil para fornecer parâmetros e retornar valores usando opcional `ByVal` variável do objeto de estado de <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A> método. Se você usar essa variável para passar uma referência a uma instância de uma classe, os membros da instância podem ser modificados pelo thread do pool de segmentos e usados como valores de retorno.  
  
 Primeiro talvez não seja óbvio que você pode modificar um objeto referenciado por uma variável que é passada por valor. Você pode fazer isso porque somente a referência de objeto é passada por valor. Quando você faz alterações a membros do objeto referido pela referência de objeto, as alterações são aplicadas à instância real da classe.  
  
 Estruturas não podem ser usadas para retornar valores dentro de objetos de estado. Como estruturas são tipos de valor, as alterações que o processo assíncrono faz não alteram os membros da estrutura original. Use estruturas para fornecer parâmetros quando valores de retorno não são necessários.  
  
## Consulte também  
 <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A>   
 <xref:System.Threading>   
 <xref:System.Threading.ThreadPool>   
 [Como: usar um Pool de Thread \(c\#\)](../Topic/How%20to:%20Use%20a%20Thread%20Pool%20\(C%23\).md)   
 [Threading \(c\#\)](../../../../visual-basic/reference/command-line-compiler/index.md)   
 [Aplicativos multithread \(c\#\)](../../../../csharp/programming-guide/concepts/threading/multithreaded-applications.md)   
 [Sincronização de thread \(c\#\)](../../../../csharp/programming-guide/concepts/threading/thread-synchronization.md)