---
title: MDA failedQI
ms.date: 03/30/2017
helpviewer_keywords:
- failed QueryInterface
- FailedQI MDA
- QueryInterface call failures
- MDAs (managed debugging assistants), failed QueryInterface
- managed debugging assistants (MDAs), failed QueryInterface
ms.assetid: 902dc863-34b3-477c-b433-b8a6bb6133c6
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0ac478644561d2aab13d10811987d8d02c8d7608
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59217621"
---
# <a name="failedqi-mda"></a><span data-ttu-id="1f31e-102">MDA failedQI</span><span class="sxs-lookup"><span data-stu-id="1f31e-102">failedQI MDA</span></span>
<span data-ttu-id="1f31e-103">O MDA (assistente para depuração gerenciada) `failedQI` é ativado quando o tempo de execução chama `QueryInterface` em um ponteiro de interface COM em nome de um RCW (Runtime Callable Wrapper) e a chamada `QueryInterface` falha.</span><span class="sxs-lookup"><span data-stu-id="1f31e-103">The `failedQI` managed debugging assistant (MDA) is activated when the runtime calls `QueryInterface` on a COM interface pointer on behalf of a runtime callable wrapper (RCW), and the `QueryInterface` call fails.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="1f31e-104">Sintomas</span><span class="sxs-lookup"><span data-stu-id="1f31e-104">Symptoms</span></span>  
 <span data-ttu-id="1f31e-105">Uma conversão em um RCW falha ou uma chamada ao COM em um RCW falha inesperadamente.</span><span class="sxs-lookup"><span data-stu-id="1f31e-105">A cast on an RCW fails, or a call to COM from an RCW fails unexpectedly.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="1f31e-106">Causa</span><span class="sxs-lookup"><span data-stu-id="1f31e-106">Cause</span></span>  
  
-   <span data-ttu-id="1f31e-107">A chamada é feita do contexto incorreto.</span><span class="sxs-lookup"><span data-stu-id="1f31e-107">The call is made from the wrong context.</span></span>  
  
-   <span data-ttu-id="1f31e-108">O proxy registrado está falhando a chamada `QueryInterface` porque houve uma tentativa de realizar a chamada no contexto incorreto.</span><span class="sxs-lookup"><span data-stu-id="1f31e-108">The registered proxy is failing the `QueryInterface` call because the call was attempted in the wrong context.</span></span>  
  
-   <span data-ttu-id="1f31e-109">Um proxy de propriedade do OLE retornou uma falha HRESULT.</span><span class="sxs-lookup"><span data-stu-id="1f31e-109">An OLE-owned proxy returned a failure HRESULT.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="1f31e-110">Resolução</span><span class="sxs-lookup"><span data-stu-id="1f31e-110">Resolution</span></span>  
 <span data-ttu-id="1f31e-111">Consulte a documentação do MSDN sobre as regras do COM.</span><span class="sxs-lookup"><span data-stu-id="1f31e-111">See the MSDN documentation on COM rules.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="1f31e-112">Efeito sobre o tempo de execução</span><span class="sxs-lookup"><span data-stu-id="1f31e-112">Effect on the Runtime</span></span>  
 <span data-ttu-id="1f31e-113">Se uma chamada `QueryInterface` falhar, o contexto será alternado e haverá uma tentativa de realizar a chamada `QueryInterface` novamente para ver se um contexto incorreto estava com uma falha.</span><span class="sxs-lookup"><span data-stu-id="1f31e-113">If a `QueryInterface` call fails, the context is switched and the `QueryInterface` call is attempted again to see if an incorrect context was at fault.</span></span>  
  
## <a name="output"></a><span data-ttu-id="1f31e-114">Saída</span><span class="sxs-lookup"><span data-stu-id="1f31e-114">Output</span></span>  
 <span data-ttu-id="1f31e-115">O nome gerenciado da interface, o GUID da interface e o HRESULT da falha.</span><span class="sxs-lookup"><span data-stu-id="1f31e-115">The managed name of the interface, the GUID of the interface, and the HRESULT of the failure.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="1f31e-116">Configuração</span><span class="sxs-lookup"><span data-stu-id="1f31e-116">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <failedQI/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1f31e-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1f31e-117">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="1f31e-118">Diagnosticando erros com assistentes de depuração gerenciados</span><span class="sxs-lookup"><span data-stu-id="1f31e-118">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="1f31e-119">Realizando marshaling de interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="1f31e-119">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
