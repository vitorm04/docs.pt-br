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
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: eea7c94dffe525bb36c677bf3414f25ed0210074
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="thread-pooling-visual-basic"></a><span data-ttu-id="3db78-102">Thread Pooling (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3db78-102">Thread Pooling (Visual Basic)</span></span>
<span data-ttu-id="3db78-103">A *pool de threads* é uma coleção de segmentos que podem ser usados para executar várias tarefas em segundo plano.</span><span class="sxs-lookup"><span data-stu-id="3db78-103">A *thread pool* is a collection of threads that can be used to perform several tasks in the background.</span></span> <span data-ttu-id="3db78-104">(Consulte [Threading (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/index.md) para obter mais informações.) Isso deixa o thread primário livre para executar outras tarefas de forma assíncrona.</span><span class="sxs-lookup"><span data-stu-id="3db78-104">(See [Threading (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/index.md) for background information.) This leaves the primary thread free to perform other tasks asynchronously.</span></span>  
  
 <span data-ttu-id="3db78-105">Pools de threads geralmente são empregados em aplicativos de servidor.</span><span class="sxs-lookup"><span data-stu-id="3db78-105">Thread pools are often employed in server applications.</span></span> <span data-ttu-id="3db78-106">Cada solicitação de entrada é atribuída a um thread do pool de threads, para que a solicitação pode ser processada de forma assíncrona, sem prender o thread primário ou atrasar o processamento das solicitações subsequentes.</span><span class="sxs-lookup"><span data-stu-id="3db78-106">Each incoming request is assigned to a thread from the thread pool, so that the request can be processed asynchronously, without tying up the primary thread or delaying the processing of subsequent requests.</span></span>  
  
 <span data-ttu-id="3db78-107">Depois que um thread do pool conclui sua tarefa, ele é retornado para uma fila de segmentos em espera, onde ele pode ser reutilizado.</span><span class="sxs-lookup"><span data-stu-id="3db78-107">Once a thread in the pool completes its task, it is returned to a queue of waiting threads, where it can be reused.</span></span> <span data-ttu-id="3db78-108">Essa reutilização permite que os aplicativos evitar o custo de criação de um novo thread para cada tarefa.</span><span class="sxs-lookup"><span data-stu-id="3db78-108">This reuse enables applications to avoid the cost of creating a new thread for each task.</span></span>  
  
 <span data-ttu-id="3db78-109">Pools de threads geralmente têm um número máximo de threads.</span><span class="sxs-lookup"><span data-stu-id="3db78-109">Thread pools typically have a maximum number of threads.</span></span> <span data-ttu-id="3db78-110">Se todos os threads estiverem ocupados, tarefas adicionais são colocadas na fila até que possam ser atendidos conforme threads se tornam disponíveis.</span><span class="sxs-lookup"><span data-stu-id="3db78-110">If all the threads are busy, additional tasks are put in queue until they can be serviced as threads become available.</span></span>  
  
 <span data-ttu-id="3db78-111">Você pode implementar seu próprio pool de threads, mas é mais fácil de usar o pool de threads fornecido pelo .NET Framework por meio de <xref:System.Threading.ThreadPool>classe.</xref:System.Threading.ThreadPool></span><span class="sxs-lookup"><span data-stu-id="3db78-111">You can implement your own thread pool, but it is easier to use the thread pool provided by the .NET Framework through the <xref:System.Threading.ThreadPool> class.</span></span>  
  
 <span data-ttu-id="3db78-112">Com o pool de thread, você chama o <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=fullName>método com um representante para o procedimento que você deseja executar, e o Visual Basic cria o segmento e executa o procedimento.</xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="3db78-112">With thread pooling, you call the <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=fullName> method with a delegate for the procedure you want to run, and Visual Basic creates the thread and runs your procedure.</span></span>  
  
## <a name="thread-pooling-example"></a><span data-ttu-id="3db78-113">Exemplo de pool de segmentos</span><span class="sxs-lookup"><span data-stu-id="3db78-113">Thread Pooling Example</span></span>  
 <span data-ttu-id="3db78-114">O exemplo a seguir mostra como você pode usar o pool de segmentos para iniciar várias tarefas.</span><span class="sxs-lookup"><span data-stu-id="3db78-114">The following example shows how you can use thread pooling to start several tasks.</span></span>  
  
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
  
 <span data-ttu-id="3db78-115">Uma vantagem do pool de segmentos é que você pode passar argumentos em um objeto de estado para o procedimento de tarefas.</span><span class="sxs-lookup"><span data-stu-id="3db78-115">One advantage of thread pooling is that you can pass arguments in a state object to the task procedure.</span></span> <span data-ttu-id="3db78-116">Se o procedimento que você está chamando exigir mais de um argumento, você pode converter uma estrutura ou uma instância de uma classe em um `Object` tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="3db78-116">If the procedure you are calling requires more than one argument, you can cast a structure or an instance of a class into an `Object` data type.</span></span>  
  
## <a name="thread-pool-parameters-and-return-values"></a><span data-ttu-id="3db78-117">Parâmetros do Pool de threads e valores de retorno</span><span class="sxs-lookup"><span data-stu-id="3db78-117">Thread Pool Parameters and Return Values</span></span>  
 <span data-ttu-id="3db78-118">Retornar valores de um thread do pool de threads não é simples.</span><span class="sxs-lookup"><span data-stu-id="3db78-118">Returning values from a thread-pool thread is not straightforward.</span></span> <span data-ttu-id="3db78-119">A forma padrão de retornar valores de uma chamada de função não é permitida porque `Sub` procedimentos são os únicos tipos de procedimentos que podem ser colocados na fila para um pool de threads.</span><span class="sxs-lookup"><span data-stu-id="3db78-119">The standard way of returning values from a function call is not allowed because `Sub` procedures are the only type of procedure that can be queued to a thread pool.</span></span> <span data-ttu-id="3db78-120">Uma maneira de você fornecer parâmetros e retornar valores é envolvendo os parâmetros, valores de retorno, e métodos em um classe wrapper conforme descrito em [parâmetros e valores de retorno para procedimentos multithread (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/parameters-and-return-values-for-multithreaded-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="3db78-120">One way you can provide parameters and return values is by wrapping the parameters, return values, and methods in a wrapper class as described in [Parameters and Return Values for Multithreaded Procedures (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/parameters-and-return-values-for-multithreaded-procedures.md).</span></span>  
  
 <span data-ttu-id="3db78-121">É uma maneira mais fácil para fornecer parâmetros e retornar valores usando opcional `ByVal` variável do objeto de estado de <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A>método.</xref:System.Threading.ThreadPool.QueueUserWorkItem%2A></span><span class="sxs-lookup"><span data-stu-id="3db78-121">An easer way to provide parameters and return values is by using the optional `ByVal` state object variable of the <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A> method.</span></span> <span data-ttu-id="3db78-122">Se você usar essa variável para passar uma referência a uma instância de uma classe, os membros da instância podem ser modificados pelo thread do pool de segmentos e usados como valores de retorno.</span><span class="sxs-lookup"><span data-stu-id="3db78-122">If you use this variable to pass a reference to an instance of a class, the members of the instance can be modified by the thread-pool thread and used as return values.</span></span>  
  
 <span data-ttu-id="3db78-123">Primeiro talvez não seja óbvio que você pode modificar um objeto referenciado por uma variável que é passada por valor.</span><span class="sxs-lookup"><span data-stu-id="3db78-123">At first it may not be obvious that you can modify an object referred to by a variable that is passed by value.</span></span> <span data-ttu-id="3db78-124">Você pode fazer isso porque somente a referência de objeto é passada por valor.</span><span class="sxs-lookup"><span data-stu-id="3db78-124">You can do this because only the object reference is passed by value.</span></span> <span data-ttu-id="3db78-125">Quando você faz alterações a membros do objeto referido pela referência de objeto, as alterações são aplicadas à instância real da classe.</span><span class="sxs-lookup"><span data-stu-id="3db78-125">When you make changes to members of the object referred to by the object reference, the changes apply to the actual class instance.</span></span>  
  
 <span data-ttu-id="3db78-126">Estruturas não podem ser usadas para retornar valores dentro de objetos de estado.</span><span class="sxs-lookup"><span data-stu-id="3db78-126">Structures cannot be used to return values inside state objects.</span></span> <span data-ttu-id="3db78-127">Como estruturas são tipos de valor, as alterações que o processo assíncrono faz não alteram os membros da estrutura original.</span><span class="sxs-lookup"><span data-stu-id="3db78-127">Because structures are value types, changes that the asynchronous process makes do not change the members of the original structure.</span></span> <span data-ttu-id="3db78-128">Use estruturas para fornecer parâmetros quando valores de retorno não são necessários.</span><span class="sxs-lookup"><span data-stu-id="3db78-128">Use structures to provide parameters when return values are not needed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3db78-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3db78-129">See Also</span></span>  
 <span data-ttu-id="3db78-130"><xref:System.Threading.ThreadPool.QueueUserWorkItem%2A></xref:System.Threading.ThreadPool.QueueUserWorkItem%2A></span><span class="sxs-lookup"><span data-stu-id="3db78-130"><xref:System.Threading.ThreadPool.QueueUserWorkItem%2A></span></span>   
 <span data-ttu-id="3db78-131"><xref:System.Threading></xref:System.Threading></span><span class="sxs-lookup"><span data-stu-id="3db78-131"><xref:System.Threading></span></span>   
 <span data-ttu-id="3db78-132"><xref:System.Threading.ThreadPool></xref:System.Threading.ThreadPool></span><span class="sxs-lookup"><span data-stu-id="3db78-132"><xref:System.Threading.ThreadPool></span></span>   
<span data-ttu-id="3db78-133"> [Como: usar um Pool de threads (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/how-to-use-a-thread-pool.md) </span><span class="sxs-lookup"><span data-stu-id="3db78-133"> [How to: Use a Thread Pool (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/how-to-use-a-thread-pool.md) </span></span>  
<span data-ttu-id="3db78-134"> [Threading (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/index.md) </span><span class="sxs-lookup"><span data-stu-id="3db78-134"> [Threading (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/index.md) </span></span>  
<span data-ttu-id="3db78-135"> [Aplicativos multithread (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/multithreaded-applications.md) </span><span class="sxs-lookup"><span data-stu-id="3db78-135"> [Multithreaded Applications (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/multithreaded-applications.md) </span></span>  
<span data-ttu-id="3db78-136"> [Sincronização de thread (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-synchronization.md)</span><span class="sxs-lookup"><span data-stu-id="3db78-136"> [Thread Synchronization (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-synchronization.md)</span></span>
