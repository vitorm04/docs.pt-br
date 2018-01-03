---
title: MDA reentrancy
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- unmanaged code, debugging
- transitioning threads unmanaged to managed code
- reentrancy MDA
- reentrancy without an orderly transition
- managed debugging assistants (MDAs), reentrancy
- illegal reentrancy
- MDAs (managed debugging assistants), reentrancy
- threading [.NET Framework], managed debugging assistants
- managed code, debugging
- native debugging, MDAs
ms.assetid: 7240c3f3-7df8-4b03-bbf1-17cdce142d45
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a305658068e6d59f27957879c053b18742ea642f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="reentrancy-mda"></a><span data-ttu-id="347a1-102">MDA reentrancy</span><span class="sxs-lookup"><span data-stu-id="347a1-102">reentrancy MDA</span></span>
<span data-ttu-id="347a1-103">O MDA (Assistente de Depuração Gerenciado) de `reentrancy` é ativado quando é feita uma tentativa de transição de código nativo para gerenciado em casos nos quais um comutador anterior do código gerenciado para nativo não foi executado por meio de uma transição ordenada.</span><span class="sxs-lookup"><span data-stu-id="347a1-103">The `reentrancy` managed debugging assistant (MDA) is activated when an attempt is made to transition from native to managed code in cases where a prior switch from managed to native code was not performed through an orderly transition.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="347a1-104">Sintomas</span><span class="sxs-lookup"><span data-stu-id="347a1-104">Symptoms</span></span>  
 <span data-ttu-id="347a1-105">O heap do objeto está corrompido ou outros erros graves estão ocorrendo durante a transição de código nativo para gerenciado.</span><span class="sxs-lookup"><span data-stu-id="347a1-105">The object heap is corrupted or other serious errors are occurring when transitioning from native to managed code.</span></span>  
  
 <span data-ttu-id="347a1-106">Threads que alternam entre o código nativo e o gerenciado em qualquer direção devem realizar uma transição ordenada.</span><span class="sxs-lookup"><span data-stu-id="347a1-106">Threads that switch between native and managed code in either direction must perform an orderly transition.</span></span> <span data-ttu-id="347a1-107">No entanto, certos pontos de extensibilidade de nível inferior no sistema operacional, tais como o manipulador de exceção em vetor, permitem mudanças de código gerenciado para código nativo sem realizar uma transição ordenada.</span><span class="sxs-lookup"><span data-stu-id="347a1-107">However, certain low-level extensibility points in the operating system, such as the vectored exception handler, allow switches from managed to native code without performing an orderly transition.</span></span>  <span data-ttu-id="347a1-108">Essas opções estão sob controle do sistema operacional, em vez de sob o controle do CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="347a1-108">These switches are under operating system control, rather than under common language runtime (CLR) control.</span></span>  <span data-ttu-id="347a1-109">Qualquer código nativo executado dentro desses pontos de extensibilidade deve evitar retornar a chamada para o código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="347a1-109">Any native code that executes inside these extensibility points must avoid calling back into managed code.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="347a1-110">Causa</span><span class="sxs-lookup"><span data-stu-id="347a1-110">Cause</span></span>  
 <span data-ttu-id="347a1-111">Um ponto de extensibilidade do sistema de operacional de baixo nível, tal como o manipulador de exceção em vetor, foi ativado durante a execução de código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="347a1-111">A low-level operating system extensibility point, such as the vectored exception handler, has activated while executing managed code.</span></span>  <span data-ttu-id="347a1-112">O código do aplicativo que é invocado por meio desse ponto de extensibilidade está tentando retornar a chamada para o código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="347a1-112">The application code that is invoked through that extensibility point is attempting to call back into managed code.</span></span>  
  
 <span data-ttu-id="347a1-113">Esse problema é sempre causado pelo código do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="347a1-113">This problem is always caused by application code.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="347a1-114">Resolução</span><span class="sxs-lookup"><span data-stu-id="347a1-114">Resolution</span></span>  
 <span data-ttu-id="347a1-115">Examine o rastreamento de pilha do thread que ativou esse MDA.</span><span class="sxs-lookup"><span data-stu-id="347a1-115">Examine the stack trace for the thread that has activated this MDA.</span></span>  <span data-ttu-id="347a1-116">O thread está tentando fazer uma chamada ilegal para o código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="347a1-116">The thread is attempting to illegally call into managed code.</span></span>  <span data-ttu-id="347a1-117">O rastreamento de pilha deve revelar o código do aplicativo usando esse ponto de extensibilidade, o código de sistema operacional que fornece esse ponto de extensibilidade e o código gerenciado que foi interrompido pelo ponto de extensibilidade.</span><span class="sxs-lookup"><span data-stu-id="347a1-117">The stack trace should reveal the application code using this extensibility point, the operating system code that provides this extensibility point, and the managed code that was interrupted by the extensibility point.</span></span>  
  
 <span data-ttu-id="347a1-118">Por exemplo, você verá o MDA ativado em uma tentativa de chamar código gerenciado de dentro de um manipulador de exceção em vetor.</span><span class="sxs-lookup"><span data-stu-id="347a1-118">For example, you will see the MDA activated in an attempt to call managed code from inside a vectored exception handler.</span></span>  <span data-ttu-id="347a1-119">Na pilha, você verá o código de tratamento de exceção do sistema operacional e algum código gerenciado disparando uma exceção, tal como uma <xref:System.DivideByZeroException> ou uma <xref:System.AccessViolationException>.</span><span class="sxs-lookup"><span data-stu-id="347a1-119">On the stack you will see the operating system exception handling code and some managed code triggering an exception such as a <xref:System.DivideByZeroException> or an <xref:System.AccessViolationException>.</span></span>  
  
 <span data-ttu-id="347a1-120">Neste exemplo, a resolução correta é implementar o manipulador de exceção em vetor completamente em código não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="347a1-120">In this example, the correct resolution is to implement the vectored exception handler completely in unmanaged code.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="347a1-121">Efeito sobre o tempo de execução</span><span class="sxs-lookup"><span data-stu-id="347a1-121">Effect on the Runtime</span></span>  
 <span data-ttu-id="347a1-122">Esse MDA não tem efeito sobre o CLR.</span><span class="sxs-lookup"><span data-stu-id="347a1-122">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="347a1-123">Saída</span><span class="sxs-lookup"><span data-stu-id="347a1-123">Output</span></span>  
 <span data-ttu-id="347a1-124">O MDA informa que está ocorrendo uma tentativa de reentrada ilegal.</span><span class="sxs-lookup"><span data-stu-id="347a1-124">The MDA reports that illegal reentrancy is being attempted.</span></span>  <span data-ttu-id="347a1-125">Examine a pilha do thread para determinar por que isso está acontecendo e como corrigir o problema.</span><span class="sxs-lookup"><span data-stu-id="347a1-125">Examine the thread's stack to determine why this is happening and how to correct the problem.</span></span> <span data-ttu-id="347a1-126">O demonstrado a seguir é uma saída de exemplo.</span><span class="sxs-lookup"><span data-stu-id="347a1-126">The following is sample output.</span></span>  
  
```  
Additional Information: Attempting to call into managed code without   
transitioning out first.  Do not attempt to run managed code inside   
low-level native extensibility points. Managed Debugging Assistant   
'Reentrancy' has detected a problem in 'D:\ConsoleApplication1\  
ConsoleApplication1\bin\Debug\ConsoleApplication1.vshost.exe'.  
```  
  
## <a name="configuration"></a><span data-ttu-id="347a1-127">Configuração</span><span class="sxs-lookup"><span data-stu-id="347a1-127">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <reentrancy />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="347a1-128">Exemplo</span><span class="sxs-lookup"><span data-stu-id="347a1-128">Example</span></span>  
 <span data-ttu-id="347a1-129">O código de exemplo a seguir faz com que uma <xref:System.AccessViolationException> seja lançada.</span><span class="sxs-lookup"><span data-stu-id="347a1-129">The following code example causes an <xref:System.AccessViolationException> to be thrown.</span></span>  <span data-ttu-id="347a1-130">Em versões do Windows que dão suporte à manipulação de exceção em vetor, isso fará com que o manipulador de exceção em vetor gerenciado seja chamado.</span><span class="sxs-lookup"><span data-stu-id="347a1-130">On versions of Windows that support vectored exception handling, this will cause the managed vectored exception handler to be called.</span></span>  <span data-ttu-id="347a1-131">Se o MDA `reentrancy` estiver habilitado, o MDA será ativado durante a tentativa de chamada para `MyHandler` do código de suporte de manipulação de exceção em vetor do sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="347a1-131">If the `reentrancy` MDA is enabled, the MDA will activate during the attempted call to `MyHandler` from the operating system's vectored exception handling support code.</span></span>  
  
```  
using System;  
public delegate int ExceptionHandler(IntPtr ptrExceptionInfo);  
  
public class Reenter   
{  
    public static ExceptionHandler keepAlive;  
  
    [System.Runtime.InteropServices.DllImport("kernel32", ExactSpelling=true,   
        CharSet=System.Runtime.InteropServices.CharSet.Auto)]  
    public static extern IntPtr AddVectoredExceptionHandler(int bFirst,   
        ExceptionHandler handler);  
  
    static int MyHandler(IntPtr ptrExceptionInfo)   
    {  
        // EXCEPTION_CONTINUE_SEARCH  
        return 0;  
    }  
    void Run() {}  
  
    static void Main()   
    {  
        keepAlive = new ExceptionHandler(Reenter.MyHandler);  
        IntPtr ret = AddVectoredExceptionHandler(1, keepAlive);  
        try   
        {  
            // Dispatch on null should AV.  
            Reenter r = null;   
            r.Run();  
        }   
        catch { }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="347a1-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="347a1-132">See Also</span></span>  
 [<span data-ttu-id="347a1-133">Diagnosticando erros com Assistentes de Depuração Gerenciados</span><span class="sxs-lookup"><span data-stu-id="347a1-133">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
