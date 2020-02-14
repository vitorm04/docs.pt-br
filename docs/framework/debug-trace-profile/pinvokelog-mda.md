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
ms.openlocfilehash: 12d7f60bcaedc5a97a7718610f40188547f87050
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77216123"
---
# <a name="pinvokelog-mda"></a><span data-ttu-id="4c42d-102">MDA pInvokeLog</span><span class="sxs-lookup"><span data-stu-id="4c42d-102">pInvokeLog MDA</span></span>
<span data-ttu-id="4c42d-103">O MDA (Assistente de Depuração Gerenciado) de `pInvokeLog` é ativado para cada assinatura de invocação de plataforma exclusiva usada durante a execução.</span><span class="sxs-lookup"><span data-stu-id="4c42d-103">The `pInvokeLog` managed debugging assistant (MDA) is activated for each unique platform invoke signature used during execution.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="4c42d-104">Efeito sobre o runtime</span><span class="sxs-lookup"><span data-stu-id="4c42d-104">Effect on the Runtime</span></span>  
 <span data-ttu-id="4c42d-105">Esse MDA não tem efeito sobre o CLR.</span><span class="sxs-lookup"><span data-stu-id="4c42d-105">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="4c42d-106">Saída</span><span class="sxs-lookup"><span data-stu-id="4c42d-106">Output</span></span>  
 <span data-ttu-id="4c42d-107">Uma mensagem que indica a assinatura de invocação de plataforma usada durante a execução.</span><span class="sxs-lookup"><span data-stu-id="4c42d-107">A message indicating the platform invoke signature used during execution.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="4c42d-108">Configuração</span><span class="sxs-lookup"><span data-stu-id="4c42d-108">Configuration</span></span>  
 <span data-ttu-id="4c42d-109">Cada elemento de correspondência filtra os arquivos .dll para os quais as chamadas de invocação de plataforma são feitas.</span><span class="sxs-lookup"><span data-stu-id="4c42d-109">Each match element filters the .dll files to which platform invoke calls are made.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4c42d-110">Confira também</span><span class="sxs-lookup"><span data-stu-id="4c42d-110">See also</span></span>

- [<span data-ttu-id="4c42d-111">Diagnosticando erros com Assistentes de Depuração Gerenciados</span><span class="sxs-lookup"><span data-stu-id="4c42d-111">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="4c42d-112">Consumindo funções de DLL não gerenciadas</span><span class="sxs-lookup"><span data-stu-id="4c42d-112">Consuming Unmanaged DLL Functions</span></span>](../interop/consuming-unmanaged-dll-functions.md)
