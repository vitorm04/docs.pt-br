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
ms.openlocfilehash: a7fe0b33bbd77143da6d2f4a26b170e4d7afe1fb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59104462"
---
# <a name="pinvokelog-mda"></a><span data-ttu-id="a5fda-102">MDA pInvokeLog</span><span class="sxs-lookup"><span data-stu-id="a5fda-102">pInvokeLog MDA</span></span>
<span data-ttu-id="a5fda-103">O MDA (Assistente de Depuração Gerenciado) de `pInvokeLog` é ativado para cada assinatura de invocação de plataforma exclusiva usada durante a execução.</span><span class="sxs-lookup"><span data-stu-id="a5fda-103">The `pInvokeLog` managed debugging assistant (MDA) is activated for each unique platform invoke signature used during execution.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="a5fda-104">Efeito sobre o tempo de execução</span><span class="sxs-lookup"><span data-stu-id="a5fda-104">Effect on the Runtime</span></span>  
 <span data-ttu-id="a5fda-105">Esse MDA não tem efeito sobre o CLR.</span><span class="sxs-lookup"><span data-stu-id="a5fda-105">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="a5fda-106">Saída</span><span class="sxs-lookup"><span data-stu-id="a5fda-106">Output</span></span>  
 <span data-ttu-id="a5fda-107">Uma mensagem que indica a assinatura de invocação de plataforma usada durante a execução.</span><span class="sxs-lookup"><span data-stu-id="a5fda-107">A message indicating the platform invoke signature used during execution.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="a5fda-108">Configuração</span><span class="sxs-lookup"><span data-stu-id="a5fda-108">Configuration</span></span>  
 <span data-ttu-id="a5fda-109">Cada elemento de correspondência filtra os arquivos .dll para os quais as chamadas de invocação de plataforma são feitas.</span><span class="sxs-lookup"><span data-stu-id="a5fda-109">Each match element filters the .dll files to which platform invoke calls are made.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a5fda-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a5fda-110">See also</span></span>

- [<span data-ttu-id="a5fda-111">Diagnosticando erros com Assistentes de Depuração Gerenciados</span><span class="sxs-lookup"><span data-stu-id="a5fda-111">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="a5fda-112">Consumindo funções de DLL não gerenciadas</span><span class="sxs-lookup"><span data-stu-id="a5fda-112">Consuming Unmanaged DLL Functions</span></span>](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md)
