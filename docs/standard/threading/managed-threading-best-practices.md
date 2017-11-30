---
title: "Práticas recomendadas de threading gerenciado"
ms.custom: 
ms.date: 11/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- threading [.NET Framework], design guidelines
- threading [.NET Framework], best practices
- managed threading
ms.assetid: e51988e7-7f4b-4646-a06d-1416cee8d557
caps.latest.revision: "19"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e396bb1f6a710e49e311ca1526a7aae9bca7bf90
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="managed-threading-best-practices"></a><span data-ttu-id="ee2dc-102">Práticas recomendadas de threading gerenciado</span><span class="sxs-lookup"><span data-stu-id="ee2dc-102">Managed Threading Best Practices</span></span>
<span data-ttu-id="ee2dc-103">Multithreading requer programação cuidadosa.</span><span class="sxs-lookup"><span data-stu-id="ee2dc-103">Multithreading requires careful programming.</span></span> <span data-ttu-id="ee2dc-104">Para a maioria das tarefas, você pode reduzir a complexidade por solicitações de enfileiramento de mensagens para execução por threads de pool.</span><span class="sxs-lookup"><span data-stu-id="ee2dc-104">For most tasks, you can reduce complexity by queuing requests for execution by thread pool threads.</span></span> <span data-ttu-id="ee2dc-105">Este tópico aborda as situações mais difíceis, como coordenar o trabalho de vários threads ou manipular threads esse bloco.</span><span class="sxs-lookup"><span data-stu-id="ee2dc-105">This topic addresses more difficult situations, such as coordinating the work of multiple threads, or handling threads that block.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ee2dc-106">Começando com o .NET Framework 4, a biblioteca de tarefas paralelas e em PLINQ fornecem APIs que reduza alguns a complexidade e os riscos de programação multithread.</span><span class="sxs-lookup"><span data-stu-id="ee2dc-106">Starting with the .NET Framework 4, the Task Parallel Library and PLINQ provide APIs that reduce some of the complexity and risks of multi-threaded programming.</span></span> <span data-ttu-id="ee2dc-107">Para obter mais informações, consulte [programação paralela no .NET](../../../docs/standard/parallel-programming/index.md).</span><span class="sxs-lookup"><span data-stu-id="ee2dc-107">For more information, see [Parallel Programming in .NET](../../../docs/standard/parallel-programming/index.md).</span></span>  
  
## <a name="deadlocks-and-race-conditions"></a><span data-ttu-id="ee2dc-108">Deadlocks e condições de corrida</span><span class="sxs-lookup"><span data-stu-id="ee2dc-108">Deadlocks and Race Conditions</span></span>  
 <span data-ttu-id="ee2dc-109">Multithreading soluciona problemas com a taxa de transferência e a capacidade de resposta, mas isso introduz novos problemas: deadlocks e condições de corrida.</span><span class="sxs-lookup"><span data-stu-id="ee2dc-109">Multithreading solves problems with throughput and responsiveness, but in doing so it introduces new problems: deadlocks and race conditions.</span></span>  
  
### <a name="deadlocks"></a><span data-ttu-id="ee2dc-110">Deadlocks</span><span class="sxs-lookup"><span data-stu-id="ee2dc-110">Deadlocks</span></span>  
 <span data-ttu-id="ee2dc-111">Um deadlock ocorre quando cada um dos dois threads tenta bloquear um recurso que já bloqueado por outro.</span><span class="sxs-lookup"><span data-stu-id="ee2dc-111">A deadlock occurs when each of two threads tries to lock a resource the other has already locked.</span></span> <span data-ttu-id="ee2dc-112">Nenhum thread pode tornar qualquer progresso adicional.</span><span class="sxs-lookup"><span data-stu-id="ee2dc-112">Neither thread can make any further progress.</span></span>  
  
 <span data-ttu-id="ee2dc-113">Muitos métodos das classes de threading gerenciados fornecem tempos limite para ajudá-lo a detectar deadlocks.</span><span class="sxs-lookup"><span data-stu-id="ee2dc-113">Many methods of the managed threading classes provide time-outs to help you detect deadlocks.</span></span> <span data-ttu-id="ee2dc-114">Por exemplo, o código a seguir tenta adquirir um bloqueio em um objeto denominado `lockObject`.</span><span class="sxs-lookup"><span data-stu-id="ee2dc-114">For example, the following code attempts to acquire a lock on an object named `lockObject`.</span></span> <span data-ttu-id="ee2dc-115">Se o bloqueio não é obtido em 300 milissegundos, <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType> retorna `false`.</span><span class="sxs-lookup"><span data-stu-id="ee2dc-115">If the lock is not obtained in 300 milliseconds, <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType> returns `false`.</span></span>  
  
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
  
### <a name="race-conditions"></a><span data-ttu-id="ee2dc-116">Condições de corrida</span><span class="sxs-lookup"><span data-stu-id="ee2dc-116">Race Conditions</span></span>  
 <span data-ttu-id="ee2dc-117">Uma condição de corrida é um erro que ocorre quando o resultado de um programa depende de qual dos dois ou mais threads atingir um determinado bloco de código primeiro.</span><span class="sxs-lookup"><span data-stu-id="ee2dc-117">A race condition is a bug that occurs when the outcome of a program depends on which of two or more threads reaches a particular block of code first.</span></span> <span data-ttu-id="ee2dc-118">Executar o programa muitas vezes produz resultados diferentes, e o resultado de qualquer execução especificada não pode ser previsto.</span><span class="sxs-lookup"><span data-stu-id="ee2dc-118">Running the program many times produces different results, and the result of any given run cannot be predicted.</span></span>  
  
 <span data-ttu-id="ee2dc-119">Um exemplo simples de uma condição de corrida é incrementar um campo.</span><span class="sxs-lookup"><span data-stu-id="ee2dc-119">A simple example of a race condition is incrementing a field.</span></span> <span data-ttu-id="ee2dc-120">Suponha que uma classe tem uma particular **estático** campo (**compartilhado** no Visual Basic) que é incrementado toda vez que uma instância da classe é criada, usando um código como `objCt++;` (c#) ou `objCt += 1` ( Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="ee2dc-120">Suppose a class has a private **static** field (**Shared** in Visual Basic) that is incremented every time an instance of the class is created, using code such as `objCt++;` (C#) or `objCt += 1` (Visual Basic).</span></span> <span data-ttu-id="ee2dc-121">Esta operação requer a carregar o valor de `objCt` em um registro, aumentando o valor e armazená-los em `objCt`.</span><span class="sxs-lookup"><span data-stu-id="ee2dc-121">This operation requires loading the value from `objCt` into a register, incrementing the value, and storing it in `objCt`.</span></span>  
  
 <span data-ttu-id="ee2dc-122">Em um aplicativo multithread, um thread que foi carregado e incrementado o valor pode ser impedido por outro thread que executa todas as três etapas; Quando o primeiro thread retoma a execução e armazena seu valor, ele substitui `objCt` sem levar em conta o fato de que o valor é alterado durante o processo.</span><span class="sxs-lookup"><span data-stu-id="ee2dc-122">In a multithreaded application, a thread that has loaded and incremented the value might be preempted by another thread which performs all three steps; when the first thread resumes execution and stores its value, it overwrites `objCt` without taking into account the fact that the value has changed in the interim.</span></span>  
  
 <span data-ttu-id="ee2dc-123">Essa condição de corrida específica é evitada facilmente usando métodos do <xref:System.Threading.Interlocked> classe, como <xref:System.Threading.Interlocked.Increment%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ee2dc-123">This particular race condition is easily avoided by using methods of the <xref:System.Threading.Interlocked> class, such as <xref:System.Threading.Interlocked.Increment%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="ee2dc-124">Para ler sobre outras técnicas para sincronizar dados entre vários threads, consulte [sincronizando dados para Multithreading](../../../docs/standard/threading/synchronizing-data-for-multithreading.md).</span><span class="sxs-lookup"><span data-stu-id="ee2dc-124">To read about other techniques for synchronizing data among multiple threads, see [Synchronizing Data for Multithreading](../../../docs/standard/threading/synchronizing-data-for-multithreading.md).</span></span>  
  
 <span data-ttu-id="ee2dc-125">Condições de corrida também podem ocorrer quando você sincronizar as atividades de vários threads.</span><span class="sxs-lookup"><span data-stu-id="ee2dc-125">Race conditions can also occur when you synchronize the activities of multiple threads.</span></span> <span data-ttu-id="ee2dc-126">Sempre que você escreve uma linha de código, você deve considerar o que poderia acontecer se um thread foram capturadas antes de executar a linha (ou antes de qualquer uma das instruções de computadores individuais que compõem a linha) e outro thread overtook-lo.</span><span class="sxs-lookup"><span data-stu-id="ee2dc-126">Whenever you write a line of code, you must consider what might happen if a thread were preempted before executing the line (or before any of the individual machine instructions that make up the line), and another thread overtook it.</span></span>  
  
## <a name="number-of-processors"></a><span data-ttu-id="ee2dc-127">Número de processadores</span><span class="sxs-lookup"><span data-stu-id="ee2dc-127">Number of Processors</span></span>  
 <span data-ttu-id="ee2dc-128">A maioria dos computadores agora tem vários processadores (também chamados de núcleos), até mesmo pequenos dispositivos como tablets e telefones.</span><span class="sxs-lookup"><span data-stu-id="ee2dc-128">Most computers now have multiple processors (also called cores), even small devices such as tablets and phones.</span></span> <span data-ttu-id="ee2dc-129">Se você souber que você está desenvolvendo software também é executados em computadores com processador único, você deve estar ciente multithreading que resolve problemas diferentes para computadores com processador único e computadores com multiprocessadores.</span><span class="sxs-lookup"><span data-stu-id="ee2dc-129">If you know you're developing software that will also run on single-processor computers, you should be aware that multithreading solves different problems for single-processor computers and multiprocessor computers.</span></span>  
  
### <a name="multiprocessor-computers"></a><span data-ttu-id="ee2dc-130">Computadores com multiprocessadores</span><span class="sxs-lookup"><span data-stu-id="ee2dc-130">Multiprocessor Computers</span></span>  
 <span data-ttu-id="ee2dc-131">Multithreading fornece maior taxa de transferência.</span><span class="sxs-lookup"><span data-stu-id="ee2dc-131">Multithreading provides greater throughput.</span></span> <span data-ttu-id="ee2dc-132">Dez processadores podem fazer dez vezes o trabalho de uma, mas somente se o trabalho é dividido para que os dez podem estar trabalhando ao mesmo tempo; threads fornecem uma maneira fácil para dividir o trabalho e explorar o poder de processamento extra.</span><span class="sxs-lookup"><span data-stu-id="ee2dc-132">Ten processors can do ten times the work of one, but only if the work is divided so that all ten can be working at once; threads provide an easy way to divide the work and exploit the extra processing power.</span></span> <span data-ttu-id="ee2dc-133">Se você usar multithreading em um computador multiprocessador:</span><span class="sxs-lookup"><span data-stu-id="ee2dc-133">If you use multithreading on a multiprocessor computer:</span></span>  
  
-   <span data-ttu-id="ee2dc-134">O número de threads que podem ser executados simultaneamente é limitado pelo número de processadores.</span><span class="sxs-lookup"><span data-stu-id="ee2dc-134">The number of threads that can execute concurrently is limited by the number of processors.</span></span>  
  
-   <span data-ttu-id="ee2dc-135">Um thread em segundo plano é executado somente quando o número de threads de primeiro plano em execução é menor do que o número de processadores.</span><span class="sxs-lookup"><span data-stu-id="ee2dc-135">A background thread executes only when the number of foreground threads executing is smaller than the number of processors.</span></span>  
  
-   <span data-ttu-id="ee2dc-136">Quando você chama o <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> método em um thread, o thread pode ou não pode iniciar a execução imediatamente, dependendo do número de processadores e o número de threads que estão aguardando para executar.</span><span class="sxs-lookup"><span data-stu-id="ee2dc-136">When you call the <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> method on a thread, that thread might or might not start executing immediately, depending on the number of processors and the number of threads currently waiting to execute.</span></span>  
  
-   <span data-ttu-id="ee2dc-137">Condições de corrida podem ocorrer não só porque threads são capturados inesperadamente, mas porque dois threads em execução em diferentes processadores podem ser corrida para alcançar o mesmo bloco de código.</span><span class="sxs-lookup"><span data-stu-id="ee2dc-137">Race conditions can occur not only because threads are preempted unexpectedly, but because two threads executing on different processors might be racing to reach the same code block.</span></span>  
  
### <a name="single-processor-computers"></a><span data-ttu-id="ee2dc-138">Computadores com processador único</span><span class="sxs-lookup"><span data-stu-id="ee2dc-138">Single-Processor Computers</span></span>  
 <span data-ttu-id="ee2dc-139">Multithreading fornece maior capacidade de resposta para o usuário do computador e usa o tempo ocioso para tarefas em segundo plano.</span><span class="sxs-lookup"><span data-stu-id="ee2dc-139">Multithreading provides greater responsiveness to the computer user, and uses idle time for background tasks.</span></span> <span data-ttu-id="ee2dc-140">Se você usar multithreading em um computador com processador único:</span><span class="sxs-lookup"><span data-stu-id="ee2dc-140">If you use multithreading on a single-processor computer:</span></span>  
  
-   <span data-ttu-id="ee2dc-141">Apenas um thread é executado em qualquer momento.</span><span class="sxs-lookup"><span data-stu-id="ee2dc-141">Only one thread runs at any instant.</span></span>  
  
-   <span data-ttu-id="ee2dc-142">Um thread em segundo plano é executado somente quando o thread principal de usuário estiver ocioso.</span><span class="sxs-lookup"><span data-stu-id="ee2dc-142">A background thread executes only when the main user thread is idle.</span></span> <span data-ttu-id="ee2dc-143">Um thread de primeiro plano que é executado constantemente impede threads de plano de fundo de tempo do processador.</span><span class="sxs-lookup"><span data-stu-id="ee2dc-143">A foreground thread that executes constantly starves background threads of processor time.</span></span>  
  
-   <span data-ttu-id="ee2dc-144">Quando você chama o <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> método em um thread que thread não iniciar, executar até que o thread atual produz ou é executada pelo sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="ee2dc-144">When you call the <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> method on a thread, that thread does not start executing until the current thread yields or is preempted by the operating system.</span></span>  
  
-   <span data-ttu-id="ee2dc-145">Condições de corrida ocorrem normalmente porque o programador não previu o fato de que um thread pode ser impedido em um momento inadequado, às vezes, permitindo que outro thread alcançar um bloco de código primeiro.</span><span class="sxs-lookup"><span data-stu-id="ee2dc-145">Race conditions typically occur because the programmer did not anticipate the fact that a thread can be preempted at an awkward moment, sometimes allowing another thread to reach a code block first.</span></span>  
  
## <a name="static-members-and-static-constructors"></a><span data-ttu-id="ee2dc-146">Membros estáticos e construtores estáticos</span><span class="sxs-lookup"><span data-stu-id="ee2dc-146">Static Members and Static Constructors</span></span>  
 <span data-ttu-id="ee2dc-147">Uma classe não foi inicializada até que o construtor de classe (`static` construtor em c#, `Shared Sub New` no Visual Basic) concluiu a execução.</span><span class="sxs-lookup"><span data-stu-id="ee2dc-147">A class is not initialized until its class constructor (`static` constructor in C#, `Shared Sub New` in Visual Basic) has finished running.</span></span> <span data-ttu-id="ee2dc-148">Para impedir a execução de código em um tipo que não é inicializado, o common language runtime bloqueia todas as chamadas de outros threads para `static` membros da classe (`Shared` membros no Visual Basic) até que o construtor da classe concluiu a execução.</span><span class="sxs-lookup"><span data-stu-id="ee2dc-148">To prevent the execution of code on a type that is not initialized, the common language runtime blocks all calls from other threads to `static` members of the class (`Shared` members in Visual Basic) until the class constructor has finished running.</span></span>  
  
 <span data-ttu-id="ee2dc-149">Por exemplo, se um construtor de classe inicia um novo thread, e chama o procedimento de thread um `static` membro da classe, os novos blocos de thread até que o construtor da classe seja concluída.</span><span class="sxs-lookup"><span data-stu-id="ee2dc-149">For example, if a class constructor starts a new thread, and the thread procedure calls a `static` member of the class, the new thread blocks until the class constructor completes.</span></span>  
  
 <span data-ttu-id="ee2dc-150">Isso se aplica a qualquer tipo que pode ter um `static` construtor.</span><span class="sxs-lookup"><span data-stu-id="ee2dc-150">This applies to any type that can have a `static` constructor.</span></span>  
  
## <a name="general-recommendations"></a><span data-ttu-id="ee2dc-151">Recomendações gerais</span><span class="sxs-lookup"><span data-stu-id="ee2dc-151">General Recommendations</span></span>  
 <span data-ttu-id="ee2dc-152">Ao usar vários threads, considere as seguintes diretrizes:</span><span class="sxs-lookup"><span data-stu-id="ee2dc-152">Consider the following guidelines when using multiple threads:</span></span>  
  
-   <span data-ttu-id="ee2dc-153">Não use <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> encerrar outros threads.</span><span class="sxs-lookup"><span data-stu-id="ee2dc-153">Don't use <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> to terminate other threads.</span></span> <span data-ttu-id="ee2dc-154">Chamando **anular** em outro thread equivale a gerar uma exceção que o thread, sem saber o que esse thread de ponto alcançou em seu processamento.</span><span class="sxs-lookup"><span data-stu-id="ee2dc-154">Calling **Abort** on another thread is akin to throwing an exception on that thread, without knowing what point that thread has reached in its processing.</span></span>  
  
-   <span data-ttu-id="ee2dc-155">Não use <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> e <xref:System.Threading.Thread.Resume%2A?displayProperty=nameWithType> para sincronizar as atividades de vários threads.</span><span class="sxs-lookup"><span data-stu-id="ee2dc-155">Don't use <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> and <xref:System.Threading.Thread.Resume%2A?displayProperty=nameWithType> to synchronize the activities of multiple threads.</span></span> <span data-ttu-id="ee2dc-156">Use <xref:System.Threading.Mutex>, <xref:System.Threading.ManualResetEvent>, <xref:System.Threading.AutoResetEvent>, e <xref:System.Threading.Monitor>.</span><span class="sxs-lookup"><span data-stu-id="ee2dc-156">Do use <xref:System.Threading.Mutex>, <xref:System.Threading.ManualResetEvent>, <xref:System.Threading.AutoResetEvent>, and <xref:System.Threading.Monitor>.</span></span>  
  
-   <span data-ttu-id="ee2dc-157">Não controla a execução de threads de trabalho em seu programa principal (usando eventos, por exemplo).</span><span class="sxs-lookup"><span data-stu-id="ee2dc-157">Don't control the execution of worker threads from your main program (using events, for example).</span></span> <span data-ttu-id="ee2dc-158">Em vez disso, crie seu programa para que os threads de trabalho são responsáveis por esperar até que o trabalho está disponível, executá-lo e notificar outras partes do seu programa quando terminar.</span><span class="sxs-lookup"><span data-stu-id="ee2dc-158">Instead, design your program so that worker threads are responsible for waiting until work is available, executing it, and notifying other parts of your program when finished.</span></span> <span data-ttu-id="ee2dc-159">Se seus threads de trabalho não bloqueiam, considere o uso de threads de pool.</span><span class="sxs-lookup"><span data-stu-id="ee2dc-159">If your worker threads do not block, consider using thread pool threads.</span></span> <span data-ttu-id="ee2dc-160"><xref:System.Threading.Monitor.PulseAll%2A?displayProperty=nameWithType>é útil em situações em que os threads de trabalho do bloco.</span><span class="sxs-lookup"><span data-stu-id="ee2dc-160"><xref:System.Threading.Monitor.PulseAll%2A?displayProperty=nameWithType> is useful in situations where worker threads block.</span></span>  
  
-   <span data-ttu-id="ee2dc-161">Não use tipos como objetos de bloqueio.</span><span class="sxs-lookup"><span data-stu-id="ee2dc-161">Don't use types as lock objects.</span></span> <span data-ttu-id="ee2dc-162">Isto é, evite código como `lock(typeof(X))` em c# ou `SyncLock(GetType(X))` no Visual Basic ou o uso de <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> com <xref:System.Type> objetos.</span><span class="sxs-lookup"><span data-stu-id="ee2dc-162">That is, avoid code such as `lock(typeof(X))` in C# or `SyncLock(GetType(X))` in Visual Basic, or the use of <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> with <xref:System.Type> objects.</span></span> <span data-ttu-id="ee2dc-163">Para um determinado tipo, há apenas uma instância de <xref:System.Type?displayProperty=nameWithType> por domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ee2dc-163">For a given type, there is only one instance of <xref:System.Type?displayProperty=nameWithType> per application domain.</span></span> <span data-ttu-id="ee2dc-164">Se o tipo de em que usar um bloqueio for público, o código que não seja o seu próprio pode assumir bloqueios, levando a deadlocks.</span><span class="sxs-lookup"><span data-stu-id="ee2dc-164">If the type you take a lock on is public, code other than your own can take locks on it, leading to deadlocks.</span></span> <span data-ttu-id="ee2dc-165">Para problemas adicionais, consulte [práticas recomendadas de confiabilidade](../../../docs/framework/performance/reliability-best-practices.md).</span><span class="sxs-lookup"><span data-stu-id="ee2dc-165">For additional issues, see [Reliability Best Practices](../../../docs/framework/performance/reliability-best-practices.md).</span></span>  
  
-   <span data-ttu-id="ee2dc-166">Tenha cuidado ao bloqueio em instâncias, por exemplo `lock(this)` em c# ou `SyncLock(Me)` no Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="ee2dc-166">Use caution when locking on instances, for example `lock(this)` in C# or `SyncLock(Me)` in Visual Basic.</span></span> <span data-ttu-id="ee2dc-167">Se outro código no seu aplicativo externo para o tipo tem um bloqueio no objeto, podem ocorrer deadlocks.</span><span class="sxs-lookup"><span data-stu-id="ee2dc-167">If other code in your application, external to the type, takes a lock on the object, deadlocks could occur.</span></span>  
  
-   <span data-ttu-id="ee2dc-168">Certifique-se de que um thread que entrou em um monitor sempre deixa monitor, mesmo se uma exceção ocorre enquanto o thread está no monitor.</span><span class="sxs-lookup"><span data-stu-id="ee2dc-168">Do ensure that a thread that has entered a monitor always leaves that monitor, even if an exception occurs while the thread is in the monitor.</span></span> <span data-ttu-id="ee2dc-169">C# [bloqueio](~/docs/csharp/language-reference/keywords/lock-statement.md) instrução e o Visual Basic [SyncLock](~/docs/visual-basic/language-reference/statements/synclock-statement.md) instrução fornecer esse comportamento automaticamente, empregando uma **finalmente** bloco para garantir que <xref:System.Threading.Monitor.Exit%2A?displayProperty=nameWithType> é chamado.</span><span class="sxs-lookup"><span data-stu-id="ee2dc-169">The C# [lock](~/docs/csharp/language-reference/keywords/lock-statement.md) statement and the Visual Basic [SyncLock](~/docs/visual-basic/language-reference/statements/synclock-statement.md) statement provide this behavior automatically, employing a **finally** block to ensure that <xref:System.Threading.Monitor.Exit%2A?displayProperty=nameWithType> is called.</span></span> <span data-ttu-id="ee2dc-170">Se você não pode garantir que **Exit** será chamado, considere alterar o design para usar **Mutex**.</span><span class="sxs-lookup"><span data-stu-id="ee2dc-170">If you cannot ensure that **Exit** will be called, consider changing your design to use **Mutex**.</span></span> <span data-ttu-id="ee2dc-171">Um mutex é liberado automaticamente quando o thread que atualmente possui ele termina.</span><span class="sxs-lookup"><span data-stu-id="ee2dc-171">A mutex is automatically released when the thread that currently owns it terminates.</span></span>  
  
-   <span data-ttu-id="ee2dc-172">Usar vários threads para tarefas que exigem recursos diferentes e evite atribuir vários threads para um único recurso.</span><span class="sxs-lookup"><span data-stu-id="ee2dc-172">Do use multiple threads for tasks that require different resources, and avoid assigning multiple threads to a single resource.</span></span> <span data-ttu-id="ee2dc-173">Por exemplo, se beneficia ter seu próprio thread, porque esse thread bloqueará durante as operações de e/s e assim permitir que outros threads executar qualquer tarefa que envolvem a e/s.</span><span class="sxs-lookup"><span data-stu-id="ee2dc-173">For example, any task involving I/O benefits from having its own thread, because that thread will block during I/O operations and thus allow other threads to execute.</span></span> <span data-ttu-id="ee2dc-174">Entrada do usuário é outro recurso que se beneficia com um thread dedicado.</span><span class="sxs-lookup"><span data-stu-id="ee2dc-174">User input is another resource that benefits from a dedicated thread.</span></span> <span data-ttu-id="ee2dc-175">Em um computador com processador único, uma tarefa que envolve a computação intensiva coexiste com a entrada do usuário e tarefas que envolvem a e/s, mas várias tarefas de computação intensa conteúdo uns com os outros.</span><span class="sxs-lookup"><span data-stu-id="ee2dc-175">On a single-processor computer, a task that involves intensive computation coexists with user input and with tasks that involve I/O, but multiple computation-intensive tasks contend with each other.</span></span>  
  
-   <span data-ttu-id="ee2dc-176">Considere o uso de métodos do <xref:System.Threading.Interlocked> classe para alterações de estado simples, em vez de usar o `lock` instrução (`SyncLock` no Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="ee2dc-176">Consider using methods of the <xref:System.Threading.Interlocked> class for simple state changes, instead of using the `lock` statement (`SyncLock` in Visual Basic).</span></span> <span data-ttu-id="ee2dc-177">O `lock` instrução é uma boa ferramenta para fins gerais, mas o <xref:System.Threading.Interlocked> classe fornece um melhor desempenho para atualizações que devem ser atômica.</span><span class="sxs-lookup"><span data-stu-id="ee2dc-177">The `lock` statement is a good general-purpose tool, but the <xref:System.Threading.Interlocked> class provides better performance for updates that must be atomic.</span></span> <span data-ttu-id="ee2dc-178">Internamente, ele executa um prefixo único bloqueio se não houver nenhuma contenção.</span><span class="sxs-lookup"><span data-stu-id="ee2dc-178">Internally, it executes a single lock prefix if there is no contention.</span></span> <span data-ttu-id="ee2dc-179">Em revisões de código, atente para código semelhante ao mostrado nos exemplos a seguir.</span><span class="sxs-lookup"><span data-stu-id="ee2dc-179">In code reviews, watch for code like that shown in the following examples.</span></span> <span data-ttu-id="ee2dc-180">No primeiro exemplo, uma variável de estado é incrementada:</span><span class="sxs-lookup"><span data-stu-id="ee2dc-180">In the first example, a state variable is incremented:</span></span>  
  
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
  
     <span data-ttu-id="ee2dc-181">Você pode melhorar o desempenho usando o <xref:System.Threading.Interlocked.Increment%2A> método em vez do `lock` instrução, da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="ee2dc-181">You can improve performance by using the <xref:System.Threading.Interlocked.Increment%2A> method instead of the `lock` statement, as follows:</span></span>  
  
    ```vb  
    System.Threading.Interlocked.Increment(myField)  
    ```  
  
    ```csharp  
    System.Threading.Interlocked.Increment(myField);  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="ee2dc-182">No .NET Framework versão 2.0, o <xref:System.Threading.Interlocked.Add%2A> método fornece atualizações atômicas em incrementos maiores do que 1.</span><span class="sxs-lookup"><span data-stu-id="ee2dc-182">In the .NET Framework version 2.0, the <xref:System.Threading.Interlocked.Add%2A> method provides atomic updates in increments larger than 1.</span></span>  
  
     <span data-ttu-id="ee2dc-183">No segundo exemplo, uma variável de tipo de referência é atualizada somente se ele for uma referência nula (`Nothing` no Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="ee2dc-183">In the second example, a reference type variable is updated only if it is a null reference (`Nothing` in Visual Basic).</span></span>  
  
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
  
     <span data-ttu-id="ee2dc-184">É possível melhorar o desempenho usando o <xref:System.Threading.Interlocked.CompareExchange%2A> método em vez disso, da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="ee2dc-184">Performance can be improved by using the <xref:System.Threading.Interlocked.CompareExchange%2A> method instead, as follows:</span></span>  
  
    ```vb  
    System.Threading.Interlocked.CompareExchange(x, y, Nothing)  
    ```  
  
    ```csharp  
    System.Threading.Interlocked.CompareExchange(ref x, y, null);  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="ee2dc-185">No .NET Framework versão 2.0, o <xref:System.Threading.Interlocked.CompareExchange%2A> método tem uma sobrecarga genérica que pode ser usada para a substituição de segurança de tipos de qualquer tipo de referência.</span><span class="sxs-lookup"><span data-stu-id="ee2dc-185">In the .NET Framework version 2.0, the <xref:System.Threading.Interlocked.CompareExchange%2A> method has a generic overload that can be used for type-safe replacement of any reference type.</span></span>  
  
## <a name="recommendations-for-class-libraries"></a><span data-ttu-id="ee2dc-186">Recomendações para bibliotecas de classe</span><span class="sxs-lookup"><span data-stu-id="ee2dc-186">Recommendations for Class Libraries</span></span>  
 <span data-ttu-id="ee2dc-187">Considere as seguintes diretrizes ao criar bibliotecas de classes para multithreading:</span><span class="sxs-lookup"><span data-stu-id="ee2dc-187">Consider the following guidelines when designing class libraries for multithreading:</span></span>  
  
-   <span data-ttu-id="ee2dc-188">Evite a necessidade de sincronização, se possível.</span><span class="sxs-lookup"><span data-stu-id="ee2dc-188">Avoid the need for synchronization, if possible.</span></span> <span data-ttu-id="ee2dc-189">Isso é especialmente verdadeiro para o código de uso intensivo.</span><span class="sxs-lookup"><span data-stu-id="ee2dc-189">This is especially true for heavily used code.</span></span> <span data-ttu-id="ee2dc-190">Por exemplo, um algoritmo pode ser ajustado para tolerar uma condição de corrida em vez de eliminá-lo.</span><span class="sxs-lookup"><span data-stu-id="ee2dc-190">For example, an algorithm might be adjusted to tolerate a race condition rather than eliminate it.</span></span> <span data-ttu-id="ee2dc-191">Sincronização desnecessária diminui o desempenho e cria a possibilidade de deadlocks e condições de corrida.</span><span class="sxs-lookup"><span data-stu-id="ee2dc-191">Unnecessary synchronization decreases performance and creates the possibility of deadlocks and race conditions.</span></span>  
  
-   <span data-ttu-id="ee2dc-192">Verifique os dados estáticos (`Shared` no Visual Basic) thread-safe por padrão.</span><span class="sxs-lookup"><span data-stu-id="ee2dc-192">Make static data (`Shared` in Visual Basic) thread safe by default.</span></span>  
  
-   <span data-ttu-id="ee2dc-193">Não faça instância de segmento de dados seguro por padrão.</span><span class="sxs-lookup"><span data-stu-id="ee2dc-193">Do not make instance data thread safe by default.</span></span> <span data-ttu-id="ee2dc-194">Adicionar bloqueios para criar o código de thread-safe diminui o desempenho, aumenta a contenção de bloqueio e cria a possibilidade de deadlocks ocorra.</span><span class="sxs-lookup"><span data-stu-id="ee2dc-194">Adding locks to create thread-safe code decreases performance, increases lock contention, and creates the possibility for deadlocks to occur.</span></span> <span data-ttu-id="ee2dc-195">Modelos de aplicativo, em comum que apenas um thread por vez executa código do usuário, o que minimiza a necessidade de acesso thread-safe.</span><span class="sxs-lookup"><span data-stu-id="ee2dc-195">In common application models, only one thread at a time executes user code, which minimizes the need for thread safety.</span></span> <span data-ttu-id="ee2dc-196">Por esse motivo, as bibliotecas de classes do .NET Framework não são thread-safe por padrão.</span><span class="sxs-lookup"><span data-stu-id="ee2dc-196">For this reason, the .NET Framework class libraries are not thread safe by default.</span></span>  
  
-   <span data-ttu-id="ee2dc-197">Evite fornecer métodos estáticos que alteram o estado estático.</span><span class="sxs-lookup"><span data-stu-id="ee2dc-197">Avoid providing static methods that alter static state.</span></span> <span data-ttu-id="ee2dc-198">Em cenários de servidor comum, estado estático é compartilhado entre as solicitações, que significa que vários threads podem executar esse código ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="ee2dc-198">In common server scenarios, static state is shared across requests, which means multiple threads can execute that code at the same time.</span></span> <span data-ttu-id="ee2dc-199">Isso abre a possibilidade de threading bugs.</span><span class="sxs-lookup"><span data-stu-id="ee2dc-199">This opens up the possibility of threading bugs.</span></span> <span data-ttu-id="ee2dc-200">Considere usar um padrão de design que encapsula dados em instâncias que não são compartilhadas entre solicitações.</span><span class="sxs-lookup"><span data-stu-id="ee2dc-200">Consider using a design pattern that encapsulates data into instances that are not shared across requests.</span></span> <span data-ttu-id="ee2dc-201">Além disso, se os dados estáticos são sincronizados, chamadas entre os métodos estáticos que alteram o estado podem resultar em deadlocks ou sincronização redundante, afetando negativamente o desempenho.</span><span class="sxs-lookup"><span data-stu-id="ee2dc-201">Furthermore, if static data are synchronized, calls between static methods that alter state can result in deadlocks or redundant synchronization, adversely affecting performance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee2dc-202">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ee2dc-202">See Also</span></span>  
 [<span data-ttu-id="ee2dc-203">Threading</span><span class="sxs-lookup"><span data-stu-id="ee2dc-203">Threading</span></span>](../../../docs/standard/threading/index.md)  
 [<span data-ttu-id="ee2dc-204">Threads e threading</span><span class="sxs-lookup"><span data-stu-id="ee2dc-204">Threads and Threading</span></span>](../../../docs/standard/threading/threads-and-threading.md)
