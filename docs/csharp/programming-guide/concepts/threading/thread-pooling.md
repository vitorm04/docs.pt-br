---
title: Pooling de threads (C#)
ms.date: 07/20/2015
ms.assetid: 98ae68c1-ace8-44b9-9317-8920ac9ef2b6
ms.openlocfilehash: 42e1dcedc1897dc82bbd13f12882cbef6a5da4c3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33334191"
---
# <a name="thread-pooling-c"></a><span data-ttu-id="58aa2-102">Pooling de threads (C#)</span><span class="sxs-lookup"><span data-stu-id="58aa2-102">Thread Pooling (C#)</span></span>
<span data-ttu-id="58aa2-103">Um *pool de threads* é uma coleção de threads que pode ser usada para executar várias tarefas em segundo plano.</span><span class="sxs-lookup"><span data-stu-id="58aa2-103">A *thread pool* is a collection of threads that can be used to perform several tasks in the background.</span></span> <span data-ttu-id="58aa2-104">(Consulte [Threading (C#)](../../../../csharp/programming-guide/concepts/threading/index.md) para obter informações gerais.) Isso deixa o thread primário livre para executar outras tarefas de forma assíncrona.</span><span class="sxs-lookup"><span data-stu-id="58aa2-104">(See [Threading (C#)](../../../../csharp/programming-guide/concepts/threading/index.md) for background information.) This leaves the primary thread free to perform other tasks asynchronously.</span></span>  
  
 <span data-ttu-id="58aa2-105">Os pools de threads geralmente são empregados em aplicativos de servidor.</span><span class="sxs-lookup"><span data-stu-id="58aa2-105">Thread pools are often employed in server applications.</span></span> <span data-ttu-id="58aa2-106">Cada solicitação de entrada é atribuída a um thread do pool de threads para que a solicitação possa ser processada de forma assíncrona, sem prender o thread primário ou atrasar o processamento das solicitações subsequentes.</span><span class="sxs-lookup"><span data-stu-id="58aa2-106">Each incoming request is assigned to a thread from the thread pool, so that the request can be processed asynchronously, without tying up the primary thread or delaying the processing of subsequent requests.</span></span>  
  
 <span data-ttu-id="58aa2-107">Depois que um thread do pool conclui sua tarefa, ele é retornado para uma fila de segmentos em espera, no qual ele pode ser reutilizado.</span><span class="sxs-lookup"><span data-stu-id="58aa2-107">Once a thread in the pool completes its task, it is returned to a queue of waiting threads, where it can be reused.</span></span> <span data-ttu-id="58aa2-108">Essa reutilização permite que os aplicativos evitem o custo de criação de um novo thread para cada tarefa.</span><span class="sxs-lookup"><span data-stu-id="58aa2-108">This reuse enables applications to avoid the cost of creating a new thread for each task.</span></span>  
  
 <span data-ttu-id="58aa2-109">Os pools de threads geralmente têm um número máximo de threads.</span><span class="sxs-lookup"><span data-stu-id="58aa2-109">Thread pools typically have a maximum number of threads.</span></span> <span data-ttu-id="58aa2-110">Se todos os threads estiverem ocupados, as tarefas adicionais serão colocadas na fila até que possam ser atendidas conforme threads se tornam disponíveis.</span><span class="sxs-lookup"><span data-stu-id="58aa2-110">If all the threads are busy, additional tasks are put in queue until they can be serviced as threads become available.</span></span>  
  
 <span data-ttu-id="58aa2-111">Você pode implementar seu próprio pool de threads, mas é mais fácil de usar o pool de threads fornecido pelo .NET Framework por meio da classe <xref:System.Threading.ThreadPool>.</span><span class="sxs-lookup"><span data-stu-id="58aa2-111">You can implement your own thread pool, but it is easier to use the thread pool provided by the .NET Framework through the <xref:System.Threading.ThreadPool> class.</span></span>  
  
 <span data-ttu-id="58aa2-112">Com o pooling de threads, você chama o método <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=nameWithType> com um delegado para o procedimento que deseja executar e o C# cria o thread e executa o procedimento.</span><span class="sxs-lookup"><span data-stu-id="58aa2-112">With thread pooling, you call the <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=nameWithType> method with a delegate for the procedure you want to run, and C# creates the thread and runs your procedure.</span></span>  
  
## <a name="thread-pooling-example"></a><span data-ttu-id="58aa2-113">Exemplo de pooling de threads</span><span class="sxs-lookup"><span data-stu-id="58aa2-113">Thread Pooling Example</span></span>  
 <span data-ttu-id="58aa2-114">O exemplo a seguir mostra como você pode usar o pooling de threads para iniciar várias tarefas.</span><span class="sxs-lookup"><span data-stu-id="58aa2-114">The following example shows how you can use thread pooling to start several tasks.</span></span>  
  
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
  
 <span data-ttu-id="58aa2-115">Uma vantagem do pooling de threads é que você pode passar argumentos em um objeto de estado para o procedimento da tarefa.</span><span class="sxs-lookup"><span data-stu-id="58aa2-115">One advantage of thread pooling is that you can pass arguments in a state object to the task procedure.</span></span> <span data-ttu-id="58aa2-116">Se o procedimento que você está chamando exigir mais de um argumento, você pode converter uma estrutura ou uma instância de uma classe em um tipo de dados `Object`.</span><span class="sxs-lookup"><span data-stu-id="58aa2-116">If the procedure you are calling requires more than one argument, you can cast a structure or an instance of a class into an `Object` data type.</span></span>  
  
## <a name="thread-pool-parameters-and-return-values"></a><span data-ttu-id="58aa2-117">Parâmetros do pool de threads e valores retornados</span><span class="sxs-lookup"><span data-stu-id="58aa2-117">Thread Pool Parameters and Return Values</span></span>  
 <span data-ttu-id="58aa2-118">Os valores retornados de um thread do pool de threads não são simples.</span><span class="sxs-lookup"><span data-stu-id="58aa2-118">Returning values from a thread-pool thread is not straightforward.</span></span> <span data-ttu-id="58aa2-119">A forma padrão de retornar valores de uma chamada de função não é permitida porque os procedimentos `Sub` são o único tipo de procedimento que pode ser colocado na fila para um pool de thread.</span><span class="sxs-lookup"><span data-stu-id="58aa2-119">The standard way of returning values from a function call is not allowed because `Sub` procedures are the only type of procedure that can be queued to a thread pool.</span></span> <span data-ttu-id="58aa2-120">Uma maneira de você fornecer parâmetros e valores retornados é encapsular os parâmetros, valores retornados e métodos em uma classe wrapper conforme descrito em [Parâmetros e valores de retorno para procedimentos multithreaded (C#)](../../../../csharp/programming-guide/concepts/threading/parameters-and-return-values-for-multithreaded-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="58aa2-120">One way you can provide parameters and return values is by wrapping the parameters, return values, and methods in a wrapper class as described in [Parameters and Return Values for Multithreaded Procedures (C#)](../../../../csharp/programming-guide/concepts/threading/parameters-and-return-values-for-multithreaded-procedures.md).</span></span>  
  
 <span data-ttu-id="58aa2-121">Um modo mais fácil de fornecer parâmetros e retornar valores é usando a variável de objeto de estado `ByVal` do método <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A>.</span><span class="sxs-lookup"><span data-stu-id="58aa2-121">An easier way to provide parameters and return values is by using the optional `ByVal` state object variable of the <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A> method.</span></span> <span data-ttu-id="58aa2-122">Se você usar essa variável para passar uma referência para uma instância de uma classe, os membros da instância poderão ser modificados pelo thread do pool de threads e usados como valores retornados.</span><span class="sxs-lookup"><span data-stu-id="58aa2-122">If you use this variable to pass a reference to an instance of a class, the members of the instance can be modified by the thread-pool thread and used as return values.</span></span>  
  
 <span data-ttu-id="58aa2-123">Inicialmente pode não ser óbvio que você pode modificar um objeto referenciado por uma variável passada por valor.</span><span class="sxs-lookup"><span data-stu-id="58aa2-123">At first it may not be obvious that you can modify an object referred to by a variable that is passed by value.</span></span> <span data-ttu-id="58aa2-124">Você pode fazer isso porque somente a referência de objeto é passada por valor.</span><span class="sxs-lookup"><span data-stu-id="58aa2-124">You can do this because only the object reference is passed by value.</span></span> <span data-ttu-id="58aa2-125">Quando você faz alterações em membros do objeto referenciado pela referência de objeto, as alterações se aplicam à instância de classe real.</span><span class="sxs-lookup"><span data-stu-id="58aa2-125">When you make changes to members of the object referred to by the object reference, the changes apply to the actual class instance.</span></span>  
  
 <span data-ttu-id="58aa2-126">As estruturas não podem ser usadas para retornar valores dentro de objetos de estado.</span><span class="sxs-lookup"><span data-stu-id="58aa2-126">Structures cannot be used to return values inside state objects.</span></span> <span data-ttu-id="58aa2-127">Como estruturas são tipos de valor, as alterações que o processo assíncrono faz não alteram os membros da estrutura original.</span><span class="sxs-lookup"><span data-stu-id="58aa2-127">Because structures are value types, changes that the asynchronous process makes do not change the members of the original structure.</span></span> <span data-ttu-id="58aa2-128">Use estruturas para fornecer parâmetros quando valores de retorno não são necessários.</span><span class="sxs-lookup"><span data-stu-id="58aa2-128">Use structures to provide parameters when return values are not needed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58aa2-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="58aa2-129">See Also</span></span>  
 <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A>  
 <xref:System.Threading>  
 <xref:System.Threading.ThreadPool>  
 [<span data-ttu-id="58aa2-130">Como usar um pool de thread (C#)</span><span class="sxs-lookup"><span data-stu-id="58aa2-130">How to: Use a Thread Pool (C#)</span></span>](../../../../csharp/programming-guide/concepts/threading/how-to-use-a-thread-pool.md)  
 [<span data-ttu-id="58aa2-131">Threading (C#)</span><span class="sxs-lookup"><span data-stu-id="58aa2-131">Threading (C#)</span></span>](../../../../csharp/programming-guide/concepts/threading/index.md)  
 [<span data-ttu-id="58aa2-132">Aplicativos com multithread (C#)</span><span class="sxs-lookup"><span data-stu-id="58aa2-132">Multithreaded Applications (C#)</span></span>](../../../../csharp/programming-guide/concepts/threading/multithreaded-applications.md)  
 [<span data-ttu-id="58aa2-133">Sincronização de thread (C#)</span><span class="sxs-lookup"><span data-stu-id="58aa2-133">Thread Synchronization (C#)</span></span>](../../../../csharp/programming-guide/concepts/threading/thread-synchronization.md)
