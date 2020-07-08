---
title: MDA illegalPrepareConstrainedRegion
description: Examine o assistente de depuração gerenciada do illegalPrepareConstrainedRegion, que é invocado se uma chamada PrepareConstrainedRegions não é seguida por uma instrução try.
ms.date: 03/30/2017
helpviewer_keywords:
- PrepareConstrainedRegions method
- managed debugging assistants (MDAs), illegal PrepareConstrainedRegions
- try/catch exception handling, managed debugging assistants
- IllegalPrepareConstrainedRegions MDA
- MDAs (managed debugging assistants), illegal PrepareConstrainedRegions
ms.assetid: 2f9b5031-f910-4e01-a196-f89eab313eaf
ms.openlocfilehash: d6a0d1d95840ebd735806c5547730ae9e0b2aace
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: pt-BR
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051279"
---
# <a name="illegalprepareconstrainedregion-mda"></a><span data-ttu-id="12595-103">MDA illegalPrepareConstrainedRegion</span><span class="sxs-lookup"><span data-stu-id="12595-103">illegalPrepareConstrainedRegion MDA</span></span>
<span data-ttu-id="12595-104">O MDA (Assistente de Depuração Gerenciado) de `illegalPrepareConstrainedRegion` é ativado quando uma chamada de método <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A?displayProperty=nameWithType> não precede imediatamente a instrução `try` do manipulador de exceção.</span><span class="sxs-lookup"><span data-stu-id="12595-104">The `illegalPrepareConstrainedRegion` managed debugging assistant (MDA) is activated when a <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A?displayProperty=nameWithType> method call does not immediately precede the `try` statement of the exception handler.</span></span> <span data-ttu-id="12595-105">Essa restrição é em nível de MSIL, portanto, é possível ter uma origem não geradora de código entre a chamada e o `try`, assim como comentários.</span><span class="sxs-lookup"><span data-stu-id="12595-105">This restriction is at the MSIL level, so it is permissible to have non-code-generating source between the call and the `try`, such as comments.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="12595-106">Sintomas</span><span class="sxs-lookup"><span data-stu-id="12595-106">Symptoms</span></span>  
 <span data-ttu-id="12595-107">Uma região de execução restrita (CER) que nunca é tratada como tal, mas como uma bloco de tratamento de exceção simples (`finally` ou `catch`).</span><span class="sxs-lookup"><span data-stu-id="12595-107">A constrained execution region (CER) that is never treated as such, but as a simple exception handling block (`finally` or `catch`).</span></span> <span data-ttu-id="12595-108">Como consequência, a região não é executada no caso de uma condição de falta de memória ou uma anulação de thread.</span><span class="sxs-lookup"><span data-stu-id="12595-108">As a consequence, the region does not run in the event of an out-of-memory condition or a thread abort.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="12595-109">Causa</span><span class="sxs-lookup"><span data-stu-id="12595-109">Cause</span></span>  
 <span data-ttu-id="12595-110">O padrão de preparação para uma CER não é seguido corretamente.</span><span class="sxs-lookup"><span data-stu-id="12595-110">The preparation pattern for a CER is not followed correctly.</span></span>  <span data-ttu-id="12595-111">Isso é um evento de erro.</span><span class="sxs-lookup"><span data-stu-id="12595-111">This is an error event.</span></span> <span data-ttu-id="12595-112">A <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> chamada de método usada para marcar manipuladores de exceção como introdução a uma CER em seus `catch` / `finally` / `fault` / `filter` blocos deve ser usada imediatamente antes da `try` instrução.</span><span class="sxs-lookup"><span data-stu-id="12595-112">The <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> method call used to mark exception handlers as introducing a CER in their `catch`/`finally`/`fault`/`filter` blocks must be used immediately before the `try` statement.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="12595-113">Resolução</span><span class="sxs-lookup"><span data-stu-id="12595-113">Resolution</span></span>  
 <span data-ttu-id="12595-114">Certifique-se de que a chamada para <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> ocorre imediatamente antes da instrução `try`.</span><span class="sxs-lookup"><span data-stu-id="12595-114">Ensure that the call to <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> happens immediately before the `try` statement.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="12595-115">Efeito sobre o runtime</span><span class="sxs-lookup"><span data-stu-id="12595-115">Effect on the Runtime</span></span>  
 <span data-ttu-id="12595-116">Esse MDA não tem efeito sobre o CLR.</span><span class="sxs-lookup"><span data-stu-id="12595-116">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="12595-117">Saída</span><span class="sxs-lookup"><span data-stu-id="12595-117">Output</span></span>  
 <span data-ttu-id="12595-118">O MDA exibe o nome do método chamando o método <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A>, o deslocamento da MSIL e uma mensagem indicando que a chamada não precede imediatamente o início do bloco try.</span><span class="sxs-lookup"><span data-stu-id="12595-118">The MDA displays the name of the method calling the <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> method, the MSIL offset, and a message indicating the call does not immediately precede the beginning of the try block.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="12595-119">Configuração</span><span class="sxs-lookup"><span data-stu-id="12595-119">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <illegalPrepareConstrainedRegion/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="12595-120">Exemplo</span><span class="sxs-lookup"><span data-stu-id="12595-120">Example</span></span>  
 <span data-ttu-id="12595-121">O exemplo de código a seguir demonstra o padrão que faz com que esse MDA seja ativado.</span><span class="sxs-lookup"><span data-stu-id="12595-121">The following code example demonstrates the pattern that causes this MDA to be activated.</span></span>  
  
```csharp
void MethodWithInvalidPCR()  
{  
    RuntimeHelpers.PrepareConstrainedRegions();  
    Object o = new Object();  
    try  
    {  
        …  
    }  
    finally  
    {  
        …  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="12595-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="12595-122">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A>
- [<span data-ttu-id="12595-123">Diagnosticando erros com assistentes para depuração gerenciada</span><span class="sxs-lookup"><span data-stu-id="12595-123">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="12595-124">Realizando marshaling de interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="12595-124">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
