---
title: MDA overlappedFreeError
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
- OverlappedFreeError MDA
- overlapped free method call error
- managed debugging assistants (MDAs), overlapped structures
- overlapped structures
- MDAs (managed debugging assistants), overlapped structures
- freeing overlapped structures
ms.assetid: b6ab2d48-6eee-4bab-97a3-046b3b0a5470
caps.latest.revision: 8
author: mairaw
ms.author: mairaw
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 68d5098c1a26e186790ba9dafb27b66fedc3f1e9
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="overlappedfreeerror-mda"></a><span data-ttu-id="6b7ab-102">MDA overlappedFreeError</span><span class="sxs-lookup"><span data-stu-id="6b7ab-102">overlappedFreeError MDA</span></span>
<span data-ttu-id="6b7ab-103">O MDA (Assistente de Depuração Gerenciado) de `overlappedFreeError` é ativado quando o método <xref:System.Threading.Overlapped.Free%28System.Threading.NativeOverlapped%2A%29?displayProperty=fullName> é chamado antes da conclusão da operação sobreposta.</span><span class="sxs-lookup"><span data-stu-id="6b7ab-103">The `overlappedFreeError` managed debugging assistant (MDA) is activated when the <xref:System.Threading.Overlapped.Free%28System.Threading.NativeOverlapped%2A%29?displayProperty=fullName> method is called before the overlapped operation has completed.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="6b7ab-104">Sintomas</span><span class="sxs-lookup"><span data-stu-id="6b7ab-104">Symptoms</span></span>  
 <span data-ttu-id="6b7ab-105">Violações de acesso ou corrupção de heap coletado como lixo.</span><span class="sxs-lookup"><span data-stu-id="6b7ab-105">Access violations or corruption of the garbage-collected heap.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="6b7ab-106">Causa</span><span class="sxs-lookup"><span data-stu-id="6b7ab-106">Cause</span></span>  
 <span data-ttu-id="6b7ab-107">Uma estrutura sobreposta foi liberada antes da operação ter sido concluída.</span><span class="sxs-lookup"><span data-stu-id="6b7ab-107">An overlapped structure was freed before the operation completed.</span></span> <span data-ttu-id="6b7ab-108">A função que está usando o ponteiro sobreposto pode gravar a estrutura mais tarde, depois de ele ter sido liberado.</span><span class="sxs-lookup"><span data-stu-id="6b7ab-108">The function that is using the overlapped pointer might write to the structure later, after it has been freed.</span></span> <span data-ttu-id="6b7ab-109">Isso pode causar corrupção de heap porque outro objeto agora pode ocupar essa região.</span><span class="sxs-lookup"><span data-stu-id="6b7ab-109">That can cause heap corruption because another object might now occupy that region.</span></span>  
  
 <span data-ttu-id="6b7ab-110">Esse MDA poderá não representar um erro se a operação sobreposta não for iniciada com êxito.</span><span class="sxs-lookup"><span data-stu-id="6b7ab-110">This MDA might not represent an error if the overlapped operation did not start successfully.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="6b7ab-111">Resolução</span><span class="sxs-lookup"><span data-stu-id="6b7ab-111">Resolution</span></span>  
 <span data-ttu-id="6b7ab-112">Verifique se a operação de E/S usando a estrutura sobreposta foi concluída antes de chamar o método <xref:System.Threading.Overlapped.Free%28System.Threading.NativeOverlapped%2A%29>.</span><span class="sxs-lookup"><span data-stu-id="6b7ab-112">Ensure that the I/O operation using the overlapped structure has completed before calling the <xref:System.Threading.Overlapped.Free%28System.Threading.NativeOverlapped%2A%29> method.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="6b7ab-113">Efeito sobre o tempo de execução</span><span class="sxs-lookup"><span data-stu-id="6b7ab-113">Effect on the Runtime</span></span>  
 <span data-ttu-id="6b7ab-114">Esse MDA não tem efeito sobre o CLR.</span><span class="sxs-lookup"><span data-stu-id="6b7ab-114">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="6b7ab-115">Saída</span><span class="sxs-lookup"><span data-stu-id="6b7ab-115">Output</span></span>  
 <span data-ttu-id="6b7ab-116">O demonstrado a seguir é uma saída de exemplo para esse MDA.</span><span class="sxs-lookup"><span data-stu-id="6b7ab-116">The following is sample output for this MDA.</span></span>  
  
 `An overlapped pointer (0x00ea3430) that was not allocated on the GC heap was passed via Pinvoke to the win32 function 'WriteFile' in module 'KERNEL32.DLL'. If the AppDomain is shut down, this can cause heap corruption when the async I/O completes. The best solution is to pass a NativeOverlappedStructure retrieved from a call to System.Threading.Overlapped.Pack(). If the AppDomain exits, the CLR will keep this structure alive and pinned until the I/O completes.`  
  
## <a name="configuration"></a><span data-ttu-id="6b7ab-117">Configuração</span><span class="sxs-lookup"><span data-stu-id="6b7ab-117">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <overlappedFreeError/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="6b7ab-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6b7ab-118">See Also</span></span>  
 <span data-ttu-id="6b7ab-119"><xref:System.Runtime.InteropServices.MarshalAsAttribute></span><span class="sxs-lookup"><span data-stu-id="6b7ab-119"><xref:System.Runtime.InteropServices.MarshalAsAttribute></span></span>   
 <span data-ttu-id="6b7ab-120">[Diagnosticando erros com Assistentes de Depuração Gerenciados](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md) </span><span class="sxs-lookup"><span data-stu-id="6b7ab-120">[Diagnosing Errors with Managed Debugging Assistants](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md) </span></span>  
 [<span data-ttu-id="6b7ab-121">Marshaling de interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="6b7ab-121">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)

