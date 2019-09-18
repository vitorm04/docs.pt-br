---
title: MDA pInvokeLog
ms.date: 03/30/2017
helpviewer_keywords:
- signatures, platform invoke
- MDAs (managed debugging assistants), platform invoke
- platform invoke, run-time errors
- platform invoke log
- PInvokeLog MDA
- managed debugging assistants (MDAs), platform invoke
ms.assetid: b830444a-5003-49fe-b89b-b8bee22f7b1a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0883849eee12922601e50c2337bb0048d77cab68
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052373"
---
# <a name="pinvokelog-mda"></a><span data-ttu-id="dbe00-102">MDA pInvokeLog</span><span class="sxs-lookup"><span data-stu-id="dbe00-102">pInvokeLog MDA</span></span>
<span data-ttu-id="dbe00-103">O MDA (Assistente de Depuração Gerenciado) de `pInvokeLog` é ativado para cada assinatura de invocação de plataforma exclusiva usada durante a execução.</span><span class="sxs-lookup"><span data-stu-id="dbe00-103">The `pInvokeLog` managed debugging assistant (MDA) is activated for each unique platform invoke signature used during execution.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="dbe00-104">Efeito sobre o tempo de execução</span><span class="sxs-lookup"><span data-stu-id="dbe00-104">Effect on the Runtime</span></span>  
 <span data-ttu-id="dbe00-105">Esse MDA não tem efeito sobre o CLR.</span><span class="sxs-lookup"><span data-stu-id="dbe00-105">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="dbe00-106">Saída</span><span class="sxs-lookup"><span data-stu-id="dbe00-106">Output</span></span>  
 <span data-ttu-id="dbe00-107">Uma mensagem que indica a assinatura de invocação de plataforma usada durante a execução.</span><span class="sxs-lookup"><span data-stu-id="dbe00-107">A message indicating the platform invoke signature used during execution.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="dbe00-108">Configuração</span><span class="sxs-lookup"><span data-stu-id="dbe00-108">Configuration</span></span>  
 <span data-ttu-id="dbe00-109">Cada elemento de correspondência filtra os arquivos .dll para os quais as chamadas de invocação de plataforma são feitas.</span><span class="sxs-lookup"><span data-stu-id="dbe00-109">Each match element filters the .dll files to which platform invoke calls are made.</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <pInvokeLog>  
      <filter>  
        <match dllName="user32.dll"/>  
        <match dllName="kernel32.dll"/>  
      </filter>  
    </pInvokeLog>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="dbe00-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dbe00-110">See also</span></span>

- [<span data-ttu-id="dbe00-111">Diagnosticando erros com Assistentes de Depuração Gerenciados</span><span class="sxs-lookup"><span data-stu-id="dbe00-111">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="dbe00-112">Consumindo funções de DLL não gerenciadas</span><span class="sxs-lookup"><span data-stu-id="dbe00-112">Consuming Unmanaged DLL Functions</span></span>](../interop/consuming-unmanaged-dll-functions.md)
