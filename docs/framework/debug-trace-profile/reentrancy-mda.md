---
title: MDA reentrancy
description: Examine o MDA de reentrância, que poderá ser ativado se o heap de objeto estiver corrompido ou se outros erros graves ocorrerem ao fazer a transição de código nativo para o gerenciado.
ms.date: 03/30/2017
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
ms.openlocfilehash: f666e505b8382b0bec8dcfdb34c775850e46c429
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85803099"
---
# <a name="reentrancy-mda"></a><span data-ttu-id="5aa00-103">MDA reentrancy</span><span class="sxs-lookup"><span data-stu-id="5aa00-103">reentrancy MDA</span></span>
<span data-ttu-id="5aa00-104">O MDA (Assistente de Depuração Gerenciado) de `reentrancy` é ativado quando é feita uma tentativa de transição de código nativo para gerenciado em casos nos quais um comutador anterior do código gerenciado para nativo não foi executado por meio de uma transição ordenada.</span><span class="sxs-lookup"><span data-stu-id="5aa00-104">The `reentrancy` managed debugging assistant (MDA) is activated when an attempt is made to transition from native to managed code in cases where a prior switch from managed to native code was not performed through an orderly transition.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="5aa00-105">Sintomas</span><span class="sxs-lookup"><span data-stu-id="5aa00-105">Symptoms</span></span>  
 <span data-ttu-id="5aa00-106">O heap do objeto está corrompido ou outros erros graves estão ocorrendo durante a transição de código nativo para gerenciado.</span><span class="sxs-lookup"><span data-stu-id="5aa00-106">The object heap is corrupted or other serious errors are occurring when transitioning from native to managed code.</span></span>  
  
 <span data-ttu-id="5aa00-107">Threads que alternam entre o código nativo e o gerenciado em qualquer direção devem realizar uma transição ordenada.</span><span class="sxs-lookup"><span data-stu-id="5aa00-107">Threads that switch between native and managed code in either direction must perform an orderly transition.</span></span> <span data-ttu-id="5aa00-108">No entanto, certos pontos de extensibilidade de nível inferior no sistema operacional, tais como o manipulador de exceção em vetor, permitem mudanças de código gerenciado para código nativo sem realizar uma transição ordenada.</span><span class="sxs-lookup"><span data-stu-id="5aa00-108">However, certain low-level extensibility points in the operating system, such as the vectored exception handler, allow switches from managed to native code without performing an orderly transition.</span></span>  <span data-ttu-id="5aa00-109">Essas opções estão sob controle do sistema operacional, em vez de sob o controle do CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="5aa00-109">These switches are under operating system control, rather than under common language runtime (CLR) control.</span></span>  <span data-ttu-id="5aa00-110">Qualquer código nativo executado dentro desses pontos de extensibilidade deve evitar retornar a chamada para o código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="5aa00-110">Any native code that executes inside these extensibility points must avoid calling back into managed code.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="5aa00-111">Causa</span><span class="sxs-lookup"><span data-stu-id="5aa00-111">Cause</span></span>  
 <span data-ttu-id="5aa00-112">Um ponto de extensibilidade do sistema de operacional de baixo nível, tal como o manipulador de exceção em vetor, foi ativado durante a execução de código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="5aa00-112">A low-level operating system extensibility point, such as the vectored exception handler, has activated while executing managed code.</span></span>  <span data-ttu-id="5aa00-113">O código do aplicativo que é invocado por meio desse ponto de extensibilidade está tentando retornar a chamada para o código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="5aa00-113">The application code that is invoked through that extensibility point is attempting to call back into managed code.</span></span>  
  
 <span data-ttu-id="5aa00-114">Esse problema é sempre causado pelo código do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5aa00-114">This problem is always caused by application code.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="5aa00-115">Resolução</span><span class="sxs-lookup"><span data-stu-id="5aa00-115">Resolution</span></span>  
 <span data-ttu-id="5aa00-116">Examine o rastreamento de pilha do thread que ativou esse MDA.</span><span class="sxs-lookup"><span data-stu-id="5aa00-116">Examine the stack trace for the thread that has activated this MDA.</span></span>  <span data-ttu-id="5aa00-117">O thread está tentando fazer uma chamada ilegal para o código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="5aa00-117">The thread is attempting to illegally call into managed code.</span></span>  <span data-ttu-id="5aa00-118">O rastreamento de pilha deve revelar o código do aplicativo usando esse ponto de extensibilidade, o código de sistema operacional que fornece esse ponto de extensibilidade e o código gerenciado que foi interrompido pelo ponto de extensibilidade.</span><span class="sxs-lookup"><span data-stu-id="5aa00-118">The stack trace should reveal the application code using this extensibility point, the operating system code that provides this extensibility point, and the managed code that was interrupted by the extensibility point.</span></span>  
  
 <span data-ttu-id="5aa00-119">Por exemplo, você verá o MDA ativado em uma tentativa de chamar código gerenciado de dentro de um manipulador de exceção em vetor.</span><span class="sxs-lookup"><span data-stu-id="5aa00-119">For example, you will see the MDA activated in an attempt to call managed code from inside a vectored exception handler.</span></span>  <span data-ttu-id="5aa00-120">Na pilha, você verá o código de tratamento de exceção do sistema operacional e algum código gerenciado disparando uma exceção, tal como uma <xref:System.DivideByZeroException> ou uma <xref:System.AccessViolationException>.</span><span class="sxs-lookup"><span data-stu-id="5aa00-120">On the stack you will see the operating system exception handling code and some managed code triggering an exception such as a <xref:System.DivideByZeroException> or an <xref:System.AccessViolationException>.</span></span>  
  
 <span data-ttu-id="5aa00-121">Neste exemplo, a resolução correta é implementar o manipulador de exceção em vetor completamente em código não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="5aa00-121">In this example, the correct resolution is to implement the vectored exception handler completely in unmanaged code.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="5aa00-122">Efeito sobre o runtime</span><span class="sxs-lookup"><span data-stu-id="5aa00-122">Effect on the Runtime</span></span>  
 <span data-ttu-id="5aa00-123">Esse MDA não tem efeito sobre o CLR.</span><span class="sxs-lookup"><span data-stu-id="5aa00-123">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="5aa00-124">Saída</span><span class="sxs-lookup"><span data-stu-id="5aa00-124">Output</span></span>  
 <span data-ttu-id="5aa00-125">O MDA informa que está ocorrendo uma tentativa de reentrada ilegal.</span><span class="sxs-lookup"><span data-stu-id="5aa00-125">The MDA reports that illegal reentrancy is being attempted.</span></span>  <span data-ttu-id="5aa00-126">Examine a pilha do thread para determinar por que isso está acontecendo e como corrigir o problema.</span><span class="sxs-lookup"><span data-stu-id="5aa00-126">Examine the thread's stack to determine why this is happening and how to correct the problem.</span></span> <span data-ttu-id="5aa00-127">O demonstrado a seguir é uma saída de exemplo.</span><span class="sxs-lookup"><span data-stu-id="5aa00-127">The following is sample output.</span></span>  
  
```output
Additional Information: Attempting to call into managed code without
transitioning out first.  Do not attempt to run managed code inside
low-level native extensibility points. Managed Debugging Assistant
'Reentrancy' has detected a problem in 'D:\ConsoleApplication1\  
ConsoleApplication1\bin\Debug\ConsoleApplication1.vshost.exe'.  
```  
  
## <a name="configuration"></a><span data-ttu-id="5aa00-128">Configuração</span><span class="sxs-lookup"><span data-stu-id="5aa00-128">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <reentrancy />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="5aa00-129">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5aa00-129">Example</span></span>  
 <span data-ttu-id="5aa00-130">O código de exemplo a seguir faz com que uma <xref:System.AccessViolationException> seja lançada.</span><span class="sxs-lookup"><span data-stu-id="5aa00-130">The following code example causes an <xref:System.AccessViolationException> to be thrown.</span></span>  <span data-ttu-id="5aa00-131">Em versões do Windows que dão suporte à manipulação de exceção em vetor, isso fará com que o manipulador de exceção em vetor gerenciado seja chamado.</span><span class="sxs-lookup"><span data-stu-id="5aa00-131">On versions of Windows that support vectored exception handling, this will cause the managed vectored exception handler to be called.</span></span>  <span data-ttu-id="5aa00-132">Se o MDA `reentrancy` estiver habilitado, o MDA será ativado durante a tentativa de chamada para `MyHandler` do código de suporte de manipulação de exceção em vetor do sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="5aa00-132">If the `reentrancy` MDA is enabled, the MDA will activate during the attempted call to `MyHandler` from the operating system's vectored exception handling support code.</span></span>  
  
```csharp
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
  
## <a name="see-also"></a><span data-ttu-id="5aa00-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5aa00-133">See also</span></span>

- [<span data-ttu-id="5aa00-134">Diagnosticando erros com assistentes para depuração gerenciada</span><span class="sxs-lookup"><span data-stu-id="5aa00-134">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
