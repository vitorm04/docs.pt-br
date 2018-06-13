---
title: Práticas recomendadas de threading gerenciado
ms.date: 11/30/2017
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
ms.openlocfilehash: 15261291f40b6a41e0d6033fb92e1b23b4042019
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33592458"
---
# <a name="managed-threading-best-practices"></a><span data-ttu-id="53b46-102">Práticas recomendadas de threading gerenciado</span><span class="sxs-lookup"><span data-stu-id="53b46-102">Managed Threading Best Practices</span></span>
<span data-ttu-id="53b46-103">O multithreading requer programação cuidadosa.</span><span class="sxs-lookup"><span data-stu-id="53b46-103">Multithreading requires careful programming.</span></span> <span data-ttu-id="53b46-104">Para a maioria das tarefas, você pode reduzir a complexidade ao enfileirar solicitações para a execução por parte de threads de pool.</span><span class="sxs-lookup"><span data-stu-id="53b46-104">For most tasks, you can reduce complexity by queuing requests for execution by thread pool threads.</span></span> <span data-ttu-id="53b46-105">Este tópico aborda situações mais difíceis, como coordenar o trabalho de vários threads ou manipular threads que bloqueiam.</span><span class="sxs-lookup"><span data-stu-id="53b46-105">This topic addresses more difficult situations, such as coordinating the work of multiple threads, or handling threads that block.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="53b46-106">A partir do .NET Framework 4, a biblioteca de paralelismo de tarefas e o PLINQ fornecem APIs que reduzem parte da complexidade e os riscos da programação de multithreading.</span><span class="sxs-lookup"><span data-stu-id="53b46-106">Starting with the .NET Framework 4, the Task Parallel Library and PLINQ provide APIs that reduce some of the complexity and risks of multi-threaded programming.</span></span> <span data-ttu-id="53b46-107">Para saber mais, confira [Programação paralela em .NET](../../../docs/standard/parallel-programming/index.md).</span><span class="sxs-lookup"><span data-stu-id="53b46-107">For more information, see [Parallel Programming in .NET](../../../docs/standard/parallel-programming/index.md).</span></span>  
  
## <a name="deadlocks-and-race-conditions"></a><span data-ttu-id="53b46-108">Deadlocks e condições de corrida</span><span class="sxs-lookup"><span data-stu-id="53b46-108">Deadlocks and Race Conditions</span></span>  
 <span data-ttu-id="53b46-109">O multithreading resolve problemas com taxa de transferência e capacidade de resposta, mas, ao fazer isso, ele introduz novos problemas: deadlocks e condições de corrida.</span><span class="sxs-lookup"><span data-stu-id="53b46-109">Multithreading solves problems with throughput and responsiveness, but in doing so it introduces new problems: deadlocks and race conditions.</span></span>  
  
### <a name="deadlocks"></a><span data-ttu-id="53b46-110">Deadlocks</span><span class="sxs-lookup"><span data-stu-id="53b46-110">Deadlocks</span></span>  
 <span data-ttu-id="53b46-111">Um deadlock ocorre quando um dos dois threads tenta bloquear um recurso que o outro já bloqueou.</span><span class="sxs-lookup"><span data-stu-id="53b46-111">A deadlock occurs when each of two threads tries to lock a resource the other has already locked.</span></span> <span data-ttu-id="53b46-112">Nenhum dos threads pode fazer progresso adicional.</span><span class="sxs-lookup"><span data-stu-id="53b46-112">Neither thread can make any further progress.</span></span>  
  
 <span data-ttu-id="53b46-113">Muitos métodos das classes de threading gerenciadas fornecem tempos limite para ajudá-lo a detectar deadlocks.</span><span class="sxs-lookup"><span data-stu-id="53b46-113">Many methods of the managed threading classes provide time-outs to help you detect deadlocks.</span></span> <span data-ttu-id="53b46-114">Por exemplo, o código a seguir tenta adquirir um bloqueio em um objeto denominado `lockObject`.</span><span class="sxs-lookup"><span data-stu-id="53b46-114">For example, the following code attempts to acquire a lock on an object named `lockObject`.</span></span> <span data-ttu-id="53b46-115">Se o bloqueio não for obtido em 300 milissegundos, <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType> retornará `false`.</span><span class="sxs-lookup"><span data-stu-id="53b46-115">If the lock is not obtained in 300 milliseconds, <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType> returns `false`.</span></span>  
  
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
  
### <a name="race-conditions"></a><span data-ttu-id="53b46-116">Condições de corrida</span><span class="sxs-lookup"><span data-stu-id="53b46-116">Race Conditions</span></span>  
 <span data-ttu-id="53b46-117">Uma condição de corrida é um bug que ocorre quando o resultado de um programa depende de qual dos dois ou mais threads alcança um determinado bloco de código primeiro.</span><span class="sxs-lookup"><span data-stu-id="53b46-117">A race condition is a bug that occurs when the outcome of a program depends on which of two or more threads reaches a particular block of code first.</span></span> <span data-ttu-id="53b46-118">Executar o programa muitas vezes produz resultados diferentes e o resultado de qualquer execução não pode ser previsto.</span><span class="sxs-lookup"><span data-stu-id="53b46-118">Running the program many times produces different results, and the result of any given run cannot be predicted.</span></span>  
  
 <span data-ttu-id="53b46-119">Um exemplo simples de uma condição de corrida é incrementar um campo.</span><span class="sxs-lookup"><span data-stu-id="53b46-119">A simple example of a race condition is incrementing a field.</span></span> <span data-ttu-id="53b46-120">Suponha que uma classe tem um campo **static** particular (**Shared** no Visual Basic) que é incrementado toda vez que uma instância da classe é criada, usando um código como `objCt++;` (C#) ou `objCt += 1` (Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="53b46-120">Suppose a class has a private **static** field (**Shared** in Visual Basic) that is incremented every time an instance of the class is created, using code such as `objCt++;` (C#) or `objCt += 1` (Visual Basic).</span></span> <span data-ttu-id="53b46-121">Esta operação requer o carregamento do valor de `objCt` em um registro, incrementando o valor e o armazenando em `objCt`.</span><span class="sxs-lookup"><span data-stu-id="53b46-121">This operation requires loading the value from `objCt` into a register, incrementing the value, and storing it in `objCt`.</span></span>  
  
 <span data-ttu-id="53b46-122">Em um aplicativo com multithreading, um thread que carregou e incrementou o valor pode ser impedido por outro thread que execute todas as três etapas; quando o primeiro thread retomar a execução e armazenar seu valor, ele substituirá `objCt` sem levar em conta o fato de que o valor foi alterado durante o processo.</span><span class="sxs-lookup"><span data-stu-id="53b46-122">In a multithreaded application, a thread that has loaded and incremented the value might be preempted by another thread which performs all three steps; when the first thread resumes execution and stores its value, it overwrites `objCt` without taking into account the fact that the value has changed in the interim.</span></span>  
  
 <span data-ttu-id="53b46-123">Essa condição de corrida específica pode ser evitada facilmente usando métodos da classe <xref:System.Threading.Interlocked>, como <xref:System.Threading.Interlocked.Increment%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="53b46-123">This particular race condition is easily avoided by using methods of the <xref:System.Threading.Interlocked> class, such as <xref:System.Threading.Interlocked.Increment%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="53b46-124">Para ler sobre outras técnicas para sincronizar dados entre vários threads, confira [Sincronizando dados para multithreading](../../../docs/standard/threading/synchronizing-data-for-multithreading.md).</span><span class="sxs-lookup"><span data-stu-id="53b46-124">To read about other techniques for synchronizing data among multiple threads, see [Synchronizing Data for Multithreading](../../../docs/standard/threading/synchronizing-data-for-multithreading.md).</span></span>  
  
 <span data-ttu-id="53b46-125">Condições de corrida também podem ocorrer quando você sincroniza as atividades de vários threads.</span><span class="sxs-lookup"><span data-stu-id="53b46-125">Race conditions can also occur when you synchronize the activities of multiple threads.</span></span> <span data-ttu-id="53b46-126">Sempre que você escreve uma linha de código, é preciso considerar o que poderia acontecer se um thread fosse impedido antes de executar a linha (ou antes de qualquer uma das instruções de máquina individuais que compõem a linha) e outro thread o substituísse.</span><span class="sxs-lookup"><span data-stu-id="53b46-126">Whenever you write a line of code, you must consider what might happen if a thread were preempted before executing the line (or before any of the individual machine instructions that make up the line), and another thread overtook it.</span></span>  
  
## <a name="number-of-processors"></a><span data-ttu-id="53b46-127">Número de processadores</span><span class="sxs-lookup"><span data-stu-id="53b46-127">Number of Processors</span></span>  
 <span data-ttu-id="53b46-128">A maioria dos computadores agora tem vários processadores (também chamados de núcleos), até mesmo pequenos dispositivos como tablets e telefones.</span><span class="sxs-lookup"><span data-stu-id="53b46-128">Most computers now have multiple processors (also called cores), even small devices such as tablets and phones.</span></span> <span data-ttu-id="53b46-129">Se você souber que está desenvolvendo software que também será executado em computadores com um só processador, saiba que o multithreading soluciona problemas diferentes para computadores com um processador e computadores multiprocessadores.</span><span class="sxs-lookup"><span data-stu-id="53b46-129">If you know you're developing software that will also run on single-processor computers, you should be aware that multithreading solves different problems for single-processor computers and multiprocessor computers.</span></span>  
  
### <a name="multiprocessor-computers"></a><span data-ttu-id="53b46-130">Computadores multiprocessadores</span><span class="sxs-lookup"><span data-stu-id="53b46-130">Multiprocessor Computers</span></span>  
 <span data-ttu-id="53b46-131">O multithreading oferece uma taxa de transferência maior.</span><span class="sxs-lookup"><span data-stu-id="53b46-131">Multithreading provides greater throughput.</span></span> <span data-ttu-id="53b46-132">Dez processadores podem fazer dez vezes o trabalho de um, mas somente se o trabalho for dividido de forma que os dez possam trabalhar ao mesmo tempo; threads oferecem uma maneira fácil de dividir o trabalho e explorar a capacidade de processamento adicional.</span><span class="sxs-lookup"><span data-stu-id="53b46-132">Ten processors can do ten times the work of one, but only if the work is divided so that all ten can be working at once; threads provide an easy way to divide the work and exploit the extra processing power.</span></span> <span data-ttu-id="53b46-133">Se você usar multithreading em um computador multiprocessador:</span><span class="sxs-lookup"><span data-stu-id="53b46-133">If you use multithreading on a multiprocessor computer:</span></span>  
  
-   <span data-ttu-id="53b46-134">O número de threads que podem ser executados simultaneamente é limitado pelo número de processadores.</span><span class="sxs-lookup"><span data-stu-id="53b46-134">The number of threads that can execute concurrently is limited by the number of processors.</span></span>  
  
-   <span data-ttu-id="53b46-135">Um thread em segundo plano é executado somente quando o número de threads de primeiro plano em execução é menor do que o número de processadores.</span><span class="sxs-lookup"><span data-stu-id="53b46-135">A background thread executes only when the number of foreground threads executing is smaller than the number of processors.</span></span>  
  
-   <span data-ttu-id="53b46-136">Quando você chama o método <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> em um thread, esse thread pode ou não começar a execução imediatamente, dependendo do número de processadores e do número de threads que estão aguardando para serem executados.</span><span class="sxs-lookup"><span data-stu-id="53b46-136">When you call the <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> method on a thread, that thread might or might not start executing immediately, depending on the number of processors and the number of threads currently waiting to execute.</span></span>  
  
-   <span data-ttu-id="53b46-137">Condições de corrida podem ocorrer não só porque threads são apropriados inesperadamente, mas também porque dois threads em execução em diferentes processadores podem estar correndo para alcançar o mesmo bloco de código.</span><span class="sxs-lookup"><span data-stu-id="53b46-137">Race conditions can occur not only because threads are preempted unexpectedly, but because two threads executing on different processors might be racing to reach the same code block.</span></span>  
  
### <a name="single-processor-computers"></a><span data-ttu-id="53b46-138">Computadores de um processador</span><span class="sxs-lookup"><span data-stu-id="53b46-138">Single-Processor Computers</span></span>  
 <span data-ttu-id="53b46-139">O multithreading oferece maior capacidade de resposta para o usuário do computador e usa o tempo ocioso para tarefas em segundo plano.</span><span class="sxs-lookup"><span data-stu-id="53b46-139">Multithreading provides greater responsiveness to the computer user, and uses idle time for background tasks.</span></span> <span data-ttu-id="53b46-140">Se você usar multithreading em um computador de um processador:</span><span class="sxs-lookup"><span data-stu-id="53b46-140">If you use multithreading on a single-processor computer:</span></span>  
  
-   <span data-ttu-id="53b46-141">Apenas um thread será executado em qualquer momento.</span><span class="sxs-lookup"><span data-stu-id="53b46-141">Only one thread runs at any instant.</span></span>  
  
-   <span data-ttu-id="53b46-142">Um thread em segundo plano será executado somente quando o thread do usuário principal estiver ocioso.</span><span class="sxs-lookup"><span data-stu-id="53b46-142">A background thread executes only when the main user thread is idle.</span></span> <span data-ttu-id="53b46-143">Um thread de primeiro plano que é executado constantemente consome o tempo de processamento de threads de segundo plano.</span><span class="sxs-lookup"><span data-stu-id="53b46-143">A foreground thread that executes constantly starves background threads of processor time.</span></span>  
  
-   <span data-ttu-id="53b46-144">Quando você chama o método <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> em um thread, esse thread não começa a ser executado até que o thread atual seja suspenso ou apropriado pelo sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="53b46-144">When you call the <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> method on a thread, that thread does not start executing until the current thread yields or is preempted by the operating system.</span></span>  
  
-   <span data-ttu-id="53b46-145">Condições de corrida normalmente ocorrem porque o programador não antecipou o fato de que um thread pudesse ser apropriado em um momento inadequado, às vezes permitindo que outro thread alcance um bloco de código primeiro.</span><span class="sxs-lookup"><span data-stu-id="53b46-145">Race conditions typically occur because the programmer did not anticipate the fact that a thread can be preempted at an awkward moment, sometimes allowing another thread to reach a code block first.</span></span>  
  
## <a name="static-members-and-static-constructors"></a><span data-ttu-id="53b46-146">Membros estáticos e construtores estáticos</span><span class="sxs-lookup"><span data-stu-id="53b46-146">Static Members and Static Constructors</span></span>  
 <span data-ttu-id="53b46-147">Uma classe não é inicializada até que o construtor de classe (construtor `static` em C#, `Shared Sub New` no Visual Basic) tenha terminado de ser executado.</span><span class="sxs-lookup"><span data-stu-id="53b46-147">A class is not initialized until its class constructor (`static` constructor in C#, `Shared Sub New` in Visual Basic) has finished running.</span></span> <span data-ttu-id="53b46-148">Para impedir a execução de código em um tipo não inicializado, o Common Language Runtime bloqueia todas as chamadas de outros threads para membros `static` da classe (membros `Shared` no Visual Basic) até que o construtor da classe tenha concluído sua execução.</span><span class="sxs-lookup"><span data-stu-id="53b46-148">To prevent the execution of code on a type that is not initialized, the common language runtime blocks all calls from other threads to `static` members of the class (`Shared` members in Visual Basic) until the class constructor has finished running.</span></span>  
  
 <span data-ttu-id="53b46-149">Por exemplo, se um construtor de classe iniciar um novo thread, e o procedimento do thread chamar um membro `static` da classe, o novo thread bloqueia até que o construtor da classe seja concluído.</span><span class="sxs-lookup"><span data-stu-id="53b46-149">For example, if a class constructor starts a new thread, and the thread procedure calls a `static` member of the class, the new thread blocks until the class constructor completes.</span></span>  
  
 <span data-ttu-id="53b46-150">Isso se aplica a qualquer tipo que possa ter um construtor `static`.</span><span class="sxs-lookup"><span data-stu-id="53b46-150">This applies to any type that can have a `static` constructor.</span></span>  
  
## <a name="general-recommendations"></a><span data-ttu-id="53b46-151">Recomendações gerais</span><span class="sxs-lookup"><span data-stu-id="53b46-151">General Recommendations</span></span>  
 <span data-ttu-id="53b46-152">Ao usar vários threads, considere as seguintes diretrizes:</span><span class="sxs-lookup"><span data-stu-id="53b46-152">Consider the following guidelines when using multiple threads:</span></span>  
  
-   <span data-ttu-id="53b46-153">Não use <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> para encerrar outros threads.</span><span class="sxs-lookup"><span data-stu-id="53b46-153">Don't use <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> to terminate other threads.</span></span> <span data-ttu-id="53b46-154">Chamar **Abort** em outro thread equivale a gerar uma exceção nesse thread sem saber qual ponto ele alcançou nesse processamento.</span><span class="sxs-lookup"><span data-stu-id="53b46-154">Calling **Abort** on another thread is akin to throwing an exception on that thread, without knowing what point that thread has reached in its processing.</span></span>  
  
-   <span data-ttu-id="53b46-155">Não use <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> e <xref:System.Threading.Thread.Resume%2A?displayProperty=nameWithType> para sincronizar as atividades de vários threads.</span><span class="sxs-lookup"><span data-stu-id="53b46-155">Don't use <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> and <xref:System.Threading.Thread.Resume%2A?displayProperty=nameWithType> to synchronize the activities of multiple threads.</span></span> <span data-ttu-id="53b46-156">Use <xref:System.Threading.Mutex>, <xref:System.Threading.ManualResetEvent>, <xref:System.Threading.AutoResetEvent>, e <xref:System.Threading.Monitor>.</span><span class="sxs-lookup"><span data-stu-id="53b46-156">Do use <xref:System.Threading.Mutex>, <xref:System.Threading.ManualResetEvent>, <xref:System.Threading.AutoResetEvent>, and <xref:System.Threading.Monitor>.</span></span>  
  
-   <span data-ttu-id="53b46-157">Não controle a execução de threads de trabalho do seu programa principal (usando eventos, por exemplo).</span><span class="sxs-lookup"><span data-stu-id="53b46-157">Don't control the execution of worker threads from your main program (using events, for example).</span></span> <span data-ttu-id="53b46-158">Em vez disso, projete seu programa de forma que os threads de trabalho sejam responsáveis por esperar até que o trabalho esteja disponível, executá-lo e notificar outras partes do seu programa quando terminar.</span><span class="sxs-lookup"><span data-stu-id="53b46-158">Instead, design your program so that worker threads are responsible for waiting until work is available, executing it, and notifying other parts of your program when finished.</span></span> <span data-ttu-id="53b46-159">Se seus threads de trabalho não bloquearem, considere o uso de threads de pool.</span><span class="sxs-lookup"><span data-stu-id="53b46-159">If your worker threads do not block, consider using thread pool threads.</span></span> <span data-ttu-id="53b46-160"><xref:System.Threading.Monitor.PulseAll%2A?displayProperty=nameWithType> é útil em situações em que os threads de trabalho bloqueiam.</span><span class="sxs-lookup"><span data-stu-id="53b46-160"><xref:System.Threading.Monitor.PulseAll%2A?displayProperty=nameWithType> is useful in situations where worker threads block.</span></span>  
  
-   <span data-ttu-id="53b46-161">Não use tipos como objetos de bloqueio.</span><span class="sxs-lookup"><span data-stu-id="53b46-161">Don't use types as lock objects.</span></span> <span data-ttu-id="53b46-162">Isto é, evite códigos como `lock(typeof(X))` em C# ou `SyncLock(GetType(X))` no Visual Basic ou o uso de <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> com objetos <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="53b46-162">That is, avoid code such as `lock(typeof(X))` in C# or `SyncLock(GetType(X))` in Visual Basic, or the use of <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> with <xref:System.Type> objects.</span></span> <span data-ttu-id="53b46-163">Para um determinado tipo, há apenas uma instância de <xref:System.Type?displayProperty=nameWithType> por domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="53b46-163">For a given type, there is only one instance of <xref:System.Type?displayProperty=nameWithType> per application domain.</span></span> <span data-ttu-id="53b46-164">Se o tipo no qual você usar um bloqueio for público, o código que não for o seu próprio poderá assumir bloqueios, levando a deadlocks.</span><span class="sxs-lookup"><span data-stu-id="53b46-164">If the type you take a lock on is public, code other than your own can take locks on it, leading to deadlocks.</span></span> <span data-ttu-id="53b46-165">Para problemas adicionais, consulte [Práticas recomendadas de confiabilidade](../../../docs/framework/performance/reliability-best-practices.md).</span><span class="sxs-lookup"><span data-stu-id="53b46-165">For additional issues, see [Reliability Best Practices](../../../docs/framework/performance/reliability-best-practices.md).</span></span>  
  
-   <span data-ttu-id="53b46-166">Tenha cuidado ao bloquear em instâncias, por exemplo `lock(this)` em C# ou `SyncLock(Me)` no Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="53b46-166">Use caution when locking on instances, for example `lock(this)` in C# or `SyncLock(Me)` in Visual Basic.</span></span> <span data-ttu-id="53b46-167">Se outro código no seu aplicativo, externo ao tipo, assumir um bloqueio no objeto, podem ocorrer deadlocks.</span><span class="sxs-lookup"><span data-stu-id="53b46-167">If other code in your application, external to the type, takes a lock on the object, deadlocks could occur.</span></span>  
  
-   <span data-ttu-id="53b46-168">Certifique-se de que um thread que tenha entrado em um monitor sempre o deixe, mesmo que uma exceção ocorra enquanto o thread estiver no monitor.</span><span class="sxs-lookup"><span data-stu-id="53b46-168">Do ensure that a thread that has entered a monitor always leaves that monitor, even if an exception occurs while the thread is in the monitor.</span></span> <span data-ttu-id="53b46-169">A instrução [lock](~/docs/csharp/language-reference/keywords/lock-statement.md) do C# e a instrução [SyncLock](~/docs/visual-basic/language-reference/statements/synclock-statement.md) do Visual Basic oferece esse comportamento automaticamente, empregando um bloco **finally** para garantir que <xref:System.Threading.Monitor.Exit%2A?displayProperty=nameWithType> seja chamado.</span><span class="sxs-lookup"><span data-stu-id="53b46-169">The C# [lock](~/docs/csharp/language-reference/keywords/lock-statement.md) statement and the Visual Basic [SyncLock](~/docs/visual-basic/language-reference/statements/synclock-statement.md) statement provide this behavior automatically, employing a **finally** block to ensure that <xref:System.Threading.Monitor.Exit%2A?displayProperty=nameWithType> is called.</span></span> <span data-ttu-id="53b46-170">Se você não puder garantir que **Exit** seja chamado, considere alterar o design para usar **Mutex**.</span><span class="sxs-lookup"><span data-stu-id="53b46-170">If you cannot ensure that **Exit** will be called, consider changing your design to use **Mutex**.</span></span> <span data-ttu-id="53b46-171">Um mutex é liberado automaticamente quando o thread que o possui atualmente for encerrado.</span><span class="sxs-lookup"><span data-stu-id="53b46-171">A mutex is automatically released when the thread that currently owns it terminates.</span></span>  
  
-   <span data-ttu-id="53b46-172">Usar vários threads para tarefas que exigem recursos diferentes e evite atribuir vários threads para um único recurso.</span><span class="sxs-lookup"><span data-stu-id="53b46-172">Do use multiple threads for tasks that require different resources, and avoid assigning multiple threads to a single resource.</span></span> <span data-ttu-id="53b46-173">Por exemplo, qualquer tarefa que envolva E/S se beneficia em ter seu próprio thread, porque esse thread bloqueará durante as operações de E/S e, assim, permitirá que outros threads sejam executados.</span><span class="sxs-lookup"><span data-stu-id="53b46-173">For example, any task involving I/O benefits from having its own thread, because that thread will block during I/O operations and thus allow other threads to execute.</span></span> <span data-ttu-id="53b46-174">A entrada do usuário é outro recurso que se beneficia com um thread dedicado.</span><span class="sxs-lookup"><span data-stu-id="53b46-174">User input is another resource that benefits from a dedicated thread.</span></span> <span data-ttu-id="53b46-175">Em um computador de um processador, uma tarefa que envolve a computação intensiva coexiste com a entrada do usuário e com tarefas que envolvem E/S, mas várias tarefas competem umas com as outras.</span><span class="sxs-lookup"><span data-stu-id="53b46-175">On a single-processor computer, a task that involves intensive computation coexists with user input and with tasks that involve I/O, but multiple computation-intensive tasks contend with each other.</span></span>  
  
-   <span data-ttu-id="53b46-176">Considere o uso de métodos da classe <xref:System.Threading.Interlocked> para alterações de estado simples, em vez de usar a instrução `lock` (`SyncLock` no Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="53b46-176">Consider using methods of the <xref:System.Threading.Interlocked> class for simple state changes, instead of using the `lock` statement (`SyncLock` in Visual Basic).</span></span> <span data-ttu-id="53b46-177">A instrução `lock` é uma boa ferramenta para fins gerais, mas a classe <xref:System.Threading.Interlocked> oferece um melhor desempenho para atualizações que devem ser atômicas.</span><span class="sxs-lookup"><span data-stu-id="53b46-177">The `lock` statement is a good general-purpose tool, but the <xref:System.Threading.Interlocked> class provides better performance for updates that must be atomic.</span></span> <span data-ttu-id="53b46-178">Internamente, ela executa um único prefixo de bloqueio se não houver nenhuma contenção.</span><span class="sxs-lookup"><span data-stu-id="53b46-178">Internally, it executes a single lock prefix if there is no contention.</span></span> <span data-ttu-id="53b46-179">Em revisões de código, atente para códigos semelhantes aos mostrados nos exemplos a seguir.</span><span class="sxs-lookup"><span data-stu-id="53b46-179">In code reviews, watch for code like that shown in the following examples.</span></span> <span data-ttu-id="53b46-180">No primeiro exemplo, uma variável de estado é incrementada:</span><span class="sxs-lookup"><span data-stu-id="53b46-180">In the first example, a state variable is incremented:</span></span>  
  
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
  
     <span data-ttu-id="53b46-181">Você pode melhorar o desempenho usando o método <xref:System.Threading.Interlocked.Increment%2A> em vez da instrução `lock`, da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="53b46-181">You can improve performance by using the <xref:System.Threading.Interlocked.Increment%2A> method instead of the `lock` statement, as follows:</span></span>  
  
    ```vb  
    System.Threading.Interlocked.Increment(myField)  
    ```  
  
    ```csharp  
    System.Threading.Interlocked.Increment(myField);  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="53b46-182">No .NET Framework versão 2.0, o método <xref:System.Threading.Interlocked.Add%2A> fornece atualizações atômicas em incrementos maiores do que 1.</span><span class="sxs-lookup"><span data-stu-id="53b46-182">In the .NET Framework version 2.0, the <xref:System.Threading.Interlocked.Add%2A> method provides atomic updates in increments larger than 1.</span></span>  
  
     <span data-ttu-id="53b46-183">No segundo exemplo, uma variável de tipo de referência é atualizada somente se ela for uma referência nula (`Nothing` no Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="53b46-183">In the second example, a reference type variable is updated only if it is a null reference (`Nothing` in Visual Basic).</span></span>  
  
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
  
     <span data-ttu-id="53b46-184">É possível melhorar o desempenho usando o método <xref:System.Threading.Interlocked.CompareExchange%2A>, da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="53b46-184">Performance can be improved by using the <xref:System.Threading.Interlocked.CompareExchange%2A> method instead, as follows:</span></span>  
  
    ```vb  
    System.Threading.Interlocked.CompareExchange(x, y, Nothing)  
    ```  
  
    ```csharp  
    System.Threading.Interlocked.CompareExchange(ref x, y, null);  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="53b46-185">No .NET Framework versão 2.0, o método <xref:System.Threading.Interlocked.CompareExchange%2A> tem uma sobrecarga genérica que pode ser usada para a substituição fortemente tipada de qualquer tipo de referência.</span><span class="sxs-lookup"><span data-stu-id="53b46-185">In the .NET Framework version 2.0, the <xref:System.Threading.Interlocked.CompareExchange%2A> method has a generic overload that can be used for type-safe replacement of any reference type.</span></span>  
  
## <a name="recommendations-for-class-libraries"></a><span data-ttu-id="53b46-186">Recomendações para bibliotecas de classes</span><span class="sxs-lookup"><span data-stu-id="53b46-186">Recommendations for Class Libraries</span></span>  
 <span data-ttu-id="53b46-187">Considere as seguintes diretrizes ao criar bibliotecas de classes para multithreading:</span><span class="sxs-lookup"><span data-stu-id="53b46-187">Consider the following guidelines when designing class libraries for multithreading:</span></span>  
  
-   <span data-ttu-id="53b46-188">Evite a necessidade de sincronização, se possível.</span><span class="sxs-lookup"><span data-stu-id="53b46-188">Avoid the need for synchronization, if possible.</span></span> <span data-ttu-id="53b46-189">Isso é especialmente válido para o código de uso intensivo.</span><span class="sxs-lookup"><span data-stu-id="53b46-189">This is especially true for heavily used code.</span></span> <span data-ttu-id="53b46-190">Por exemplo, um algoritmo pode ser ajustado para tolerar uma condição de corrida em vez de eliminá-la.</span><span class="sxs-lookup"><span data-stu-id="53b46-190">For example, an algorithm might be adjusted to tolerate a race condition rather than eliminate it.</span></span> <span data-ttu-id="53b46-191">Sincronização desnecessária reduz o desempenho e cria a possibilidade de deadlocks e condições de corrida.</span><span class="sxs-lookup"><span data-stu-id="53b46-191">Unnecessary synchronization decreases performance and creates the possibility of deadlocks and race conditions.</span></span>  
  
-   <span data-ttu-id="53b46-192">Torne os dados estáticos (`Shared` no Visual Basic) thread-safe por padrão.</span><span class="sxs-lookup"><span data-stu-id="53b46-192">Make static data (`Shared` in Visual Basic) thread safe by default.</span></span>  
  
-   <span data-ttu-id="53b46-193">Não torne dados de instância thread-safe por padrão.</span><span class="sxs-lookup"><span data-stu-id="53b46-193">Do not make instance data thread safe by default.</span></span> <span data-ttu-id="53b46-194">Adicionar bloqueios para criar códigos de thread-safe reduz o desempenho, aumenta a contenção de bloqueios e cria a possibilidade de deadlocks.</span><span class="sxs-lookup"><span data-stu-id="53b46-194">Adding locks to create thread-safe code decreases performance, increases lock contention, and creates the possibility for deadlocks to occur.</span></span> <span data-ttu-id="53b46-195">Em modelos de aplicativo comuns, somente um thread por vez executa código do usuário, o que minimiza a necessidade de acesso thread-safe.</span><span class="sxs-lookup"><span data-stu-id="53b46-195">In common application models, only one thread at a time executes user code, which minimizes the need for thread safety.</span></span> <span data-ttu-id="53b46-196">Por esse motivo, as bibliotecas de classes do .NET Framework não são thread-safe por padrão.</span><span class="sxs-lookup"><span data-stu-id="53b46-196">For this reason, the .NET Framework class libraries are not thread safe by default.</span></span>  
  
-   <span data-ttu-id="53b46-197">Evite fornecer métodos estáticos que alteram o estado estático.</span><span class="sxs-lookup"><span data-stu-id="53b46-197">Avoid providing static methods that alter static state.</span></span> <span data-ttu-id="53b46-198">Em cenários de servidor comuns, o estado estático é compartilhado entre as solicitações, que significa que vários threads podem executar esse código ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="53b46-198">In common server scenarios, static state is shared across requests, which means multiple threads can execute that code at the same time.</span></span> <span data-ttu-id="53b46-199">Isso abre a possibilidade de bugs de threading.</span><span class="sxs-lookup"><span data-stu-id="53b46-199">This opens up the possibility of threading bugs.</span></span> <span data-ttu-id="53b46-200">Considere usar um padrão de design que encapsule dados em instâncias que não sejam compartilhadas entre solicitações.</span><span class="sxs-lookup"><span data-stu-id="53b46-200">Consider using a design pattern that encapsulates data into instances that are not shared across requests.</span></span> <span data-ttu-id="53b46-201">Além disso, se os dados estáticos forem sincronizados, chamadas entre os métodos estáticos que alteram o estado podem resultar em deadlocks ou em sincronização redundante, afetando negativamente o desempenho.</span><span class="sxs-lookup"><span data-stu-id="53b46-201">Furthermore, if static data are synchronized, calls between static methods that alter state can result in deadlocks or redundant synchronization, adversely affecting performance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53b46-202">Consulte também</span><span class="sxs-lookup"><span data-stu-id="53b46-202">See Also</span></span>  
 [<span data-ttu-id="53b46-203">Threading</span><span class="sxs-lookup"><span data-stu-id="53b46-203">Threading</span></span>](../../../docs/standard/threading/index.md)  
 [<span data-ttu-id="53b46-204">Threads e threading</span><span class="sxs-lookup"><span data-stu-id="53b46-204">Threads and Threading</span></span>](../../../docs/standard/threading/threads-and-threading.md)
