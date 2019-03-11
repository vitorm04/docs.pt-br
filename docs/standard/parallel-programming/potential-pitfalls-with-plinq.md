---
title: Armadilhas em potencial com PLINQ
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, pitfalls
ms.assetid: 75a38b55-4bc4-488a-87d5-89dbdbdc76a2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2b996b09ed3973125d4d848d5e00c18ab02a6967
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/08/2019
ms.locfileid: "57673737"
---
# <a name="potential-pitfalls-with-plinq"></a><span data-ttu-id="dd06e-102">Armadilhas em potencial com PLINQ</span><span class="sxs-lookup"><span data-stu-id="dd06e-102">Potential Pitfalls with PLINQ</span></span>

<span data-ttu-id="dd06e-103">Em muitos casos, o PLINQ pode fornecer melhorias de desempenho significativas em relação a consultas sequenciais do LINQ to Objects.</span><span class="sxs-lookup"><span data-stu-id="dd06e-103">In many cases, PLINQ can provide significant performance improvements over sequential LINQ to Objects queries.</span></span> <span data-ttu-id="dd06e-104">No entanto, o trabalho de paralelizar a execução da consulta apresenta complexidade que pode levar a problemas que, em código sequencial, não são tão comuns ou não são encontrados.</span><span class="sxs-lookup"><span data-stu-id="dd06e-104">However, the work of parallelizing the query execution introduces complexity that can lead to problems that, in sequential code, are not as common or are not encountered at all.</span></span> <span data-ttu-id="dd06e-105">Este tópico lista algumas práticas a evitar ao escrever consultas PLINQ.</span><span class="sxs-lookup"><span data-stu-id="dd06e-105">This topic lists some practices to avoid when you write PLINQ queries.</span></span>

## <a name="do-not-assume-that-parallel-is-always-faster"></a><span data-ttu-id="dd06e-106">Não suponha que paralelo é sempre mais rápido</span><span class="sxs-lookup"><span data-stu-id="dd06e-106">Do Not Assume That Parallel Is Always Faster</span></span>

<span data-ttu-id="dd06e-107">A paralelização, por vezes, faz com que uma consulta PLINQ seja executada de forma mais devagar do que seu LINQ to Object equivalente.</span><span class="sxs-lookup"><span data-stu-id="dd06e-107">Parallelization sometimes causes a PLINQ query to run slower than its LINQ to Objects equivalent.</span></span> <span data-ttu-id="dd06e-108">A regra básica é que as consultas que têm poucos elementos fonte e delegados de usuários rápidos provavelmente não acelerarão muito.</span><span class="sxs-lookup"><span data-stu-id="dd06e-108">The basic rule of thumb is that queries that have few source elements and fast user delegates are unlikely to speedup much.</span></span> <span data-ttu-id="dd06e-109">No entanto, como muitos fatores estão envolvidos no desempenho, recomendamos avaliar os resultados reais antes de decidir pelo uso do PLINQ.</span><span class="sxs-lookup"><span data-stu-id="dd06e-109">However, because many factors are involved in performance, we recommend that you measure actual results before you decide whether to use PLINQ.</span></span> <span data-ttu-id="dd06e-110">Para saber mais, veja [Noções básicas sobre agilização em PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="dd06e-110">For more information, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span>

## <a name="avoid-writing-to-shared-memory-locations"></a><span data-ttu-id="dd06e-111">Evite gravar em locais de memória compartilhada</span><span class="sxs-lookup"><span data-stu-id="dd06e-111">Avoid Writing to Shared Memory Locations</span></span>

<span data-ttu-id="dd06e-112">No código sequencial, não é incomum ler ou gravar em variáveis estáticas ou campos de classe.</span><span class="sxs-lookup"><span data-stu-id="dd06e-112">In sequential code, it is not uncommon to read from or write to static variables or class fields.</span></span> <span data-ttu-id="dd06e-113">No entanto, sempre que vários threads estão acessando essas variáveis simultaneamente, existe um grande potencial para condições de corrida.</span><span class="sxs-lookup"><span data-stu-id="dd06e-113">However, whenever multiple threads are accessing such variables concurrently, there is a big potential for race conditions.</span></span> <span data-ttu-id="dd06e-114">Embora você possa usar bloqueios para sincronizar o acesso à variável, o custo da sincronização pode prejudicar o desempenho.</span><span class="sxs-lookup"><span data-stu-id="dd06e-114">Even though you can use locks to synchronize access to the variable, the cost of synchronization can hurt performance.</span></span> <span data-ttu-id="dd06e-115">Portanto, recomendamos que você evite, ou pelo menos limite, o acesso ao estado compartilhado em uma consulta PLINQ tanto quanto possível.</span><span class="sxs-lookup"><span data-stu-id="dd06e-115">Therefore, we recommend that you avoid, or at least limit, access to shared state in a PLINQ query as much as possible.</span></span>

## <a name="avoid-over-parallelization"></a><span data-ttu-id="dd06e-116">Evite o excesso de paralelização</span><span class="sxs-lookup"><span data-stu-id="dd06e-116">Avoid Over-Parallelization</span></span>

<span data-ttu-id="dd06e-117">Ao usar o operador `AsParallel`, você incorre em custos indiretos de particionar a coleção de origem e sincronizar os threads de trabalho.</span><span class="sxs-lookup"><span data-stu-id="dd06e-117">By using the `AsParallel` operator, you incur the overhead costs of partitioning the source collection and synchronizing the worker threads.</span></span> <span data-ttu-id="dd06e-118">Os benefícios da paralelização ainda estão limitados pelo número de processadores no computador.</span><span class="sxs-lookup"><span data-stu-id="dd06e-118">The benefits of parallelization are further limited by the number of processors on the computer.</span></span> <span data-ttu-id="dd06e-119">Não há nenhum aumento de velocidade a ser obtido executando vários threads vinculados à computação em apenas um processador.</span><span class="sxs-lookup"><span data-stu-id="dd06e-119">There is no speedup to be gained by running multiple compute-bound threads on just one processor.</span></span> <span data-ttu-id="dd06e-120">Portanto, você deve ter cuidado para não paralelizar excessivamente uma consulta.</span><span class="sxs-lookup"><span data-stu-id="dd06e-120">Therefore, you must be careful not to over-parallelize a query.</span></span>

<span data-ttu-id="dd06e-121">O cenário mais comum em que a paralelização excessiva pode ocorrer é em consultas aninhadas, como mostrado no seguinte snippet.</span><span class="sxs-lookup"><span data-stu-id="dd06e-121">The most common scenario in which over-parallelization can occur is in nested queries, as shown in the following snippet.</span></span>

[!code-csharp[PLINQ#20](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#20)]
[!code-vb[PLINQ#20](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#20)]

<span data-ttu-id="dd06e-122">Nesse caso, é melhor paralelizar apenas a fonte de dados externa (clientes), a menos que uma ou mais das seguintes condições se apliquem:</span><span class="sxs-lookup"><span data-stu-id="dd06e-122">In this case, it is best to parallelize only the outer data source (customers) unless one or more of the following conditions apply:</span></span>

- <span data-ttu-id="dd06e-123">A fonte interna de dados (cust.Orders) é muito longa.</span><span class="sxs-lookup"><span data-stu-id="dd06e-123">The inner data source (cust.Orders) is known to be very long.</span></span>

- <span data-ttu-id="dd06e-124">Você está realizando uma computação cara em cada ordem.</span><span class="sxs-lookup"><span data-stu-id="dd06e-124">You are performing an expensive computation on each order.</span></span> <span data-ttu-id="dd06e-125">(A operação mostrada no exemplo não é cara).</span><span class="sxs-lookup"><span data-stu-id="dd06e-125">(The operation shown in the example is not expensive.)</span></span>

- <span data-ttu-id="dd06e-126">O sistema de destino tem processadores suficientes para lidar com o número de threads que serão produzidos paralelizando a consulta em `cust.Orders`.</span><span class="sxs-lookup"><span data-stu-id="dd06e-126">The target system is known to have enough processors to handle the number of threads that will be produced by parallelizing the query on `cust.Orders`.</span></span>

<span data-ttu-id="dd06e-127">Em todos os casos, a melhor maneira de determinar a forma ideal da consulta é testar e medir.</span><span class="sxs-lookup"><span data-stu-id="dd06e-127">In all cases, the best way to determine the optimum query shape is to test and measure.</span></span> <span data-ttu-id="dd06e-128">Para obter mais informações, confira [Como: Avaliar o desempenho da consulta PLINQ](../../../docs/standard/parallel-programming/how-to-measure-plinq-query-performance.md).</span><span class="sxs-lookup"><span data-stu-id="dd06e-128">For more information, see [How to: Measure PLINQ Query Performance](../../../docs/standard/parallel-programming/how-to-measure-plinq-query-performance.md).</span></span>

## <a name="avoid-calls-to-non-thread-safe-methods"></a><span data-ttu-id="dd06e-129">Evite chamadas para métodos não thread-safe</span><span class="sxs-lookup"><span data-stu-id="dd06e-129">Avoid Calls to Non-Thread-Safe Methods</span></span>

<span data-ttu-id="dd06e-130">Gravar para métodos de instância não thread-safe a partir de uma consulta PLINQ pode levar à corrupção de dados que pode ou não ser detectada no seu programa.</span><span class="sxs-lookup"><span data-stu-id="dd06e-130">Writing to non-thread-safe instance methods from a PLINQ query can lead to data corruption which may or may not go undetected in your program.</span></span> <span data-ttu-id="dd06e-131">Isso também poderá levar a exceções.</span><span class="sxs-lookup"><span data-stu-id="dd06e-131">It can also lead to exceptions.</span></span> <span data-ttu-id="dd06e-132">No exemplo a seguir, vários segmentos estão tentando chamar simultaneamente o método `FileStream.Write`, que não é compatível com a classe.</span><span class="sxs-lookup"><span data-stu-id="dd06e-132">In the following example, multiple threads would be attempting to call the `FileStream.Write` method simultaneously, which is not supported by the class.</span></span>

```vb
Dim fs As FileStream = File.OpenWrite(…)
a.AsParallel().Where(...).OrderBy(...).Select(...).ForAll(Sub(x) fs.Write(x))
```

```csharp
FileStream fs = File.OpenWrite(...);
a.AsParallel().Where(...).OrderBy(...).Select(...).ForAll(x => fs.Write(x));
```

## <a name="limit-calls-to-thread-safe-methods"></a><span data-ttu-id="dd06e-133">Limite chamadas para métodos thread-safe</span><span class="sxs-lookup"><span data-stu-id="dd06e-133">Limit Calls to Thread-Safe Methods</span></span>

<span data-ttu-id="dd06e-134">A maioria dos métodos estáticos no .NET Framework é thread-safe e pode ser chamada de vários threads simultaneamente.</span><span class="sxs-lookup"><span data-stu-id="dd06e-134">Most static methods in the .NET Framework are thread-safe and can be called from multiple threads concurrently.</span></span> <span data-ttu-id="dd06e-135">No entanto, mesmo nesses casos, a sincronização envolvida pode levar a uma desaceleração significativa na consulta.</span><span class="sxs-lookup"><span data-stu-id="dd06e-135">However, even in these cases, the synchronization involved can lead to significant slowdown in the query.</span></span>

> [!NOTE]
> <span data-ttu-id="dd06e-136">Você pode testar isso sozinho inserindo algumas chamadas para <xref:System.Console.WriteLine%2A> nas suas consultas.</span><span class="sxs-lookup"><span data-stu-id="dd06e-136">You can test for this yourself by inserting some calls to <xref:System.Console.WriteLine%2A> in your queries.</span></span> <span data-ttu-id="dd06e-137">Embora esse método seja usado nos exemplos de documentação para fins de demonstração, não o use em consultas PLINQ.</span><span class="sxs-lookup"><span data-stu-id="dd06e-137">Although this method is used in the documentation examples for demonstration purposes, do not use it in PLINQ queries.</span></span>

## <a name="avoid-unnecessary-ordering-operations"></a><span data-ttu-id="dd06e-138">Evite operações de classificação desnecessárias</span><span class="sxs-lookup"><span data-stu-id="dd06e-138">Avoid Unnecessary Ordering Operations</span></span>

<span data-ttu-id="dd06e-139">Quando o PLINQ executa uma consulta em paralelo, divide a sequência de origem em partições que podem ser operadas simultaneamente em múltiplos segmentos.</span><span class="sxs-lookup"><span data-stu-id="dd06e-139">When PLINQ executes a query in parallel, it divides the source sequence into partitions that can be operated on concurrently on multiple threads.</span></span> <span data-ttu-id="dd06e-140">Por padrão, a ordem em que as partições são processadas e os resultados fornecidos não é previsível (exceto para operadores como `OrderBy`).</span><span class="sxs-lookup"><span data-stu-id="dd06e-140">By default, the order in which the partitions are processed and the results are delivered is not predictable (except for operators such as `OrderBy`).</span></span> <span data-ttu-id="dd06e-141">Você pode instruir o PLINQ a preservar a classificação de qualquer sequência de origem, mas isso tem um impacto negativo no desempenho.</span><span class="sxs-lookup"><span data-stu-id="dd06e-141">You can instruct PLINQ to preserve the ordering of any source sequence, but this has a negative impact on performance.</span></span> <span data-ttu-id="dd06e-142">A prática recomendada, sempre que possível, é estruturar consultas para que elas não dependam da preservação da classificação.</span><span class="sxs-lookup"><span data-stu-id="dd06e-142">The best practice, whenever possible, is to structure queries so that they do not rely on order preservation.</span></span> <span data-ttu-id="dd06e-143">Para saber mais, veja [Preservação da ordem em PLINQ](../../../docs/standard/parallel-programming/order-preservation-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="dd06e-143">For more information, see [Order Preservation in PLINQ](../../../docs/standard/parallel-programming/order-preservation-in-plinq.md).</span></span>

## <a name="prefer-forall-to-foreach-when-it-is-possible"></a><span data-ttu-id="dd06e-144">Dê preferência a ForAll em vez de ForEach quando possível</span><span class="sxs-lookup"><span data-stu-id="dd06e-144">Prefer ForAll to ForEach When It Is Possible</span></span>

<span data-ttu-id="dd06e-145">Embora o PLINQ execute uma consulta em múltiplos threads, se você consumir os resultados em um loop `foreach` (`For Each` no Visual Basic), os resultados da consulta devem ser mesclados novamente em um thread e acessados em série pelo enumerador.</span><span class="sxs-lookup"><span data-stu-id="dd06e-145">Although PLINQ executes a query on multiple threads, if you consume the results in a `foreach` loop (`For Each` in Visual Basic), then the query results must be merged back into one thread and accessed serially by the enumerator.</span></span> <span data-ttu-id="dd06e-146">Em alguns casos, isso é inevitável. No entanto, sempre que possível, use o método `ForAll` para habilitar cada thread a gerar seus próprios resultados, por exemplo, gravando para uma coleção thread-safe como <xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="dd06e-146">In some cases, this is unavoidable; however, whenever possible, use the `ForAll` method to enable each thread to output its own results, for example, by writing to a thread-safe collection such as <xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="dd06e-147">A mesma questão se aplica a <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>. Em outras palavras, `source.AsParallel().Where().ForAll(...)` devem ser fortemente preferidos no lugar de</span><span class="sxs-lookup"><span data-stu-id="dd06e-147">The same issue applies to <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> In other words, `source.AsParallel().Where().ForAll(...)` should be strongly preferred to</span></span>

<span data-ttu-id="dd06e-148">`Parallel.ForEach(source.AsParallel().Where(), ...)`.</span><span class="sxs-lookup"><span data-stu-id="dd06e-148">`Parallel.ForEach(source.AsParallel().Where(), ...)`.</span></span>

## <a name="be-aware-of-thread-affinity-issues"></a><span data-ttu-id="dd06e-149">Esteja ciente de questões de afinidade de thread</span><span class="sxs-lookup"><span data-stu-id="dd06e-149">Be Aware of Thread Affinity Issues</span></span>

<span data-ttu-id="dd06e-150">Algumas tecnologias, por exemplo, interoperabilidade COM para componentes de um único segmento (STA), Windows Forms e Windows Presentation Foundation (WPF), impõem restrições de afinidade de thread que exigem que o código seja executado em um thread específico.</span><span class="sxs-lookup"><span data-stu-id="dd06e-150">Some technologies, for example, COM interoperability for Single-Threaded Apartment (STA) components, Windows Forms, and Windows Presentation Foundation (WPF), impose thread affinity restrictions that require code to run on a specific thread.</span></span> <span data-ttu-id="dd06e-151">Por exemplo, tanto no Windows Forms quanto no WPF, um controle só pode ser acessado no thread em que foi criado.</span><span class="sxs-lookup"><span data-stu-id="dd06e-151">For example, in both Windows Forms and WPF, a control can only be accessed on the thread on which it was created.</span></span> <span data-ttu-id="dd06e-152">Se você tenta acessar o estado compartilhado de um controle Windows Forms em uma consulta PLINQ, uma exceção é gerada se você estiver executando no depurador.</span><span class="sxs-lookup"><span data-stu-id="dd06e-152">If you try to access the shared state of a Windows Forms control in a PLINQ query, an exception is raised if you are running in the debugger.</span></span> <span data-ttu-id="dd06e-153">(Essa configuração pode ser desligada). No entanto, se sua consulta for consumada no thread da IU, você pode acessar o controle do loop `foreach` que enumera os resultados da consulta, pois esse código é executado em apenas um thread.</span><span class="sxs-lookup"><span data-stu-id="dd06e-153">(This setting can be turned off.) However, if your query is consumed on the UI thread, then you can access the control from the `foreach` loop that enumerates the query results because that code executes on just one thread.</span></span>

## <a name="do-not-assume-that-iterations-of-foreach-for-and-forall-always-execute-in-parallel"></a><span data-ttu-id="dd06e-154">Não suponha que iterações para ForEach, For e ForAll sempre sejam executadas em paralelo</span><span class="sxs-lookup"><span data-stu-id="dd06e-154">Do Not Assume that Iterations of ForEach, For and ForAll Always Execute in Parallel</span></span>

<span data-ttu-id="dd06e-155">É importante ter em mente que iterações individuais em um loop <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> ou <xref:System.Linq.ParallelEnumerable.ForAll%2A> podem, mas não necessariamente têm que, ser executadas em paralelo.</span><span class="sxs-lookup"><span data-stu-id="dd06e-155">It is important to keep in mind that individual iterations in a <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> or <xref:System.Linq.ParallelEnumerable.ForAll%2A> loop may but do not have to execute in parallel.</span></span> <span data-ttu-id="dd06e-156">Portanto, você deve evitar gravar qualquer código que dependa da correção na execução paralela de iterações ou na execução de iterações em qualquer classificação específica.</span><span class="sxs-lookup"><span data-stu-id="dd06e-156">Therefore, you should avoid writing any code that depends for correctness on parallel execution of iterations or on the execution of iterations in any particular order.</span></span>

<span data-ttu-id="dd06e-157">Por exemplo, esse código é provavelmente um deadlock:</span><span class="sxs-lookup"><span data-stu-id="dd06e-157">For example, this code is likely to deadlock:</span></span>

```vb
Dim mre = New ManualResetEventSlim()
Enumerable.Range(0, Environment.ProcessorCount * 100).AsParallel().ForAll(Sub(j)
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
Enumerable.Range(0, Environment.ProcessorCount * 100).AsParallel().ForAll((j) =>
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

<span data-ttu-id="dd06e-158">Neste exemplo, uma iteração define um evento e todas as outras iterações aguardam o evento.</span><span class="sxs-lookup"><span data-stu-id="dd06e-158">In this example, one iteration sets an event, and all other iterations wait on the event.</span></span> <span data-ttu-id="dd06e-159">Nenhuma das iterações em espera pode ser concluída até que a iteração de configuração do evento tenha sido concluída.</span><span class="sxs-lookup"><span data-stu-id="dd06e-159">None of the waiting iterations can complete until the event-setting iteration has completed.</span></span> <span data-ttu-id="dd06e-160">No entanto, é possível que as iterações em espera bloqueiem todos os threads que são usados para executar o loop paralelo, antes que a iteração de configuração do evento tenha tido a chance de ser executada.</span><span class="sxs-lookup"><span data-stu-id="dd06e-160">However, it is possible that the waiting iterations block all threads that are used to execute the parallel loop, before the event-setting iteration has had a chance to execute.</span></span> <span data-ttu-id="dd06e-161">Isso resulta em um deadlock – a iteração de configuração do evento nunca será executada e as iterações em espera nunca serão ativadas.</span><span class="sxs-lookup"><span data-stu-id="dd06e-161">This results in a deadlock – the event-setting iteration will never execute, and the waiting iterations will never wake up.</span></span>

<span data-ttu-id="dd06e-162">Em particular, uma iteração de um loop paralelo nunca deve aguardar outra iteração do loop para progredir.</span><span class="sxs-lookup"><span data-stu-id="dd06e-162">In particular, one iteration of a parallel loop should never wait on another iteration of the loop to make progress.</span></span> <span data-ttu-id="dd06e-163">Se o loop paralelo decidir agendar as iterações sequencialmente, mas em ordem oposta, ocorrerá um deadlock.</span><span class="sxs-lookup"><span data-stu-id="dd06e-163">If the parallel loop decides to schedule the iterations sequentially but in the opposite order, a deadlock will occur.</span></span>

## <a name="see-also"></a><span data-ttu-id="dd06e-164">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dd06e-164">See also</span></span>

- [<span data-ttu-id="dd06e-165">PLINQ (LINQ paralelo)</span><span class="sxs-lookup"><span data-stu-id="dd06e-165">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
