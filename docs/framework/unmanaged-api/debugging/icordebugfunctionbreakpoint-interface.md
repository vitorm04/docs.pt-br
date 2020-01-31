---
title: Interface ICorDebugFunctionBreakpoint
ms.date: 03/30/2017
api_name:
- ICorDebugFunctionBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunctionBreakpoint
helpviewer_keywords:
- ICorDebugFunctionBreakpoint interface [.NET Framework debugging]
ms.assetid: 9c149303-14b1-4138-83d7-e8c3e0fcd332
topic_type:
- apiref
ms.openlocfilehash: 5e3804335bacefad61c4f521ea1ef1444b7b1fed
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76777703"
---
# <a name="icordebugfunctionbreakpoint-interface"></a><span data-ttu-id="e2999-102">Interface ICorDebugFunctionBreakpoint</span><span class="sxs-lookup"><span data-stu-id="e2999-102">ICorDebugFunctionBreakpoint Interface</span></span>

<span data-ttu-id="e2999-103">Estende a interface ICorDebugBreakpoint para dar suporte a pontos de interrupção dentro de funções.</span><span class="sxs-lookup"><span data-stu-id="e2999-103">Extends the ICorDebugBreakpoint interface to support breakpoints within functions.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e2999-104">{1&gt;Métodos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="e2999-104">Methods</span></span>  
  
|<span data-ttu-id="e2999-105">Método</span><span class="sxs-lookup"><span data-stu-id="e2999-105">Method</span></span>|<span data-ttu-id="e2999-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="e2999-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e2999-107">Método GetFunction</span><span class="sxs-lookup"><span data-stu-id="e2999-107">GetFunction Method</span></span>](icordebugfunctionbreakpoint-getfunction-method.md)|<span data-ttu-id="e2999-108">Obtém um ponteiro de interface para um ICorDebugFunction que faz referência à função na qual o ponto de interrupção está definido.</span><span class="sxs-lookup"><span data-stu-id="e2999-108">Gets an interface pointer to an ICorDebugFunction that references the function in which the breakpoint is set.</span></span>|  
|[<span data-ttu-id="e2999-109">Método GetOffset</span><span class="sxs-lookup"><span data-stu-id="e2999-109">GetOffset Method</span></span>](icordebugfunctionbreakpoint-getoffset-method.md)|<span data-ttu-id="e2999-110">Obtém o deslocamento do ponto de interrupção dentro da função.</span><span class="sxs-lookup"><span data-stu-id="e2999-110">Gets the offset of the breakpoint within the function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e2999-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="e2999-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e2999-112">Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.</span><span class="sxs-lookup"><span data-stu-id="e2999-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e2999-113">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="e2999-113">Requirements</span></span>  
 <span data-ttu-id="e2999-114">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e2999-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e2999-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e2999-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e2999-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e2999-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e2999-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e2999-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2999-118">Veja também</span><span class="sxs-lookup"><span data-stu-id="e2999-118">See also</span></span>

- [<span data-ttu-id="e2999-119">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="e2999-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
