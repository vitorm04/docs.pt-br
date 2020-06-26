---
title: MDA dllMainReturnsFalse
description: Leia sobre o assistente de depuração gerenciada do dllMainReturnsFalse no .NET. Este MDA será ativado se a inicialização da DLL falhar.
ms.date: 03/30/2017
helpviewer_keywords:
- managed debugging assistants (MDAs), DllMain returns false
- DllMainReturnsFalse MDA
- DllMain function
- MDAs (managed debugging assistants), DllMain returns false
ms.assetid: e2abdd04-f571-4b97-8c16-2221b8588429
ms.openlocfilehash: 21d5e37d6823876e07cf5b2cbb881c1cf8b47b11
ms.sourcegitcommit: a2c8b19e813a52b91facbb5d7e3c062c7188b457
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85416051"
---
# <a name="dllmainreturnsfalse-mda"></a><span data-ttu-id="53c37-104">MDA dllMainReturnsFalse</span><span class="sxs-lookup"><span data-stu-id="53c37-104">dllMainReturnsFalse MDA</span></span>
<span data-ttu-id="53c37-105">O MDA (assistente para depuração gerenciada) `dllMainReturnsFalse` é ativado se a função `DllMain` gerenciada de um assembly de usuário, chamada com o motivo DLL_PROCESS_ATTACH, retorna FALSE.</span><span class="sxs-lookup"><span data-stu-id="53c37-105">The `dllMainReturnsFalse` managed debugging assistant (MDA) is activated if the managed `DllMain` function of a user assembly, called with reason DLL_PROCESS_ATTACH, returns FALSE.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="53c37-106">Sintomas</span><span class="sxs-lookup"><span data-stu-id="53c37-106">Symptoms</span></span>  
 <span data-ttu-id="53c37-107">A função `DllMain` retornou FALSE, indicando que ela não foi executada corretamente.</span><span class="sxs-lookup"><span data-stu-id="53c37-107">The `DllMain` function returned FALSE, indicating that it did not execute properly.</span></span> <span data-ttu-id="53c37-108">Isso pode causar problemas indeterminados porque as funções `DllMain` normalmente contêm um código de inicialização importante.</span><span class="sxs-lookup"><span data-stu-id="53c37-108">This can cause undetermined issues because `DllMain` functions typically contain important initialization code.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="53c37-109">Causa</span><span class="sxs-lookup"><span data-stu-id="53c37-109">Cause</span></span>  
 <span data-ttu-id="53c37-110">A função `DllMain` é chamada com o motivo DLL_PROCESS_ATTACH para a inicialização da DLL após o carregamento.</span><span class="sxs-lookup"><span data-stu-id="53c37-110">The `DllMain` function is called with reason DLL_PROCESS_ATTACH for DLL initialization upon load.</span></span> <span data-ttu-id="53c37-111">Se ela retorna FALSE, isso significa que a inicialização da DLL falhou.</span><span class="sxs-lookup"><span data-stu-id="53c37-111">If it returns FALSE, it means that DLL initialization failed.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="53c37-112">Resolução</span><span class="sxs-lookup"><span data-stu-id="53c37-112">Resolution</span></span>  
 <span data-ttu-id="53c37-113">Analise o código da função `DllMain` da DLL com falha e identifique a causa da falha de inicialização.</span><span class="sxs-lookup"><span data-stu-id="53c37-113">Analyze the code of the `DllMain` function of the failed DLL and identify the cause of the initialization failure.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="53c37-114">Efeito sobre o runtime</span><span class="sxs-lookup"><span data-stu-id="53c37-114">Effect on the Runtime</span></span>  
 <span data-ttu-id="53c37-115">Esse MDA não tem efeito sobre o CLR.</span><span class="sxs-lookup"><span data-stu-id="53c37-115">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="53c37-116">Ele apenas relata dados sobre o valor retornado de `DllMain`.</span><span class="sxs-lookup"><span data-stu-id="53c37-116">It only reports data about the return value for `DllMain`.</span></span>  
  
## <a name="output"></a><span data-ttu-id="53c37-117">Saída</span><span class="sxs-lookup"><span data-stu-id="53c37-117">Output</span></span>  
 <span data-ttu-id="53c37-118">Uma mensagem indicando que uma função `DllMain`, chamada pelo motivo DLL_PROCESS_ATTACH, retornou FALSE.</span><span class="sxs-lookup"><span data-stu-id="53c37-118">A message indicating that a `DllMain` function, called for reason DLL_PROCESS_ATTACH, returned FALSE.</span></span> <span data-ttu-id="53c37-119">Observe que esse MDA é ativado somente se `DllMain` é implementado no código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="53c37-119">Note that this MDA is activated only if `DllMain` is implemented in managed code.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="53c37-120">Configuração</span><span class="sxs-lookup"><span data-stu-id="53c37-120">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dllMainReturnsFalse />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="53c37-121">Veja também</span><span class="sxs-lookup"><span data-stu-id="53c37-121">See also</span></span>

- [<span data-ttu-id="53c37-122">Diagnosticando erros com assistentes para depuração gerenciada</span><span class="sxs-lookup"><span data-stu-id="53c37-122">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
