---
title: Aplicativos com multithread (C#)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: b7015cfb-d506-4eac-b2f8-b2caaa9cc977
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 48b056172e3260952155eb40a1a393d86da78344
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="multithreaded-applications-c"></a><span data-ttu-id="0844d-102">Aplicativos com multithread (C#)</span><span class="sxs-lookup"><span data-stu-id="0844d-102">Multithreaded Applications (C#)</span></span>
<span data-ttu-id="0844d-103">Com o C#, é possível escrever aplicativos que executam várias tarefas ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="0844d-103">With C#, you can write applications that perform multiple tasks at the same time.</span></span> <span data-ttu-id="0844d-104">Tarefas com o potencial de atrasar outras tarefas podem ser executadas em threads separados, um processo conhecido como *multithreading* ou *free threading*.</span><span class="sxs-lookup"><span data-stu-id="0844d-104">Tasks with the potential of holding up other tasks can execute on separate threads, a process known as *multithreading* or *free threading*.</span></span>  
  
 <span data-ttu-id="0844d-105">Aplicativos que usam multithreading são mais responsivos a entradas do usuário porque a interface do usuário permanece ativa, enquanto tarefas com uso intensivo do processador são executadas em threads separados.</span><span class="sxs-lookup"><span data-stu-id="0844d-105">Applications that use multithreading are more responsive to user input because the user interface stays active as processor-intensive tasks execute on separate threads.</span></span> <span data-ttu-id="0844d-106">O multithreading também é útil quando você cria aplicativos escalonáveis, porque você pode adicionar threads conforme a carga de trabalho aumenta.</span><span class="sxs-lookup"><span data-stu-id="0844d-106">Multithreading is also useful when you create scalable applications, because you can add threads as the workload increases.</span></span>  
  
## <a name="creating-and-using-threads"></a><span data-ttu-id="0844d-107">Criando e usando threads</span><span class="sxs-lookup"><span data-stu-id="0844d-107">Creating and Using Threads</span></span>  
 <span data-ttu-id="0844d-108">Se precisar de mais controle sobre o comportamento dos threads de seu aplicativo, você pode gerenciar os threads por conta própria.</span><span class="sxs-lookup"><span data-stu-id="0844d-108">If you need more control over the behavior of your application's threads, you can manage the threads yourself.</span></span> <span data-ttu-id="0844d-109">No entanto, observe que escrever aplicativos multi-threaded corretamente pode ser difícil: o aplicativo pode parar de responder ou passar por erros transitórios causados por condições de corrida.</span><span class="sxs-lookup"><span data-stu-id="0844d-109">However, realize that writing correct multithreaded applications can be difficult: Your application may stop responding or experience transient errors caused by race conditions.</span></span> <span data-ttu-id="0844d-110">Para obter mais informações, veja [Componentes thread-safe](http://msdn.microsoft.com/library/4f7c7377-a782-4bd0-aaa3-9db8c12945ee).</span><span class="sxs-lookup"><span data-stu-id="0844d-110">For more information, see [Thread-Safe Components](http://msdn.microsoft.com/library/4f7c7377-a782-4bd0-aaa3-9db8c12945ee).</span></span>  
  
 <span data-ttu-id="0844d-111">Você cria um novo thread declarando uma variável do tipo <xref:System.Threading.Thread> e chamando o construtor, fornecendo o nome do procedimento ou método que deseja executar no novo thread.</span><span class="sxs-lookup"><span data-stu-id="0844d-111">You create a new thread by declaring a variable of type <xref:System.Threading.Thread> and calling the constructor, providing the name of the procedure or method that you want to execute on the new thread.</span></span> <span data-ttu-id="0844d-112">O código a seguir fornece um exemplo.</span><span class="sxs-lookup"><span data-stu-id="0844d-112">The following code provides an example.</span></span>  
  
```csharp  
System.Threading.Thread newThread =  
    new System.Threading.Thread(AMethod);  
```  
  
### <a name="starting-and-stopping-threads"></a><span data-ttu-id="0844d-113">Iniciando e parando threads</span><span class="sxs-lookup"><span data-stu-id="0844d-113">Starting and Stopping Threads</span></span>  
 <span data-ttu-id="0844d-114">Para iniciar a execução de um novo thread, use o método <xref:System.Threading.Thread.Start%2A>, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="0844d-114">To start the execution of a new thread, use the <xref:System.Threading.Thread.Start%2A> method, as shown in the following code.</span></span>  
  
```csharp  
newThread.Start();  
```  
  
 <span data-ttu-id="0844d-115">Para interromper a execução de um thread, use o método <xref:System.Threading.Thread.Abort%2A>, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="0844d-115">To stop the execution of a thread, use the <xref:System.Threading.Thread.Abort%2A> method, as shown in the following code.</span></span>  
  
```csharp  
newThread.Abort();  
```  
  
 <span data-ttu-id="0844d-116">Além de iniciar e parar threads, você também pode pausar threads chamando o método <xref:System.Threading.Thread.Sleep%2A> ou <xref:System.Threading.Thread.Suspend%2A>, retomar um thread suspenso usando o método <xref:System.Threading.Thread.Resume%2A> e destruir um thread usando o método <xref:System.Threading.Thread.Abort%2A></span><span class="sxs-lookup"><span data-stu-id="0844d-116">Besides starting and stopping threads, you can also pause threads by calling the <xref:System.Threading.Thread.Sleep%2A> or <xref:System.Threading.Thread.Suspend%2A> method, resume a suspended thread by using the <xref:System.Threading.Thread.Resume%2A> method, and destroy a thread by using the <xref:System.Threading.Thread.Abort%2A> method</span></span>  
  
### <a name="thread-methods"></a><span data-ttu-id="0844d-117">Métodos de thread</span><span class="sxs-lookup"><span data-stu-id="0844d-117">Thread Methods</span></span>  
 <span data-ttu-id="0844d-118">A tabela a seguir mostra alguns dos métodos que você pode usar para controlar segmentos individuais.</span><span class="sxs-lookup"><span data-stu-id="0844d-118">The following table shows some of the methods that you can use to control individual threads.</span></span>  
  
|<span data-ttu-id="0844d-119">Método</span><span class="sxs-lookup"><span data-stu-id="0844d-119">Method</span></span>|<span data-ttu-id="0844d-120">Ação</span><span class="sxs-lookup"><span data-stu-id="0844d-120">Action</span></span>|  
|------------|------------|  
|<xref:System.Threading.Thread.Start%2A>|<span data-ttu-id="0844d-121">Faz com que um thread comece a ser executado.</span><span class="sxs-lookup"><span data-stu-id="0844d-121">Causes a thread to start to run.</span></span>|  
|<xref:System.Threading.Thread.Sleep%2A>|<span data-ttu-id="0844d-122">Pausa um thread por um período especificado.</span><span class="sxs-lookup"><span data-stu-id="0844d-122">Pauses a thread for a specified time.</span></span>|  
|<xref:System.Threading.Thread.Suspend%2A>|<span data-ttu-id="0844d-123">Pausa um thread quando ele atinge um ponto de segurança.</span><span class="sxs-lookup"><span data-stu-id="0844d-123">Pauses a thread when it reaches a safe point.</span></span>|  
|<xref:System.Threading.Thread.Abort%2A>|<span data-ttu-id="0844d-124">Para um thread quando ele atinge um ponto de segurança.</span><span class="sxs-lookup"><span data-stu-id="0844d-124">Stops a thread when it reaches a safe point.</span></span>|  
|<xref:System.Threading.Thread.Resume%2A>|<span data-ttu-id="0844d-125">Reinicia um thread suspenso</span><span class="sxs-lookup"><span data-stu-id="0844d-125">Restarts a suspended thread</span></span>|  
|<xref:System.Threading.Thread.Join%2A>|<span data-ttu-id="0844d-126">Faz com que o thread atual aguarde até que outro thread seja finalizado.</span><span class="sxs-lookup"><span data-stu-id="0844d-126">Causes the current thread to wait for another thread to finish.</span></span> <span data-ttu-id="0844d-127">Se for usado com um valor de tempo limite, este método retorna `True` se o thread terminar no tempo alocado.</span><span class="sxs-lookup"><span data-stu-id="0844d-127">If used with a time-out value, this method returns `True` if the thread finishes in the allocated time.</span></span>|  
  
### <a name="safe-points"></a><span data-ttu-id="0844d-128">Pontos de segurança</span><span class="sxs-lookup"><span data-stu-id="0844d-128">Safe Points</span></span>  
 <span data-ttu-id="0844d-129">A maioria desses métodos são autoexplicativos, mas o conceito de *pontos de segurança* pode ser novidade para você.</span><span class="sxs-lookup"><span data-stu-id="0844d-129">Most of these methods are self-explanatory, but the concept of *safe points* may be new to you.</span></span> <span data-ttu-id="0844d-130">Pontos de segurança são locais no código em que é seguro para o Common Language Runtime executar a *coleta de lixo* automática, que é o processo de liberar variáveis não utilizadas e recuperar memória.</span><span class="sxs-lookup"><span data-stu-id="0844d-130">Safe points are locations in code where it is safe for the common language runtime to perform automatic *garbage collection*, the process of releasing unused variables and reclaiming memory.</span></span> <span data-ttu-id="0844d-131">Quando você chama o método <xref:System.Threading.Thread.Abort%2A> ou <xref:System.Threading.Thread.Suspend%2A> de um thread, o Common Language Runtime analisa o código e determina o local apropriado para o thread parar a execução.</span><span class="sxs-lookup"><span data-stu-id="0844d-131">When you call the <xref:System.Threading.Thread.Abort%2A> or <xref:System.Threading.Thread.Suspend%2A> method of a thread, the common language runtime analyzes the code and determines the location of an appropriate location for the thread to stop running.</span></span>  
  
### <a name="thread-properties"></a><span data-ttu-id="0844d-132">Propriedades da Thread</span><span class="sxs-lookup"><span data-stu-id="0844d-132">Thread Properties</span></span>  
 <span data-ttu-id="0844d-133">Threads também contêm diversas propriedades úteis, como mostrado na tabela a seguir:</span><span class="sxs-lookup"><span data-stu-id="0844d-133">Threads also contain several useful properties, as shown in the following table:</span></span>  
  
|<span data-ttu-id="0844d-134">Propriedade</span><span class="sxs-lookup"><span data-stu-id="0844d-134">Property</span></span>|<span data-ttu-id="0844d-135">Valor</span><span class="sxs-lookup"><span data-stu-id="0844d-135">Value</span></span>|  
|--------------|-----------|  
|<xref:System.Threading.Thread.IsAlive%2A>|<span data-ttu-id="0844d-136">Contém o valor `True` se um thread estiver ativo.</span><span class="sxs-lookup"><span data-stu-id="0844d-136">Contains the value `True` if a thread is active.</span></span>|  
|<xref:System.Threading.Thread.IsBackground%2A>|<span data-ttu-id="0844d-137">Obtém ou define um valor booliano que indica se um thread é ou deve ser um thread de segundo plano.</span><span class="sxs-lookup"><span data-stu-id="0844d-137">Gets or sets a Boolean that indicates if a thread is or should be a background thread.</span></span> <span data-ttu-id="0844d-138">Threads de segundo plano são como threads de primeiro plano, mas um thread de segundo plano não impede que um processo pare.</span><span class="sxs-lookup"><span data-stu-id="0844d-138">Background threads are like foreground threads, but a background thread does not prevent a process from stopping.</span></span> <span data-ttu-id="0844d-139">Após todos os threads de primeiro plano que pertencem a um processo serem parados, o Common Language Runtime finaliza o processo chamando o método <xref:System.Threading.Thread.Abort%2A> em threads em segundo plano que ainda estão ativos.</span><span class="sxs-lookup"><span data-stu-id="0844d-139">Once all foreground threads that belong to a process have stopped, the common language runtime ends the process by calling the <xref:System.Threading.Thread.Abort%2A> method on background threads that are still alive.</span></span>|  
|<xref:System.Threading.Thread.Name%2A>|<span data-ttu-id="0844d-140">Obtém ou define o nome de um thread.</span><span class="sxs-lookup"><span data-stu-id="0844d-140">Gets or sets the name of a thread.</span></span> <span data-ttu-id="0844d-141">Usado com mais frequência para descobrir threads individuais quando você depura.</span><span class="sxs-lookup"><span data-stu-id="0844d-141">Most frequently used to discover individual threads when you debug.</span></span>|  
|<xref:System.Threading.Thread.Priority%2A>|<span data-ttu-id="0844d-142">Obtém ou define um valor usado pelo sistema operacional para priorizar agendamento de threads.</span><span class="sxs-lookup"><span data-stu-id="0844d-142">Gets or sets a value that is used by the operating system to prioritize thread scheduling.</span></span>|  
|<xref:System.Threading.Thread.ThreadState%2A>|<span data-ttu-id="0844d-143">Contém um valor que descreve o estado ou estados de um thread.</span><span class="sxs-lookup"><span data-stu-id="0844d-143">Contains a value that describes a thread's state or states.</span></span>|  
  
## <a name="thread-priorities"></a><span data-ttu-id="0844d-144">Prioridades do thread</span><span class="sxs-lookup"><span data-stu-id="0844d-144">Thread Priorities</span></span>  
 <span data-ttu-id="0844d-145">Cada thread tem uma propriedade de prioridade que determina quanto tempo do processador ele tem para ser executado.</span><span class="sxs-lookup"><span data-stu-id="0844d-145">Every thread has a priority property that determines how big or small a slice of processor time it has to execute.</span></span> <span data-ttu-id="0844d-146">O sistema operacional aloca frações de tempo maiores para segmentos de maior prioridade e frações de tempo mais curtas para segmentos de menor prioridade.</span><span class="sxs-lookup"><span data-stu-id="0844d-146">The operating system allocates longer time slices to high-priority threads and shorter time slices to low-priority threads.</span></span> <span data-ttu-id="0844d-147">Novos segmentos são criados com o valor de `Normal`, mas você pode alterar a propriedade <xref:System.Threading.Thread.Priority%2A> para qualquer valor na enumeração <xref:System.Threading.ThreadPriority>.</span><span class="sxs-lookup"><span data-stu-id="0844d-147">New threads are created with the value of `Normal`, but you can change the <xref:System.Threading.Thread.Priority%2A> property to any value in the <xref:System.Threading.ThreadPriority> enumeration.</span></span>  
  
 <span data-ttu-id="0844d-148">Consulte <xref:System.Threading.ThreadPriority> para obter uma descrição detalhada sobre as várias prioridades de thread.</span><span class="sxs-lookup"><span data-stu-id="0844d-148">See <xref:System.Threading.ThreadPriority> for a detailed description of the various thread priorities.</span></span>  
  
## <a name="foreground-and-background-threads"></a><span data-ttu-id="0844d-149">Threads em primeiro plano e em segundo plano</span><span class="sxs-lookup"><span data-stu-id="0844d-149">Foreground and Background Threads</span></span>  
 <span data-ttu-id="0844d-150">Um *thread de primeiro plano* é executado indefinidamente, enquanto um *thread de segundo plano* para assim que o último thread do primeiro plano parar.</span><span class="sxs-lookup"><span data-stu-id="0844d-150">A *foreground thread* runs indefinitely, whereas a *background thread* stops as soon as the last foreground thread has stopped.</span></span> <span data-ttu-id="0844d-151">Você pode usar a propriedade <xref:System.Threading.Thread.IsBackground%2A> para determinar ou alterar o status em segundo plano de um thread.</span><span class="sxs-lookup"><span data-stu-id="0844d-151">You can use the <xref:System.Threading.Thread.IsBackground%2A> property to determine or change the background status of a thread.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0844d-152">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0844d-152">See Also</span></span>  
 <xref:System.Threading.Thread>  
 [<span data-ttu-id="0844d-153">Sincronização de thread (C#)</span><span class="sxs-lookup"><span data-stu-id="0844d-153">Thread Synchronization (C#)</span></span>](../../../../csharp/programming-guide/concepts/threading/thread-synchronization.md)  
 [<span data-ttu-id="0844d-154">Parâmetros e valores de retorno para procedimentos multi-threaded (C#)</span><span class="sxs-lookup"><span data-stu-id="0844d-154">Parameters and Return Values for Multithreaded Procedures (C#)</span></span>](../../../../csharp/programming-guide/concepts/threading/parameters-and-return-values-for-multithreaded-procedures.md)  
 [<span data-ttu-id="0844d-155">Threading (C#)</span><span class="sxs-lookup"><span data-stu-id="0844d-155">Threading (C#)</span></span>](../../../../csharp/programming-guide/concepts/threading/index.md)
