---
title: Destruindo threads
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- destroying threads
- threading [.NET Framework], destroying threads
ms.assetid: df54e648-c5d1-47c9-bd29-8e4438c1db6d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 986b4dee17c41928327e7b2672d641bbb8b16f1d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960086"
---
# <a name="destroying-threads"></a><span data-ttu-id="80957-102">Destruindo threads</span><span class="sxs-lookup"><span data-stu-id="80957-102">Destroying threads</span></span>
<span data-ttu-id="80957-103">O método <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> é usado para interromper um thread gerenciado permanentemente.</span><span class="sxs-lookup"><span data-stu-id="80957-103">The <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> method is used to stop a managed thread permanently.</span></span> <span data-ttu-id="80957-104">Quando você chama <xref:System.Threading.Thread.Abort%2A>, o CLR lança um <xref:System.Threading.ThreadAbortException> no thread de destino, que o thread de destino pode capturar.</span><span class="sxs-lookup"><span data-stu-id="80957-104">When you call <xref:System.Threading.Thread.Abort%2A>, the common language runtime throws a <xref:System.Threading.ThreadAbortException> in the target thread, which the target thread can catch.</span></span> <span data-ttu-id="80957-105">Para obter mais informações, consulte <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="80957-105">For more information, see <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="80957-106">Se um thread estiver executando um código não gerenciado quando seu método <xref:System.Threading.Thread.Abort%2A> for chamado, o tempo de execução o marca <xref:System.Threading.ThreadState.AbortRequested?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="80957-106">If a thread is executing unmanaged code when its <xref:System.Threading.Thread.Abort%2A> method is called, the runtime marks it <xref:System.Threading.ThreadState.AbortRequested?displayProperty=nameWithType>.</span></span> <span data-ttu-id="80957-107">A exceção é lançada quando o thread retorna para código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="80957-107">The exception is thrown when the thread returns to managed code.</span></span>  
  
 <span data-ttu-id="80957-108">Após a anulação de um thread, ele não poderá ser reiniciado.</span><span class="sxs-lookup"><span data-stu-id="80957-108">Once a thread is aborted, it cannot be restarted.</span></span>  
  
 <span data-ttu-id="80957-109">O método <xref:System.Threading.Thread.Abort%2A> não causa a anulação imediata do thread, porque o thread de destino pode capturar o <xref:System.Threading.ThreadAbortException> e executar valores arbitrários de código em um bloco `finally`.</span><span class="sxs-lookup"><span data-stu-id="80957-109">The <xref:System.Threading.Thread.Abort%2A> method does not cause the thread to abort immediately, because the target thread can catch the <xref:System.Threading.ThreadAbortException> and execute arbitrary amounts of code in a `finally` block.</span></span> <span data-ttu-id="80957-110">Você poderá chamar <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> se precisar esperar até que o thread seja encerrado.</span><span class="sxs-lookup"><span data-stu-id="80957-110">You can call <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> if you need to wait until the thread has ended.</span></span> <span data-ttu-id="80957-111"><xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> é uma chamada de bloqueio que não retorna até que o thread realmente tenha parado de executar ou um intervalo de tempo limite opcional tenha transcorrido.</span><span class="sxs-lookup"><span data-stu-id="80957-111"><xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> is a blocking call that does not return until the thread has actually stopped executing or an optional timeout interval has elapsed.</span></span> <span data-ttu-id="80957-112">O thread anulado poderia chamar o método <xref:System.Threading.Thread.ResetAbort%2A> ou executar o processamento não associado em um bloqueio `finally`, então se você não especificar um tempo limite, não será garantido o término da espera.</span><span class="sxs-lookup"><span data-stu-id="80957-112">The aborted thread could call the <xref:System.Threading.Thread.ResetAbort%2A> method or perform unbounded processing in a `finally` block, so if you do not specify a timeout, the wait is not guaranteed to end.</span></span>  
  
 <span data-ttu-id="80957-113">Os threads que estão aguardando uma chamada para o método <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> podem ser interrompidos por outros threads de chamam <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="80957-113">Threads that are waiting on a call to the <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> method can be interrupted by other threads that call <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType>.</span></span>  
  
## <a name="handling-threadabortexception"></a><span data-ttu-id="80957-114">Como lidar com a ThreadAbortException</span><span class="sxs-lookup"><span data-stu-id="80957-114">Handling ThreadAbortException</span></span>  
 <span data-ttu-id="80957-115">Se você espera que o thread seja anulado, como resultado de uma chamada a <xref:System.Threading.Thread.Abort%2A> de seu próprio código, ou como resultado do descarregamento de um domínio de aplicativo no qual o thread está em execução (<xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> usa <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> para encerrar os threads), o thread deverá tratar de <xref:System.Threading.ThreadAbortException> e executar qualquer processamento final em uma cláusula `finally`, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="80957-115">If you expect your thread to be aborted, either as a result of calling <xref:System.Threading.Thread.Abort%2A> from your own code or as a result of unloading an application domain in which the thread is running (<xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> uses <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> to terminate threads), your thread must handle the <xref:System.Threading.ThreadAbortException> and perform any final processing in a `finally` clause, as shown in the following code.</span></span>  
  
```vb  
Try  
    ' Code that is executing when the thread is aborted.  
Catch ex As ThreadAbortException  
    ' Clean-up code can go here.  
    ' If there is no Finally clause, ThreadAbortException is  
    ' re-thrown by the system at the end of the Catch clause.   
Finally  
    ' Clean-up code can go here.  
End Try  
' Do not put clean-up code here, because the exception   
' is rethrown at the end of the Finally clause.  
```  
  
```csharp  
try   
{  
    // Code that is executing when the thread is aborted.  
}   
catch (ThreadAbortException ex)   
{  
    // Clean-up code can go here.  
    // If there is no Finally clause, ThreadAbortException is  
    // re-thrown by the system at the end of the Catch clause.   
}  
// Do not put clean-up code here, because the exception   
// is rethrown at the end of the Finally clause.  
```  
  
 <span data-ttu-id="80957-116">Seu código de limpeza deve estar na cláusula `catch` ou na cláusula `finally`, porque uma <xref:System.Threading.ThreadAbortException> é lançada novamente pelo sistema no final da cláusula `finally` ou no final da cláusula `catch` se não houver nenhuma cláusula `finally`.</span><span class="sxs-lookup"><span data-stu-id="80957-116">Your clean-up code must be in the `catch` clause or the `finally` clause, because a <xref:System.Threading.ThreadAbortException> is rethrown by the system at the end of the `finally` clause, or at the end of the `catch` clause if there is no `finally` clause.</span></span>  
  
 <span data-ttu-id="80957-117">Você pode impedir que o sistema relance a exceção chamando o método <xref:System.Threading.Thread.ResetAbort%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="80957-117">You can prevent the system from rethrowing the exception by calling the <xref:System.Threading.Thread.ResetAbort%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="80957-118">No entanto, você deve fazer isso apenas se seu próprio código tiver causado a <xref:System.Threading.ThreadAbortException>.</span><span class="sxs-lookup"><span data-stu-id="80957-118">However, you should do this only if your own code caused the <xref:System.Threading.ThreadAbortException>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80957-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="80957-119">See also</span></span>

- <xref:System.Threading.ThreadAbortException>
- <xref:System.Threading.Thread>
- [<span data-ttu-id="80957-120">Usando threads e threading</span><span class="sxs-lookup"><span data-stu-id="80957-120">Using Threads and Threading</span></span>](../../../docs/standard/threading/using-threads-and-threading.md)
