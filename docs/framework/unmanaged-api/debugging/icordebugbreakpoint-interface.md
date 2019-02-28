---
title: Interface ICorDebugBreakpoint
ms.date: 03/30/2017
api_name:
- ICorDebugBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBreakpoint
helpviewer_keywords:
- ICorDebugBreakpoint interface [.NET Framework debugging]
ms.assetid: aa5ad3d7-e1bb-42af-99bc-471224e3bcaa
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a7e454c15ddfa977a6d06921a5d80a6c05dca92f
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56973568"
---
# <a name="icordebugbreakpoint-interface"></a><span data-ttu-id="6edd7-102">Interface ICorDebugBreakpoint</span><span class="sxs-lookup"><span data-stu-id="6edd7-102">ICorDebugBreakpoint Interface</span></span>

<span data-ttu-id="6edd7-103">Representa um ponto de interrupção em uma função ou um ponto de inspeção em um valor.</span><span class="sxs-lookup"><span data-stu-id="6edd7-103">Represents a breakpoint in a function, or a watch point on a value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6edd7-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="6edd7-104">Methods</span></span>  
  
|<span data-ttu-id="6edd7-105">Método</span><span class="sxs-lookup"><span data-stu-id="6edd7-105">Method</span></span>|<span data-ttu-id="6edd7-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="6edd7-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6edd7-107">Método Activate</span><span class="sxs-lookup"><span data-stu-id="6edd7-107">Activate Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpoint-activate-method.md)|<span data-ttu-id="6edd7-108">Define o estado ativo disso `ICorDebugBreakpoint`.</span><span class="sxs-lookup"><span data-stu-id="6edd7-108">Sets the active state of this `ICorDebugBreakpoint`.</span></span>|  
|[<span data-ttu-id="6edd7-109">Método IsActive</span><span class="sxs-lookup"><span data-stu-id="6edd7-109">IsActive Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpoint-isactive-method.md)|<span data-ttu-id="6edd7-110">Obtém um valor que indica se este `ICorDebugBreakpoint` está ativa.</span><span class="sxs-lookup"><span data-stu-id="6edd7-110">Gets a value that indicates whether this `ICorDebugBreakpoint` is active.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6edd7-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="6edd7-111">Remarks</span></span>  
 <span data-ttu-id="6edd7-112">Pontos de interrupção não suportam diretamente expressões condicionais.</span><span class="sxs-lookup"><span data-stu-id="6edd7-112">Breakpoints do not directly support conditional expressions.</span></span> <span data-ttu-id="6edd7-113">Se desejar essa funcionalidade, um depurador deve implementar a ele na parte superior da `ICorDebugBreakpoint`.</span><span class="sxs-lookup"><span data-stu-id="6edd7-113">If such functionality is desired, a debugger must implement it on top of `ICorDebugBreakpoint`.</span></span>  
  
 <span data-ttu-id="6edd7-114">Estende a interface ICorDebugFunctionBreakpoint `ICorDebugBreakpoint` para dar suporte a pontos de interrupção em funções.</span><span class="sxs-lookup"><span data-stu-id="6edd7-114">The ICorDebugFunctionBreakpoint interface extends `ICorDebugBreakpoint` to support breakpoints within functions.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6edd7-115">Essa interface não dá suporte a ser chamada remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="6edd7-115">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6edd7-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6edd7-116">Requirements</span></span>  
 <span data-ttu-id="6edd7-117">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6edd7-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6edd7-118">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6edd7-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6edd7-119">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6edd7-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6edd7-120">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6edd7-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6edd7-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6edd7-121">See also</span></span>
- [<span data-ttu-id="6edd7-122">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="6edd7-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
