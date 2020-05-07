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
ms.openlocfilehash: b92c3d3328c657762ed002155ef4947a9292b19e
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894728"
---
# <a name="icordebugbreakpoint-interface"></a><span data-ttu-id="c7b7c-102">Interface ICorDebugBreakpoint</span><span class="sxs-lookup"><span data-stu-id="c7b7c-102">ICorDebugBreakpoint Interface</span></span>

<span data-ttu-id="c7b7c-103">Representa um ponto de interrupção em uma função ou um apontador em um valor.</span><span class="sxs-lookup"><span data-stu-id="c7b7c-103">Represents a breakpoint in a function, or a watch point on a value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c7b7c-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="c7b7c-104">Methods</span></span>  
  
|<span data-ttu-id="c7b7c-105">Método</span><span class="sxs-lookup"><span data-stu-id="c7b7c-105">Method</span></span>|<span data-ttu-id="c7b7c-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="c7b7c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c7b7c-107">Método Activate</span><span class="sxs-lookup"><span data-stu-id="c7b7c-107">Activate Method</span></span>](icordebugbreakpoint-activate-method.md)|<span data-ttu-id="c7b7c-108">Define o estado ativo deste `ICorDebugBreakpoint`.</span><span class="sxs-lookup"><span data-stu-id="c7b7c-108">Sets the active state of this `ICorDebugBreakpoint`.</span></span>|  
|[<span data-ttu-id="c7b7c-109">Método IsActive</span><span class="sxs-lookup"><span data-stu-id="c7b7c-109">IsActive Method</span></span>](icordebugbreakpoint-isactive-method.md)|<span data-ttu-id="c7b7c-110">Obtém um valor que indica se ele `ICorDebugBreakpoint` está ativo.</span><span class="sxs-lookup"><span data-stu-id="c7b7c-110">Gets a value that indicates whether this `ICorDebugBreakpoint` is active.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c7b7c-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="c7b7c-111">Remarks</span></span>  
 <span data-ttu-id="c7b7c-112">Os pontos de interrupção não oferecem suporte direto a expressões condicionais.</span><span class="sxs-lookup"><span data-stu-id="c7b7c-112">Breakpoints do not directly support conditional expressions.</span></span> <span data-ttu-id="c7b7c-113">Se essa funcionalidade for desejada, um depurador deverá implementá-la sobre `ICorDebugBreakpoint`o.</span><span class="sxs-lookup"><span data-stu-id="c7b7c-113">If such functionality is desired, a debugger must implement it on top of `ICorDebugBreakpoint`.</span></span>  
  
 <span data-ttu-id="c7b7c-114">A interface ICorDebugFunctionBreakpoint se `ICorDebugBreakpoint` estende para dar suporte a pontos de interrupção dentro de funções.</span><span class="sxs-lookup"><span data-stu-id="c7b7c-114">The ICorDebugFunctionBreakpoint interface extends `ICorDebugBreakpoint` to support breakpoints within functions.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c7b7c-115">Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.</span><span class="sxs-lookup"><span data-stu-id="c7b7c-115">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c7b7c-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c7b7c-116">Requirements</span></span>  
 <span data-ttu-id="c7b7c-117">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c7b7c-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c7b7c-118">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c7b7c-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c7b7c-119">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c7b7c-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c7b7c-120">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c7b7c-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7b7c-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c7b7c-121">See also</span></span>

- [<span data-ttu-id="c7b7c-122">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="c7b7c-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
