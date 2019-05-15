---
title: Práticas recomendadas de threading gerenciado
ms.date: 10/15/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- threading [.NET Framework], design guidelines
- threading [.NET Framework], best practices
- managed threading
ms.assetid: e51988e7-7f4b-4646-a06d-1416cee8d557
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d8319424c82327fd9743c573846663bdd76ed1b9
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64644620"
---
# <a name="managed-threading-best-practices"></a><span data-ttu-id="d209b-102">Práticas recomendadas de threading gerenciado</span><span class="sxs-lookup"><span data-stu-id="d209b-102">Managed threading best practices</span></span>
<span data-ttu-id="d209b-103">O multithreading requer programação cuidadosa.</span><span class="sxs-lookup"><span data-stu-id="d209b-103">Multithreading requires careful programming.</span></span> <span data-ttu-id="d209b-104">Para a maioria das tarefas, você pode reduzir a complexidade ao enfileirar solicitações para a execução por parte de threads de pool.</span><span class="sxs-lookup"><span data-stu-id="d209b-104">For most tasks, you can reduce complexity by queuing requests for execution by thread pool threads.</span></span> <span data-ttu-id="d209b-105">Este tópico aborda situações mais difíceis, como coordenar o trabalho de vários threads ou manipular threads que bloqueiam.</span><span class="sxs-lookup"><span data-stu-id="d209b-105">This topic addresses more difficult situations, such as coordinating the work of multiple threads, or handling threads that block.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d209b-106">A partir do .NET Framework 4, a biblioteca de paralelismo de tarefas e o PLINQ fornecem APIs que reduzem parte da complexidade e os riscos da programação de multithreading.</span><span class="sxs-lookup"><span data-stu-id="d209b-106">Starting with the .NET Framework 4, the Task Parallel Library and PLINQ provide APIs that reduce some of the complexity and risks of multi-threaded programming.</span></span> <span data-ttu-id="d209b-107">Para saber mais, confira [Programação paralela em .NET](../../../docs/standard/parallel-programming/index.md).</span><span class="sxs-lookup"><span data-stu-id="d209b-107">For more information, see [Parallel Programming in .NET](../../../docs/standard/parallel-programming/index.md).</span></span>  
  
## <a name="deadlocks-and-race-conditions"></a><span data-ttu-id="d209b-108">Deadlocks e condições de corrida</span><span class="sxs-lookup"><span data-stu-id="d209b-108">Deadlocks and race conditions</span></span>  
 <span data-ttu-id="d209b-109">O multithreading resolve problemas com taxa de transferência e capacidade de resposta, mas, ao fazer isso, ele introduz novos problemas: deadlocks e condições de corrida.</span><span class="sxs-lookup"><span data-stu-id="d209b-109">Multithreading solves problems with throughput and responsiveness, but in doing so it introduces new problems: deadlocks and race conditions.</span></span>  
  
### <a name="deadlocks"></a><span data-ttu-id="d209b-110">Deadlocks</span><span class="sxs-lookup"><span data-stu-id="d209b-110">Deadlocks</span></span>  
 <span data-ttu-id="d209b-111">Um deadlock ocorre quando um dos dois threads tenta bloquear um recurso que o outro já bloqueou.</span><span class="sxs-lookup"><span data-stu-id="d209b-111">A deadlock occurs when each of two threads tries to lock a resource the other has already locked.</span></span> <span data-ttu-id="d209b-112">Nenhum dos threads pode fazer progresso adicional.</span><span class="sxs-lookup"><span data-stu-id="d209b-112">Neither thread can make any further progress.</span></span>  
  
 <span data-ttu-id="d209b-113">Muitos métodos das classes de threading gerenciadas fornecem tempos limite para ajudá-lo a detectar deadlocks.</span><span class="sxs-lookup"><span data-stu-id="d209b-113">Many methods of the managed threading classes provide time-outs to help you detect deadlocks.</span></span> <span data-ttu-id="d209b-114">Por exemplo, o código a seguir tenta adquirir um bloqueio em um objeto denominado `lockObject`.</span><span class="sxs-lookup"><span data-stu-id="d209b-114">For example, the following code attempts to acquire a lock on an object named `lockObject`.</span></span> <span data-ttu-id="d209b-115">Se o bloqueio não for obtido em 300 milissegundos, <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType> retornará `false`.</span><span class="sxs-lookup"><span data-stu-id="d209b-115">If the lock is not obtained in 300 milliseconds, <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType> returns `false`.</span></span>  
  
```vb  
If Monitor.TryEnter(lockObject, 300) Then  
    Try  
        ' Place code protected by the Monitor here.  
    Finally  
        Monitor.Exit(lockObject)  
    End Try  
Else  
    ' Code to execute if the attempt times out.  
End If  
```  
  
```csharp  
if (Monitor.TryEnter(lockObject, 300)) {  
    try {  
        // Place code protected by the Monitor here.  
    }  
    finally {  
        Monitor.Exit(lockObject);  
    }  
}  
else {  
    // Code to execute if the attempt times out.  
}  
```  
  
### <a name="race-conditions"></a><span data-ttu-id="d209b-116">Condições de corrida</span><span class="sxs-lookup"><span data-stu-id="d209b-116">Race conditions</span></span>  
 <span data-ttu-id="d209b-117">Uma condição de corrida é um bug que ocorre quando o resultado de um programa depende de qual dos dois ou mais threads alcança um determinado bloco de código primeiro.</span><span class="sxs-lookup"><span data-stu-id="d209b-117">A race condition is a bug that occurs when the outcome of a program depends on which of two or more threads reaches a particular block of code first.</span></span> <span data-ttu-id="d209b-118">Executar o programa muitas vezes produz resultados diferentes e o resultado de qualquer execução não pode ser previsto.</span><span class="sxs-lookup"><span data-stu-id="d209b-118">Running the program many times produces different results, and the result of any given run cannot be predicted.</span></span>  
  
 <span data-ttu-id="d209b-119">Um exemplo simples de uma condição de corrida é incrementar um campo.</span><span class="sxs-lookup"><span data-stu-id="d209b-119">A simple example of a race condition is incrementing a field.</span></span> <span data-ttu-id="d209b-120">Suponha que uma classe tem um campo **static** particular (**Shared** no Visual Basic) que é incrementado toda vez que uma instância da classe é criada, usando um código como `objCt++;` (C#) ou `objCt += 1` (Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="d209b-120">Suppose a class has a private **static** field (**Shared** in Visual Basic) that is incremented every time an instance of the class is created, using code such as `objCt++;` (C#) or `objCt += 1` (Visual Basic).</span></span> <span data-ttu-id="d209b-121">Esta operação requer o carregamento do valor de `objCt` em um registro, incrementando o valor e o armazenando em `objCt`.</span><span class="sxs-lookup"><span data-stu-id="d209b-121">This operation requires loading the value from `objCt` into a register, incrementing the value, and storing it in `objCt`.</span></span>  
  
 <span data-ttu-id="d209b-122">Em um aplicativo com multithreading, um thread que carregou e incrementou o valor pode ser impedido por outro thread que execute todas as três etapas; quando o primeiro thread retomar a execução e armazenar seu valor, ele substituirá `objCt` sem levar em conta o fato de que o valor foi alterado durante o processo.</span><span class="sxs-lookup"><span data-stu-id="d209b-122">In a multithreaded application, a thread that has loaded and incremented the value might be preempted by another thread which performs all three steps; when the first thread resumes execution and stores its value, it overwrites `objCt` without taking into account the fact that the value has changed in the interim.</span></span>  
  
 <span data-ttu-id="d209b-123">Essa condição de corrida específica pode ser evitada facilmente usando métodos da classe <xref:System.Threading.Interlocked>, como <xref:System.Threading.Interlocked.Increment%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d209b-123">This particular race condition is easily avoided by using methods of the <xref:System.Threading.Interlocked> class, such as <xref:System.Threading.Interlocked.Increment%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="d209b-124">Para ler sobre outras técnicas para sincronizar dados entre vários threads, confira [Sincronizando dados para multithreading](../../../docs/standard/threading/synchronizing-data-for-multithreading.md).</span><span class="sxs-lookup"><span data-stu-id="d209b-124">To read about other techniques for synchronizing data among multiple threads, see [Synchronizing Data for Multithreading](../../../docs/standard/threading/synchronizing-data-for-multithreading.md).</span></span>  
  
 <span data-ttu-id="d209b-125">Condições de corrida também podem ocorrer quando você sincroniza as atividades de vários threads.</span><span class="sxs-lookup"><span data-stu-id="d209b-125">Race conditions can also occur when you synchronize the activities of multiple threads.</span></span> <span data-ttu-id="d209b-126">Sempre que você escreve uma linha de código, é preciso considerar o que poderia acontecer se um thread fosse impedido antes de executar a linha (ou antes de qualquer uma das instruções de máquina individuais que compõem a linha) e outro thread o substituísse.</span><span class="sxs-lookup"><span data-stu-id="d209b-126">Whenever you write a line of code, you must consider what might happen if a thread were preempted before executing the line (or before any of the individual machine instructions that make up the line), and another thread overtook it.</span></span>  
  
## <a name="static-members-and-static-constructors"></a><span data-ttu-id="d209b-127">Membros estáticos e construtores estáticos</span><span class="sxs-lookup"><span data-stu-id="d209b-127">Static members and static constructors</span></span>  
 <span data-ttu-id="d209b-128">Uma classe não é inicializada até que o construtor de classe (construtor `static` em C#, `Shared Sub New` no Visual Basic) tenha terminado de ser executado.</span><span class="sxs-lookup"><span data-stu-id="d209b-128">A class is not initialized until its class constructor (`static` constructor in C#, `Shared Sub New` in Visual Basic) has finished running.</span></span> <span data-ttu-id="d209b-129">Para impedir a execução de código em um tipo não inicializado, o Common Language Runtime bloqueia todas as chamadas de outros threads para membros `static` da classe (membros `Shared` no Visual Basic) até que o construtor da classe tenha concluído sua execução.</span><span class="sxs-lookup"><span data-stu-id="d209b-129">To prevent the execution of code on a type that is not initialized, the common language runtime blocks all calls from other threads to `static` members of the class (`Shared` members in Visual Basic) until the class constructor has finished running.</span></span>  
  
 <span data-ttu-id="d209b-130">Por exemplo, se um construtor de classe iniciar um novo thread, e o procedimento do thread chamar um membro `static` da classe, o novo thread bloqueia até que o construtor da classe seja concluído.</span><span class="sxs-lookup"><span data-stu-id="d209b-130">For example, if a class constructor starts a new thread, and the thread procedure calls a `static` member of the class, the new thread blocks until the class constructor completes.</span></span>  
  
 <span data-ttu-id="d209b-131">Isso se aplica a qualquer tipo que possa ter um construtor `static`.</span><span class="sxs-lookup"><span data-stu-id="d209b-131">This applies to any type that can have a `static` constructor.</span></span>  

## <a name="number-of-processors"></a><span data-ttu-id="d209b-132">Número de processadores</span><span class="sxs-lookup"><span data-stu-id="d209b-132">Number of processors</span></span>

<span data-ttu-id="d209b-133">A existência de apenas um ou de vários processadores disponíveis em um sistema pode influenciar a arquitetura de vários threads.</span><span class="sxs-lookup"><span data-stu-id="d209b-133">Whether there are multiple processors or only one processor available on a system can influence multithreaded architecture.</span></span> <span data-ttu-id="d209b-134">Para obter mais informações, veja [Número de processadores](https://docs.microsoft.com/previous-versions/dotnet/netframework-1.1/1c9txz50(v%3dvs.71)#number-of-processors).</span><span class="sxs-lookup"><span data-stu-id="d209b-134">For more information, see [Number of Processors](https://docs.microsoft.com/previous-versions/dotnet/netframework-1.1/1c9txz50(v%3dvs.71)#number-of-processors).</span></span>

<span data-ttu-id="d209b-135">Use a propriedade <xref:System.Environment.ProcessorCount?displayProperty=nameWithType> para determinar o número de processadores disponíveis no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="d209b-135">Use the <xref:System.Environment.ProcessorCount?displayProperty=nameWithType> property to determine the number of processors available at runtime.</span></span>
  
## <a name="general-recommendations"></a><span data-ttu-id="d209b-136">Recomendações gerais</span><span class="sxs-lookup"><span data-stu-id="d209b-136">General recommendations</span></span>  
 <span data-ttu-id="d209b-137">Ao usar vários threads, considere as seguintes diretrizes:</span><span class="sxs-lookup"><span data-stu-id="d209b-137">Consider the following guidelines when using multiple threads:</span></span>  
  
- <span data-ttu-id="d209b-138">Não use <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> para encerrar outros threads.</span><span class="sxs-lookup"><span data-stu-id="d209b-138">Don't use <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> to terminate other threads.</span></span> <span data-ttu-id="d209b-139">Chamar **Abort** em outro thread equivale a gerar uma exceção nesse thread sem saber qual ponto ele alcançou nesse processamento.</span><span class="sxs-lookup"><span data-stu-id="d209b-139">Calling **Abort** on another thread is akin to throwing an exception on that thread, without knowing what point that thread has reached in its processing.</span></span>  
  
- <span data-ttu-id="d209b-140">Não use <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> e <xref:System.Threading.Thread.Resume%2A?displayProperty=nameWithType> para sincronizar as atividades de vários threads.</span><span class="sxs-lookup"><span data-stu-id="d209b-140">Don't use <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> and <xref:System.Threading.Thread.Resume%2A?displayProperty=nameWithType> to synchronize the activities of multiple threads.</span></span> <span data-ttu-id="d209b-141">Use <xref:System.Threading.Mutex>, <xref:System.Threading.ManualResetEvent>, <xref:System.Threading.AutoResetEvent>, e <xref:System.Threading.Monitor>.</span><span class="sxs-lookup"><span data-stu-id="d209b-141">Do use <xref:System.Threading.Mutex>, <xref:System.Threading.ManualResetEvent>, <xref:System.Threading.AutoResetEvent>, and <xref:System.Threading.Monitor>.</span></span>  
  
- <span data-ttu-id="d209b-142">Não controle a execução de threads de trabalho do seu programa principal (usando eventos, por exemplo).</span><span class="sxs-lookup"><span data-stu-id="d209b-142">Don't control the execution of worker threads from your main program (using events, for example).</span></span> <span data-ttu-id="d209b-143">Em vez disso, projete seu programa de forma que os threads de trabalho sejam responsáveis por esperar até que o trabalho esteja disponível, executá-lo e notificar outras partes do seu programa quando terminar.</span><span class="sxs-lookup"><span data-stu-id="d209b-143">Instead, design your program so that worker threads are responsible for waiting until work is available, executing it, and notifying other parts of your program when finished.</span></span> <span data-ttu-id="d209b-144">Se seus threads de trabalho não bloquearem, considere o uso de threads de pool.</span><span class="sxs-lookup"><span data-stu-id="d209b-144">If your worker threads do not block, consider using thread pool threads.</span></span> <span data-ttu-id="d209b-145"><xref:System.Threading.Monitor.PulseAll%2A?displayProperty=nameWithType> é útil em situações em que os threads de trabalho bloqueiam.</span><span class="sxs-lookup"><span data-stu-id="d209b-145"><xref:System.Threading.Monitor.PulseAll%2A?displayProperty=nameWithType> is useful in situations where worker threads block.</span></span>  
  
- <span data-ttu-id="d209b-146">Não use tipos como objetos de bloqueio.</span><span class="sxs-lookup"><span data-stu-id="d209b-146">Don't use types as lock objects.</span></span> <span data-ttu-id="d209b-147">Isto é, evite códigos como `lock(typeof(X))` em C# ou `SyncLock(GetType(X))` no Visual Basic ou o uso de <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> com objetos <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="d209b-147">That is, avoid code such as `lock(typeof(X))` in C# or `SyncLock(GetType(X))` in Visual Basic, or the use of <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> with <xref:System.Type> objects.</span></span> <span data-ttu-id="d209b-148">Para um determinado tipo, há apenas uma instância de <xref:System.Type?displayProperty=nameWithType> por domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d209b-148">For a given type, there is only one instance of <xref:System.Type?displayProperty=nameWithType> per application domain.</span></span> <span data-ttu-id="d209b-149">Se o tipo no qual você usar um bloqueio for público, o código que não for o seu próprio poderá assumir bloqueios, levando a deadlocks.</span><span class="sxs-lookup"><span data-stu-id="d209b-149">If the type you take a lock on is public, code other than your own can take locks on it, leading to deadlocks.</span></span> <span data-ttu-id="d209b-150">Para problemas adicionais, consulte [Práticas recomendadas de confiabilidade](../../../docs/framework/performance/reliability-best-practices.md).</span><span class="sxs-lookup"><span data-stu-id="d209b-150">For additional issues, see [Reliability Best Practices](../../../docs/framework/performance/reliability-best-practices.md).</span></span>  
  
- <span data-ttu-id="d209b-151">Tenha cuidado ao bloquear em instâncias, por exemplo `lock(this)` em C# ou `SyncLock(Me)` no Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="d209b-151">Use caution when locking on instances, for example `lock(this)` in C# or `SyncLock(Me)` in Visual Basic.</span></span> <span data-ttu-id="d209b-152">Se outro código no seu aplicativo, externo ao tipo, assumir um bloqueio no objeto, podem ocorrer deadlocks.</span><span class="sxs-lookup"><span data-stu-id="d209b-152">If other code in your application, external to the type, takes a lock on the object, deadlocks could occur.</span></span>  
  
- <span data-ttu-id="d209b-153">Certifique-se de que um thread que tenha entrado em um monitor sempre o deixe, mesmo que uma exceção ocorra enquanto o thread estiver no monitor.</span><span class="sxs-lookup"><span data-stu-id="d209b-153">Do ensure that a thread that has entered a monitor always leaves that monitor, even if an exception occurs while the thread is in the monitor.</span></span> <span data-ttu-id="d209b-154">A instrução [lock](~/docs/csharp/language-reference/keywords/lock-statement.md) do C# e a instrução [SyncLock](~/docs/visual-basic/language-reference/statements/synclock-statement.md) do Visual Basic oferece esse comportamento automaticamente, empregando um bloco **finally** para garantir que <xref:System.Threading.Monitor.Exit%2A?displayProperty=nameWithType> seja chamado.</span><span class="sxs-lookup"><span data-stu-id="d209b-154">The C# [lock](~/docs/csharp/language-reference/keywords/lock-statement.md) statement and the Visual Basic [SyncLock](~/docs/visual-basic/language-reference/statements/synclock-statement.md) statement provide this behavior automatically, employing a **finally** block to ensure that <xref:System.Threading.Monitor.Exit%2A?displayProperty=nameWithType> is called.</span></span> <span data-ttu-id="d209b-155">Se você não puder garantir que **Exit** seja chamado, considere alterar o design para usar **Mutex**.</span><span class="sxs-lookup"><span data-stu-id="d209b-155">If you cannot ensure that **Exit** will be called, consider changing your design to use **Mutex**.</span></span> <span data-ttu-id="d209b-156">Um mutex é liberado automaticamente quando o thread que o possui atualmente for encerrado.</span><span class="sxs-lookup"><span data-stu-id="d209b-156">A mutex is automatically released when the thread that currently owns it terminates.</span></span>  
  
- <span data-ttu-id="d209b-157">Usar vários threads para tarefas que exigem recursos diferentes e evite atribuir vários threads para um único recurso.</span><span class="sxs-lookup"><span data-stu-id="d209b-157">Do use multiple threads for tasks that require different resources, and avoid assigning multiple threads to a single resource.</span></span> <span data-ttu-id="d209b-158">Por exemplo, qualquer tarefa que envolva E/S se beneficia em ter seu próprio thread, porque esse thread bloqueará durante as operações de E/S e, assim, permitirá que outros threads sejam executados.</span><span class="sxs-lookup"><span data-stu-id="d209b-158">For example, any task involving I/O benefits from having its own thread, because that thread will block during I/O operations and thus allow other threads to execute.</span></span> <span data-ttu-id="d209b-159">A entrada do usuário é outro recurso que se beneficia com um thread dedicado.</span><span class="sxs-lookup"><span data-stu-id="d209b-159">User input is another resource that benefits from a dedicated thread.</span></span> <span data-ttu-id="d209b-160">Em um computador de um processador, uma tarefa que envolve a computação intensiva coexiste com a entrada do usuário e com tarefas que envolvem E/S, mas várias tarefas competem umas com as outras.</span><span class="sxs-lookup"><span data-stu-id="d209b-160">On a single-processor computer, a task that involves intensive computation coexists with user input and with tasks that involve I/O, but multiple computation-intensive tasks contend with each other.</span></span>  
  
- <span data-ttu-id="d209b-161">Considere o uso de métodos da classe <xref:System.Threading.Interlocked> para alterações de estado simples, em vez de usar a instrução `lock` (`SyncLock` no Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="d209b-161">Consider using methods of the <xref:System.Threading.Interlocked> class for simple state changes, instead of using the `lock` statement (`SyncLock` in Visual Basic).</span></span> <span data-ttu-id="d209b-162">A instrução `lock` é uma boa ferramenta para fins gerais, mas a classe <xref:System.Threading.Interlocked> oferece um melhor desempenho para atualizações que devem ser atômicas.</span><span class="sxs-lookup"><span data-stu-id="d209b-162">The `lock` statement is a good general-purpose tool, but the <xref:System.Threading.Interlocked> class provides better performance for updates that must be atomic.</span></span> <span data-ttu-id="d209b-163">Internamente, ela executa um único prefixo de bloqueio se não houver nenhuma contenção.</span><span class="sxs-lookup"><span data-stu-id="d209b-163">Internally, it executes a single lock prefix if there is no contention.</span></span> <span data-ttu-id="d209b-164">Em revisões de código, atente para códigos semelhantes aos mostrados nos exemplos a seguir.</span><span class="sxs-lookup"><span data-stu-id="d209b-164">In code reviews, watch for code like that shown in the following examples.</span></span> <span data-ttu-id="d209b-165">No primeiro exemplo, uma variável de estado é incrementada:</span><span class="sxs-lookup"><span data-stu-id="d209b-165">In the first example, a state variable is incremented:</span></span>  
  
    ```vb  
    SyncLock lockObject  
        myField += 1  
    End SyncLock  
    ```  
  
    ```csharp  
    lock(lockObject)   
    {  
        myField++;  
    }  
    ```  
  
     <span data-ttu-id="d209b-166">Você pode melhorar o desempenho usando o método <xref:System.Threading.Interlocked.Increment%2A> em vez da instrução `lock`, da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="d209b-166">You can improve performance by using the <xref:System.Threading.Interlocked.Increment%2A> method instead of the `lock` statement, as follows:</span></span>  
  
    ```vb  
    System.Threading.Interlocked.Increment(myField)  
    ```  
  
    ```csharp  
    System.Threading.Interlocked.Increment(myField);  
    ```  
  
    > [!NOTE]
    > <span data-ttu-id="d209b-167">No .NET Framework 2.0 e posteriores, use o método <xref:System.Threading.Interlocked.Add%2A> para incrementos atômicos maiores do que 1.</span><span class="sxs-lookup"><span data-stu-id="d209b-167">In the .NET Framework 2.0 and later, use the <xref:System.Threading.Interlocked.Add%2A> method for atomic increments larger than 1.</span></span>  
  
     <span data-ttu-id="d209b-168">No segundo exemplo, uma variável de tipo de referência é atualizada somente se ela for uma referência nula (`Nothing` no Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="d209b-168">In the second example, a reference type variable is updated only if it is a null reference (`Nothing` in Visual Basic).</span></span>  
  
    ```vb  
    If x Is Nothing Then  
        SyncLock lockObject  
            If x Is Nothing Then  
                x = y  
            End If  
        End SyncLock  
    End If  
    ```  
  
    ```csharp  
    if (x == null)  
    {  
        lock (lockObject)  
        {  
            if (x == null)  
            {  
                x = y;  
            }  
        }  
    }  
    ```  
  
     <span data-ttu-id="d209b-169">É possível melhorar o desempenho usando o método <xref:System.Threading.Interlocked.CompareExchange%2A>, da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="d209b-169">Performance can be improved by using the <xref:System.Threading.Interlocked.CompareExchange%2A> method instead, as follows:</span></span>  
  
    ```vb  
    System.Threading.Interlocked.CompareExchange(x, y, Nothing)  
    ```  
  
    ```csharp  
    System.Threading.Interlocked.CompareExchange(ref x, y, null);  
    ```  
  
    > [!NOTE]
    > <span data-ttu-id="d209b-170">Começando com o .NET Framework 2.0, a sobrecarga do método <xref:System.Threading.Interlocked.CompareExchange%60%601%28%60%600%40%2C%60%600%2C%60%600%29> fornece uma alternativa fortemente tipada para tipos de referência.</span><span class="sxs-lookup"><span data-stu-id="d209b-170">Beginning with .NET Framework 2.0, the <xref:System.Threading.Interlocked.CompareExchange%60%601%28%60%600%40%2C%60%600%2C%60%600%29> method overload provides a type-safe alternative for reference types.</span></span>
  
## <a name="recommendations-for-class-libraries"></a><span data-ttu-id="d209b-171">Recomendações para bibliotecas de classes</span><span class="sxs-lookup"><span data-stu-id="d209b-171">Recommendations for class libraries</span></span>  
 <span data-ttu-id="d209b-172">Considere as seguintes diretrizes ao criar bibliotecas de classes para multithreading:</span><span class="sxs-lookup"><span data-stu-id="d209b-172">Consider the following guidelines when designing class libraries for multithreading:</span></span>  
  
- <span data-ttu-id="d209b-173">Evite a necessidade de sincronização, se possível.</span><span class="sxs-lookup"><span data-stu-id="d209b-173">Avoid the need for synchronization, if possible.</span></span> <span data-ttu-id="d209b-174">Isso é especialmente válido para o código de uso intensivo.</span><span class="sxs-lookup"><span data-stu-id="d209b-174">This is especially true for heavily used code.</span></span> <span data-ttu-id="d209b-175">Por exemplo, um algoritmo pode ser ajustado para tolerar uma condição de corrida em vez de eliminá-la.</span><span class="sxs-lookup"><span data-stu-id="d209b-175">For example, an algorithm might be adjusted to tolerate a race condition rather than eliminate it.</span></span> <span data-ttu-id="d209b-176">Sincronização desnecessária reduz o desempenho e cria a possibilidade de deadlocks e condições de corrida.</span><span class="sxs-lookup"><span data-stu-id="d209b-176">Unnecessary synchronization decreases performance and creates the possibility of deadlocks and race conditions.</span></span>  
  
- <span data-ttu-id="d209b-177">Torne os dados estáticos (`Shared` no Visual Basic) thread-safe por padrão.</span><span class="sxs-lookup"><span data-stu-id="d209b-177">Make static data (`Shared` in Visual Basic) thread safe by default.</span></span>  
  
- <span data-ttu-id="d209b-178">Não torne dados de instância thread-safe por padrão.</span><span class="sxs-lookup"><span data-stu-id="d209b-178">Do not make instance data thread safe by default.</span></span> <span data-ttu-id="d209b-179">Adicionar bloqueios para criar códigos de thread-safe reduz o desempenho, aumenta a contenção de bloqueios e cria a possibilidade de deadlocks.</span><span class="sxs-lookup"><span data-stu-id="d209b-179">Adding locks to create thread-safe code decreases performance, increases lock contention, and creates the possibility for deadlocks to occur.</span></span> <span data-ttu-id="d209b-180">Em modelos de aplicativo comuns, somente um thread por vez executa código do usuário, o que minimiza a necessidade de acesso thread-safe.</span><span class="sxs-lookup"><span data-stu-id="d209b-180">In common application models, only one thread at a time executes user code, which minimizes the need for thread safety.</span></span> <span data-ttu-id="d209b-181">Por esse motivo, as bibliotecas de classes do .NET Framework não são thread-safe por padrão.</span><span class="sxs-lookup"><span data-stu-id="d209b-181">For this reason, the .NET Framework class libraries are not thread safe by default.</span></span>  
  
- <span data-ttu-id="d209b-182">Evite fornecer métodos estáticos que alteram o estado estático.</span><span class="sxs-lookup"><span data-stu-id="d209b-182">Avoid providing static methods that alter static state.</span></span> <span data-ttu-id="d209b-183">Em cenários de servidor comuns, o estado estático é compartilhado entre as solicitações, que significa que vários threads podem executar esse código ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="d209b-183">In common server scenarios, static state is shared across requests, which means multiple threads can execute that code at the same time.</span></span> <span data-ttu-id="d209b-184">Isso abre a possibilidade de bugs de threading.</span><span class="sxs-lookup"><span data-stu-id="d209b-184">This opens up the possibility of threading bugs.</span></span> <span data-ttu-id="d209b-185">Considere usar um padrão de design que encapsule dados em instâncias que não sejam compartilhadas entre solicitações.</span><span class="sxs-lookup"><span data-stu-id="d209b-185">Consider using a design pattern that encapsulates data into instances that are not shared across requests.</span></span> <span data-ttu-id="d209b-186">Além disso, se os dados estáticos forem sincronizados, chamadas entre os métodos estáticos que alteram o estado podem resultar em deadlocks ou em sincronização redundante, afetando negativamente o desempenho.</span><span class="sxs-lookup"><span data-stu-id="d209b-186">Furthermore, if static data are synchronized, calls between static methods that alter state can result in deadlocks or redundant synchronization, adversely affecting performance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d209b-187">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d209b-187">See also</span></span>

- [<span data-ttu-id="d209b-188">Threading</span><span class="sxs-lookup"><span data-stu-id="d209b-188">Threading</span></span>](../../../docs/standard/threading/index.md)
- [<span data-ttu-id="d209b-189">Threads e threading</span><span class="sxs-lookup"><span data-stu-id="d209b-189">Threads and Threading</span></span>](../../../docs/standard/threading/threads-and-threading.md)
