---
title: MDA invalidIUnknown
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MDAs (managed debugging assistants), invalid IUnknown pointer
- InvalidIUnknown MDA
- invalid IUnknown pointers
- IUnknown pointers
- managed debugging assistants (MDAs), invalid IUnknown pointer
ms.assetid: c7924771-a16b-40fe-b337-ce51dcdf6a12
caps.latest.revision: 13
author: mairaw
ms.author: mairaw
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 970d4dddd473fc671da510cb76b35eca94c55af9
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="invalidiunknown-mda"></a><span data-ttu-id="eaa67-102">MDA invalidIUnknown</span><span class="sxs-lookup"><span data-stu-id="eaa67-102">invalidIUnknown MDA</span></span>
<span data-ttu-id="eaa67-103">O MDA (Assistente de Depuração Gerenciado) de `invalidIUnknown` é ativado quando um ponteiro `IUnknown` inválido é passado do código nativo para o código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="eaa67-103">The `invalidIUnknown` managed debugging assistant (MDA) is activated when an invalid `IUnknown` pointer is passed to managed code from native code.</span></span> <span data-ttu-id="eaa67-104">O `IUnknown` falha em retornar êxito quando consultado para a interface `IUnknown`.</span><span class="sxs-lookup"><span data-stu-id="eaa67-104">The `IUnknown` fails to return success when queried for the `IUnknown` interface.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="eaa67-105">Sintomas</span><span class="sxs-lookup"><span data-stu-id="eaa67-105">Symptoms</span></span>  
 <span data-ttu-id="eaa67-106">Um erro inesperado ocorre ao fazer marshaling de um ponteiro de interface COM durante o marshaling de argumento.</span><span class="sxs-lookup"><span data-stu-id="eaa67-106">An unexpected error occurs when marshaling a COM interface pointer during argument marshaling.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="eaa67-107">Causa</span><span class="sxs-lookup"><span data-stu-id="eaa67-107">Cause</span></span>  
 <span data-ttu-id="eaa67-108">Uma implementação de `QueryInterface` incorreta na interface COM passada para o CLR.</span><span class="sxs-lookup"><span data-stu-id="eaa67-108">An incorrect `QueryInterface` implementation on the COM interface passed to the CLR.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="eaa67-109">Resolução</span><span class="sxs-lookup"><span data-stu-id="eaa67-109">Resolution</span></span>  
 <span data-ttu-id="eaa67-110">Corrija a implementação de `QueryInterface`.</span><span class="sxs-lookup"><span data-stu-id="eaa67-110">Correct the `QueryInterface` implementation.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="eaa67-111">Efeito sobre o tempo de execução</span><span class="sxs-lookup"><span data-stu-id="eaa67-111">Effect on the Runtime</span></span>  
 <span data-ttu-id="eaa67-112">Esse MDA não tem efeito sobre o CLR.</span><span class="sxs-lookup"><span data-stu-id="eaa67-112">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="eaa67-113">Saída</span><span class="sxs-lookup"><span data-stu-id="eaa67-113">Output</span></span>  
 <span data-ttu-id="eaa67-114">A descrição do erro.</span><span class="sxs-lookup"><span data-stu-id="eaa67-114">The description of the error.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="eaa67-115">Configuração</span><span class="sxs-lookup"><span data-stu-id="eaa67-115">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidIUnknown />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="eaa67-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="eaa67-116">See Also</span></span>  
 <span data-ttu-id="eaa67-117"><xref:System.Runtime.InteropServices.MarshalAsAttribute></span><span class="sxs-lookup"><span data-stu-id="eaa67-117"><xref:System.Runtime.InteropServices.MarshalAsAttribute></span></span>   
 <span data-ttu-id="eaa67-118">[Diagnosticando erros com Assistentes de Depuração Gerenciados](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md) </span><span class="sxs-lookup"><span data-stu-id="eaa67-118">[Diagnosing Errors with Managed Debugging Assistants](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md) </span></span>  
 [<span data-ttu-id="eaa67-119">Marshaling de interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="eaa67-119">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)

