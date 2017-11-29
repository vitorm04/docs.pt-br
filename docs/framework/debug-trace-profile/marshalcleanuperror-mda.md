---
title: MDA marshalCleanupError
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- cleanup operations
- marshaling, run-time errors
- managed debugging assistants (MDAs), marshaling
- MDAs (managed debugging assistants), marshaling
- marshaling cleanup error
- MarshalCleanupError MDA
- memory, cleanup errors
ms.assetid: 2f5d9e7c-ae51-4155-a435-54347aa1f091
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c78fedaab26ff7f1da7bccd98c83a90e550d9014
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="marshalcleanuperror-mda"></a><span data-ttu-id="d686b-102">MDA marshalCleanupError</span><span class="sxs-lookup"><span data-stu-id="d686b-102">marshalCleanupError MDA</span></span>
<span data-ttu-id="d686b-103">O MDA (assistente de depuração gerenciado) do `marshalCleanupError` é ativado quando o CLR (Common Language Runtime) encontra um erro ao tentar limpar estruturas temporárias e a memória usada para realizar marshaling de tipos de dados entre limites de código gerenciado e nativo.</span><span class="sxs-lookup"><span data-stu-id="d686b-103">The `marshalCleanupError` managed debugging assistant (MDA) is activated when the common language runtime (CLR) encounters an error while attempting to clean up temporary structures and memory used for marshaling data types between native and managed code boundaries.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="d686b-104">Sintomas</span><span class="sxs-lookup"><span data-stu-id="d686b-104">Symptoms</span></span>  
 <span data-ttu-id="d686b-105">A perda de memória ocorre em transações de código gerenciado e nativo, no estado de tempo de execução, como quando a cultura de thread não é restaurada ou quando há um erro na limpeza de <xref:System.Runtime.InteropServices.SafeHandle>.</span><span class="sxs-lookup"><span data-stu-id="d686b-105">A memory leak occurs when making native and managed code transitions, runtime state such as thread culture is not restored, or errors occur in <xref:System.Runtime.InteropServices.SafeHandle> cleanup.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="d686b-106">Causa</span><span class="sxs-lookup"><span data-stu-id="d686b-106">Cause</span></span>  
 <span data-ttu-id="d686b-107">Ocorreu um erro inesperado durante a limpeza das estruturas temporárias.</span><span class="sxs-lookup"><span data-stu-id="d686b-107">An unexpected error occurred while cleaning up temporary structures.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="d686b-108">Resolução</span><span class="sxs-lookup"><span data-stu-id="d686b-108">Resolution</span></span>  
 <span data-ttu-id="d686b-109">Verifique se há erro em todas as implementações do destruidor, do finalizador e do marshaler personalizado <xref:System.Runtime.InteropServices.SafeHandle>.</span><span class="sxs-lookup"><span data-stu-id="d686b-109">Review all <xref:System.Runtime.InteropServices.SafeHandle> destructor, finalizer, and custom marshaler implementations for errors.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="d686b-110">Efeito sobre o tempo de execução</span><span class="sxs-lookup"><span data-stu-id="d686b-110">Effect on the Runtime</span></span>  
 <span data-ttu-id="d686b-111">Esse MDA não tem efeito sobre o CLR.</span><span class="sxs-lookup"><span data-stu-id="d686b-111">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="d686b-112">Saída</span><span class="sxs-lookup"><span data-stu-id="d686b-112">Output</span></span>  
 <span data-ttu-id="d686b-113">Uma mensagem que indica que a operação falhou durante a limpeza.</span><span class="sxs-lookup"><span data-stu-id="d686b-113">A message reporting the operation that failed during cleanup.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="d686b-114">Configuração</span><span class="sxs-lookup"><span data-stu-id="d686b-114">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <marshalCleanupError />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d686b-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d686b-115">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="d686b-116">Diagnosticando erros com Assistentes de Depuração Gerenciados</span><span class="sxs-lookup"><span data-stu-id="d686b-116">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="d686b-117">Marshaling de interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="d686b-117">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
