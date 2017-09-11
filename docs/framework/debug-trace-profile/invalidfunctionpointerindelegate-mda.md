---
title: MDA invalidFunctionPointerInDelegate
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
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
caps.latest.revision: 11
author: mairaw
ms.author: mairaw
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: c448f1e60570ae8eff9c0af0dfc942c1ed5d7599
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="invalidfunctionpointerindelegate-mda"></a><span data-ttu-id="1ba71-102">MDA invalidFunctionPointerInDelegate</span><span class="sxs-lookup"><span data-stu-id="1ba71-102">invalidFunctionPointerInDelegate MDA</span></span>
<span data-ttu-id="1ba71-103">O `invalidFunctionPointerInDelegate` MDA (assistente de depuração gerenciada) é ativado quando é informado um ponteiro de função inválido para construir um representante ao invés de um ponteiro de função nativo.</span><span class="sxs-lookup"><span data-stu-id="1ba71-103">The `invalidFunctionPointerInDelegate` managed debugging assistant (MDA) is activated when an invalid function pointer is passed in to construct a delegate over a native function pointer.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="1ba71-104">Sintomas</span><span class="sxs-lookup"><span data-stu-id="1ba71-104">Symptoms</span></span>  
 <span data-ttu-id="1ba71-105">Violações de acesso ou dano inesperado à memória ao usar um representante no lugar de um ponteiro de função.</span><span class="sxs-lookup"><span data-stu-id="1ba71-105">Access violations or unexpected memory corruption when using a delegate over a function pointer.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="1ba71-106">Causa</span><span class="sxs-lookup"><span data-stu-id="1ba71-106">Cause</span></span>  
 <span data-ttu-id="1ba71-107">Foi especificado um ponteiro de função inválido.</span><span class="sxs-lookup"><span data-stu-id="1ba71-107">An invalid function pointer was specified.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="1ba71-108">Resolução</span><span class="sxs-lookup"><span data-stu-id="1ba71-108">Resolution</span></span>  
 <span data-ttu-id="1ba71-109">Especifique um ponteiro de função válido</span><span class="sxs-lookup"><span data-stu-id="1ba71-109">Specify a valid function pointer</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="1ba71-110">Efeito sobre o tempo de execução</span><span class="sxs-lookup"><span data-stu-id="1ba71-110">Effect on the Runtime</span></span>  
 <span data-ttu-id="1ba71-111">Esse MDA não tem efeito sobre o CLR.</span><span class="sxs-lookup"><span data-stu-id="1ba71-111">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="1ba71-112">Saída</span><span class="sxs-lookup"><span data-stu-id="1ba71-112">Output</span></span>  
 <span data-ttu-id="1ba71-113">O ponteiro de função inválido.</span><span class="sxs-lookup"><span data-stu-id="1ba71-113">The invalid function pointer.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="1ba71-114">Configuração</span><span class="sxs-lookup"><span data-stu-id="1ba71-114">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidFunctionPointerInDelegate />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1ba71-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1ba71-115">See Also</span></span>  
 <span data-ttu-id="1ba71-116"><xref:System.Runtime.InteropServices.MarshalAsAttribute></span><span class="sxs-lookup"><span data-stu-id="1ba71-116"><xref:System.Runtime.InteropServices.MarshalAsAttribute></span></span>   
 <span data-ttu-id="1ba71-117">[Diagnosticando erros com Assistentes de Depuração Gerenciados](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md) </span><span class="sxs-lookup"><span data-stu-id="1ba71-117">[Diagnosing Errors with Managed Debugging Assistants](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md) </span></span>  
 [<span data-ttu-id="1ba71-118">Marshaling de interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="1ba71-118">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)

