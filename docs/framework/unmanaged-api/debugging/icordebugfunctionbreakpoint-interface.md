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
ms.openlocfilehash: 0f15b9f5961699f905e765426576bdf6f3416793
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59141148"
---
# <a name="icordebugfunctionbreakpoint-interface"></a><span data-ttu-id="a0608-102">Interface ICorDebugFunctionBreakpoint</span><span class="sxs-lookup"><span data-stu-id="a0608-102">ICorDebugFunctionBreakpoint Interface</span></span>

<span data-ttu-id="a0608-103">Estende a interface ICorDebugBreakpoint para dar suporte a pontos de interrupção em funções.</span><span class="sxs-lookup"><span data-stu-id="a0608-103">Extends the ICorDebugBreakpoint interface to support breakpoints within functions.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a0608-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="a0608-104">Methods</span></span>  
  
|<span data-ttu-id="a0608-105">Método</span><span class="sxs-lookup"><span data-stu-id="a0608-105">Method</span></span>|<span data-ttu-id="a0608-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="a0608-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a0608-107">Método GetFunction</span><span class="sxs-lookup"><span data-stu-id="a0608-107">GetFunction Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunctionbreakpoint-getfunction-method.md)|<span data-ttu-id="a0608-108">Obtém um ponteiro de interface para um ICorDebugFunction que faz referência à função na qual o ponto de interrupção é definido.</span><span class="sxs-lookup"><span data-stu-id="a0608-108">Gets an interface pointer to an ICorDebugFunction that references the function in which the breakpoint is set.</span></span>|  
|[<span data-ttu-id="a0608-109">Método GetOffset</span><span class="sxs-lookup"><span data-stu-id="a0608-109">GetOffset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunctionbreakpoint-getoffset-method.md)|<span data-ttu-id="a0608-110">Obtém o deslocamento do ponto de interrupção dentro da função.</span><span class="sxs-lookup"><span data-stu-id="a0608-110">Gets the offset of the breakpoint within the function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a0608-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="a0608-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a0608-112">Essa interface não dá suporte a ser chamada remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="a0608-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a0608-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a0608-113">Requirements</span></span>  
 <span data-ttu-id="a0608-114">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a0608-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a0608-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a0608-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a0608-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a0608-116">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="a0608-117">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="a0608-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="a0608-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a0608-118">See also</span></span>

- [<span data-ttu-id="a0608-119">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="a0608-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
