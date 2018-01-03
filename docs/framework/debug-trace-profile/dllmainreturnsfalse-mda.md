---
title: MDA dllMainReturnsFalse
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managed debugging assistants (MDAs), DllMain returns false
- DllMainReturnsFalse MDA
- DllMain function
- MDAs (managed debugging assistants), DllMain returns false
ms.assetid: e2abdd04-f571-4b97-8c16-2221b8588429
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: eb5de2b1c41d102fbf9fc47db0ff3d8bd72a3bcd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="dllmainreturnsfalse-mda"></a><span data-ttu-id="bac3a-102">MDA dllMainReturnsFalse</span><span class="sxs-lookup"><span data-stu-id="bac3a-102">dllMainReturnsFalse MDA</span></span>
<span data-ttu-id="bac3a-103">O MDA (assistente para depuração gerenciada) `dllMainReturnsFalse` é ativado se a função `DllMain` gerenciada de um assembly de usuário, chamada com o motivo DLL_PROCESS_ATTACH, retorna FALSE.</span><span class="sxs-lookup"><span data-stu-id="bac3a-103">The `dllMainReturnsFalse` managed debugging assistant (MDA) is activated if the managed `DllMain` function of a user assembly, called with reason DLL_PROCESS_ATTACH, returns FALSE.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="bac3a-104">Sintomas</span><span class="sxs-lookup"><span data-stu-id="bac3a-104">Symptoms</span></span>  
 <span data-ttu-id="bac3a-105">A função `DllMain` retornou FALSE, indicando que ela não foi executada corretamente.</span><span class="sxs-lookup"><span data-stu-id="bac3a-105">The `DllMain` function returned FALSE, indicating that it did not execute properly.</span></span> <span data-ttu-id="bac3a-106">Isso pode causar problemas indeterminados porque as funções `DllMain` normalmente contêm um código de inicialização importante.</span><span class="sxs-lookup"><span data-stu-id="bac3a-106">This can cause undetermined issues because `DllMain` functions typically contain important initialization code.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="bac3a-107">Causa</span><span class="sxs-lookup"><span data-stu-id="bac3a-107">Cause</span></span>  
 <span data-ttu-id="bac3a-108">A função `DllMain` é chamada com o motivo DLL_PROCESS_ATTACH para a inicialização da DLL após o carregamento.</span><span class="sxs-lookup"><span data-stu-id="bac3a-108">The `DllMain` function is called with reason DLL_PROCESS_ATTACH for DLL initialization upon load.</span></span> <span data-ttu-id="bac3a-109">Se ela retorna FALSE, isso significa que a inicialização da DLL falhou.</span><span class="sxs-lookup"><span data-stu-id="bac3a-109">If it returns FALSE, it means that DLL initialization failed.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="bac3a-110">Resolução</span><span class="sxs-lookup"><span data-stu-id="bac3a-110">Resolution</span></span>  
 <span data-ttu-id="bac3a-111">Analise o código da função `DllMain` da DLL com falha e identifique a causa da falha de inicialização.</span><span class="sxs-lookup"><span data-stu-id="bac3a-111">Analyze the code of the `DllMain` function of the failed DLL and identify the cause of the initialization failure.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="bac3a-112">Efeito sobre o tempo de execução</span><span class="sxs-lookup"><span data-stu-id="bac3a-112">Effect on the Runtime</span></span>  
 <span data-ttu-id="bac3a-113">Esse MDA não tem efeito sobre o CLR.</span><span class="sxs-lookup"><span data-stu-id="bac3a-113">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="bac3a-114">Ele apenas relata dados sobre o valor retornado de `DllMain`.</span><span class="sxs-lookup"><span data-stu-id="bac3a-114">It only reports data about the return value for `DllMain`.</span></span>  
  
## <a name="output"></a><span data-ttu-id="bac3a-115">Saída</span><span class="sxs-lookup"><span data-stu-id="bac3a-115">Output</span></span>  
 <span data-ttu-id="bac3a-116">Uma mensagem indicando que uma função `DllMain`, chamada pelo motivo DLL_PROCESS_ATTACH, retornou FALSE.</span><span class="sxs-lookup"><span data-stu-id="bac3a-116">A message indicating that a `DllMain` function, called for reason DLL_PROCESS_ATTACH, returned FALSE.</span></span> <span data-ttu-id="bac3a-117">Observe que esse MDA é ativado somente se `DllMain` é implementado no código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="bac3a-117">Note that this MDA is activated only if `DllMain` is implemented in managed code.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="bac3a-118">Configuração</span><span class="sxs-lookup"><span data-stu-id="bac3a-118">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dllMainReturnsFalse />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="bac3a-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bac3a-119">See Also</span></span>  
 [<span data-ttu-id="bac3a-120">Diagnosticando erros com Assistentes de Depuração Gerenciados</span><span class="sxs-lookup"><span data-stu-id="bac3a-120">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
