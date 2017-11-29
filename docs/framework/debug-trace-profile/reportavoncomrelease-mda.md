---
title: MDA reportAvOnComRelease
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MDAs (managed debugging assistants), reference counting errors
- exceptions, reference counting errors
- ReportAvOnComRelease MDA
- COM release access violations
- user reference counting errors
- managed debugging assistants (MDAs), reference counting errors
- report access violation on Com release
- reference counting errors
ms.assetid: a2b86b63-08b2-4943-b344-3c2cf46ccd31
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: de48fca818f8456627c9507756cc2d8a200c50e2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="reportavoncomrelease-mda"></a><span data-ttu-id="a5dab-102">MDA reportAvOnComRelease</span><span class="sxs-lookup"><span data-stu-id="a5dab-102">reportAvOnComRelease MDA</span></span>
<span data-ttu-id="a5dab-103">O MDA (Assistente para Depuração Gerenciada) do `reportAvOnComRelease` é ativado quando as exceções são lançadas por causa da contagem de erros pela referência do usuário durante a realização da interoperabilidade COM e do uso do método <xref:System.Runtime.InteropServices.Marshal.Release%2A> ou <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> combinado com chamadas COM brutas.</span><span class="sxs-lookup"><span data-stu-id="a5dab-103">The `reportAvOnComRelease` managed debugging assistant (MDA) is activated when exceptions are thrown due to user reference counting errors while performing COM interop and using the <xref:System.Runtime.InteropServices.Marshal.Release%2A> or <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> method combined with raw COM calls.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="a5dab-104">Sintomas</span><span class="sxs-lookup"><span data-stu-id="a5dab-104">Symptoms</span></span>  
 <span data-ttu-id="a5dab-105">Violações de acesso e corrupção de memória.</span><span class="sxs-lookup"><span data-stu-id="a5dab-105">Access violations and memory corruption.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="a5dab-106">Causa</span><span class="sxs-lookup"><span data-stu-id="a5dab-106">Cause</span></span>  
 <span data-ttu-id="a5dab-107">Às vezes, uma exceção é lançada por causa da contagem de erros pela referência do usuário durante a realização da interoperabilidade COM e do uso do método <xref:System.Runtime.InteropServices.Marshal.Release%2A> ou <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> combinado com chamadas COM brutas.</span><span class="sxs-lookup"><span data-stu-id="a5dab-107">Occasionally, an exception is thrown due to user reference counting errors while performing COM interop and using the <xref:System.Runtime.InteropServices.Marshal.Release%2A> or <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> method combined with raw COM calls.</span></span> <span data-ttu-id="a5dab-108">Normalmente, essa exceção é descartada porque deixar de fazer isso causaria uma violação de acesso no CLR, desativando-o.</span><span class="sxs-lookup"><span data-stu-id="a5dab-108">Normally, this exception is discarded because not doing so would cause an access violation in the CLR, bringing it down.</span></span> <span data-ttu-id="a5dab-109">Quando esse assistente é habilitado, essas exceções podem ser detectadas e relatadas em vez de ser simplesmente descartadas.</span><span class="sxs-lookup"><span data-stu-id="a5dab-109">When this assistant is enabled, such exceptions can be detected and reported instead of being simply discarded.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="a5dab-110">Resolução</span><span class="sxs-lookup"><span data-stu-id="a5dab-110">Resolution</span></span>  
 <span data-ttu-id="a5dab-111">Examine o código de contagem de referência e procure erros, também examine os clientes nativos do objeto em busca de erros de contagem de referência.</span><span class="sxs-lookup"><span data-stu-id="a5dab-111">Examine your reference counting code and search for errors as well as examining the native clients of your object for reference counting errors.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="a5dab-112">Efeito sobre o tempo de execução</span><span class="sxs-lookup"><span data-stu-id="a5dab-112">Effect on the Runtime</span></span>  
 <span data-ttu-id="a5dab-113">Há dois modos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="a5dab-113">Two modes are available.</span></span> <span data-ttu-id="a5dab-114">Se o atributo `allowAv` for `true`, o assistente evitará que o tempo de execução descarte a violação de acesso.</span><span class="sxs-lookup"><span data-stu-id="a5dab-114">If the `allowAv` attribute is `true`, the assistant prevents the runtime from discarding the access violation.</span></span> <span data-ttu-id="a5dab-115">Se `allowAv` for `false` (o padrão), o tempo de execução descartará a violação de acesso, mas uma mensagem de aviso será relatada ao usuário para indicar que uma exceção foi lançada e descartada.</span><span class="sxs-lookup"><span data-stu-id="a5dab-115">If `allowAv` is `false`, which is the default, the runtime discards the access violation, but a warning message is reported to the user to indicate that an exception was thrown and discarded.</span></span>  
  
## <a name="output"></a><span data-ttu-id="a5dab-116">Saída</span><span class="sxs-lookup"><span data-stu-id="a5dab-116">Output</span></span>  
 <span data-ttu-id="a5dab-117">Se possível, a saída contém a vtable original do ponteiro da interface COM.</span><span class="sxs-lookup"><span data-stu-id="a5dab-117">If possible, the output contains the COM interface pointer's original vtable.</span></span> <span data-ttu-id="a5dab-118">Do contrário, é exibida uma mensagem informativa.</span><span class="sxs-lookup"><span data-stu-id="a5dab-118">Otherwise, an informational message is displayed.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="a5dab-119">Configuração</span><span class="sxs-lookup"><span data-stu-id="a5dab-119">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <reportAvOnComRelease />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a5dab-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a5dab-120">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="a5dab-121">Diagnosticando erros com Assistentes de Depuração Gerenciados</span><span class="sxs-lookup"><span data-stu-id="a5dab-121">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="a5dab-122">Marshaling de interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="a5dab-122">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
