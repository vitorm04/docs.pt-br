---
title: MDA raceOnRCWCleanup
description: Examine o MDA (Assistente de depuração gerenciada) raceOnRCWCleanup, que será ativado se o RCW estiver em uso em outro thread ou na pilha de threads de liberação no .NET.
ms.date: 03/30/2017
helpviewer_keywords:
- RCW
- managed debugging assistants (MDAs), RCWs
- race on RCW cleanup
- MDAs (managed debugging assistants), RCWs
- RaceOnRCWCleanup MDA
- runtime callable wrappers
ms.assetid: bee1e9b1-50a8-4c89-9cd9-7dd6b2458187
ms.openlocfilehash: e86ef96bebb648c7927ae5fec8b68fc4429b268b
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85803645"
---
# <a name="raceonrcwcleanup-mda"></a><span data-ttu-id="07707-103">MDA raceOnRCWCleanup</span><span class="sxs-lookup"><span data-stu-id="07707-103">raceOnRCWCleanup MDA</span></span>
<span data-ttu-id="07707-104">O MDA (Assistente de Depuração Gerenciado) de `raceOnRCWCleanup` é ativado quando o CLR (Common Language Runtime) detecta que um [RCW](../../standard/native-interop/runtime-callable-wrapper.md) (Runtime Callable Wrapper) está em uso quando uma chamada para liberá-lo é feita usando um comando, assim como o método <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="07707-104">The `raceOnRCWCleanup` managed debugging assistant (MDA) is activated when the common language runtime (CLR) detects that a [Runtime Callable Wrapper](../../standard/native-interop/runtime-callable-wrapper.md) (RCW) is in use when a call to release it is made using a command such as the <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="07707-105">Sintomas</span><span class="sxs-lookup"><span data-stu-id="07707-105">Symptoms</span></span>  
 <span data-ttu-id="07707-106">Violações de acesso ou corrupção de memória durante após liberar um RCW usando <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> ou um método semelhante.</span><span class="sxs-lookup"><span data-stu-id="07707-106">Access violations or memory corruption during or after freeing an RCW using <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> or a similar method.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="07707-107">Causa</span><span class="sxs-lookup"><span data-stu-id="07707-107">Cause</span></span>  
 <span data-ttu-id="07707-108">O RCW está em uso em outro thread ou na pilha do thread de liberação.</span><span class="sxs-lookup"><span data-stu-id="07707-108">The RCW is in use on another thread or on the freeing thread stack.</span></span>  <span data-ttu-id="07707-109">Não é possível liberar um RCW que está em uso.</span><span class="sxs-lookup"><span data-stu-id="07707-109">An RCW that is in use cannot be released.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="07707-110">Resolução</span><span class="sxs-lookup"><span data-stu-id="07707-110">Resolution</span></span>  
 <span data-ttu-id="07707-111">Não libere um RCW que possa estar em uso no thread atual ou em outros.</span><span class="sxs-lookup"><span data-stu-id="07707-111">Do not free an RCW that could be in use either in the current or in other threads.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="07707-112">Efeito sobre o runtime</span><span class="sxs-lookup"><span data-stu-id="07707-112">Effect on the Runtime</span></span>  
 <span data-ttu-id="07707-113">Esse MDA não tem efeito sobre o CLR.</span><span class="sxs-lookup"><span data-stu-id="07707-113">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="07707-114">Saída</span><span class="sxs-lookup"><span data-stu-id="07707-114">Output</span></span>  
 <span data-ttu-id="07707-115">Uma mensagem que descreve o erro.</span><span class="sxs-lookup"><span data-stu-id="07707-115">A message describing the error.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="07707-116">Configuração</span><span class="sxs-lookup"><span data-stu-id="07707-116">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <raceOnRCWCleanup/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="07707-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="07707-117">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="07707-118">Diagnosticando erros com assistentes para depuração gerenciada</span><span class="sxs-lookup"><span data-stu-id="07707-118">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="07707-119">Realizando marshaling de interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="07707-119">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
