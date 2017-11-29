---
title: MDA fatalExecutionEngineError
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: cda166645bad2ad7780da58c287880398605806f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="fatalexecutionengineerror-mda"></a><span data-ttu-id="a323b-102">MDA fatalExecutionEngineError</span><span class="sxs-lookup"><span data-stu-id="a323b-102">fatalExecutionEngineError MDA</span></span>
<span data-ttu-id="a323b-103">O MDA (assistente para depuração gerenciada) `fatalExecutionEngine``Error` é ativado quando um erro fatal no CLR (Common Language Runtime) é detectado.</span><span class="sxs-lookup"><span data-stu-id="a323b-103">The `fatalExecutionEngine``Error` managed debugging assistant (MDA) is activated when a fatal error in the common language runtime (CLR) has been detected.</span></span> <span data-ttu-id="a323b-104">O processo será terminado.</span><span class="sxs-lookup"><span data-stu-id="a323b-104">The process will be terminated.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="a323b-105">Sintomas</span><span class="sxs-lookup"><span data-stu-id="a323b-105">Symptoms</span></span>  
 <span data-ttu-id="a323b-106">Término inesperado do processo.</span><span class="sxs-lookup"><span data-stu-id="a323b-106">Unexpected process termination.</span></span> <span data-ttu-id="a323b-107">Outros sintomas não podem ser determinados porque uma falha do CLR pode ocorrer por vários motivos.</span><span class="sxs-lookup"><span data-stu-id="a323b-107">Other symptoms cannot be determined because a CLR failure can occur for a variety of reasons.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="a323b-108">Causa</span><span class="sxs-lookup"><span data-stu-id="a323b-108">Cause</span></span>  
 <span data-ttu-id="a323b-109">O CLR foi fatalmente corrompido.</span><span class="sxs-lookup"><span data-stu-id="a323b-109">The CLR has been fatally corrupted.</span></span> <span data-ttu-id="a323b-110">Isso geralmente é causado por dados corrompidos, que podem ser causados por vários problemas, como chamadas a funções de invocação de plataforma malformadas e passagem de dados inválidos para o CLR.</span><span class="sxs-lookup"><span data-stu-id="a323b-110">This is most often caused by data corruption, which can be caused by a number of problems, such as calls to malformed platform invoke functions and passing invalid data to the CLR.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="a323b-111">Resolução</span><span class="sxs-lookup"><span data-stu-id="a323b-111">Resolution</span></span>  
 <span data-ttu-id="a323b-112">A habilitação de MDAs adicionais pode ajudar a identificar o problema.</span><span class="sxs-lookup"><span data-stu-id="a323b-112">Enabling additional MDAs might help identify the problem.</span></span> <span data-ttu-id="a323b-113">Os seguintes MDAs podem ser especialmente úteis para diagnosticar o problema:</span><span class="sxs-lookup"><span data-stu-id="a323b-113">The following MDAs can be particularly helpful in diagnosing the issue:</span></span>  
  
-   [<span data-ttu-id="a323b-114">invalidOverlappedToPinvoke</span><span class="sxs-lookup"><span data-stu-id="a323b-114">invalidOverlappedToPinvoke</span></span>](../../../docs/framework/debug-trace-profile/invalidoverlappedtopinvoke-mda.md)  
  
-   [<span data-ttu-id="a323b-115">overlappedFreeError</span><span class="sxs-lookup"><span data-stu-id="a323b-115">overlappedFreeError</span></span>](../../../docs/framework/debug-trace-profile/overlappedfreeerror-mda.md)  
  
-   [<span data-ttu-id="a323b-116">pInvokeStackImbalance</span><span class="sxs-lookup"><span data-stu-id="a323b-116">pInvokeStackImbalance</span></span>](../../../docs/framework/debug-trace-profile/pinvokestackimbalance-mda.md)  
  
-   [<span data-ttu-id="a323b-117">gcUnmanagedToManaged</span><span class="sxs-lookup"><span data-stu-id="a323b-117">gcUnmanagedToManaged</span></span>](../../../docs/framework/debug-trace-profile/gcunmanagedtomanaged-mda.md)  
  
-   [<span data-ttu-id="a323b-118">gcManagedToUnmanaged</span><span class="sxs-lookup"><span data-stu-id="a323b-118">gcManagedToUnmanaged</span></span>](../../../docs/framework/debug-trace-profile/gcmanagedtounmanaged-mda.md)  
  
-   [<span data-ttu-id="a323b-119">callbackOnCollectedDelegate</span><span class="sxs-lookup"><span data-stu-id="a323b-119">callbackOnCollectedDelegate</span></span>](../../../docs/framework/debug-trace-profile/callbackoncollecteddelegate-mda.md)  
  
-   [<span data-ttu-id="a323b-120">reportAvOnComRelease</span><span class="sxs-lookup"><span data-stu-id="a323b-120">reportAvOnComRelease</span></span>](../../../docs/framework/debug-trace-profile/reportavoncomrelease-mda.md)  
  
-   [<span data-ttu-id="a323b-121">invalidVariant</span><span class="sxs-lookup"><span data-stu-id="a323b-121">invalidVariant</span></span>](../../../docs/framework/debug-trace-profile/invalidvariant-mda.md)  
  
-   [<span data-ttu-id="a323b-122">invalidIUnknown</span><span class="sxs-lookup"><span data-stu-id="a323b-122">invalidIUnknown</span></span>](../../../docs/framework/debug-trace-profile/invalidiunknown-mda.md)  
  
-   [<span data-ttu-id="a323b-123">raceOnRCWCleanup</span><span class="sxs-lookup"><span data-stu-id="a323b-123">raceOnRCWCleanup</span></span>](../../../docs/framework/debug-trace-profile/raceonrcwcleanup-mda.md)  
  
-   [<span data-ttu-id="a323b-124">invalidFunctionPointerInDelegate</span><span class="sxs-lookup"><span data-stu-id="a323b-124">invalidFunctionPointerInDelegate</span></span>](../../../docs/framework/debug-trace-profile/invalidfunctionpointerindelegate-mda.md)  
  
-   [<span data-ttu-id="a323b-125">invalidGCHandleCookie</span><span class="sxs-lookup"><span data-stu-id="a323b-125">invalidGCHandleCookie</span></span>](../../../docs/framework/debug-trace-profile/invalidgchandlecookie-mda.md)  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="a323b-126">Efeito sobre o tempo de execução</span><span class="sxs-lookup"><span data-stu-id="a323b-126">Effect on the Runtime</span></span>  
 <span data-ttu-id="a323b-127">Esse MDA não tem nenhum efeito sobre o comportamento do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="a323b-127">This MDA has no effect on the runtime's behavior.</span></span>  
  
## <a name="output"></a><span data-ttu-id="a323b-128">Saída</span><span class="sxs-lookup"><span data-stu-id="a323b-128">Output</span></span>  
 <span data-ttu-id="a323b-129">O endereço da função CLR que causou o erro fatal, a ID do thread em que ocorreu o erro e o código de erro.</span><span class="sxs-lookup"><span data-stu-id="a323b-129">The address of the CLR function that caused the fatal error, the ID of the thread where the error occurred, and the error code.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="a323b-130">Configuração</span><span class="sxs-lookup"><span data-stu-id="a323b-130">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <fatalExecutionEngineError />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a323b-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a323b-131">See Also</span></span>  
 <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A>  
 <xref:System.Runtime.ConstrainedExecution.Cer>  
 [<span data-ttu-id="a323b-132">Diagnosticando erros com Assistentes de Depuração Gerenciados</span><span class="sxs-lookup"><span data-stu-id="a323b-132">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
