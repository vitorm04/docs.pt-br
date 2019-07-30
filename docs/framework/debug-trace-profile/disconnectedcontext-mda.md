---
title: MDA disconnectedContext
ms.date: 03/30/2017
helpviewer_keywords:
- DisconnectedContext MDA
- MDAs (managed debugging assistants), disconnected context
- dead context
- transitioning disconnected apartment or context
- context disconnections
- managed debugging assistants (MDAs), disconnected context
ms.assetid: 1887d31d-7006-4491-93b3-68fd5b05f71d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5d97ee808ef7d2a14902259c47227b787f0830fb
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68629388"
---
# <a name="disconnectedcontext-mda"></a><span data-ttu-id="d1892-102">MDA disconnectedContext</span><span class="sxs-lookup"><span data-stu-id="d1892-102">disconnectedContext MDA</span></span>
<span data-ttu-id="d1892-103">O MDA (Assistente para depuração gerenciada) `disconnectedContext` é ativado quando o CLR tenta realizar a transição para um apartment ou contexto desconectado durante a manutenção de uma solicitação sobre um objeto COM.</span><span class="sxs-lookup"><span data-stu-id="d1892-103">The `disconnectedContext` managed debugging assistant (MDA) is activated when the CLR attempts to transition into a disconnected apartment or context while servicing a request concerning a COM object.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="d1892-104">Sintomas</span><span class="sxs-lookup"><span data-stu-id="d1892-104">Symptoms</span></span>  
 <span data-ttu-id="d1892-105">As chamadas feitas em um [RCW](../../../docs/standard/native-interop/runtime-callable-wrapper.md) (Runtime Callable Wrapper) são entregues ao componente COM subjacente no apartment ou no contexto atual, em vez de aquele no qual elas existem.</span><span class="sxs-lookup"><span data-stu-id="d1892-105">Calls made on a [Runtime Callable Wrapper](../../../docs/standard/native-interop/runtime-callable-wrapper.md) (RCW) are delivered to the underlying COM component in the current apartment or context instead of the one in which they exist.</span></span> <span data-ttu-id="d1892-106">Isso pode causar corrupção ou perda de dados se o componente COM não for com vários threads, como no caso de componentes STA (Single-Threaded Apartment).</span><span class="sxs-lookup"><span data-stu-id="d1892-106">This can cause corruption and or data loss if the COM component is not multithreaded, as in the case of single-threaded apartment (STA) components.</span></span> <span data-ttu-id="d1892-107">Como alternativa, se o RCW em si for um proxy, a chamada pode resultar no lançamento de um <xref:System.Runtime.InteropServices.COMException> com um HRESULT de RPC_E_WRONG_THREAD.</span><span class="sxs-lookup"><span data-stu-id="d1892-107">Alternatively, if the RCW is itself a proxy, the call might result in the throwing of a <xref:System.Runtime.InteropServices.COMException> with an HRESULT of RPC_E_WRONG_THREAD.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="d1892-108">Causa</span><span class="sxs-lookup"><span data-stu-id="d1892-108">Cause</span></span>  
 <span data-ttu-id="d1892-109">O apartment ou contexto OLE foi desligado quando o CLR tenta realizar a transição para ele.</span><span class="sxs-lookup"><span data-stu-id="d1892-109">The OLE apartment or context has been shut down when the CLR attempts to transition into it.</span></span> <span data-ttu-id="d1892-110">Isso é comumente causado por apartments STA a serem desligados antes de todos os componentes COM de propriedade do apartment terem sido completamente liberados. Isso pode ocorrer como resultado de uma chamada explícita de um código de usuário em um RCW ou enquanto o CLR em si está manipulando o componente COM, por exemplo, quando o CLR está liberando o componente COM quando o RCW associado passou por coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="d1892-110">This is most commonly caused by STA apartments being shut down before all the COM components owned by the apartment were completely released This can occur as a result of an explicit call from user code on an RCW or while the CLR itself is manipulating the COM component, for example when the CLR is releasing the COM component when the associated RCW has been garbage collected.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="d1892-111">Resolução</span><span class="sxs-lookup"><span data-stu-id="d1892-111">Resolution</span></span>  
 <span data-ttu-id="d1892-112">Para evitar esse problema, garanta que o thread que possui o STA não termine antes de o aplicativo ter concluído todos os objetos que residem no apartment.</span><span class="sxs-lookup"><span data-stu-id="d1892-112">To avoid this problem, ensure the thread that owns the STA does not terminate before the application has finished with all the objects that live in the apartment.</span></span> <span data-ttu-id="d1892-113">O mesmo se aplica a contextos; garanta que os contextos não desliguem antes de o aplicativo ser totalmente encerrado com qualquer componente COM que resida dentro do contexto.</span><span class="sxs-lookup"><span data-stu-id="d1892-113">The same applies to contexts; ensure contexts are not shut down before the application is completely finished with any COM components that live inside the context.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="d1892-114">Efeito sobre o tempo de execução</span><span class="sxs-lookup"><span data-stu-id="d1892-114">Effect on the Runtime</span></span>  
 <span data-ttu-id="d1892-115">Esse MDA não tem efeito sobre o CLR.</span><span class="sxs-lookup"><span data-stu-id="d1892-115">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="d1892-116">Apenas relata dados sobre o contexto desconectado.</span><span class="sxs-lookup"><span data-stu-id="d1892-116">It only reports data about the disconnected context.</span></span>  
  
## <a name="output"></a><span data-ttu-id="d1892-117">Saída</span><span class="sxs-lookup"><span data-stu-id="d1892-117">Output</span></span>  
 <span data-ttu-id="d1892-118">Relata o cookie de contexto do apartment ou contexto desconectado.</span><span class="sxs-lookup"><span data-stu-id="d1892-118">Reports the context cookie of the disconnected apartment or context.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="d1892-119">Configuração</span><span class="sxs-lookup"><span data-stu-id="d1892-119">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <disconnectedContext />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d1892-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d1892-120">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="d1892-121">Diagnosticando erros com Assistentes de Depuração Gerenciados</span><span class="sxs-lookup"><span data-stu-id="d1892-121">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="d1892-122">Marshaling de interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="d1892-122">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
