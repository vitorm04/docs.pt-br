---
title: Thread Pooling (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 4903fb7a-eaad-435a-9add-1d1b32de3b83
ms.openlocfilehash: 445c1c70cc1371ef918f32046e0c30ae2a473da2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33647827"
---
# <a name="thread-pooling-visual-basic"></a><span data-ttu-id="9f067-102">Thread Pooling (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9f067-102">Thread Pooling (Visual Basic)</span></span>
<span data-ttu-id="9f067-103">Um *pool de threads* é uma coleção de threads que pode ser usada para executar várias tarefas em segundo plano.</span><span class="sxs-lookup"><span data-stu-id="9f067-103">A *thread pool* is a collection of threads that can be used to perform several tasks in the background.</span></span> <span data-ttu-id="9f067-104">(Consulte [Threading (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/index.md) para obter mais informações.) Isso deixa o thread primário livre para executar outras tarefas de forma assíncrona.</span><span class="sxs-lookup"><span data-stu-id="9f067-104">(See [Threading (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/index.md) for background information.) This leaves the primary thread free to perform other tasks asynchronously.</span></span>  
  
 <span data-ttu-id="9f067-105">Os pools de threads geralmente são empregados em aplicativos de servidor.</span><span class="sxs-lookup"><span data-stu-id="9f067-105">Thread pools are often employed in server applications.</span></span> <span data-ttu-id="9f067-106">Cada solicitação de entrada é atribuída a um thread do pool de threads para que a solicitação possa ser processada de forma assíncrona, sem prender o thread primário ou atrasar o processamento das solicitações subsequentes.</span><span class="sxs-lookup"><span data-stu-id="9f067-106">Each incoming request is assigned to a thread from the thread pool, so that the request can be processed asynchronously, without tying up the primary thread or delaying the processing of subsequent requests.</span></span>  
  
 <span data-ttu-id="9f067-107">Depois que um thread do pool conclui sua tarefa, ele é retornado para uma fila de segmentos em espera, no qual ele pode ser reutilizado.</span><span class="sxs-lookup"><span data-stu-id="9f067-107">Once a thread in the pool completes its task, it is returned to a queue of waiting threads, where it can be reused.</span></span> <span data-ttu-id="9f067-108">Essa reutilização permite que os aplicativos evitem o custo de criação de um novo thread para cada tarefa.</span><span class="sxs-lookup"><span data-stu-id="9f067-108">This reuse enables applications to avoid the cost of creating a new thread for each task.</span></span>  
  
 <span data-ttu-id="9f067-109">Os pools de threads geralmente têm um número máximo de threads.</span><span class="sxs-lookup"><span data-stu-id="9f067-109">Thread pools typically have a maximum number of threads.</span></span> <span data-ttu-id="9f067-110">Se todos os threads estiverem ocupados, as tarefas adicionais serão colocadas na fila até que possam ser atendidas conforme threads se tornam disponíveis.</span><span class="sxs-lookup"><span data-stu-id="9f067-110">If all the threads are busy, additional tasks are put in queue until they can be serviced as threads become available.</span></span>  
  
 <span data-ttu-id="9f067-111">Você pode implementar seu próprio pool de threads, mas é mais fácil de usar o pool de threads fornecido pelo .NET Framework por meio da classe <xref:System.Threading.ThreadPool>.</span><span class="sxs-lookup"><span data-stu-id="9f067-111">You can implement your own thread pool, but it is easier to use the thread pool provided by the .NET Framework through the <xref:System.Threading.ThreadPool> class.</span></span>  
  
 <span data-ttu-id="9f067-112">Com o pool de thread, você deve chamar o <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=nameWithType> método com um representante para o procedimento que você deseja executar, e o Visual Basic cria a thread e executa o procedimento.</span><span class="sxs-lookup"><span data-stu-id="9f067-112">With thread pooling, you call the <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=nameWithType> method with a delegate for the procedure you want to run, and Visual Basic creates the thread and runs your procedure.</span></span>  
  
## <a name="thread-pooling-example"></a><span data-ttu-id="9f067-113">Exemplo de pooling de threads</span><span class="sxs-lookup"><span data-stu-id="9f067-113">Thread Pooling Example</span></span>  
 <span data-ttu-id="9f067-114">O exemplo a seguir mostra como você pode usar o pooling de threads para iniciar várias tarefas.</span><span class="sxs-lookup"><span data-stu-id="9f067-114">The following example shows how you can use thread pooling to start several tasks.</span></span>  
  
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
  
 <span data-ttu-id="9f067-115">Uma vantagem do pooling de threads é que você pode passar argumentos em um objeto de estado para o procedimento da tarefa.</span><span class="sxs-lookup"><span data-stu-id="9f067-115">One advantage of thread pooling is that you can pass arguments in a state object to the task procedure.</span></span> <span data-ttu-id="9f067-116">Se o procedimento que você está chamando exigir mais de um argumento, você pode converter uma estrutura ou uma instância de uma classe em um tipo de dados `Object`.</span><span class="sxs-lookup"><span data-stu-id="9f067-116">If the procedure you are calling requires more than one argument, you can cast a structure or an instance of a class into an `Object` data type.</span></span>  
  
## <a name="thread-pool-parameters-and-return-values"></a><span data-ttu-id="9f067-117">Parâmetros do pool de threads e valores retornados</span><span class="sxs-lookup"><span data-stu-id="9f067-117">Thread Pool Parameters and Return Values</span></span>  
 <span data-ttu-id="9f067-118">Os valores retornados de um thread do pool de threads não são simples.</span><span class="sxs-lookup"><span data-stu-id="9f067-118">Returning values from a thread-pool thread is not straightforward.</span></span> <span data-ttu-id="9f067-119">A forma padrão de retornar valores de uma chamada de função não é permitida porque os procedimentos `Sub` são o único tipo de procedimento que pode ser colocado na fila para um pool de thread.</span><span class="sxs-lookup"><span data-stu-id="9f067-119">The standard way of returning values from a function call is not allowed because `Sub` procedures are the only type of procedure that can be queued to a thread pool.</span></span> <span data-ttu-id="9f067-120">Uma forma você pode fornecer parâmetros e retornar valores é envolvendo os parâmetros, valores de retorno, e métodos em um classe wrapper conforme descrito em [parâmetros e valores de retorno para procedimentos multithread (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/parameters-and-return-values-for-multithreaded-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="9f067-120">One way you can provide parameters and return values is by wrapping the parameters, return values, and methods in a wrapper class as described in [Parameters and Return Values for Multithreaded Procedures (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/parameters-and-return-values-for-multithreaded-procedures.md).</span></span>  
  
 <span data-ttu-id="9f067-121">Um modo mais fácil de fornecer parâmetros e retornar valores é usando a variável de objeto de estado `ByVal` do método <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A>.</span><span class="sxs-lookup"><span data-stu-id="9f067-121">An easer way to provide parameters and return values is by using the optional `ByVal` state object variable of the <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A> method.</span></span> <span data-ttu-id="9f067-122">Se você usar essa variável para passar uma referência para uma instância de uma classe, os membros da instância poderão ser modificados pelo thread do pool de threads e usados como valores retornados.</span><span class="sxs-lookup"><span data-stu-id="9f067-122">If you use this variable to pass a reference to an instance of a class, the members of the instance can be modified by the thread-pool thread and used as return values.</span></span>  
  
 <span data-ttu-id="9f067-123">Inicialmente pode não ser óbvio que você pode modificar um objeto referenciado por uma variável passada por valor.</span><span class="sxs-lookup"><span data-stu-id="9f067-123">At first it may not be obvious that you can modify an object referred to by a variable that is passed by value.</span></span> <span data-ttu-id="9f067-124">Você pode fazer isso porque somente a referência de objeto é passada por valor.</span><span class="sxs-lookup"><span data-stu-id="9f067-124">You can do this because only the object reference is passed by value.</span></span> <span data-ttu-id="9f067-125">Quando você faz alterações em membros do objeto referenciado pela referência de objeto, as alterações se aplicam à instância de classe real.</span><span class="sxs-lookup"><span data-stu-id="9f067-125">When you make changes to members of the object referred to by the object reference, the changes apply to the actual class instance.</span></span>  
  
 <span data-ttu-id="9f067-126">As estruturas não podem ser usadas para retornar valores dentro de objetos de estado.</span><span class="sxs-lookup"><span data-stu-id="9f067-126">Structures cannot be used to return values inside state objects.</span></span> <span data-ttu-id="9f067-127">Como estruturas são tipos de valor, as alterações que o processo assíncrono faz não alteram os membros da estrutura original.</span><span class="sxs-lookup"><span data-stu-id="9f067-127">Because structures are value types, changes that the asynchronous process makes do not change the members of the original structure.</span></span> <span data-ttu-id="9f067-128">Use estruturas para fornecer parâmetros quando valores de retorno não são necessários.</span><span class="sxs-lookup"><span data-stu-id="9f067-128">Use structures to provide parameters when return values are not needed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f067-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9f067-129">See Also</span></span>  
 <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A>  
 <xref:System.Threading>  
 <xref:System.Threading.ThreadPool>  
 [<span data-ttu-id="9f067-130">Como usar um pool de thread (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9f067-130">How to: Use a Thread Pool (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/threading/how-to-use-a-thread-pool.md)  
 [<span data-ttu-id="9f067-131">Threading (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9f067-131">Threading (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/threading/index.md)  
 [<span data-ttu-id="9f067-132">Aplicativos multithread (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9f067-132">Multithreaded Applications (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/threading/multithreaded-applications.md)  
 [<span data-ttu-id="9f067-133">Sincronização de thread (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9f067-133">Thread Synchronization (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/threading/thread-synchronization.md)
