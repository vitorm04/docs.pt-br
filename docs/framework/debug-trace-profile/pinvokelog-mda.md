---
title: MDA pInvokeLog
description: Entenda o MDA (Assistente de depuração gerenciada) pInvokeLog, que é ativado para cada assinatura de invocação de plataforma exclusiva usada durante a execução no .NET.
ms.date: 03/30/2017
helpviewer_keywords:
- signatures, platform invoke
- MDAs (managed debugging assistants), platform invoke
- platform invoke, run-time errors
- platform invoke log
- PInvokeLog MDA
- managed debugging assistants (MDAs), platform invoke
ms.assetid: b830444a-5003-49fe-b89b-b8bee22f7b1a
ms.openlocfilehash: 05af4e17a91f7c0d8f3576a86d3d784ef6666aed
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85803684"
---
# <a name="pinvokelog-mda"></a><span data-ttu-id="3bb61-103">MDA pInvokeLog</span><span class="sxs-lookup"><span data-stu-id="3bb61-103">pInvokeLog MDA</span></span>
<span data-ttu-id="3bb61-104">O MDA (Assistente de Depuração Gerenciado) de `pInvokeLog` é ativado para cada assinatura de invocação de plataforma exclusiva usada durante a execução.</span><span class="sxs-lookup"><span data-stu-id="3bb61-104">The `pInvokeLog` managed debugging assistant (MDA) is activated for each unique platform invoke signature used during execution.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="3bb61-105">Efeito sobre o runtime</span><span class="sxs-lookup"><span data-stu-id="3bb61-105">Effect on the Runtime</span></span>  
 <span data-ttu-id="3bb61-106">Esse MDA não tem efeito sobre o CLR.</span><span class="sxs-lookup"><span data-stu-id="3bb61-106">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="3bb61-107">Saída</span><span class="sxs-lookup"><span data-stu-id="3bb61-107">Output</span></span>  
 <span data-ttu-id="3bb61-108">Uma mensagem que indica a assinatura de invocação de plataforma usada durante a execução.</span><span class="sxs-lookup"><span data-stu-id="3bb61-108">A message indicating the platform invoke signature used during execution.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="3bb61-109">Configuração</span><span class="sxs-lookup"><span data-stu-id="3bb61-109">Configuration</span></span>  
 <span data-ttu-id="3bb61-110">Cada elemento de correspondência filtra os arquivos .dll para os quais as chamadas de invocação de plataforma são feitas.</span><span class="sxs-lookup"><span data-stu-id="3bb61-110">Each match element filters the .dll files to which platform invoke calls are made.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3bb61-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3bb61-111">See also</span></span>

- [<span data-ttu-id="3bb61-112">Diagnosticando erros com assistentes para depuração gerenciada</span><span class="sxs-lookup"><span data-stu-id="3bb61-112">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="3bb61-113">Consumindo funções de DLL não gerenciadas</span><span class="sxs-lookup"><span data-stu-id="3bb61-113">Consuming Unmanaged DLL Functions</span></span>](../interop/consuming-unmanaged-dll-functions.md)
