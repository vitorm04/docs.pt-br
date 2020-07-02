---
title: MDA notMarshalable
description: Examine o assistente de depuração gerenciada não Marshalable, que pode ser ativado se as chamadas não forem atendidas ou ocorrerem no contexto errado para ponteiros de interface COM.
ms.date: 03/30/2017
helpviewer_keywords:
- managed debugging assistants (MDAs), interface pointer not marshalable
- interface pointer not marshalable MDA
- MDAs (managed debugging assistants), interface pointer not marshalable
- marshaling, run-time errors
- managed debugging assistants (MDAs), marshaling
- marshalable interface pointers
- MDAs (managed debugging assistants), marshaling
- notMarshalable MDA
ms.assetid: 96e7b2c1-843f-4d64-b519-740c3a18b50a
ms.openlocfilehash: b464d914a8d83504daaf4cb276914da7798262dc
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85803788"
---
# <a name="notmarshalable-mda"></a><span data-ttu-id="742aa-103">MDA notMarshalable</span><span class="sxs-lookup"><span data-stu-id="742aa-103">notMarshalable MDA</span></span>
<span data-ttu-id="742aa-104">O MDA (Assistente de Depuração Gerenciado) de `notMarshalable` é ativado quando o CLR (Common Language Runtime) encontra um ponteiro de interface COM sem um proxy/stub registrado válido ou uma implementação incorreta da interface `IMarshal` ao tentar realizar marshaling da interface entre contextos.</span><span class="sxs-lookup"><span data-stu-id="742aa-104">The `notMarshalable` managed debugging assistant (MDA) is activated when the common language runtime (CLR) encounters a COM interface pointer without a valid registered proxy/stub or an incorrect `IMarshal` interface implementation while attempting to marshal the interface across contexts.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="742aa-105">Sintomas</span><span class="sxs-lookup"><span data-stu-id="742aa-105">Symptoms</span></span>  
 <span data-ttu-id="742aa-106">Chamadas não são atendidas ou chamadas ocorrem no contexto errado para ponteiros de interface COM.</span><span class="sxs-lookup"><span data-stu-id="742aa-106">Calls are not serviced, or calls occur in the wrong context for COM interface pointers.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="742aa-107">Causa</span><span class="sxs-lookup"><span data-stu-id="742aa-107">Cause</span></span>  
 <span data-ttu-id="742aa-108">Nenhum proxy/stub registrado válido ou uma `IMarshal` incorreta ao tentar realizar marshaling da interface entre contextos.</span><span class="sxs-lookup"><span data-stu-id="742aa-108">No valid registered proxy/stub or an incorrect `IMarshal` while attempting to marshal the interface across contexts.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="742aa-109">Resolução</span><span class="sxs-lookup"><span data-stu-id="742aa-109">Resolution</span></span>  
 <span data-ttu-id="742aa-110">Verifique se você tem um stub de proxy registrado e que a implementação `IMarshal` é válida.</span><span class="sxs-lookup"><span data-stu-id="742aa-110">Make sure you have a proxy stub registered and that the `IMarshal` implementation is valid.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="742aa-111">Efeito sobre o runtime</span><span class="sxs-lookup"><span data-stu-id="742aa-111">Effect on the Runtime</span></span>  
 <span data-ttu-id="742aa-112">Esse MDA não tem nenhum efeito sobre o runtime.</span><span class="sxs-lookup"><span data-stu-id="742aa-112">This MDA has no effect on the runtime.</span></span>  
  
## <a name="output"></a><span data-ttu-id="742aa-113">Saída</span><span class="sxs-lookup"><span data-stu-id="742aa-113">Output</span></span>  
 <span data-ttu-id="742aa-114">Uma mensagem que descreve o problema.</span><span class="sxs-lookup"><span data-stu-id="742aa-114">A message describing the problem.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="742aa-115">Configuração</span><span class="sxs-lookup"><span data-stu-id="742aa-115">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <notMarshalable/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="742aa-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="742aa-116">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="742aa-117">Diagnosticando erros com assistentes para depuração gerenciada</span><span class="sxs-lookup"><span data-stu-id="742aa-117">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="742aa-118">Realizando marshaling de interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="742aa-118">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
