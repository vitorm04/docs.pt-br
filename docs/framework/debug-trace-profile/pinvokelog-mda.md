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
ms.openlocfilehash: fe1d783017369a78074e5abf278ac2facf6ee32b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54734059"
---
# <a name="pinvokelog-mda"></a><span data-ttu-id="93bb4-102">MDA pInvokeLog</span><span class="sxs-lookup"><span data-stu-id="93bb4-102">pInvokeLog MDA</span></span>
<span data-ttu-id="93bb4-103">O MDA (Assistente de Depuração Gerenciado) de `pInvokeLog` é ativado para cada assinatura de invocação de plataforma exclusiva usada durante a execução.</span><span class="sxs-lookup"><span data-stu-id="93bb4-103">The `pInvokeLog` managed debugging assistant (MDA) is activated for each unique platform invoke signature used during execution.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="93bb4-104">Efeito sobre o tempo de execução</span><span class="sxs-lookup"><span data-stu-id="93bb4-104">Effect on the Runtime</span></span>  
 <span data-ttu-id="93bb4-105">Esse MDA não tem efeito sobre o CLR.</span><span class="sxs-lookup"><span data-stu-id="93bb4-105">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="93bb4-106">Saída</span><span class="sxs-lookup"><span data-stu-id="93bb4-106">Output</span></span>  
 <span data-ttu-id="93bb4-107">Uma mensagem que indica a assinatura de invocação de plataforma usada durante a execução.</span><span class="sxs-lookup"><span data-stu-id="93bb4-107">A message indicating the platform invoke signature used during execution.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="93bb4-108">Configuração</span><span class="sxs-lookup"><span data-stu-id="93bb4-108">Configuration</span></span>  
 <span data-ttu-id="93bb4-109">Cada elemento de correspondência filtra os arquivos .dll para os quais as chamadas de invocação de plataforma são feitas.</span><span class="sxs-lookup"><span data-stu-id="93bb4-109">Each match element filters the .dll files to which platform invoke calls are made.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="93bb4-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="93bb4-110">See also</span></span>
- [<span data-ttu-id="93bb4-111">Diagnosticando erros com Assistentes de Depuração Gerenciados</span><span class="sxs-lookup"><span data-stu-id="93bb4-111">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="93bb4-112">Consumindo funções de DLL não gerenciadas</span><span class="sxs-lookup"><span data-stu-id="93bb4-112">Consuming Unmanaged DLL Functions</span></span>](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md)
