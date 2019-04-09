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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 87094532a52d8f6309998486375ef4eb33b07f20
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59189385"
---
# <a name="fatalexecutionengineerror-mda"></a><span data-ttu-id="9fa04-102">MDA fatalExecutionEngineError</span><span class="sxs-lookup"><span data-stu-id="9fa04-102">fatalExecutionEngineError MDA</span></span>
<span data-ttu-id="9fa04-103">O MDA (assistente para depuração gerenciada) `fatalExecutionEngineError` é ativado quando um erro fatal no CLR (Common Language Runtime) é detectado.</span><span class="sxs-lookup"><span data-stu-id="9fa04-103">The `fatalExecutionEngineError` managed debugging assistant (MDA) is activated when a fatal error in the common language runtime (CLR) has been detected.</span></span> <span data-ttu-id="9fa04-104">O processo será terminado.</span><span class="sxs-lookup"><span data-stu-id="9fa04-104">The process will be terminated.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="9fa04-105">Sintomas</span><span class="sxs-lookup"><span data-stu-id="9fa04-105">Symptoms</span></span>  
 <span data-ttu-id="9fa04-106">Término inesperado do processo.</span><span class="sxs-lookup"><span data-stu-id="9fa04-106">Unexpected process termination.</span></span> <span data-ttu-id="9fa04-107">Outros sintomas não podem ser determinados porque uma falha do CLR pode ocorrer por vários motivos.</span><span class="sxs-lookup"><span data-stu-id="9fa04-107">Other symptoms cannot be determined because a CLR failure can occur for a variety of reasons.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="9fa04-108">Causa</span><span class="sxs-lookup"><span data-stu-id="9fa04-108">Cause</span></span>  
 <span data-ttu-id="9fa04-109">O CLR foi fatalmente corrompido.</span><span class="sxs-lookup"><span data-stu-id="9fa04-109">The CLR has been fatally corrupted.</span></span> <span data-ttu-id="9fa04-110">Isso geralmente é causado por dados corrompidos, que podem ser causados por vários problemas, como chamadas a funções de invocação de plataforma malformadas e passagem de dados inválidos para o CLR.</span><span class="sxs-lookup"><span data-stu-id="9fa04-110">This is most often caused by data corruption, which can be caused by a number of problems, such as calls to malformed platform invoke functions and passing invalid data to the CLR.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="9fa04-111">Resolução</span><span class="sxs-lookup"><span data-stu-id="9fa04-111">Resolution</span></span>  
 <span data-ttu-id="9fa04-112">A habilitação de MDAs adicionais pode ajudar a identificar o problema.</span><span class="sxs-lookup"><span data-stu-id="9fa04-112">Enabling additional MDAs might help identify the problem.</span></span> <span data-ttu-id="9fa04-113">Os seguintes MDAs podem ser especialmente úteis para diagnosticar o problema:</span><span class="sxs-lookup"><span data-stu-id="9fa04-113">The following MDAs can be particularly helpful in diagnosing the issue:</span></span>  
  
-   [<span data-ttu-id="9fa04-114">invalidOverlappedToPinvoke</span><span class="sxs-lookup"><span data-stu-id="9fa04-114">invalidOverlappedToPinvoke</span></span>](../../../docs/framework/debug-trace-profile/invalidoverlappedtopinvoke-mda.md)  
  
-   [<span data-ttu-id="9fa04-115">overlappedFreeError</span><span class="sxs-lookup"><span data-stu-id="9fa04-115">overlappedFreeError</span></span>](../../../docs/framework/debug-trace-profile/overlappedfreeerror-mda.md)  
  
-   [<span data-ttu-id="9fa04-116">pInvokeStackImbalance</span><span class="sxs-lookup"><span data-stu-id="9fa04-116">pInvokeStackImbalance</span></span>](../../../docs/framework/debug-trace-profile/pinvokestackimbalance-mda.md)  
  
-   [<span data-ttu-id="9fa04-117">gcUnmanagedToManaged</span><span class="sxs-lookup"><span data-stu-id="9fa04-117">gcUnmanagedToManaged</span></span>](../../../docs/framework/debug-trace-profile/gcunmanagedtomanaged-mda.md)  
  
-   [<span data-ttu-id="9fa04-118">gcManagedToUnmanaged</span><span class="sxs-lookup"><span data-stu-id="9fa04-118">gcManagedToUnmanaged</span></span>](../../../docs/framework/debug-trace-profile/gcmanagedtounmanaged-mda.md)  
  
-   [<span data-ttu-id="9fa04-119">callbackOnCollectedDelegate</span><span class="sxs-lookup"><span data-stu-id="9fa04-119">callbackOnCollectedDelegate</span></span>](../../../docs/framework/debug-trace-profile/callbackoncollecteddelegate-mda.md)  
  
-   [<span data-ttu-id="9fa04-120">reportAvOnComRelease</span><span class="sxs-lookup"><span data-stu-id="9fa04-120">reportAvOnComRelease</span></span>](../../../docs/framework/debug-trace-profile/reportavoncomrelease-mda.md)  
  
-   [<span data-ttu-id="9fa04-121">invalidVariant</span><span class="sxs-lookup"><span data-stu-id="9fa04-121">invalidVariant</span></span>](../../../docs/framework/debug-trace-profile/invalidvariant-mda.md)  
  
-   [<span data-ttu-id="9fa04-122">invalidIUnknown</span><span class="sxs-lookup"><span data-stu-id="9fa04-122">invalidIUnknown</span></span>](../../../docs/framework/debug-trace-profile/invalidiunknown-mda.md)  
  
-   [<span data-ttu-id="9fa04-123">raceOnRCWCleanup</span><span class="sxs-lookup"><span data-stu-id="9fa04-123">raceOnRCWCleanup</span></span>](../../../docs/framework/debug-trace-profile/raceonrcwcleanup-mda.md)  
  
-   [<span data-ttu-id="9fa04-124">invalidFunctionPointerInDelegate</span><span class="sxs-lookup"><span data-stu-id="9fa04-124">invalidFunctionPointerInDelegate</span></span>](../../../docs/framework/debug-trace-profile/invalidfunctionpointerindelegate-mda.md)  
  
-   [<span data-ttu-id="9fa04-125">invalidGCHandleCookie</span><span class="sxs-lookup"><span data-stu-id="9fa04-125">invalidGCHandleCookie</span></span>](../../../docs/framework/debug-trace-profile/invalidgchandlecookie-mda.md)  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="9fa04-126">Efeito sobre o tempo de execução</span><span class="sxs-lookup"><span data-stu-id="9fa04-126">Effect on the Runtime</span></span>  
 <span data-ttu-id="9fa04-127">Esse MDA não tem nenhum efeito sobre o comportamento do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="9fa04-127">This MDA has no effect on the runtime's behavior.</span></span>  
  
## <a name="output"></a><span data-ttu-id="9fa04-128">Saída</span><span class="sxs-lookup"><span data-stu-id="9fa04-128">Output</span></span>  
 <span data-ttu-id="9fa04-129">O endereço da função CLR que causou o erro fatal, a ID do thread em que ocorreu o erro e o código de erro.</span><span class="sxs-lookup"><span data-stu-id="9fa04-129">The address of the CLR function that caused the fatal error, the ID of the thread where the error occurred, and the error code.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="9fa04-130">Configuração</span><span class="sxs-lookup"><span data-stu-id="9fa04-130">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <fatalExecutionEngineError />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9fa04-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9fa04-131">See also</span></span>

- <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A>
- <xref:System.Runtime.ConstrainedExecution.Cer>
- [<span data-ttu-id="9fa04-132">Diagnosticando erros com assistentes de depuração gerenciados</span><span class="sxs-lookup"><span data-stu-id="9fa04-132">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
