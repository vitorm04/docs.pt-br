---
title: MDA invalidIUnknown
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MDAs (managed debugging assistants), invalid IUnknown pointer
- InvalidIUnknown MDA
- invalid IUnknown pointers
- IUnknown pointers
- managed debugging assistants (MDAs), invalid IUnknown pointer
ms.assetid: c7924771-a16b-40fe-b337-ce51dcdf6a12
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ff88f8bc544c95a4fe5149cd517d9157d5ac23c7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="invalidiunknown-mda"></a><span data-ttu-id="58500-102">MDA invalidIUnknown</span><span class="sxs-lookup"><span data-stu-id="58500-102">invalidIUnknown MDA</span></span>
<span data-ttu-id="58500-103">O MDA (Assistente de Depuração Gerenciado) de `invalidIUnknown` é ativado quando um ponteiro `IUnknown` inválido é passado do código nativo para o código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="58500-103">The `invalidIUnknown` managed debugging assistant (MDA) is activated when an invalid `IUnknown` pointer is passed to managed code from native code.</span></span> <span data-ttu-id="58500-104">O `IUnknown` falha em retornar êxito quando consultado para a interface `IUnknown`.</span><span class="sxs-lookup"><span data-stu-id="58500-104">The `IUnknown` fails to return success when queried for the `IUnknown` interface.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="58500-105">Sintomas</span><span class="sxs-lookup"><span data-stu-id="58500-105">Symptoms</span></span>  
 <span data-ttu-id="58500-106">Um erro inesperado ocorre ao fazer marshaling de um ponteiro de interface COM durante o marshaling de argumento.</span><span class="sxs-lookup"><span data-stu-id="58500-106">An unexpected error occurs when marshaling a COM interface pointer during argument marshaling.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="58500-107">Causa</span><span class="sxs-lookup"><span data-stu-id="58500-107">Cause</span></span>  
 <span data-ttu-id="58500-108">Uma implementação de `QueryInterface` incorreta na interface COM passada para o CLR.</span><span class="sxs-lookup"><span data-stu-id="58500-108">An incorrect `QueryInterface` implementation on the COM interface passed to the CLR.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="58500-109">Resolução</span><span class="sxs-lookup"><span data-stu-id="58500-109">Resolution</span></span>  
 <span data-ttu-id="58500-110">Corrija a implementação de `QueryInterface`.</span><span class="sxs-lookup"><span data-stu-id="58500-110">Correct the `QueryInterface` implementation.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="58500-111">Efeito sobre o tempo de execução</span><span class="sxs-lookup"><span data-stu-id="58500-111">Effect on the Runtime</span></span>  
 <span data-ttu-id="58500-112">Esse MDA não tem efeito sobre o CLR.</span><span class="sxs-lookup"><span data-stu-id="58500-112">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="58500-113">Saída</span><span class="sxs-lookup"><span data-stu-id="58500-113">Output</span></span>  
 <span data-ttu-id="58500-114">A descrição do erro.</span><span class="sxs-lookup"><span data-stu-id="58500-114">The description of the error.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="58500-115">Configuração</span><span class="sxs-lookup"><span data-stu-id="58500-115">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidIUnknown />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="58500-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="58500-116">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="58500-117">Diagnosticando erros com Assistentes de Depuração Gerenciados</span><span class="sxs-lookup"><span data-stu-id="58500-117">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="58500-118">Marshaling de interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="58500-118">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
