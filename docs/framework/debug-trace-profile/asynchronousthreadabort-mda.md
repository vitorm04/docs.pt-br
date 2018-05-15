---
title: MDA asynchronousThreadAbort
ms.date: 03/30/2017
helpviewer_keywords:
- asynchronous thread aborts
- AsynchronousThreadAbort MDA
- managed debugging assistants (MDAs), asynchronous thread aborts
- threading [.NET Framework], managed debugging assistants
- MDAs (managed debugging assistants), asynchronous thread aborts
ms.assetid: 9ebe40b2-d703-421e-8660-984acc42bfe0
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fd759a4167a667919a443bc6492c049631ad222c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="asynchronousthreadabort-mda"></a><span data-ttu-id="621b4-102">MDA asynchronousThreadAbort</span><span class="sxs-lookup"><span data-stu-id="621b4-102">asynchronousThreadAbort MDA</span></span>
<span data-ttu-id="621b4-103">O MDA (assistente para depuração gerenciada) `asynchronousThreadAbort` é ativado quando um thread tenta introduzir uma anulação assíncrona em outro thread.</span><span class="sxs-lookup"><span data-stu-id="621b4-103">The `asynchronousThreadAbort` managed debugging assistant (MDA) is activated when a thread attempts to introduce an asynchronous abort into another thread.</span></span> <span data-ttu-id="621b4-104">Anulações de thread síncronas não ativam o MDA `asynchronousThreadAbort`.</span><span class="sxs-lookup"><span data-stu-id="621b4-104">Synchronous thread aborts do not activate the `asynchronousThreadAbort` MDA.</span></span>

## <a name="symptoms"></a><span data-ttu-id="621b4-105">Sintomas</span><span class="sxs-lookup"><span data-stu-id="621b4-105">Symptoms</span></span>
 <span data-ttu-id="621b4-106">Um aplicativo falha com uma <xref:System.Threading.ThreadAbortException> sem tratamento quando o thread do aplicativo principal é anulado.</span><span class="sxs-lookup"><span data-stu-id="621b4-106">An application crashes with an unhandled <xref:System.Threading.ThreadAbortException> when the main application thread is aborted.</span></span> <span data-ttu-id="621b4-107">Se o aplicativo precisar continuar sendo executado, as consequências poderão ser piores do que uma falha do aplicativo, possivelmente resultando em mais dados corrompidos.</span><span class="sxs-lookup"><span data-stu-id="621b4-107">If the application were to continue to execute, the consequences might be worse than the application crashing, possibly resulting in further data corruption.</span></span>

 <span data-ttu-id="621b4-108">As operações que devem ser atômicas provavelmente foram interrompidas após a conclusão parcial, deixando os dados do aplicativo em um estado imprevisível.</span><span class="sxs-lookup"><span data-stu-id="621b4-108">Operations meant to be atomic have likely been interrupted after partial completion, leaving application data in an unpredictable state.</span></span> <span data-ttu-id="621b4-109">Uma <xref:System.Threading.ThreadAbortException> pode ser gerada com base em pontos aparentemente aleatórios na execução do código, geralmente em locais dos quais uma exceção não deve surgir.</span><span class="sxs-lookup"><span data-stu-id="621b4-109">A <xref:System.Threading.ThreadAbortException> can be generated from seemingly random points in the execution of code, often in places from which an exception is not expected to arise.</span></span> <span data-ttu-id="621b4-110">O código pode não ter a capacidade de manipular uma exceção como essa, resultando em um estado corrompido.</span><span class="sxs-lookup"><span data-stu-id="621b4-110">The code might not be capable of handling such an exception, resulting in a corrupt state.</span></span>

 <span data-ttu-id="621b4-111">Os sintomas podem variar muito devido à aleatoriedade inerente ao problema.</span><span class="sxs-lookup"><span data-stu-id="621b4-111">Symptoms can vary widely due to the randomness inherent to the problem.</span></span>

## <a name="cause"></a><span data-ttu-id="621b4-112">Causa</span><span class="sxs-lookup"><span data-stu-id="621b4-112">Cause</span></span>
 <span data-ttu-id="621b4-113">O código em um thread chamou o método <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> em um thread de destino para introduzir uma anulação de thread assíncrona.</span><span class="sxs-lookup"><span data-stu-id="621b4-113">Code in one thread called the <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> method on a target thread to introduce an asynchronous thread abort.</span></span> <span data-ttu-id="621b4-114">A anulação de thread é assíncrona porque o código que faz a chamada a <xref:System.Threading.Thread.Abort%2A> está em execução em um thread diferente do que o destino da operação de anulação.</span><span class="sxs-lookup"><span data-stu-id="621b4-114">The thread abort is asynchronous because the code that makes the call to <xref:System.Threading.Thread.Abort%2A> is running on a different thread than the target of the abort operation.</span></span> <span data-ttu-id="621b4-115">As anulações de thread síncronas não devem causar um problema porque o thread que executa a <xref:System.Threading.Thread.Abort%2A> deveria ter feito isso somente em um ponto de verificação seguro em que o estado do aplicativo é consistente.</span><span class="sxs-lookup"><span data-stu-id="621b4-115">Synchronous thread aborts should not cause a problem because the thread performing the <xref:System.Threading.Thread.Abort%2A> should have done so only at a safe checkpoint where application state is consistent.</span></span>

 <span data-ttu-id="621b4-116">Anulações de thread assíncrono apresentam um problema porque são processadas em pontos imprevisíveis na execução do thread de destino.</span><span class="sxs-lookup"><span data-stu-id="621b4-116">Asynchronous thread aborts present a problem because they are processed at unpredictable points in the target thread's execution.</span></span> <span data-ttu-id="621b4-117">Para evitar isso, o código escrito para ser executado em um thread que pode ser anulado dessa maneira precisará manipular uma <xref:System.Threading.ThreadAbortException> em quase todas as linhas de código, tomando cuidado para colocar os dados do aplicativo novamente em um estado consistente.</span><span class="sxs-lookup"><span data-stu-id="621b4-117">To avoid this, code written to run on a thread that might be aborted in this manner would need to handle a <xref:System.Threading.ThreadAbortException> at almost every line of code, taking care to put application data back into a consistent state.</span></span> <span data-ttu-id="621b4-118">Não é realista esperar que o código seja escrito com esse problema em mente ou escrever um código que proteja contra todas as circunstâncias possíveis.</span><span class="sxs-lookup"><span data-stu-id="621b4-118">It is not realistic to expect code to be written with this problem in mind or to write code that protects against all possible circumstances.</span></span>

 <span data-ttu-id="621b4-119">As chamadas no código não gerenciado e os blocos `finally` não serão anulados de forma assíncrona, mas imediatamente após a saída de uma dessas categorias.</span><span class="sxs-lookup"><span data-stu-id="621b4-119">Calls into unmanaged code and `finally` blocks will not be aborted asynchronously but immediately upon exit from one of these categories.</span></span>

 <span data-ttu-id="621b4-120">A causa pode ser difícil de ser determinada devido à aleatoriedade inerente ao problema.</span><span class="sxs-lookup"><span data-stu-id="621b4-120">The cause might be difficult to determine due to the randomness inherent to the problem.</span></span>

## <a name="resolution"></a><span data-ttu-id="621b4-121">Resolução</span><span class="sxs-lookup"><span data-stu-id="621b4-121">Resolution</span></span>
 <span data-ttu-id="621b4-122">Evite o design de código que exige o uso de anulações de thread assíncronas.</span><span class="sxs-lookup"><span data-stu-id="621b4-122">Avoid code design that requires the use of asynchronous thread aborts.</span></span> <span data-ttu-id="621b4-123">Há várias abordagens mais apropriadas para a interrupção de um thread de destino que não exigem uma chamada a <xref:System.Threading.Thread.Abort%2A>.</span><span class="sxs-lookup"><span data-stu-id="621b4-123">There are several approaches more appropriate for interruption of a target thread that do not require a call to <xref:System.Threading.Thread.Abort%2A>.</span></span> <span data-ttu-id="621b4-124">A mais segura é introduzir um mecanismo, como uma propriedade comum, que sinaliza o thread de destino a solicitar uma interrupção.</span><span class="sxs-lookup"><span data-stu-id="621b4-124">The safest is to introduce a mechanism, such as a common property, that signals the target thread to request an interrupt.</span></span> <span data-ttu-id="621b4-125">O thread de destino verifica o sinal em determinados pontos de verificação seguros.</span><span class="sxs-lookup"><span data-stu-id="621b4-125">The target thread checks the signal at certain safe checkpoints.</span></span> <span data-ttu-id="621b4-126">Se ele observa que uma interrupção foi solicitada, ele pode ser desligado normalmente.</span><span class="sxs-lookup"><span data-stu-id="621b4-126">If it notices that an interrupt has been requested, it can shut down gracefully.</span></span>

## <a name="effect-on-the-runtime"></a><span data-ttu-id="621b4-127">Efeito sobre o tempo de execução</span><span class="sxs-lookup"><span data-stu-id="621b4-127">Effect on the Runtime</span></span>
 <span data-ttu-id="621b4-128">Esse MDA não tem efeito sobre o CLR.</span><span class="sxs-lookup"><span data-stu-id="621b4-128">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="621b4-129">Ele apenas relata dados sobre as anulações de thread assíncronas.</span><span class="sxs-lookup"><span data-stu-id="621b4-129">It only reports data about asynchronous thread aborts.</span></span>

## <a name="output"></a><span data-ttu-id="621b4-130">Saída</span><span class="sxs-lookup"><span data-stu-id="621b4-130">Output</span></span>
 <span data-ttu-id="621b4-131">O MDA relata a ID do thread que executa a anulação e a ID do thread que é o destino da anulação.</span><span class="sxs-lookup"><span data-stu-id="621b4-131">The MDA reports the ID of the thread performing the abort and the ID of the thread that is the target of the abort.</span></span> <span data-ttu-id="621b4-132">Elas nunca serão as mesmas porque isso é limitado a anulações assíncronas.</span><span class="sxs-lookup"><span data-stu-id="621b4-132">These will never be the same because this is limited to asynchronous aborts.</span></span>

## <a name="configuration"></a><span data-ttu-id="621b4-133">Configuração</span><span class="sxs-lookup"><span data-stu-id="621b4-133">Configuration</span></span>

```xml
<mdaConfig>
  <assistants>
    <asynchronousThreadAbort />
  </assistants>
</mdaConfig>
```

## <a name="example"></a><span data-ttu-id="621b4-134">Exemplo</span><span class="sxs-lookup"><span data-stu-id="621b4-134">Example</span></span>
 <span data-ttu-id="621b4-135">A ativação do MDA `asynchronousThreadAbort` exige apenas uma chamada a <xref:System.Threading.Thread.Abort%2A> em um thread de execução separado.</span><span class="sxs-lookup"><span data-stu-id="621b4-135">Activating the `asynchronousThreadAbort` MDA requires only a call to <xref:System.Threading.Thread.Abort%2A> on a separate running thread.</span></span> <span data-ttu-id="621b4-136">Considere as consequências se o conteúdo da função de início do thread fosse um conjunto de operações mais complexas que poderiam ser interrompidas em qualquer ponto arbitrário pela anulação.</span><span class="sxs-lookup"><span data-stu-id="621b4-136">Consider the consequences if the contents of the thread start function were a set of more complex operations which might be interrupted at any arbitrary point by the abort.</span></span>

```csharp
using System.Threading;
void FireMda()
{
    Thread t = new Thread(delegate() { Thread.Sleep(1000); });
    t.Start();
    // The following line activates the MDA.
    t.Abort();
    t.Join();
}
```

## <a name="see-also"></a><span data-ttu-id="621b4-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="621b4-137">See Also</span></span>
 <span data-ttu-id="621b4-138"><xref:System.Threading.Thread> [Diagnosticando erros com assistentes para depuração gerenciada](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)</span><span class="sxs-lookup"><span data-stu-id="621b4-138"><xref:System.Threading.Thread> [Diagnosing Errors with Managed Debugging Assistants](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)</span></span>
