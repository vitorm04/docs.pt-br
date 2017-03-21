---
title: Thread Pooling (Visual Basic) | Documentos do Microsoft
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 4903fb7a-eaad-435a-9add-1d1b32de3b83
caps.latest.revision: 4
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 6037d7ea17e260d44bae571aa25d413996f5a123
ms.lasthandoff: 03/13/2017

---
# <a name="thread-pooling-visual-basic"></a>Thread Pooling (Visual Basic)
A *pool de threads* é uma coleção de segmentos que podem ser usados para executar várias tarefas em segundo plano. (Consulte [Threading (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/index.md) para obter mais informações.) Isso deixa o thread primário livre para executar outras tarefas de forma assíncrona.  
  
 Pools de threads geralmente são empregados em aplicativos de servidor. Cada solicitação de entrada é atribuída a um thread do pool de threads, para que a solicitação pode ser processada de forma assíncrona, sem prender o thread primário ou atrasar o processamento das solicitações subsequentes.  
  
 Depois que um thread do pool conclui sua tarefa, ele é retornado para uma fila de segmentos em espera, onde ele pode ser reutilizado. Essa reutilização permite que os aplicativos evitar o custo de criação de um novo thread para cada tarefa.  
  
 Pools de threads geralmente têm um número máximo de threads. Se todos os threads estiverem ocupados, tarefas adicionais são colocadas na fila até que possam ser atendidos conforme threads se tornam disponíveis.  
  
 Você pode implementar seu próprio pool de threads, mas é mais fácil de usar o pool de threads fornecido pelo .NET Framework por meio de <xref:System.Threading.ThreadPool>classe.</xref:System.Threading.ThreadPool>  
  
 Com o pool de thread, você chama o <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=fullName>método com um representante para o procedimento que você deseja executar, e o Visual Basic cria o segmento e executa o procedimento.</xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=fullName>  
  
## <a name="thread-pooling-example"></a>Exemplo de pool de segmentos  
 O exemplo a seguir mostra como você pode usar o pool de segmentos para iniciar várias tarefas.  
  
```vb  
Public Sub DoWork()  
    ' Queue a task.  
    System.Threading.ThreadPool.QueueUserWorkItem(  
        New System.Threading.WaitCallback(AddressOf SomeLongTask))  
    ' Queue another task.  
    System.Threading.ThreadPool.QueueUserWorkItem(  
        New System.Threading.WaitCallback(AddressOf AnotherLongTask))  
End Sub  
Private Sub SomeLongTask(ByVal state As Object)  
    ' Insert code to perform a long task.  
End Sub  
Private Sub AnotherLongTask(ByVal state As Object)  
    ' Insert code to perform another long task.  
End Sub  
```  
  
 Uma vantagem do pool de segmentos é que você pode passar argumentos em um objeto de estado para o procedimento de tarefas. Se o procedimento que você está chamando exigir mais de um argumento, você pode converter uma estrutura ou uma instância de uma classe em um `Object` tipo de dados.  
  
## <a name="thread-pool-parameters-and-return-values"></a>Parâmetros do Pool de threads e valores de retorno  
 Retornar valores de um thread do pool de threads não é simples. A forma padrão de retornar valores de uma chamada de função não é permitida porque `Sub` procedimentos são os únicos tipos de procedimentos que podem ser colocados na fila para um pool de threads. Uma maneira de você fornecer parâmetros e retornar valores é envolvendo os parâmetros, valores de retorno, e métodos em um classe wrapper conforme descrito em [parâmetros e valores de retorno para procedimentos multithread (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/parameters-and-return-values-for-multithreaded-procedures.md).  
  
 É uma maneira mais fácil para fornecer parâmetros e retornar valores usando opcional `ByVal` variável do objeto de estado de <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A>método.</xref:System.Threading.ThreadPool.QueueUserWorkItem%2A> Se você usar essa variável para passar uma referência a uma instância de uma classe, os membros da instância podem ser modificados pelo thread do pool de segmentos e usados como valores de retorno.  
  
 Primeiro talvez não seja óbvio que você pode modificar um objeto referenciado por uma variável que é passada por valor. Você pode fazer isso porque somente a referência de objeto é passada por valor. Quando você faz alterações a membros do objeto referido pela referência de objeto, as alterações são aplicadas à instância real da classe.  
  
 Estruturas não podem ser usadas para retornar valores dentro de objetos de estado. Como estruturas são tipos de valor, as alterações que o processo assíncrono faz não alteram os membros da estrutura original. Use estruturas para fornecer parâmetros quando valores de retorno não são necessários.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A></xref:System.Threading.ThreadPool.QueueUserWorkItem%2A>   
 <xref:System.Threading></xref:System.Threading>   
 <xref:System.Threading.ThreadPool></xref:System.Threading.ThreadPool>   
 [Como: usar um Pool de threads (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/how-to-use-a-thread-pool.md)   
 [Threading (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/index.md)   
 [Aplicativos multithread (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/multithreaded-applications.md)   
 [Sincronização de thread (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-synchronization.md)
