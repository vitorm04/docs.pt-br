---
title: MDA fatalExecutionEngineError
description: Examine o MDA (Assistente de depuração gerenciada) do fatalExecutionEngineError no .NET, que pode ser ativado devido a um encerramento de processo inesperado.
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
ms.openlocfilehash: 0806d2eaa1752c88bebd03304fbe5c8094416a48
ms.sourcegitcommit: a2c8b19e813a52b91facbb5d7e3c062c7188b457
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85415921"
---
# <a name="fatalexecutionengineerror-mda"></a><span data-ttu-id="b83ab-103">MDA fatalExecutionEngineError</span><span class="sxs-lookup"><span data-stu-id="b83ab-103">fatalExecutionEngineError MDA</span></span>
<span data-ttu-id="b83ab-104">O MDA (assistente para depuração gerenciada) `fatalExecutionEngineError` é ativado quando um erro fatal no CLR (Common Language Runtime) é detectado.</span><span class="sxs-lookup"><span data-stu-id="b83ab-104">The `fatalExecutionEngineError` managed debugging assistant (MDA) is activated when a fatal error in the common language runtime (CLR) has been detected.</span></span> <span data-ttu-id="b83ab-105">O processo será terminado.</span><span class="sxs-lookup"><span data-stu-id="b83ab-105">The process will be terminated.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="b83ab-106">Sintomas</span><span class="sxs-lookup"><span data-stu-id="b83ab-106">Symptoms</span></span>  
 <span data-ttu-id="b83ab-107">Término inesperado do processo.</span><span class="sxs-lookup"><span data-stu-id="b83ab-107">Unexpected process termination.</span></span> <span data-ttu-id="b83ab-108">Outros sintomas não podem ser determinados porque uma falha do CLR pode ocorrer por vários motivos.</span><span class="sxs-lookup"><span data-stu-id="b83ab-108">Other symptoms cannot be determined because a CLR failure can occur for a variety of reasons.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="b83ab-109">Causa</span><span class="sxs-lookup"><span data-stu-id="b83ab-109">Cause</span></span>  
 <span data-ttu-id="b83ab-110">O CLR foi fatalmente corrompido.</span><span class="sxs-lookup"><span data-stu-id="b83ab-110">The CLR has been fatally corrupted.</span></span> <span data-ttu-id="b83ab-111">Isso geralmente é causado por dados corrompidos, que podem ser causados por vários problemas, como chamadas a funções de invocação de plataforma malformadas e passagem de dados inválidos para o CLR.</span><span class="sxs-lookup"><span data-stu-id="b83ab-111">This is most often caused by data corruption, which can be caused by a number of problems, such as calls to malformed platform invoke functions and passing invalid data to the CLR.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="b83ab-112">Resolução</span><span class="sxs-lookup"><span data-stu-id="b83ab-112">Resolution</span></span>  
 <span data-ttu-id="b83ab-113">A habilitação de MDAs adicionais pode ajudar a identificar o problema.</span><span class="sxs-lookup"><span data-stu-id="b83ab-113">Enabling additional MDAs might help identify the problem.</span></span> <span data-ttu-id="b83ab-114">Os seguintes MDAs podem ser especialmente úteis para diagnosticar o problema:</span><span class="sxs-lookup"><span data-stu-id="b83ab-114">The following MDAs can be particularly helpful in diagnosing the issue:</span></span>  
  
- [<span data-ttu-id="b83ab-115">invalidOverlappedToPinvoke</span><span class="sxs-lookup"><span data-stu-id="b83ab-115">invalidOverlappedToPinvoke</span></span>](invalidoverlappedtopinvoke-mda.md)  
  
- [<span data-ttu-id="b83ab-116">overlappedFreeError</span><span class="sxs-lookup"><span data-stu-id="b83ab-116">overlappedFreeError</span></span>](overlappedfreeerror-mda.md)  
  
- [<span data-ttu-id="b83ab-117">pInvokeStackImbalance</span><span class="sxs-lookup"><span data-stu-id="b83ab-117">pInvokeStackImbalance</span></span>](pinvokestackimbalance-mda.md)  
  
- [<span data-ttu-id="b83ab-118">gcUnmanagedToManaged</span><span class="sxs-lookup"><span data-stu-id="b83ab-118">gcUnmanagedToManaged</span></span>](gcunmanagedtomanaged-mda.md)  
  
- [<span data-ttu-id="b83ab-119">gcManagedToUnmanaged</span><span class="sxs-lookup"><span data-stu-id="b83ab-119">gcManagedToUnmanaged</span></span>](gcmanagedtounmanaged-mda.md)  
  
- [<span data-ttu-id="b83ab-120">callbackOnCollectedDelegate</span><span class="sxs-lookup"><span data-stu-id="b83ab-120">callbackOnCollectedDelegate</span></span>](callbackoncollecteddelegate-mda.md)  
  
- [<span data-ttu-id="b83ab-121">reportAvOnComRelease</span><span class="sxs-lookup"><span data-stu-id="b83ab-121">reportAvOnComRelease</span></span>](reportavoncomrelease-mda.md)  
  
- [<span data-ttu-id="b83ab-122">invalidVariant</span><span class="sxs-lookup"><span data-stu-id="b83ab-122">invalidVariant</span></span>](invalidvariant-mda.md)  
  
- [<span data-ttu-id="b83ab-123">invalidIUnknown</span><span class="sxs-lookup"><span data-stu-id="b83ab-123">invalidIUnknown</span></span>](invalidiunknown-mda.md)  
  
- [<span data-ttu-id="b83ab-124">raceOnRCWCleanup</span><span class="sxs-lookup"><span data-stu-id="b83ab-124">raceOnRCWCleanup</span></span>](raceonrcwcleanup-mda.md)  
  
- [<span data-ttu-id="b83ab-125">invalidFunctionPointerInDelegate</span><span class="sxs-lookup"><span data-stu-id="b83ab-125">invalidFunctionPointerInDelegate</span></span>](invalidfunctionpointerindelegate-mda.md)  
  
- [<span data-ttu-id="b83ab-126">invalidGCHandleCookie</span><span class="sxs-lookup"><span data-stu-id="b83ab-126">invalidGCHandleCookie</span></span>](invalidgchandlecookie-mda.md)  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="b83ab-127">Efeito sobre o runtime</span><span class="sxs-lookup"><span data-stu-id="b83ab-127">Effect on the Runtime</span></span>  
 <span data-ttu-id="b83ab-128">Esse MDA não tem nenhum efeito sobre o comportamento do runtime.</span><span class="sxs-lookup"><span data-stu-id="b83ab-128">This MDA has no effect on the runtime's behavior.</span></span>  
  
## <a name="output"></a><span data-ttu-id="b83ab-129">Saída</span><span class="sxs-lookup"><span data-stu-id="b83ab-129">Output</span></span>  
 <span data-ttu-id="b83ab-130">O endereço da função CLR que causou o erro fatal, a ID do thread em que ocorreu o erro e o código de erro.</span><span class="sxs-lookup"><span data-stu-id="b83ab-130">The address of the CLR function that caused the fatal error, the ID of the thread where the error occurred, and the error code.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="b83ab-131">Configuração</span><span class="sxs-lookup"><span data-stu-id="b83ab-131">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <fatalExecutionEngineError />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b83ab-132">Veja também</span><span class="sxs-lookup"><span data-stu-id="b83ab-132">See also</span></span>

- <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A>
- <xref:System.Runtime.ConstrainedExecution.Cer>
- [<span data-ttu-id="b83ab-133">Diagnosticando erros com assistentes para depuração gerenciada</span><span class="sxs-lookup"><span data-stu-id="b83ab-133">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
