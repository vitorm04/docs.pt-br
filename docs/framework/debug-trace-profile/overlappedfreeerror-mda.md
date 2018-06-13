---
title: MDA overlappedFreeError
ms.date: 03/30/2017
helpviewer_keywords:
- OverlappedFreeError MDA
- overlapped free method call error
- managed debugging assistants (MDAs), overlapped structures
- overlapped structures
- MDAs (managed debugging assistants), overlapped structures
- freeing overlapped structures
ms.assetid: b6ab2d48-6eee-4bab-97a3-046b3b0a5470
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 301d36820ed5ae1d6ba1cfd2961221095b02bea6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33386399"
---
# <a name="overlappedfreeerror-mda"></a><span data-ttu-id="c7bd0-102">MDA overlappedFreeError</span><span class="sxs-lookup"><span data-stu-id="c7bd0-102">overlappedFreeError MDA</span></span>
<span data-ttu-id="c7bd0-103">O MDA (Assistente de Depuração Gerenciado) de `overlappedFreeError` é ativado quando o método <xref:System.Threading.Overlapped.Free%28System.Threading.NativeOverlapped%2A%29?displayProperty=nameWithType> é chamado antes da conclusão da operação sobreposta.</span><span class="sxs-lookup"><span data-stu-id="c7bd0-103">The `overlappedFreeError` managed debugging assistant (MDA) is activated when the <xref:System.Threading.Overlapped.Free%28System.Threading.NativeOverlapped%2A%29?displayProperty=nameWithType> method is called before the overlapped operation has completed.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="c7bd0-104">Sintomas</span><span class="sxs-lookup"><span data-stu-id="c7bd0-104">Symptoms</span></span>  
 <span data-ttu-id="c7bd0-105">Violações de acesso ou corrupção de heap coletado como lixo.</span><span class="sxs-lookup"><span data-stu-id="c7bd0-105">Access violations or corruption of the garbage-collected heap.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="c7bd0-106">Causa</span><span class="sxs-lookup"><span data-stu-id="c7bd0-106">Cause</span></span>  
 <span data-ttu-id="c7bd0-107">Uma estrutura sobreposta foi liberada antes da operação ter sido concluída.</span><span class="sxs-lookup"><span data-stu-id="c7bd0-107">An overlapped structure was freed before the operation completed.</span></span> <span data-ttu-id="c7bd0-108">A função que está usando o ponteiro sobreposto pode gravar a estrutura mais tarde, depois de ele ter sido liberado.</span><span class="sxs-lookup"><span data-stu-id="c7bd0-108">The function that is using the overlapped pointer might write to the structure later, after it has been freed.</span></span> <span data-ttu-id="c7bd0-109">Isso pode causar corrupção de heap porque outro objeto agora pode ocupar essa região.</span><span class="sxs-lookup"><span data-stu-id="c7bd0-109">That can cause heap corruption because another object might now occupy that region.</span></span>  
  
 <span data-ttu-id="c7bd0-110">Esse MDA poderá não representar um erro se a operação sobreposta não for iniciada com êxito.</span><span class="sxs-lookup"><span data-stu-id="c7bd0-110">This MDA might not represent an error if the overlapped operation did not start successfully.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="c7bd0-111">Resolução</span><span class="sxs-lookup"><span data-stu-id="c7bd0-111">Resolution</span></span>  
 <span data-ttu-id="c7bd0-112">Verifique se a operação de E/S usando a estrutura sobreposta foi concluída antes de chamar o método <xref:System.Threading.Overlapped.Free%28System.Threading.NativeOverlapped%2A%29>.</span><span class="sxs-lookup"><span data-stu-id="c7bd0-112">Ensure that the I/O operation using the overlapped structure has completed before calling the <xref:System.Threading.Overlapped.Free%28System.Threading.NativeOverlapped%2A%29> method.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="c7bd0-113">Efeito sobre o tempo de execução</span><span class="sxs-lookup"><span data-stu-id="c7bd0-113">Effect on the Runtime</span></span>  
 <span data-ttu-id="c7bd0-114">Esse MDA não tem efeito sobre o CLR.</span><span class="sxs-lookup"><span data-stu-id="c7bd0-114">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="c7bd0-115">Saída</span><span class="sxs-lookup"><span data-stu-id="c7bd0-115">Output</span></span>  
 <span data-ttu-id="c7bd0-116">O demonstrado a seguir é uma saída de exemplo para esse MDA.</span><span class="sxs-lookup"><span data-stu-id="c7bd0-116">The following is sample output for this MDA.</span></span>  
  
 `An overlapped pointer (0x00ea3430) that was not allocated on the GC heap was passed via Pinvoke to the win32 function 'WriteFile' in module 'KERNEL32.DLL'. If the AppDomain is shut down, this can cause heap corruption when the async I/O completes. The best solution is to pass a NativeOverlappedStructure retrieved from a call to System.Threading.Overlapped.Pack(). If the AppDomain exits, the CLR will keep this structure alive and pinned until the I/O completes.`  
  
## <a name="configuration"></a><span data-ttu-id="c7bd0-117">Configuração</span><span class="sxs-lookup"><span data-stu-id="c7bd0-117">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <overlappedFreeError/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c7bd0-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c7bd0-118">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="c7bd0-119">Diagnosticando erros com Assistentes de Depuração Gerenciados</span><span class="sxs-lookup"><span data-stu-id="c7bd0-119">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="c7bd0-120">Marshaling de interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="c7bd0-120">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
