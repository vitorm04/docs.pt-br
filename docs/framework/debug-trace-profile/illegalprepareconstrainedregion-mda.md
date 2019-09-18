---
title: MDA illegalPrepareConstrainedRegion
ms.date: 03/30/2017
helpviewer_keywords:
- PrepareConstrainedRegions method
- managed debugging assistants (MDAs), illegal PrepareConstrainedRegions
- try/catch exception handling, managed debugging assistants
- IllegalPrepareConstrainedRegions MDA
- MDAs (managed debugging assistants), illegal PrepareConstrainedRegions
ms.assetid: 2f9b5031-f910-4e01-a196-f89eab313eaf
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 623aff91eb801b4b32fc180bd97ed3822ad7f163
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052672"
---
# <a name="illegalprepareconstrainedregion-mda"></a><span data-ttu-id="2369a-102">MDA illegalPrepareConstrainedRegion</span><span class="sxs-lookup"><span data-stu-id="2369a-102">illegalPrepareConstrainedRegion MDA</span></span>
<span data-ttu-id="2369a-103">O MDA (Assistente de Depuração Gerenciado) de `illegalPrepareConstrainedRegion` é ativado quando uma chamada de método <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A?displayProperty=nameWithType> não precede imediatamente a instrução `try` do manipulador de exceção.</span><span class="sxs-lookup"><span data-stu-id="2369a-103">The `illegalPrepareConstrainedRegion` managed debugging assistant (MDA) is activated when a <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A?displayProperty=nameWithType> method call does not immediately precede the `try` statement of the exception handler.</span></span> <span data-ttu-id="2369a-104">Essa restrição é em nível de MSIL, portanto, é possível ter uma origem não geradora de código entre a chamada e o `try`, assim como comentários.</span><span class="sxs-lookup"><span data-stu-id="2369a-104">This restriction is at the MSIL level, so it is permissible to have non-code-generating source between the call and the `try`, such as comments.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="2369a-105">Sintomas</span><span class="sxs-lookup"><span data-stu-id="2369a-105">Symptoms</span></span>  
 <span data-ttu-id="2369a-106">Uma região de execução restrita (CER) que nunca é tratada como tal, mas como uma bloco de tratamento de exceção simples (`finally` ou `catch`).</span><span class="sxs-lookup"><span data-stu-id="2369a-106">A constrained execution region (CER) that is never treated as such, but as a simple exception handling block (`finally` or `catch`).</span></span> <span data-ttu-id="2369a-107">Como consequência, a região não é executada no caso de uma condição de falta de memória ou uma anulação de thread.</span><span class="sxs-lookup"><span data-stu-id="2369a-107">As a consequence, the region does not run in the event of an out-of-memory condition or a thread abort.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="2369a-108">Causa</span><span class="sxs-lookup"><span data-stu-id="2369a-108">Cause</span></span>  
 <span data-ttu-id="2369a-109">O padrão de preparação para uma CER não é seguido corretamente.</span><span class="sxs-lookup"><span data-stu-id="2369a-109">The preparation pattern for a CER is not followed correctly.</span></span>  <span data-ttu-id="2369a-110">Isso é um evento de erro.</span><span class="sxs-lookup"><span data-stu-id="2369a-110">This is an error event.</span></span> <span data-ttu-id="2369a-111">A <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> chamada de método usada para marcar manipuladores de exceção como introdução a uma `catch` CER em seus `fault` `filter` / `finally` / / blocos deve ser usada imediatamente antes do `try` instrução.</span><span class="sxs-lookup"><span data-stu-id="2369a-111">The <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> method call used to mark exception handlers as introducing a CER in their `catch`/`finally`/`fault`/`filter` blocks must be used immediately before the `try` statement.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="2369a-112">Resolução</span><span class="sxs-lookup"><span data-stu-id="2369a-112">Resolution</span></span>  
 <span data-ttu-id="2369a-113">Certifique-se de que a chamada para <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> ocorre imediatamente antes da instrução `try`.</span><span class="sxs-lookup"><span data-stu-id="2369a-113">Ensure that the call to <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> happens immediately before the `try` statement.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="2369a-114">Efeito sobre o tempo de execução</span><span class="sxs-lookup"><span data-stu-id="2369a-114">Effect on the Runtime</span></span>  
 <span data-ttu-id="2369a-115">Esse MDA não tem efeito sobre o CLR.</span><span class="sxs-lookup"><span data-stu-id="2369a-115">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="2369a-116">Saída</span><span class="sxs-lookup"><span data-stu-id="2369a-116">Output</span></span>  
 <span data-ttu-id="2369a-117">O MDA exibe o nome do método chamando o método <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A>, o deslocamento da MSIL e uma mensagem indicando que a chamada não precede imediatamente o início do bloco try.</span><span class="sxs-lookup"><span data-stu-id="2369a-117">The MDA displays the name of the method calling the <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> method, the MSIL offset, and a message indicating the call does not immediately precede the beginning of the try block.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="2369a-118">Configuração</span><span class="sxs-lookup"><span data-stu-id="2369a-118">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <illegalPrepareConstrainedRegion/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="2369a-119">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2369a-119">Example</span></span>  
 <span data-ttu-id="2369a-120">O exemplo de código a seguir demonstra o padrão que faz com que esse MDA seja ativado.</span><span class="sxs-lookup"><span data-stu-id="2369a-120">The following code example demonstrates the pattern that causes this MDA to be activated.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2369a-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2369a-121">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A>
- [<span data-ttu-id="2369a-122">Diagnosticando erros com Assistentes de Depuração Gerenciados</span><span class="sxs-lookup"><span data-stu-id="2369a-122">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="2369a-123">Marshaling de interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="2369a-123">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
