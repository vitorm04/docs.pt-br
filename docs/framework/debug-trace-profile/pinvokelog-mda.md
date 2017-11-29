---
title: MDA pInvokeLog
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- signatures, platform invoke
- MDAs (managed debugging assistants), platform invoke
- platform invoke, run-time errors
- platform invoke log
- PInvokeLog MDA
- managed debugging assistants (MDAs), platform invoke
ms.assetid: b830444a-5003-49fe-b89b-b8bee22f7b1a
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 9c4842d838fd5b4fee29187f118c784c55e0eb13
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="pinvokelog-mda"></a><span data-ttu-id="17ac0-102">MDA pInvokeLog</span><span class="sxs-lookup"><span data-stu-id="17ac0-102">pInvokeLog MDA</span></span>
<span data-ttu-id="17ac0-103">O MDA (Assistente de Depuração Gerenciado) de `pInvokeLog` é ativado para cada assinatura de invocação de plataforma exclusiva usada durante a execução.</span><span class="sxs-lookup"><span data-stu-id="17ac0-103">The `pInvokeLog` managed debugging assistant (MDA) is activated for each unique platform invoke signature used during execution.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="17ac0-104">Efeito sobre o tempo de execução</span><span class="sxs-lookup"><span data-stu-id="17ac0-104">Effect on the Runtime</span></span>  
 <span data-ttu-id="17ac0-105">Esse MDA não tem efeito sobre o CLR.</span><span class="sxs-lookup"><span data-stu-id="17ac0-105">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="17ac0-106">Saída</span><span class="sxs-lookup"><span data-stu-id="17ac0-106">Output</span></span>  
 <span data-ttu-id="17ac0-107">Uma mensagem que indica a assinatura de invocação de plataforma usada durante a execução.</span><span class="sxs-lookup"><span data-stu-id="17ac0-107">A message indicating the platform invoke signature used during execution.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="17ac0-108">Configuração</span><span class="sxs-lookup"><span data-stu-id="17ac0-108">Configuration</span></span>  
 <span data-ttu-id="17ac0-109">Cada elemento de correspondência filtra os arquivos .dll para os quais as chamadas de invocação de plataforma são feitas.</span><span class="sxs-lookup"><span data-stu-id="17ac0-109">Each match element filters the .dll files to which platform invoke calls are made.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="17ac0-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="17ac0-110">See Also</span></span>  
 [<span data-ttu-id="17ac0-111">Diagnosticando erros com Assistentes de Depuração Gerenciados</span><span class="sxs-lookup"><span data-stu-id="17ac0-111">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="17ac0-112">Consumindo funções de DLL não gerenciadas</span><span class="sxs-lookup"><span data-stu-id="17ac0-112">Consuming Unmanaged DLL Functions</span></span>](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md)
