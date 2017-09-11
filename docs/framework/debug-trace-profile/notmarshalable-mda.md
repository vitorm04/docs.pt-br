---
title: MDA notMarshalable
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
- managed debugging assistants (MDAs), interface pointer not marshalable
- interface pointer not marshalable MDA
- MDAs (managed debugging assistants), interface pointer not marshalable
- marshaling, run-time errors
- managed debugging assistants (MDAs), marshaling
- marshalable interface pointers
- MDAs (managed debugging assistants), marshaling
- notMarshalable MDA
ms.assetid: 96e7b2c1-843f-4d64-b519-740c3a18b50a
caps.latest.revision: 11
author: mairaw
ms.author: mairaw
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 1dcce60b18169e1ca7c87440cec7e36e08634461
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="notmarshalable-mda"></a><span data-ttu-id="1b7e0-102">MDA notMarshalable</span><span class="sxs-lookup"><span data-stu-id="1b7e0-102">notMarshalable MDA</span></span>
<span data-ttu-id="1b7e0-103">O MDA (Assistente de Depuração Gerenciado) de `notMarshalable` é ativado quando o CLR (Common Language Runtime) encontra um ponteiro de interface COM sem um proxy/stub registrado válido ou uma implementação incorreta da interface `IMarshal` ao tentar realizar marshaling da interface entre contextos.</span><span class="sxs-lookup"><span data-stu-id="1b7e0-103">The `notMarshalable` managed debugging assistant (MDA) is activated when the common language runtime (CLR) encounters a COM interface pointer without a valid registered proxy/stub or an incorrect `IMarshal` interface implementation while attempting to marshal the interface across contexts.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="1b7e0-104">Sintomas</span><span class="sxs-lookup"><span data-stu-id="1b7e0-104">Symptoms</span></span>  
 <span data-ttu-id="1b7e0-105">Chamadas não são atendidas ou chamadas ocorrem no contexto errado para ponteiros de interface COM.</span><span class="sxs-lookup"><span data-stu-id="1b7e0-105">Calls are not serviced, or calls occur in the wrong context for COM interface pointers.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="1b7e0-106">Causa</span><span class="sxs-lookup"><span data-stu-id="1b7e0-106">Cause</span></span>  
 <span data-ttu-id="1b7e0-107">Nenhum proxy/stub registrado válido ou uma `IMarshal` incorreta ao tentar realizar marshaling da interface entre contextos.</span><span class="sxs-lookup"><span data-stu-id="1b7e0-107">No valid registered proxy/stub or an incorrect `IMarshal` while attempting to marshal the interface across contexts.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="1b7e0-108">Resolução</span><span class="sxs-lookup"><span data-stu-id="1b7e0-108">Resolution</span></span>  
 <span data-ttu-id="1b7e0-109">Verifique se você tem um stub de proxy registrado e que a implementação `IMarshal` é válida.</span><span class="sxs-lookup"><span data-stu-id="1b7e0-109">Make sure you have a proxy stub registered and that the `IMarshal` implementation is valid.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="1b7e0-110">Efeito sobre o tempo de execução</span><span class="sxs-lookup"><span data-stu-id="1b7e0-110">Effect on the Runtime</span></span>  
 <span data-ttu-id="1b7e0-111">Esse MDA não tem nenhum efeito sobre o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="1b7e0-111">This MDA has no effect on the runtime.</span></span>  
  
## <a name="output"></a><span data-ttu-id="1b7e0-112">Saída</span><span class="sxs-lookup"><span data-stu-id="1b7e0-112">Output</span></span>  
 <span data-ttu-id="1b7e0-113">Uma mensagem que descreve o problema.</span><span class="sxs-lookup"><span data-stu-id="1b7e0-113">A message describing the problem.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="1b7e0-114">Configuração</span><span class="sxs-lookup"><span data-stu-id="1b7e0-114">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <notMarshalable/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1b7e0-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1b7e0-115">See Also</span></span>  
 <span data-ttu-id="1b7e0-116"><xref:System.Runtime.InteropServices.MarshalAsAttribute></span><span class="sxs-lookup"><span data-stu-id="1b7e0-116"><xref:System.Runtime.InteropServices.MarshalAsAttribute></span></span>   
 <span data-ttu-id="1b7e0-117">[Diagnosticando erros com Assistentes de Depuração Gerenciados](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md) </span><span class="sxs-lookup"><span data-stu-id="1b7e0-117">[Diagnosing Errors with Managed Debugging Assistants](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md) </span></span>  
 [<span data-ttu-id="1b7e0-118">Marshaling de interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="1b7e0-118">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)

