---
title: MDA dangerousThreadingAPI
description: Examine o MDA (Assistente de depuração gerenciada) dangerousThreadingAPI, que é ativado quando thread. Suspend é chamado em um thread diferente do thread atual.
ms.date: 03/30/2017
helpviewer_keywords:
- suspending threads
- DangerousThreadingAPI MDA
- managed debugging assistants (MDAs), dangerous threading operations
- threading [.NET Framework], suspending
- MDAs (managed debugging assistants), dangerous threading operations
- Suspend method
- threading [.NET Framework], managed debugging assistants
ms.assetid: 3e5efbc5-92e4-4229-b31f-ce368a1adb96
ms.openlocfilehash: 9069ccb6f106c83db94f88bc464bc0888d28586c
ms.sourcegitcommit: a2c8b19e813a52b91facbb5d7e3c062c7188b457
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85415999"
---
# <a name="dangerousthreadingapi-mda"></a><span data-ttu-id="47c10-103">MDA dangerousThreadingAPI</span><span class="sxs-lookup"><span data-stu-id="47c10-103">dangerousThreadingAPI MDA</span></span>
<span data-ttu-id="47c10-104">O MDA (assistente para depuração gerenciada) `dangerousThreadingAPI` é ativado quando o método <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> é chamado em um thread que não seja o thread atual.</span><span class="sxs-lookup"><span data-stu-id="47c10-104">The `dangerousThreadingAPI` managed debugging assistant (MDA) is activated when the <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> method is called on a thread other than the current thread.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="47c10-105">Sintomas</span><span class="sxs-lookup"><span data-stu-id="47c10-105">Symptoms</span></span>  
 <span data-ttu-id="47c10-106">Um aplicativo não está respondendo ou para de responder por tempo indefinido.</span><span class="sxs-lookup"><span data-stu-id="47c10-106">An application is unresponsive or hangs indefinitely.</span></span> <span data-ttu-id="47c10-107">Os dados do sistema ou do aplicativo podem ser deixados em um estado imprevisível temporariamente ou mesmo depois que um aplicativo foi desligado.</span><span class="sxs-lookup"><span data-stu-id="47c10-107">System or application data might be left in an unpredictable state temporarily or even after an application has been shut down.</span></span> <span data-ttu-id="47c10-108">Algumas operações não são concluídas como esperado.</span><span class="sxs-lookup"><span data-stu-id="47c10-108">Some operations are not completing as expected.</span></span>  
  
 <span data-ttu-id="47c10-109">Os sintomas podem variar muito devido à aleatoriedade inerente ao problema.</span><span class="sxs-lookup"><span data-stu-id="47c10-109">Symptoms can vary widely due to the randomness inherent to the problem.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="47c10-110">Causa</span><span class="sxs-lookup"><span data-stu-id="47c10-110">Cause</span></span>  
 <span data-ttu-id="47c10-111">Um thread é suspenso de forma assíncrona por outro thread usando o método <xref:System.Threading.Thread.Suspend%2A>.</span><span class="sxs-lookup"><span data-stu-id="47c10-111">A thread is asynchronously suspended by another thread using the <xref:System.Threading.Thread.Suspend%2A> method.</span></span> <span data-ttu-id="47c10-112">Não há nenhuma maneira de determinar quando é seguro suspender outro thread que pode estar no meio de uma operação.</span><span class="sxs-lookup"><span data-stu-id="47c10-112">There is no way to determine when it is safe to suspend another thread which might be in the middle of an operation.</span></span> <span data-ttu-id="47c10-113">A suspensão do thread pode resultar na corrupção de dados ou na interrupção de invariáveis.</span><span class="sxs-lookup"><span data-stu-id="47c10-113">Suspending the thread can result in the corruption of data or the breaking of invariants.</span></span> <span data-ttu-id="47c10-114">Caso um thread precise ser colocado em um estado suspenso e nunca ser retomado usando o método <xref:System.Threading.Thread.Resume%2A>, o aplicativo poderá parar de responder por tempo indefinido e, possivelmente, danificar os dados do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="47c10-114">Should a thread be placed into a suspended state and never resumed using the <xref:System.Threading.Thread.Resume%2A> method, the application can hang indefinitely and possibly damage application data.</span></span> <span data-ttu-id="47c10-115">Esses métodos foram marcados como obsoletos.</span><span class="sxs-lookup"><span data-stu-id="47c10-115">These methods have been marked as obsolete.</span></span>  
  
 <span data-ttu-id="47c10-116">Se os primitivos de sincronização forem mantidos pelo thread de destino, eles permanecerão mantidos durante a suspensão.</span><span class="sxs-lookup"><span data-stu-id="47c10-116">If synchronization primitives are held by the target thread, they remain held during suspension.</span></span> <span data-ttu-id="47c10-117">Isso pode levar a deadlocks, caso outro thread, por exemplo, o thread que executa o <xref:System.Threading.Thread.Suspend%2A>, tente adquirir um bloqueio no primitivo.</span><span class="sxs-lookup"><span data-stu-id="47c10-117">This can lead to deadlocks should another thread, for example the thread performing the <xref:System.Threading.Thread.Suspend%2A>, attempt to acquire a lock on the primitive.</span></span> <span data-ttu-id="47c10-118">Nessa situação, o problema se manifesta como um deadlock.</span><span class="sxs-lookup"><span data-stu-id="47c10-118">In this situation, the problem manifests itself as a deadlock.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="47c10-119">Resolução</span><span class="sxs-lookup"><span data-stu-id="47c10-119">Resolution</span></span>  
 <span data-ttu-id="47c10-120">Evite designs que exigem o uso de <xref:System.Threading.Thread.Suspend%2A> e <xref:System.Threading.Thread.Resume%2A>.</span><span class="sxs-lookup"><span data-stu-id="47c10-120">Avoid designs that require the use of <xref:System.Threading.Thread.Suspend%2A> and <xref:System.Threading.Thread.Resume%2A>.</span></span> <span data-ttu-id="47c10-121">Para cooperação entre threads, use primitivos de sincronização como <xref:System.Threading.Monitor>, <xref:System.Threading.ReaderWriterLock>, <xref:System.Threading.Mutex> ou a instrução `lock` do C#.</span><span class="sxs-lookup"><span data-stu-id="47c10-121">For cooperation between threads, use synchronization primitives such as <xref:System.Threading.Monitor>, <xref:System.Threading.ReaderWriterLock>, <xref:System.Threading.Mutex>, or the C# `lock` statement.</span></span> <span data-ttu-id="47c10-122">Se você precisar usar esses métodos, reduza a janela de tempo e minimize a quantidade de código que é executada enquanto o thread está em um estado suspenso.</span><span class="sxs-lookup"><span data-stu-id="47c10-122">If you must use these methods, reduce the window of time and minimize the amount of code that executes while the thread is in a suspended state.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="47c10-123">Efeito sobre o runtime</span><span class="sxs-lookup"><span data-stu-id="47c10-123">Effect on the Runtime</span></span>  
 <span data-ttu-id="47c10-124">Esse MDA não tem efeito sobre o CLR.</span><span class="sxs-lookup"><span data-stu-id="47c10-124">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="47c10-125">Ele relata apenas os dados sobre operações de threading perigosas.</span><span class="sxs-lookup"><span data-stu-id="47c10-125">It only reports data about dangerous threading operations.</span></span>  
  
## <a name="output"></a><span data-ttu-id="47c10-126">Saída</span><span class="sxs-lookup"><span data-stu-id="47c10-126">Output</span></span>  
 <span data-ttu-id="47c10-127">O MDA identifica o método de threading perigoso que fez com que ele fosse ativado.</span><span class="sxs-lookup"><span data-stu-id="47c10-127">The MDA identifies the dangerous threading method that caused it to be activated.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="47c10-128">Configuração</span><span class="sxs-lookup"><span data-stu-id="47c10-128">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dangerousThreadingAPI />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="47c10-129">Exemplo</span><span class="sxs-lookup"><span data-stu-id="47c10-129">Example</span></span>  
 <span data-ttu-id="47c10-130">O exemplo de código a seguir demonstra uma chamada ao método <xref:System.Threading.Thread.Suspend%2A> que causa a ativação da `dangerousThreadingAPI`.</span><span class="sxs-lookup"><span data-stu-id="47c10-130">The following code example demonstrates a call to the <xref:System.Threading.Thread.Suspend%2A> method that causes the activation of the `dangerousThreadingAPI`.</span></span>  
  
```csharp
using System.Threading;  
void FireMda()  
{  
Thread t = new Thread(delegate() { Thread.Sleep(1000); });  
    t.Start();  
    // The following line activates the MDA.  
    t.Suspend();
    t.Resume();  
    t.Join();  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="47c10-131">Veja também</span><span class="sxs-lookup"><span data-stu-id="47c10-131">See also</span></span>

- <xref:System.Threading.Thread>
- [<span data-ttu-id="47c10-132">Diagnosticando erros com assistentes para depuração gerenciada</span><span class="sxs-lookup"><span data-stu-id="47c10-132">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="47c10-133">Instrução lock</span><span class="sxs-lookup"><span data-stu-id="47c10-133">lock Statement</span></span>](../../csharp/language-reference/keywords/lock-statement.md)
