---
title: MDA fatalExecutionEngineError
ms.date: 03/30/2017
helpviewer_keywords:
- corrupted CLR
- fatal execution error
- terminated processes
- unexpected terminations
- fatal errors
- MDAs (managed debugging assistants), fatal errors
- process termination
- FatalExecutionEngineError MDA
- managed debugging assistants (MDAs), fatal errors
ms.assetid: 8b559e44-2393-4e4e-8160-7558d37a4a89
ms.openlocfilehash: e25c9ef6ec43089f1d85479d1afe301232ed1d4f
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217497"
---
# <a name="fatalexecutionengineerror-mda"></a><span data-ttu-id="7adcb-102">MDA fatalExecutionEngineError</span><span class="sxs-lookup"><span data-stu-id="7adcb-102">fatalExecutionEngineError MDA</span></span>
<span data-ttu-id="7adcb-103">O MDA (assistente para depuração gerenciada) `fatalExecutionEngineError` é ativado quando um erro fatal no CLR (Common Language Runtime) é detectado.</span><span class="sxs-lookup"><span data-stu-id="7adcb-103">The `fatalExecutionEngineError` managed debugging assistant (MDA) is activated when a fatal error in the common language runtime (CLR) has been detected.</span></span> <span data-ttu-id="7adcb-104">O processo será terminado.</span><span class="sxs-lookup"><span data-stu-id="7adcb-104">The process will be terminated.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="7adcb-105">Sintomas</span><span class="sxs-lookup"><span data-stu-id="7adcb-105">Symptoms</span></span>  
 <span data-ttu-id="7adcb-106">Término inesperado do processo.</span><span class="sxs-lookup"><span data-stu-id="7adcb-106">Unexpected process termination.</span></span> <span data-ttu-id="7adcb-107">Outros sintomas não podem ser determinados porque uma falha do CLR pode ocorrer por vários motivos.</span><span class="sxs-lookup"><span data-stu-id="7adcb-107">Other symptoms cannot be determined because a CLR failure can occur for a variety of reasons.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="7adcb-108">Causa</span><span class="sxs-lookup"><span data-stu-id="7adcb-108">Cause</span></span>  
 <span data-ttu-id="7adcb-109">O CLR foi fatalmente corrompido.</span><span class="sxs-lookup"><span data-stu-id="7adcb-109">The CLR has been fatally corrupted.</span></span> <span data-ttu-id="7adcb-110">Isso geralmente é causado por dados corrompidos, que podem ser causados por vários problemas, como chamadas a funções de invocação de plataforma malformadas e passagem de dados inválidos para o CLR.</span><span class="sxs-lookup"><span data-stu-id="7adcb-110">This is most often caused by data corruption, which can be caused by a number of problems, such as calls to malformed platform invoke functions and passing invalid data to the CLR.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="7adcb-111">Resolução</span><span class="sxs-lookup"><span data-stu-id="7adcb-111">Resolution</span></span>  
 <span data-ttu-id="7adcb-112">A habilitação de MDAs adicionais pode ajudar a identificar o problema.</span><span class="sxs-lookup"><span data-stu-id="7adcb-112">Enabling additional MDAs might help identify the problem.</span></span> <span data-ttu-id="7adcb-113">Os seguintes MDAs podem ser especialmente úteis para diagnosticar o problema:</span><span class="sxs-lookup"><span data-stu-id="7adcb-113">The following MDAs can be particularly helpful in diagnosing the issue:</span></span>  
  
- [<span data-ttu-id="7adcb-114">invalidOverlappedToPinvoke</span><span class="sxs-lookup"><span data-stu-id="7adcb-114">invalidOverlappedToPinvoke</span></span>](invalidoverlappedtopinvoke-mda.md)  
  
- [<span data-ttu-id="7adcb-115">overlappedFreeError</span><span class="sxs-lookup"><span data-stu-id="7adcb-115">overlappedFreeError</span></span>](overlappedfreeerror-mda.md)  
  
- [<span data-ttu-id="7adcb-116">pInvokeStackImbalance</span><span class="sxs-lookup"><span data-stu-id="7adcb-116">pInvokeStackImbalance</span></span>](pinvokestackimbalance-mda.md)  
  
- [<span data-ttu-id="7adcb-117">gcUnmanagedToManaged</span><span class="sxs-lookup"><span data-stu-id="7adcb-117">gcUnmanagedToManaged</span></span>](gcunmanagedtomanaged-mda.md)  
  
- [<span data-ttu-id="7adcb-118">gcManagedToUnmanaged</span><span class="sxs-lookup"><span data-stu-id="7adcb-118">gcManagedToUnmanaged</span></span>](gcmanagedtounmanaged-mda.md)  
  
- [<span data-ttu-id="7adcb-119">callbackOnCollectedDelegate</span><span class="sxs-lookup"><span data-stu-id="7adcb-119">callbackOnCollectedDelegate</span></span>](callbackoncollecteddelegate-mda.md)  
  
- [<span data-ttu-id="7adcb-120">reportAvOnComRelease</span><span class="sxs-lookup"><span data-stu-id="7adcb-120">reportAvOnComRelease</span></span>](reportavoncomrelease-mda.md)  
  
- [<span data-ttu-id="7adcb-121">invalidVariant</span><span class="sxs-lookup"><span data-stu-id="7adcb-121">invalidVariant</span></span>](invalidvariant-mda.md)  
  
- [<span data-ttu-id="7adcb-122">invalidIUnknown</span><span class="sxs-lookup"><span data-stu-id="7adcb-122">invalidIUnknown</span></span>](invalidiunknown-mda.md)  
  
- [<span data-ttu-id="7adcb-123">raceOnRCWCleanup</span><span class="sxs-lookup"><span data-stu-id="7adcb-123">raceOnRCWCleanup</span></span>](raceonrcwcleanup-mda.md)  
  
- [<span data-ttu-id="7adcb-124">invalidFunctionPointerInDelegate</span><span class="sxs-lookup"><span data-stu-id="7adcb-124">invalidFunctionPointerInDelegate</span></span>](invalidfunctionpointerindelegate-mda.md)  
  
- [<span data-ttu-id="7adcb-125">invalidGCHandleCookie</span><span class="sxs-lookup"><span data-stu-id="7adcb-125">invalidGCHandleCookie</span></span>](invalidgchandlecookie-mda.md)  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="7adcb-126">Efeito sobre o runtime</span><span class="sxs-lookup"><span data-stu-id="7adcb-126">Effect on the Runtime</span></span>  
 <span data-ttu-id="7adcb-127">Esse MDA não tem nenhum efeito sobre o comportamento do runtime.</span><span class="sxs-lookup"><span data-stu-id="7adcb-127">This MDA has no effect on the runtime's behavior.</span></span>  
  
## <a name="output"></a><span data-ttu-id="7adcb-128">Saída</span><span class="sxs-lookup"><span data-stu-id="7adcb-128">Output</span></span>  
 <span data-ttu-id="7adcb-129">O endereço da função CLR que causou o erro fatal, a ID do thread em que ocorreu o erro e o código de erro.</span><span class="sxs-lookup"><span data-stu-id="7adcb-129">The address of the CLR function that caused the fatal error, the ID of the thread where the error occurred, and the error code.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="7adcb-130">Configuração</span><span class="sxs-lookup"><span data-stu-id="7adcb-130">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <fatalExecutionEngineError />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7adcb-131">Confira também</span><span class="sxs-lookup"><span data-stu-id="7adcb-131">See also</span></span>

- <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A>
- <xref:System.Runtime.ConstrainedExecution.Cer>
- [<span data-ttu-id="7adcb-132">Diagnosticando erros com Assistentes de Depuração Gerenciados</span><span class="sxs-lookup"><span data-stu-id="7adcb-132">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
