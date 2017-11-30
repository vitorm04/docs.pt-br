---
title: Destruindo threads
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
helpviewer_keywords:
- destroying threads
- threading [.NET Framework], destroying threads
ms.assetid: df54e648-c5d1-47c9-bd29-8e4438c1db6d
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4a41dce5db707d0be49c283256de665d316e1a1f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="destroying-threads"></a><span data-ttu-id="8ff32-102">Destruindo threads</span><span class="sxs-lookup"><span data-stu-id="8ff32-102">Destroying Threads</span></span>
<span data-ttu-id="8ff32-103">O <xref:System.Threading.Thread.Abort%2A> método é usado para interromper um thread gerenciado permanentemente.</span><span class="sxs-lookup"><span data-stu-id="8ff32-103">The <xref:System.Threading.Thread.Abort%2A> method is used to stop a managed thread permanently.</span></span> <span data-ttu-id="8ff32-104">Quando você chama <xref:System.Threading.Thread.Abort%2A>, o common language runtime lança um <xref:System.Threading.ThreadAbortException> no thread de destino, pode capturar o thread de destino.</span><span class="sxs-lookup"><span data-stu-id="8ff32-104">When you call <xref:System.Threading.Thread.Abort%2A>, the common language runtime throws a <xref:System.Threading.ThreadAbortException> in the target thread, which the target thread can catch.</span></span> <span data-ttu-id="8ff32-105">Para obter mais informações, consulte <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8ff32-105">For more information, see <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8ff32-106">Se estiver executando um thread não gerenciado de código ao seu <xref:System.Threading.Thread.Abort%2A> método é chamado, o tempo de execução a marca <xref:System.Threading.ThreadState.AbortRequested?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8ff32-106">If a thread is executing unmanaged code when its <xref:System.Threading.Thread.Abort%2A> method is called, the runtime marks it <xref:System.Threading.ThreadState.AbortRequested?displayProperty=nameWithType>.</span></span> <span data-ttu-id="8ff32-107">A exceção é lançada quando o thread retorna para código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="8ff32-107">The exception is thrown when the thread returns to managed code.</span></span>  
  
 <span data-ttu-id="8ff32-108">Depois que um thread é interrompido, ele não pode ser reiniciado.</span><span class="sxs-lookup"><span data-stu-id="8ff32-108">Once a thread is aborted, it cannot be restarted.</span></span>  
  
 <span data-ttu-id="8ff32-109">O <xref:System.Threading.Thread.Abort%2A> método não faz com que o thread anular imediatamente, porque o thread de destino pode capturar o <xref:System.Threading.ThreadAbortException> e execute valores arbitrários de código em um `finally` bloco.</span><span class="sxs-lookup"><span data-stu-id="8ff32-109">The <xref:System.Threading.Thread.Abort%2A> method does not cause the thread to abort immediately, because the target thread can catch the <xref:System.Threading.ThreadAbortException> and execute arbitrary amounts of code in a `finally` block.</span></span> <span data-ttu-id="8ff32-110">Você pode chamar <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> se você precisa esperar até que o thread foi encerrada.</span><span class="sxs-lookup"><span data-stu-id="8ff32-110">You can call <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> if you need to wait until the thread has ended.</span></span> <span data-ttu-id="8ff32-111"><xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType>é uma chamada de bloqueio que não retorna até que o thread realmente parou de executar ou um intervalo de tempo limite opcional.</span><span class="sxs-lookup"><span data-stu-id="8ff32-111"><xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> is a blocking call that does not return until the thread has actually stopped executing or an optional timeout interval has elapsed.</span></span> <span data-ttu-id="8ff32-112">O thread anulado poderia chamar o <xref:System.Threading.Thread.ResetAbort%2A> método ou executar o processamento não associado em um `finally` bloquear, se você não especificar um tempo limite, o tempo de espera não é garantida para terminar.</span><span class="sxs-lookup"><span data-stu-id="8ff32-112">The aborted thread could call the <xref:System.Threading.Thread.ResetAbort%2A> method or perform unbounded processing in a `finally` block, so if you do not specify a timeout, the wait is not guaranteed to end.</span></span>  
  
 <span data-ttu-id="8ff32-113">Threads que estão aguardando em uma chamada para o <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> método pode ser interrompido por outros threads de chamam <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8ff32-113">Threads that are waiting on a call to the <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> method can be interrupted by other threads that call <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType>.</span></span>  
  
## <a name="handling-threadabortexception"></a><span data-ttu-id="8ff32-114">Tratamento de ThreadAbortException</span><span class="sxs-lookup"><span data-stu-id="8ff32-114">Handling ThreadAbortException</span></span>  
 <span data-ttu-id="8ff32-115">Se você espera que o thread de anulação, como resultado de uma chamada <xref:System.Threading.Thread.Abort%2A> de seu próprio código, ou como resultado de descarregar um domínio de aplicativo no qual o thread está em execução (<xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> usa <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> encerrar threads), o thread deve tratar o <xref:System.Threading.ThreadAbortException> e executar qualquer processamento final em um `finally` cláusula, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="8ff32-115">If you expect your thread to be aborted, either as a result of calling <xref:System.Threading.Thread.Abort%2A> from your own code or as a result of unloading an application domain in which the thread is running (<xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> uses <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> to terminate threads), your thread must handle the <xref:System.Threading.ThreadAbortException> and perform any final processing in a `finally` clause, as shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="8ff32-116">Seu código de limpeza deve ser no `catch` cláusula ou o `finally` cláusula, porque um <xref:System.Threading.ThreadAbortException> é lançada novamente pelo sistema no final do `finally` cláusula, ou no final do `catch` cláusula se não houver nenhum `finally` cláusula.</span><span class="sxs-lookup"><span data-stu-id="8ff32-116">Your clean-up code must be in the `catch` clause or the `finally` clause, because a <xref:System.Threading.ThreadAbortException> is rethrown by the system at the end of the `finally` clause, or at the end of the `catch` clause if there is no `finally` clause.</span></span>  
  
 <span data-ttu-id="8ff32-117">Você pode impedir que o sistema relançamento de exceção ao chamar o <xref:System.Threading.Thread.ResetAbort%2A?displayProperty=nameWithType> método.</span><span class="sxs-lookup"><span data-stu-id="8ff32-117">You can prevent the system from rethrowing the exception by calling the <xref:System.Threading.Thread.ResetAbort%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="8ff32-118">No entanto, você deve fazer isso apenas se seu próprio código causado o <xref:System.Threading.ThreadAbortException>.</span><span class="sxs-lookup"><span data-stu-id="8ff32-118">However, you should do this only if your own code caused the <xref:System.Threading.ThreadAbortException>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ff32-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8ff32-119">See Also</span></span>  
 <xref:System.Threading.ThreadAbortException>  
 <xref:System.Threading.Thread>  
 [<span data-ttu-id="8ff32-120">Usando threads e threading</span><span class="sxs-lookup"><span data-stu-id="8ff32-120">Using Threads and Threading</span></span>](../../../docs/standard/threading/using-threads-and-threading.md)
