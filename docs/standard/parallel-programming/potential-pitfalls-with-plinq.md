---
title: Armadilhas em potencial com PLINQ
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
helpviewer_keywords: PLINQ queries, pitfalls
ms.assetid: 75a38b55-4bc4-488a-87d5-89dbdbdc76a2
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f7c971d2c039e6441669108e966eba472819fde5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="potential-pitfalls-with-plinq"></a><span data-ttu-id="01d88-102">Armadilhas em potencial com PLINQ</span><span class="sxs-lookup"><span data-stu-id="01d88-102">Potential Pitfalls with PLINQ</span></span>
<span data-ttu-id="01d88-103">Em muitos casos, PLINQ pode oferecer melhorias significativas no desempenho ao longo de LINQ sequencial para consultas de objetos.</span><span class="sxs-lookup"><span data-stu-id="01d88-103">In many cases, PLINQ can provide significant performance improvements over sequential LINQ to Objects queries.</span></span> <span data-ttu-id="01d88-104">No entanto, o trabalho de paralelizar a execução da consulta apresenta complexidade que pode levar a problemas que, no código sequencial, não são tão comum ou não são encontrados.</span><span class="sxs-lookup"><span data-stu-id="01d88-104">However, the work of parallelizing the query execution introduces complexity that can lead to problems that, in sequential code, are not as common or are not encountered at all.</span></span> <span data-ttu-id="01d88-105">Este tópico lista algumas práticas recomendadas para evitar ao escrever consultas PLINQ.</span><span class="sxs-lookup"><span data-stu-id="01d88-105">This topic lists some practices to avoid when you write PLINQ queries.</span></span>  
  
## <a name="do-not-assume-that-parallel-is-always-faster"></a><span data-ttu-id="01d88-106">Não suponha que paralelo é sempre mais rápido</span><span class="sxs-lookup"><span data-stu-id="01d88-106">Do Not Assume That Parallel Is Always Faster</span></span>  
 <span data-ttu-id="01d88-107">Paralelização às vezes faz com que uma consulta PLINQ executar mais lentamente do que o LINQ em equivalentes de objetos.</span><span class="sxs-lookup"><span data-stu-id="01d88-107">Parallelization sometimes causes a PLINQ query to run slower than its LINQ to Objects equivalent.</span></span> <span data-ttu-id="01d88-108">O princípio básico é que as consultas que têm alguns elementos de origem e delegados rápida de usuário são improvável de aumento de velocidade muito.</span><span class="sxs-lookup"><span data-stu-id="01d88-108">The basic rule of thumb is that queries that have few source elements and fast user delegates are unlikely to speedup much.</span></span> <span data-ttu-id="01d88-109">No entanto, como muitos fatores estão envolvidos no desempenho, é recomendável medir os resultados reais antes de decidir se deseja usar PLINQ.</span><span class="sxs-lookup"><span data-stu-id="01d88-109">However, because many factors are involved in performance, we recommend that you measure actual results before you decide whether to use PLINQ.</span></span> <span data-ttu-id="01d88-110">Para saber mais, veja [Noções básicas sobre agilização em PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="01d88-110">For more information, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span>  
  
## <a name="avoid-writing-to-shared-memory-locations"></a><span data-ttu-id="01d88-111">Evitar gravar em locais de memória compartilhada</span><span class="sxs-lookup"><span data-stu-id="01d88-111">Avoid Writing to Shared Memory Locations</span></span>  
 <span data-ttu-id="01d88-112">No código sequencial, não é incomum para ler ou gravar em variáveis estáticas ou campos de classe.</span><span class="sxs-lookup"><span data-stu-id="01d88-112">In sequential code, it is not uncommon to read from or write to static variables or class fields.</span></span> <span data-ttu-id="01d88-113">No entanto, sempre que vários threads acessam simultaneamente essas variáveis, há um grande potencial de condições de corrida.</span><span class="sxs-lookup"><span data-stu-id="01d88-113">However, whenever multiple threads are accessing such variables concurrently, there is a big potential for race conditions.</span></span> <span data-ttu-id="01d88-114">Embora você possa usar bloqueios para sincronizar o acesso à variável, o custo da sincronização pode prejudicar o desempenho.</span><span class="sxs-lookup"><span data-stu-id="01d88-114">Even though you can use locks to synchronize access to the variable, the cost of synchronization can hurt performance.</span></span> <span data-ttu-id="01d88-115">Portanto, é recomendável que você evite, ou pelo menos limita, acesso ao estado em uma consulta PLINQ tanto quanto possível compartilhado.</span><span class="sxs-lookup"><span data-stu-id="01d88-115">Therefore, we recommend that you avoid, or at least limit, access to shared state in a PLINQ query as much as possible.</span></span>  
  
## <a name="avoid-over-parallelization"></a><span data-ttu-id="01d88-116">Evitar excesso de paralelização</span><span class="sxs-lookup"><span data-stu-id="01d88-116">Avoid Over-Parallelization</span></span>  
 <span data-ttu-id="01d88-117">Usando o `AsParallel` operador, você provoca dos custos indiretos de particionamento a coleção de origem e a sincronização de threads de trabalho.</span><span class="sxs-lookup"><span data-stu-id="01d88-117">By using the `AsParallel` operator, you incur the overhead costs of partitioning the source collection and synchronizing the worker threads.</span></span> <span data-ttu-id="01d88-118">Os benefícios de paralelização ainda estão limitados pelo número de processadores no computador.</span><span class="sxs-lookup"><span data-stu-id="01d88-118">The benefits of parallelization are further limited by the number of processors on the computer.</span></span> <span data-ttu-id="01d88-119">Não há nenhum aumento de velocidade a ser obtido executando vários threads vinculada à computação em apenas um processador.</span><span class="sxs-lookup"><span data-stu-id="01d88-119">There is no speedup to be gained by running multiple compute-bound threads on just one processor.</span></span> <span data-ttu-id="01d88-120">Portanto, você deve ser cuidado para não sobrescrever paralelizar uma consulta.</span><span class="sxs-lookup"><span data-stu-id="01d88-120">Therefore, you must be careful not to over-parallelize a query.</span></span>  
  
 <span data-ttu-id="01d88-121">O cenário mais comum no qual paralelização excessiva pode ocorrer é em consultas aninhadas, conforme mostrado no trecho a seguir.</span><span class="sxs-lookup"><span data-stu-id="01d88-121">The most common scenario in which over-parallelization can occur is in nested queries, as shown in the following snippet.</span></span>  
  
 [!code-csharp[PLINQ#20](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#20)]
 [!code-vb[PLINQ#20](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#20)]  
  
 <span data-ttu-id="01d88-122">Nesse caso, é melhor paralelizar somente a fonte de dados externa (clientes), a menos que uma ou mais das seguintes condições se aplicam:</span><span class="sxs-lookup"><span data-stu-id="01d88-122">In this case, it is best to parallelize only the outer data source (customers) unless one or more of the following conditions apply:</span></span>  
  
-   <span data-ttu-id="01d88-123">A fonte de dados interna (cust. Pedidos) é conhecido por ser muito longos.</span><span class="sxs-lookup"><span data-stu-id="01d88-123">The inner data source (cust.Orders) is known to be very long.</span></span>  
  
-   <span data-ttu-id="01d88-124">Você está executando uma computação cara em cada pedido.</span><span class="sxs-lookup"><span data-stu-id="01d88-124">You are performing an expensive computation on each order.</span></span> <span data-ttu-id="01d88-125">(A operação mostrada no exemplo não é cara).</span><span class="sxs-lookup"><span data-stu-id="01d88-125">(The operation shown in the example is not expensive.)</span></span>  
  
-   <span data-ttu-id="01d88-126">O sistema de destino é conhecido por ter processadores suficientes para controlar o número de threads que será produzido pela paralelizar a consulta em `cust.Orders`.</span><span class="sxs-lookup"><span data-stu-id="01d88-126">The target system is known to have enough processors to handle the number of threads that will be produced by parallelizing the query on `cust.Orders`.</span></span>  
  
 <span data-ttu-id="01d88-127">Em todos os casos, a melhor maneira de determinar a forma de consulta ideal é testar e medidas.</span><span class="sxs-lookup"><span data-stu-id="01d88-127">In all cases, the best way to determine the optimum query shape is to test and measure.</span></span> <span data-ttu-id="01d88-128">Para obter mais informações, consulte [como: desempenho de consulta PLINQ medida](../../../docs/standard/parallel-programming/how-to-measure-plinq-query-performance.md).</span><span class="sxs-lookup"><span data-stu-id="01d88-128">For more information, see [How to: Measure PLINQ Query Performance](../../../docs/standard/parallel-programming/how-to-measure-plinq-query-performance.md).</span></span>  
  
## <a name="avoid-calls-to-non-thread-safe-methods"></a><span data-ttu-id="01d88-129">Evite chamadas para métodos de Non-Thread-Safe</span><span class="sxs-lookup"><span data-stu-id="01d88-129">Avoid Calls to Non-Thread-Safe Methods</span></span>  
 <span data-ttu-id="01d88-130">Gravar em métodos de instância non-thread-safe de um PLINQ consulta pode levar à corrupção de dados que podem ou não pode ser detectados em seu programa.</span><span class="sxs-lookup"><span data-stu-id="01d88-130">Writing to non-thread-safe instance methods from a PLINQ query can lead to data corruption which may or may not go undetected in your program.</span></span> <span data-ttu-id="01d88-131">Isso também poderá resultar em exceções.</span><span class="sxs-lookup"><span data-stu-id="01d88-131">It can also lead to exceptions.</span></span> <span data-ttu-id="01d88-132">No exemplo a seguir, vários threads é tentar chamar o `Filestream.Write` método simultaneamente, que não é compatível com a classe.</span><span class="sxs-lookup"><span data-stu-id="01d88-132">In the following example, multiple threads would be attempting to call the `Filestream.Write` method simultaneously, which is not supported by the class.</span></span>  
  
```vb  
Dim fs As FileStream = File.OpenWrite(…)  
a.Where(...).OrderBy(...).Select(...).ForAll(Sub(x) fs.Write(x))  
```  
  
```csharp  
FileStream fs = File.OpenWrite(...);  
a.Where(...).OrderBy(...).Select(...).ForAll(x => fs.Write(x));  
```  
  
## <a name="limit-calls-to-thread-safe-methods"></a><span data-ttu-id="01d88-133">Limite de chamadas para métodos de Thread-Safe</span><span class="sxs-lookup"><span data-stu-id="01d88-133">Limit Calls to Thread-Safe Methods</span></span>  
 <span data-ttu-id="01d88-134">Os métodos mais estáticos no .NET Framework são thread-safe e podem ser chamados de vários threads simultaneamente.</span><span class="sxs-lookup"><span data-stu-id="01d88-134">Most static methods in the .NET Framework are thread-safe and can be called from multiple threads concurrently.</span></span> <span data-ttu-id="01d88-135">No entanto, até mesmo nesses casos, a sincronização envolvidos pode levar a diminuição significativa na consulta.</span><span class="sxs-lookup"><span data-stu-id="01d88-135">However, even in these cases, the synchronization involved can lead to significant slowdown in the query.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="01d88-136">Você pode testar isso por conta própria, inserindo algumas chamadas para <xref:System.Console.WriteLine%2A> em suas consultas.</span><span class="sxs-lookup"><span data-stu-id="01d88-136">You can test for this yourself by inserting some calls to <xref:System.Console.WriteLine%2A> in your queries.</span></span> <span data-ttu-id="01d88-137">Embora esse método é usado nos exemplos a documentação para fins de demonstração, não a use em consultas PLINQ.</span><span class="sxs-lookup"><span data-stu-id="01d88-137">Although this method is used in the documentation examples for demonstration purposes, do not use it in PLINQ queries.</span></span>  
  
## <a name="avoid-unnecessary-ordering-operations"></a><span data-ttu-id="01d88-138">Evite operações de classificação desnecessária</span><span class="sxs-lookup"><span data-stu-id="01d88-138">Avoid Unnecessary Ordering Operations</span></span>  
 <span data-ttu-id="01d88-139">Quando o PLINQ executa uma consulta em paralelo, divide a sequência de origem em partições que podem ser operadas simultaneamente em vários threads.</span><span class="sxs-lookup"><span data-stu-id="01d88-139">When PLINQ executes a query in parallel, it divides the source sequence into partitions that can be operated on concurrently on multiple threads.</span></span> <span data-ttu-id="01d88-140">Por padrão, a ordem na qual as partições são processadas e os resultados são fornecidos não é previsível (exceto para operadores como `OrderBy`).</span><span class="sxs-lookup"><span data-stu-id="01d88-140">By default, the order in which the partitions are processed and the results are delivered is not predictable (except for operators such as `OrderBy`).</span></span> <span data-ttu-id="01d88-141">Você pode instruir o PLINQ para preservar a ordenação de qualquer sequência de origem, mas isso tem um impacto negativo no desempenho.</span><span class="sxs-lookup"><span data-stu-id="01d88-141">You can instruct PLINQ to preserve the ordering of any source sequence, but this has a negative impact on performance.</span></span> <span data-ttu-id="01d88-142">A prática recomendada, sempre que possível, é estruturar consultas para que eles não confiam na preservação da ordem.</span><span class="sxs-lookup"><span data-stu-id="01d88-142">The best practice, whenever possible, is to structure queries so that they do not rely on order preservation.</span></span> <span data-ttu-id="01d88-143">Para saber mais, veja [Preservação da ordem em PLINQ](../../../docs/standard/parallel-programming/order-preservation-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="01d88-143">For more information, see [Order Preservation in PLINQ](../../../docs/standard/parallel-programming/order-preservation-in-plinq.md).</span></span>  
  
## <a name="prefer-forall-to-foreach-when-it-is-possible"></a><span data-ttu-id="01d88-144">Preferir ForAll ForEach quando é possível</span><span class="sxs-lookup"><span data-stu-id="01d88-144">Prefer ForAll to ForEach When It Is Possible</span></span>  
 <span data-ttu-id="01d88-145">Embora o PLINQ executa uma consulta em vários threads, se você consumir os resultados em uma `foreach` loop (`For Each` no Visual Basic), em seguida, os resultados da consulta devem ser mesclados novamente em um thread e acessados em série pelo enumerador.</span><span class="sxs-lookup"><span data-stu-id="01d88-145">Although PLINQ executes a query on multiple threads, if you consume the results in a `foreach` loop (`For Each` in Visual Basic), then the query results must be merged back into one thread and accessed serially by the enumerator.</span></span> <span data-ttu-id="01d88-146">Em alguns casos, isso é inevitável; No entanto, sempre que possível, use o `ForAll` método para habilitar cada thread gerar seus próprio resultados, por exemplo, gravando em uma coleção thread-safe, como <xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="01d88-146">In some cases, this is unavoidable; however, whenever possible, use the `ForAll` method to enable each thread to output its own results, for example, by writing to a thread-safe collection such as <xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="01d88-147">O mesmo problema se aplica a <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> em outras palavras, `source.AsParallel().Where().ForAll(...)` devem ser fortemente preferidos para</span><span class="sxs-lookup"><span data-stu-id="01d88-147">The same issue applies to <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> In other words, `source.AsParallel().Where().ForAll(...)` should be strongly preferred to</span></span>  
  
 <span data-ttu-id="01d88-148">`Parallel.ForEach(source.AsParallel().Where(), ...)`.</span><span class="sxs-lookup"><span data-stu-id="01d88-148">`Parallel.ForEach(source.AsParallel().Where(), ...)`.</span></span>  
  
## <a name="be-aware-of-thread-affinity-issues"></a><span data-ttu-id="01d88-149">Estar ciente das questões de afinidade de Thread</span><span class="sxs-lookup"><span data-stu-id="01d88-149">Be Aware of Thread Affinity Issues</span></span>  
 <span data-ttu-id="01d88-150">Algumas tecnologias, por exemplo, a interoperabilidade COM para componentes de Single-Threaded Apartment (STA), formulários do Windows e Windows Presentation Foundation (WPF), impõem restrições de afinidade de thread que exigem o código para executar em um thread específico.</span><span class="sxs-lookup"><span data-stu-id="01d88-150">Some technologies, for example, COM interoperability for Single-Threaded Apartment (STA) components, Windows Forms, and Windows Presentation Foundation (WPF), impose thread affinity restrictions that require code to run on a specific thread.</span></span> <span data-ttu-id="01d88-151">Por exemplo, no Windows Forms e WPF, um controle só pode ser acessado no thread no qual ele foi criado.</span><span class="sxs-lookup"><span data-stu-id="01d88-151">For example, in both Windows Forms and WPF, a control can only be accessed on the thread on which it was created.</span></span> <span data-ttu-id="01d88-152">Se você tentar acessar o estado compartilhado de um controle de formulários do Windows em uma consulta PLINQ, uma exceção é gerada se você estiver executando o depurador.</span><span class="sxs-lookup"><span data-stu-id="01d88-152">If you try to access the shared state of a Windows Forms control in a PLINQ query, an exception is raised if you are running in the debugger.</span></span> <span data-ttu-id="01d88-153">(Essa configuração pode ter sido desligado). No entanto, se sua consulta é consumida no thread da interface do usuário, em seguida, você pode acessar o controle do `foreach` loop que enumera a consulta resultante porque esse código é executado em apenas um thread.</span><span class="sxs-lookup"><span data-stu-id="01d88-153">(This setting can be turned off.) However, if your query is consumed on the UI thread, then you can access the control from the `foreach` loop that enumerates the query results because that code executes on just one thread.</span></span>  
  
## <a name="do-not-assume-that-iterations-of-foreach-for-and-forall-always-execute-in-parallel"></a><span data-ttu-id="01d88-154">Não suponha que iterações de ForEach, para e ForAll sempre executar em paralelo</span><span class="sxs-lookup"><span data-stu-id="01d88-154">Do Not Assume that Iterations of ForEach, For and ForAll Always Execute in Parallel</span></span>  
 <span data-ttu-id="01d88-155">É importante ter em mente que iterações individuais em um <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> ou <xref:System.Linq.ParallelEnumerable.ForAll%2A> pode executar um loop, mas não é necessário que executar em paralelo.</span><span class="sxs-lookup"><span data-stu-id="01d88-155">It is important to keep in mind that individual iterations in a <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> or <xref:System.Linq.ParallelEnumerable.ForAll%2A> loop may but do not have to execute in parallel.</span></span> <span data-ttu-id="01d88-156">Portanto, você deve evitar gravar qualquer código que depende de correção de execução paralela de iterações ou na execução de iterações em nenhuma ordem específica.</span><span class="sxs-lookup"><span data-stu-id="01d88-156">Therefore, you should avoid writing any code that depends for correctness on parallel execution of iterations or on the execution of iterations in any particular order.</span></span>  
  
 <span data-ttu-id="01d88-157">Por exemplo, esse código é provavelmente um deadlock:</span><span class="sxs-lookup"><span data-stu-id="01d88-157">For example, this code is likely to deadlock:</span></span>  
  
```vb  
Dim mre = New ManualResetEventSlim()  
    Enumerable.Range(0, ProcessorCount * 100).AsParallel().ForAll(Sub(j)   
  
                                                     If j = Environment.ProcessorCount Then  
  
                                                         Console.WriteLine("Set on {0} with value of {1}", Thread.CurrentThread.ManagedThreadId, j)  
                                                         mre.Set()  
  
                                                     Else  
  
                                                         Console.WriteLine("Waiting on {0} with value of {1}", Thread.CurrentThread.ManagedThreadId, j)  
                                                         mre.Wait()  
                                                     End If  
    End Sub) ' deadlocks  
```  
  
```csharp  
ManualResetEventSlim mre = new ManualResetEventSlim();  
            Enumerable.Range(0, ProcessorCount * 100).AsParallel().ForAll((j) =>  
            {  
                if (j == Environment.ProcessorCount)  
                {  
                    Console.WriteLine("Set on {0} with value of {1}", Thread.CurrentThread.ManagedThreadId, j);  
                    mre.Set();  
                }  
                else  
                {  
                    Console.WriteLine("Waiting on {0} with value of {1}", Thread.CurrentThread.ManagedThreadId, j);  
                    mre.Wait();  
                }  
            }); //deadlocks  
```  
  
 <span data-ttu-id="01d88-158">Neste exemplo, uma iteração define um evento, e todas as outras iterações esperar o evento.</span><span class="sxs-lookup"><span data-stu-id="01d88-158">In this example, one iteration sets an event, and all other iterations wait on the event.</span></span> <span data-ttu-id="01d88-159">Nenhuma das iterações espera pode concluir até que a iteração de configuração de evento foi concluída.</span><span class="sxs-lookup"><span data-stu-id="01d88-159">None of the waiting iterations can complete until the event-setting iteration has completed.</span></span> <span data-ttu-id="01d88-160">No entanto, é possível que as iterações espera bloqueiam todos os threads que são usados para executar o loop paralelo, antes da iteração de configuração de evento teve a chance de executar.</span><span class="sxs-lookup"><span data-stu-id="01d88-160">However, it is possible that the waiting iterations block all threads that are used to execute the parallel loop, before the event-setting iteration has had a chance to execute.</span></span> <span data-ttu-id="01d88-161">Isso resulta em um deadlock – a iteração de configuração de evento nunca será executado e as iterações espera nunca serão ativada.</span><span class="sxs-lookup"><span data-stu-id="01d88-161">This results in a deadlock – the event-setting iteration will never execute, and the waiting iterations will never wake up.</span></span>  
  
 <span data-ttu-id="01d88-162">Em particular, uma iteração de um loop paralelo nunca deve aguardar outra iteração do loop para tornar o progresso.</span><span class="sxs-lookup"><span data-stu-id="01d88-162">In particular, one iteration of a parallel loop should never wait on another iteration of the loop to make progress.</span></span> <span data-ttu-id="01d88-163">Se o loop paralelo decidir agendar as iterações sequencialmente, mas em ordem oposta, ocorrerá um deadlock.</span><span class="sxs-lookup"><span data-stu-id="01d88-163">If the parallel loop decides to schedule the iterations sequentially but in the opposite order, a deadlock will occur.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01d88-164">Consulte também</span><span class="sxs-lookup"><span data-stu-id="01d88-164">See Also</span></span>  
 [<span data-ttu-id="01d88-165">PLINQ (LINQ paralelo)</span><span class="sxs-lookup"><span data-stu-id="01d88-165">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
