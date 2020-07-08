---
title: MDA invalidIUnknown
description: Examine o MDA (Assistente de depuração gerenciada) invalidIUnknown, que é ativado quando um ponteiro IUnknown inválido é passado para o código gerenciado do código nativo.
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), invalid IUnknown pointer
- InvalidIUnknown MDA
- invalid IUnknown pointers
- IUnknown pointers
- managed debugging assistants (MDAs), invalid IUnknown pointer
ms.assetid: c7924771-a16b-40fe-b337-ce51dcdf6a12
ms.openlocfilehash: 65d704463ed746390ff1710b590bf080013bf53d
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: pt-BR
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051721"
---
# <a name="invalidiunknown-mda"></a><span data-ttu-id="47fce-103">MDA invalidIUnknown</span><span class="sxs-lookup"><span data-stu-id="47fce-103">invalidIUnknown MDA</span></span>
<span data-ttu-id="47fce-104">O MDA (Assistente de Depuração Gerenciado) de `invalidIUnknown` é ativado quando um ponteiro `IUnknown` inválido é passado do código nativo para o código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="47fce-104">The `invalidIUnknown` managed debugging assistant (MDA) is activated when an invalid `IUnknown` pointer is passed to managed code from native code.</span></span> <span data-ttu-id="47fce-105">O `IUnknown` falha em retornar êxito quando consultado para a interface `IUnknown`.</span><span class="sxs-lookup"><span data-stu-id="47fce-105">The `IUnknown` fails to return success when queried for the `IUnknown` interface.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="47fce-106">Sintomas</span><span class="sxs-lookup"><span data-stu-id="47fce-106">Symptoms</span></span>  
 <span data-ttu-id="47fce-107">Um erro inesperado ocorre ao fazer marshaling de um ponteiro de interface COM durante o marshaling de argumento.</span><span class="sxs-lookup"><span data-stu-id="47fce-107">An unexpected error occurs when marshaling a COM interface pointer during argument marshaling.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="47fce-108">Causa</span><span class="sxs-lookup"><span data-stu-id="47fce-108">Cause</span></span>  
 <span data-ttu-id="47fce-109">Uma implementação de `QueryInterface` incorreta na interface COM passada para o CLR.</span><span class="sxs-lookup"><span data-stu-id="47fce-109">An incorrect `QueryInterface` implementation on the COM interface passed to the CLR.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="47fce-110">Resolução</span><span class="sxs-lookup"><span data-stu-id="47fce-110">Resolution</span></span>  
 <span data-ttu-id="47fce-111">Corrija a implementação de `QueryInterface`.</span><span class="sxs-lookup"><span data-stu-id="47fce-111">Correct the `QueryInterface` implementation.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="47fce-112">Efeito sobre o runtime</span><span class="sxs-lookup"><span data-stu-id="47fce-112">Effect on the Runtime</span></span>  
 <span data-ttu-id="47fce-113">Esse MDA não tem efeito sobre o CLR.</span><span class="sxs-lookup"><span data-stu-id="47fce-113">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="47fce-114">Saída</span><span class="sxs-lookup"><span data-stu-id="47fce-114">Output</span></span>  
 <span data-ttu-id="47fce-115">A descrição do erro.</span><span class="sxs-lookup"><span data-stu-id="47fce-115">The description of the error.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="47fce-116">Configuração</span><span class="sxs-lookup"><span data-stu-id="47fce-116">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidIUnknown />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="47fce-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="47fce-117">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="47fce-118">Diagnosticando erros com assistentes para depuração gerenciada</span><span class="sxs-lookup"><span data-stu-id="47fce-118">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="47fce-119">Realizando marshaling de interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="47fce-119">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
