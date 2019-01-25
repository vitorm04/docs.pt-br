---
title: MDA notMarshalable
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: cec3fd0c3b20c70b6ddf3e875c481e829dd5eb28
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54695485"
---
# <a name="notmarshalable-mda"></a><span data-ttu-id="c4d00-102">MDA notMarshalable</span><span class="sxs-lookup"><span data-stu-id="c4d00-102">notMarshalable MDA</span></span>
<span data-ttu-id="c4d00-103">O MDA (Assistente de Depuração Gerenciado) de `notMarshalable` é ativado quando o CLR (Common Language Runtime) encontra um ponteiro de interface COM sem um proxy/stub registrado válido ou uma implementação incorreta da interface `IMarshal` ao tentar realizar marshaling da interface entre contextos.</span><span class="sxs-lookup"><span data-stu-id="c4d00-103">The `notMarshalable` managed debugging assistant (MDA) is activated when the common language runtime (CLR) encounters a COM interface pointer without a valid registered proxy/stub or an incorrect `IMarshal` interface implementation while attempting to marshal the interface across contexts.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="c4d00-104">Sintomas</span><span class="sxs-lookup"><span data-stu-id="c4d00-104">Symptoms</span></span>  
 <span data-ttu-id="c4d00-105">Chamadas não são atendidas ou chamadas ocorrem no contexto errado para ponteiros de interface COM.</span><span class="sxs-lookup"><span data-stu-id="c4d00-105">Calls are not serviced, or calls occur in the wrong context for COM interface pointers.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="c4d00-106">Causa</span><span class="sxs-lookup"><span data-stu-id="c4d00-106">Cause</span></span>  
 <span data-ttu-id="c4d00-107">Nenhum proxy/stub registrado válido ou uma `IMarshal` incorreta ao tentar realizar marshaling da interface entre contextos.</span><span class="sxs-lookup"><span data-stu-id="c4d00-107">No valid registered proxy/stub or an incorrect `IMarshal` while attempting to marshal the interface across contexts.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="c4d00-108">Resolução</span><span class="sxs-lookup"><span data-stu-id="c4d00-108">Resolution</span></span>  
 <span data-ttu-id="c4d00-109">Verifique se você tem um stub de proxy registrado e que a implementação `IMarshal` é válida.</span><span class="sxs-lookup"><span data-stu-id="c4d00-109">Make sure you have a proxy stub registered and that the `IMarshal` implementation is valid.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="c4d00-110">Efeito sobre o tempo de execução</span><span class="sxs-lookup"><span data-stu-id="c4d00-110">Effect on the Runtime</span></span>  
 <span data-ttu-id="c4d00-111">Esse MDA não tem nenhum efeito sobre o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="c4d00-111">This MDA has no effect on the runtime.</span></span>  
  
## <a name="output"></a><span data-ttu-id="c4d00-112">Saída</span><span class="sxs-lookup"><span data-stu-id="c4d00-112">Output</span></span>  
 <span data-ttu-id="c4d00-113">Uma mensagem que descreve o problema.</span><span class="sxs-lookup"><span data-stu-id="c4d00-113">A message describing the problem.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="c4d00-114">Configuração</span><span class="sxs-lookup"><span data-stu-id="c4d00-114">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <notMarshalable/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c4d00-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c4d00-115">See also</span></span>
- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="c4d00-116">Diagnosticando erros com Assistentes de Depuração Gerenciados</span><span class="sxs-lookup"><span data-stu-id="c4d00-116">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="c4d00-117">Marshaling de interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="c4d00-117">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
