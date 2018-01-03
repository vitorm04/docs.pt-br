---
title: ICorDebugBreakpoint Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugBreakpoint
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugBreakpoint
helpviewer_keywords: ICorDebugBreakpoint interface [.NET Framework debugging]
ms.assetid: aa5ad3d7-e1bb-42af-99bc-471224e3bcaa
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cd2c4245b5e3dcc4f7b989a3ca9add8d568467cb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugbreakpoint-interface1"></a><span data-ttu-id="eee15-102">ICorDebugBreakpoint Interface1</span><span class="sxs-lookup"><span data-stu-id="eee15-102">ICorDebugBreakpoint Interface1</span></span>
<span data-ttu-id="eee15-103">Representa um ponto de interrupção em uma função ou um ponto de inspeção em um valor.</span><span class="sxs-lookup"><span data-stu-id="eee15-103">Represents a breakpoint in a function, or a watch point on a value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="eee15-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="eee15-104">Methods</span></span>  
  
|<span data-ttu-id="eee15-105">Método</span><span class="sxs-lookup"><span data-stu-id="eee15-105">Method</span></span>|<span data-ttu-id="eee15-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="eee15-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="eee15-107">Método Activate</span><span class="sxs-lookup"><span data-stu-id="eee15-107">Activate Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpoint-activate-method.md)|<span data-ttu-id="eee15-108">Define o estado ativo deste `ICorDebugBreakpoint`.</span><span class="sxs-lookup"><span data-stu-id="eee15-108">Sets the active state of this `ICorDebugBreakpoint`.</span></span>|  
|[<span data-ttu-id="eee15-109">Método IsActive</span><span class="sxs-lookup"><span data-stu-id="eee15-109">IsActive Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpoint-isactive-method.md)|<span data-ttu-id="eee15-110">Obtém um valor que indica se este `ICorDebugBreakpoint` está ativa.</span><span class="sxs-lookup"><span data-stu-id="eee15-110">Gets a value that indicates whether this `ICorDebugBreakpoint` is active.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eee15-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="eee15-111">Remarks</span></span>  
 <span data-ttu-id="eee15-112">Pontos de interrupção não dão suporte diretamente a expressões condicionais.</span><span class="sxs-lookup"><span data-stu-id="eee15-112">Breakpoints do not directly support conditional expressions.</span></span> <span data-ttu-id="eee15-113">Se essa funcionalidade é desejada, um depurador deve implementar a ele na parte superior do `ICorDebugBreakpoint`.</span><span class="sxs-lookup"><span data-stu-id="eee15-113">If such functionality is desired, a debugger must implement it on top of `ICorDebugBreakpoint`.</span></span>  
  
 <span data-ttu-id="eee15-114">Estende a interface ICorDebugFunctionBreakpoint `ICorDebugBreakpoint` para dar suporte a pontos de interrupção em funções.</span><span class="sxs-lookup"><span data-stu-id="eee15-114">The ICorDebugFunctionBreakpoint interface extends `ICorDebugBreakpoint` to support breakpoints within functions.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="eee15-115">Esta interface não dá suporte a que está sendo chamado remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="eee15-115">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eee15-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="eee15-116">Requirements</span></span>  
 <span data-ttu-id="eee15-117">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eee15-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eee15-118">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="eee15-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="eee15-119">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="eee15-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eee15-120">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eee15-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eee15-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="eee15-121">See Also</span></span>  
 [<span data-ttu-id="eee15-122">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="eee15-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
