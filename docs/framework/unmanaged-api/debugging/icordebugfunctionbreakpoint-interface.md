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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ed09b4f9be71c7f85714b9ee26d45018410fda42
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917071"
---
# <a name="icordebugfunctionbreakpoint-interface"></a><span data-ttu-id="0faa0-102">Interface ICorDebugFunctionBreakpoint</span><span class="sxs-lookup"><span data-stu-id="0faa0-102">ICorDebugFunctionBreakpoint Interface</span></span>

<span data-ttu-id="0faa0-103">Estende a interface ICorDebugBreakpoint para dar suporte a pontos de interrupção dentro de funções.</span><span class="sxs-lookup"><span data-stu-id="0faa0-103">Extends the ICorDebugBreakpoint interface to support breakpoints within functions.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0faa0-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="0faa0-104">Methods</span></span>  
  
|<span data-ttu-id="0faa0-105">Método</span><span class="sxs-lookup"><span data-stu-id="0faa0-105">Method</span></span>|<span data-ttu-id="0faa0-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="0faa0-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0faa0-107">Método GetFunction</span><span class="sxs-lookup"><span data-stu-id="0faa0-107">GetFunction Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunctionbreakpoint-getfunction-method.md)|<span data-ttu-id="0faa0-108">Obtém um ponteiro de interface para um ICorDebugFunction que faz referência à função na qual o ponto de interrupção está definido.</span><span class="sxs-lookup"><span data-stu-id="0faa0-108">Gets an interface pointer to an ICorDebugFunction that references the function in which the breakpoint is set.</span></span>|  
|[<span data-ttu-id="0faa0-109">Método GetOffset</span><span class="sxs-lookup"><span data-stu-id="0faa0-109">GetOffset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunctionbreakpoint-getoffset-method.md)|<span data-ttu-id="0faa0-110">Obtém o deslocamento do ponto de interrupção dentro da função.</span><span class="sxs-lookup"><span data-stu-id="0faa0-110">Gets the offset of the breakpoint within the function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0faa0-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="0faa0-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0faa0-112">Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.</span><span class="sxs-lookup"><span data-stu-id="0faa0-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0faa0-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0faa0-113">Requirements</span></span>  
 <span data-ttu-id="0faa0-114">**Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0faa0-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0faa0-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0faa0-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0faa0-116">**Biblioteca** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0faa0-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0faa0-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0faa0-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0faa0-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0faa0-118">See also</span></span>

- [<span data-ttu-id="0faa0-119">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="0faa0-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
