---
title: MDA disconnectedContext
description: Examine o assistente de depuração gerenciada do disconnectedContext no .NET, que é invocado quando o CLR tenta fazer a transição para um apartamento ou contexto desconectado.
ms.date: 03/30/2017
helpviewer_keywords:
- DisconnectedContext MDA
- MDAs (managed debugging assistants), disconnected context
- dead context
- transitioning disconnected apartment or context
- context disconnections
- managed debugging assistants (MDAs), disconnected context
ms.assetid: 1887d31d-7006-4491-93b3-68fd5b05f71d
ms.openlocfilehash: 0b24aadefab7a7cb2a5294f25e674d188beec814
ms.sourcegitcommit: a2c8b19e813a52b91facbb5d7e3c062c7188b457
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85416077"
---
# <a name="disconnectedcontext-mda"></a><span data-ttu-id="ff81c-103">MDA disconnectedContext</span><span class="sxs-lookup"><span data-stu-id="ff81c-103">disconnectedContext MDA</span></span>
<span data-ttu-id="ff81c-104">O MDA (Assistente para depuração gerenciada) `disconnectedContext` é ativado quando o CLR tenta realizar a transição para um apartment ou contexto desconectado durante a manutenção de uma solicitação sobre um objeto COM.</span><span class="sxs-lookup"><span data-stu-id="ff81c-104">The `disconnectedContext` managed debugging assistant (MDA) is activated when the CLR attempts to transition into a disconnected apartment or context while servicing a request concerning a COM object.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="ff81c-105">Sintomas</span><span class="sxs-lookup"><span data-stu-id="ff81c-105">Symptoms</span></span>  
 <span data-ttu-id="ff81c-106">As chamadas feitas em um [RCW](../../standard/native-interop/runtime-callable-wrapper.md) (Runtime Callable Wrapper) são entregues ao componente COM subjacente no apartment ou no contexto atual, em vez de aquele no qual elas existem.</span><span class="sxs-lookup"><span data-stu-id="ff81c-106">Calls made on a [Runtime Callable Wrapper](../../standard/native-interop/runtime-callable-wrapper.md) (RCW) are delivered to the underlying COM component in the current apartment or context instead of the one in which they exist.</span></span> <span data-ttu-id="ff81c-107">Isso pode causar corrupção ou perda de dados se o componente COM não for com vários threads, como no caso de componentes STA (Single-Threaded Apartment).</span><span class="sxs-lookup"><span data-stu-id="ff81c-107">This can cause corruption and or data loss if the COM component is not multithreaded, as in the case of single-threaded apartment (STA) components.</span></span> <span data-ttu-id="ff81c-108">Como alternativa, se o RCW em si for um proxy, a chamada pode resultar no lançamento de um <xref:System.Runtime.InteropServices.COMException> com um HRESULT de RPC_E_WRONG_THREAD.</span><span class="sxs-lookup"><span data-stu-id="ff81c-108">Alternatively, if the RCW is itself a proxy, the call might result in the throwing of a <xref:System.Runtime.InteropServices.COMException> with an HRESULT of RPC_E_WRONG_THREAD.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="ff81c-109">Causa</span><span class="sxs-lookup"><span data-stu-id="ff81c-109">Cause</span></span>  
 <span data-ttu-id="ff81c-110">O apartment ou contexto OLE foi desligado quando o CLR tenta realizar a transição para ele.</span><span class="sxs-lookup"><span data-stu-id="ff81c-110">The OLE apartment or context has been shut down when the CLR attempts to transition into it.</span></span> <span data-ttu-id="ff81c-111">Isso é comumente causado por apartments STA a serem desligados antes de todos os componentes COM de propriedade do apartment terem sido completamente liberados. Isso pode ocorrer como resultado de uma chamada explícita de um código de usuário em um RCW ou enquanto o CLR em si está manipulando o componente COM, por exemplo, quando o CLR está liberando o componente COM quando o RCW associado passou por coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="ff81c-111">This is most commonly caused by STA apartments being shut down before all the COM components owned by the apartment were completely released This can occur as a result of an explicit call from user code on an RCW or while the CLR itself is manipulating the COM component, for example when the CLR is releasing the COM component when the associated RCW has been garbage collected.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="ff81c-112">Resolução</span><span class="sxs-lookup"><span data-stu-id="ff81c-112">Resolution</span></span>  
 <span data-ttu-id="ff81c-113">Para evitar esse problema, garanta que o thread que possui o STA não termine antes de o aplicativo ter concluído todos os objetos que residem no apartment.</span><span class="sxs-lookup"><span data-stu-id="ff81c-113">To avoid this problem, ensure the thread that owns the STA does not terminate before the application has finished with all the objects that live in the apartment.</span></span> <span data-ttu-id="ff81c-114">O mesmo se aplica a contextos; garanta que os contextos não desliguem antes de o aplicativo ser totalmente encerrado com qualquer componente COM que resida dentro do contexto.</span><span class="sxs-lookup"><span data-stu-id="ff81c-114">The same applies to contexts; ensure contexts are not shut down before the application is completely finished with any COM components that live inside the context.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="ff81c-115">Efeito sobre o runtime</span><span class="sxs-lookup"><span data-stu-id="ff81c-115">Effect on the Runtime</span></span>  
 <span data-ttu-id="ff81c-116">Esse MDA não tem efeito sobre o CLR.</span><span class="sxs-lookup"><span data-stu-id="ff81c-116">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="ff81c-117">Apenas relata dados sobre o contexto desconectado.</span><span class="sxs-lookup"><span data-stu-id="ff81c-117">It only reports data about the disconnected context.</span></span>  
  
## <a name="output"></a><span data-ttu-id="ff81c-118">Saída</span><span class="sxs-lookup"><span data-stu-id="ff81c-118">Output</span></span>  
 <span data-ttu-id="ff81c-119">Relata o cookie de contexto do apartment ou contexto desconectado.</span><span class="sxs-lookup"><span data-stu-id="ff81c-119">Reports the context cookie of the disconnected apartment or context.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="ff81c-120">Configuração</span><span class="sxs-lookup"><span data-stu-id="ff81c-120">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <disconnectedContext />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ff81c-121">Veja também</span><span class="sxs-lookup"><span data-stu-id="ff81c-121">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="ff81c-122">Diagnosticando erros com assistentes para depuração gerenciada</span><span class="sxs-lookup"><span data-stu-id="ff81c-122">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="ff81c-123">Realizando marshaling de interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="ff81c-123">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
