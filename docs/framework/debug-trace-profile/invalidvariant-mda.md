---
title: MDA invalidVariant
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), invalid variant
- VARIANT type errors
- InvalidVariant MDA
- invalid VARIANT types
- managed debugging assistants (MDAs), invalid variant
ms.assetid: d273e070-d1b1-4a53-a9c7-7af837b04a3d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 426b9df449b12d2f34fa70fc721cc050fa3e4ddd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33386711"
---
# <a name="invalidvariant-mda"></a><span data-ttu-id="4f1d3-102">MDA invalidVariant</span><span class="sxs-lookup"><span data-stu-id="4f1d3-102">invalidVariant MDA</span></span>
<span data-ttu-id="4f1d3-103">O MDA (Assistente de Depuração Gerenciado) de `invalidVariant` é ativado quando uma estrutura `VARIANT` inválida é encontrada durante uma chamada de código não gerenciado ou nativo para código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="4f1d3-103">The `invalidVariant` managed debugging assistant (MDA) is activated when an invalid `VARIANT` structure is encountered during a call from native or unmanaged code to managed code.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="4f1d3-104">Sintomas</span><span class="sxs-lookup"><span data-stu-id="4f1d3-104">Symptoms</span></span>  
 <span data-ttu-id="4f1d3-105">Um comportamento inesperado durante a transição entre código nativo e gerenciado que envolve o marshaling de um `VARIANT` para um objeto.</span><span class="sxs-lookup"><span data-stu-id="4f1d3-105">Unexpected behavior during a transition between native and managed code involving the marshaling of a `VARIANT` to an object.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="4f1d3-106">Causa</span><span class="sxs-lookup"><span data-stu-id="4f1d3-106">Cause</span></span>  
 <span data-ttu-id="4f1d3-107">Código nativo está passando uma estrutura `VARIANT` malformada para código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="4f1d3-107">Native code is passing a malformed `VARIANT` structure to managed code.</span></span>  <span data-ttu-id="4f1d3-108">O tempo de execução tenta realizar marshaling dessa `VARIANT` para um objeto e ativa o MDA se o `VARIANT` não é válido.</span><span class="sxs-lookup"><span data-stu-id="4f1d3-108">The runtime attempts to marshal this `VARIANT` to an object and activates the MDA if the `VARIANT` is not valid.</span></span> <span data-ttu-id="4f1d3-109">Exemplos de `VARIANT`S inválidos incluem um `VARIANT` com `VARTYPE` VT_EMPTY &#124; VT_BYREF ou um `VARIANT` com `VARTYPE` VT_VARIANT.</span><span class="sxs-lookup"><span data-stu-id="4f1d3-109">Examples of invalid `VARIANT`S include a `VARIANT` with `VARTYPE` VT_EMPTY &#124; VT_BYREF or a `VARIANT` with `VARTYPE` VT_VARIANT.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="4f1d3-110">Resolução</span><span class="sxs-lookup"><span data-stu-id="4f1d3-110">Resolution</span></span>  
 <span data-ttu-id="4f1d3-111">O código não gerenciado ou nativo passando o `VARIANT` deve garantir que o `VARIANT` seja corretamente formado e inicializado.</span><span class="sxs-lookup"><span data-stu-id="4f1d3-111">The native or unmanaged code passing the `VARIANT` must ensure that the `VARIANT` is correctly formed and initialized.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="4f1d3-112">Efeito sobre o tempo de execução</span><span class="sxs-lookup"><span data-stu-id="4f1d3-112">Effect on the Runtime</span></span>  
 <span data-ttu-id="4f1d3-113">O MDA não tem nenhum efeito sobre o comportamento do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="4f1d3-113">The MDA has no effect on the runtime's behavior.</span></span>  
  
## <a name="output"></a><span data-ttu-id="4f1d3-114">Saída</span><span class="sxs-lookup"><span data-stu-id="4f1d3-114">Output</span></span>  
 <span data-ttu-id="4f1d3-115">Uma mensagem MDA indicando que o tempo de execução detectou inválido `VARIANT` passado para código gerenciado por um módulo não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="4f1d3-115">An MDA message indicating that the runtime detected an invalid `VARIANT` passed to managed code by an unmanaged module.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="4f1d3-116">Configuração</span><span class="sxs-lookup"><span data-stu-id="4f1d3-116">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidVariant />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4f1d3-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4f1d3-117">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="4f1d3-118">Diagnosticando erros com Assistentes de Depuração Gerenciados</span><span class="sxs-lookup"><span data-stu-id="4f1d3-118">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="4f1d3-119">Marshaling de interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="4f1d3-119">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
