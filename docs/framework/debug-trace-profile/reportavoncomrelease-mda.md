---
title: MDA reportAvOnComRelease
description: Examine o MDA (Assistente de depuração gerenciada) reportAvOnComRelease, que pode ser ativado devido a violações de acesso e corrupção de memória no .NET.
ms.date: 03/30/2017
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
ms.openlocfilehash: f9ba343060cb4d16de5909a5b619353546aca8ca
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85803602"
---
# <a name="reportavoncomrelease-mda"></a><span data-ttu-id="61a5e-103">MDA reportAvOnComRelease</span><span class="sxs-lookup"><span data-stu-id="61a5e-103">reportAvOnComRelease MDA</span></span>
<span data-ttu-id="61a5e-104">O MDA (Assistente para Depuração Gerenciada) do `reportAvOnComRelease` é ativado quando as exceções são lançadas por causa da contagem de erros pela referência do usuário durante a realização da interoperabilidade COM e do uso do método <xref:System.Runtime.InteropServices.Marshal.Release%2A> ou <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> combinado com chamadas COM brutas.</span><span class="sxs-lookup"><span data-stu-id="61a5e-104">The `reportAvOnComRelease` managed debugging assistant (MDA) is activated when exceptions are thrown due to user reference counting errors while performing COM interop and using the <xref:System.Runtime.InteropServices.Marshal.Release%2A> or <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> method combined with raw COM calls.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="61a5e-105">Sintomas</span><span class="sxs-lookup"><span data-stu-id="61a5e-105">Symptoms</span></span>  
 <span data-ttu-id="61a5e-106">Violações de acesso e corrupção de memória.</span><span class="sxs-lookup"><span data-stu-id="61a5e-106">Access violations and memory corruption.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="61a5e-107">Causa</span><span class="sxs-lookup"><span data-stu-id="61a5e-107">Cause</span></span>  
 <span data-ttu-id="61a5e-108">Às vezes, uma exceção é lançada por causa da contagem de erros pela referência do usuário durante a realização da interoperabilidade COM e do uso do método <xref:System.Runtime.InteropServices.Marshal.Release%2A> ou <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> combinado com chamadas COM brutas.</span><span class="sxs-lookup"><span data-stu-id="61a5e-108">Occasionally, an exception is thrown due to user reference counting errors while performing COM interop and using the <xref:System.Runtime.InteropServices.Marshal.Release%2A> or <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> method combined with raw COM calls.</span></span> <span data-ttu-id="61a5e-109">Normalmente, essa exceção é descartada porque deixar de fazer isso causaria uma violação de acesso no CLR, desativando-o.</span><span class="sxs-lookup"><span data-stu-id="61a5e-109">Normally, this exception is discarded because not doing so would cause an access violation in the CLR, bringing it down.</span></span> <span data-ttu-id="61a5e-110">Quando esse assistente é habilitado, essas exceções podem ser detectadas e relatadas em vez de ser simplesmente descartadas.</span><span class="sxs-lookup"><span data-stu-id="61a5e-110">When this assistant is enabled, such exceptions can be detected and reported instead of being simply discarded.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="61a5e-111">Resolução</span><span class="sxs-lookup"><span data-stu-id="61a5e-111">Resolution</span></span>  
 <span data-ttu-id="61a5e-112">Examine o código de contagem de referência e procure erros, também examine os clientes nativos do objeto em busca de erros de contagem de referência.</span><span class="sxs-lookup"><span data-stu-id="61a5e-112">Examine your reference counting code and search for errors as well as examining the native clients of your object for reference counting errors.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="61a5e-113">Efeito sobre o runtime</span><span class="sxs-lookup"><span data-stu-id="61a5e-113">Effect on the Runtime</span></span>  
 <span data-ttu-id="61a5e-114">Há dois modos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="61a5e-114">Two modes are available.</span></span> <span data-ttu-id="61a5e-115">Se o atributo `allowAv` for `true`, o assistente evitará que o runtime descarte a violação de acesso.</span><span class="sxs-lookup"><span data-stu-id="61a5e-115">If the `allowAv` attribute is `true`, the assistant prevents the runtime from discarding the access violation.</span></span> <span data-ttu-id="61a5e-116">Se `allowAv` for `false` (o padrão), o runtime descartará a violação de acesso, mas uma mensagem de aviso será relatada ao usuário para indicar que uma exceção foi lançada e descartada.</span><span class="sxs-lookup"><span data-stu-id="61a5e-116">If `allowAv` is `false`, which is the default, the runtime discards the access violation, but a warning message is reported to the user to indicate that an exception was thrown and discarded.</span></span>  
  
## <a name="output"></a><span data-ttu-id="61a5e-117">Saída</span><span class="sxs-lookup"><span data-stu-id="61a5e-117">Output</span></span>  
 <span data-ttu-id="61a5e-118">Se possível, a saída contém a vtable original do ponteiro da interface COM.</span><span class="sxs-lookup"><span data-stu-id="61a5e-118">If possible, the output contains the COM interface pointer's original vtable.</span></span> <span data-ttu-id="61a5e-119">Do contrário, é exibida uma mensagem informativa.</span><span class="sxs-lookup"><span data-stu-id="61a5e-119">Otherwise, an informational message is displayed.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="61a5e-120">Configuração</span><span class="sxs-lookup"><span data-stu-id="61a5e-120">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <reportAvOnComRelease />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="61a5e-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="61a5e-121">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="61a5e-122">Diagnosticando erros com assistentes para depuração gerenciada</span><span class="sxs-lookup"><span data-stu-id="61a5e-122">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="61a5e-123">Realizando marshaling de interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="61a5e-123">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
