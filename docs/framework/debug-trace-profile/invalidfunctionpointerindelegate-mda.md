---
title: MDA invalidFunctionPointerInDelegate
ms.date: 03/30/2017
helpviewer_keywords:
- invalidFunctionPointerInDelegate MDA
- managed debugging assistants (MDAs), invalid function pointer to delegates
- MDAs (managed debugging assistants), invalid function pointer to delegates
- function pointers, invalid
- marshaling, run-time errors
- managed debugging assistants (MDAs), marshaling
- MDAs (managed debugging assistants), marshaling
- invalid function pointers
ms.assetid: 99ae44f1-783e-49a9-9009-24f54bbd0f09
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 847ec4d861136b46383ce7d3801764f3d962049e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33390868"
---
# <a name="invalidfunctionpointerindelegate-mda"></a><span data-ttu-id="e04c2-102">MDA invalidFunctionPointerInDelegate</span><span class="sxs-lookup"><span data-stu-id="e04c2-102">invalidFunctionPointerInDelegate MDA</span></span>
<span data-ttu-id="e04c2-103">O `invalidFunctionPointerInDelegate` MDA (assistente de depuração gerenciada) é ativado quando é informado um ponteiro de função inválido para construir um representante ao invés de um ponteiro de função nativo.</span><span class="sxs-lookup"><span data-stu-id="e04c2-103">The `invalidFunctionPointerInDelegate` managed debugging assistant (MDA) is activated when an invalid function pointer is passed in to construct a delegate over a native function pointer.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="e04c2-104">Sintomas</span><span class="sxs-lookup"><span data-stu-id="e04c2-104">Symptoms</span></span>  
 <span data-ttu-id="e04c2-105">Violações de acesso ou dano inesperado à memória ao usar um representante no lugar de um ponteiro de função.</span><span class="sxs-lookup"><span data-stu-id="e04c2-105">Access violations or unexpected memory corruption when using a delegate over a function pointer.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="e04c2-106">Causa</span><span class="sxs-lookup"><span data-stu-id="e04c2-106">Cause</span></span>  
 <span data-ttu-id="e04c2-107">Foi especificado um ponteiro de função inválido.</span><span class="sxs-lookup"><span data-stu-id="e04c2-107">An invalid function pointer was specified.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="e04c2-108">Resolução</span><span class="sxs-lookup"><span data-stu-id="e04c2-108">Resolution</span></span>  
 <span data-ttu-id="e04c2-109">Especifique um ponteiro de função válido</span><span class="sxs-lookup"><span data-stu-id="e04c2-109">Specify a valid function pointer</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="e04c2-110">Efeito sobre o tempo de execução</span><span class="sxs-lookup"><span data-stu-id="e04c2-110">Effect on the Runtime</span></span>  
 <span data-ttu-id="e04c2-111">Esse MDA não tem efeito sobre o CLR.</span><span class="sxs-lookup"><span data-stu-id="e04c2-111">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="e04c2-112">Saída</span><span class="sxs-lookup"><span data-stu-id="e04c2-112">Output</span></span>  
 <span data-ttu-id="e04c2-113">O ponteiro de função inválido.</span><span class="sxs-lookup"><span data-stu-id="e04c2-113">The invalid function pointer.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="e04c2-114">Configuração</span><span class="sxs-lookup"><span data-stu-id="e04c2-114">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidFunctionPointerInDelegate />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e04c2-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e04c2-115">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="e04c2-116">Diagnosticando erros com Assistentes de Depuração Gerenciados</span><span class="sxs-lookup"><span data-stu-id="e04c2-116">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="e04c2-117">Marshaling de interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="e04c2-117">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
