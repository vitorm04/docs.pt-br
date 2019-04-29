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
ms.openlocfilehash: a68e061c6def61746ee65f8a25818f8dbcd785b5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61645351"
---
# <a name="icordebugbreakpoint-interface"></a><span data-ttu-id="3e584-102">Interface ICorDebugBreakpoint</span><span class="sxs-lookup"><span data-stu-id="3e584-102">ICorDebugBreakpoint Interface</span></span>

<span data-ttu-id="3e584-103">Representa um ponto de interrupção em uma função ou um ponto de inspeção em um valor.</span><span class="sxs-lookup"><span data-stu-id="3e584-103">Represents a breakpoint in a function, or a watch point on a value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3e584-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="3e584-104">Methods</span></span>  
  
|<span data-ttu-id="3e584-105">Método</span><span class="sxs-lookup"><span data-stu-id="3e584-105">Method</span></span>|<span data-ttu-id="3e584-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="3e584-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3e584-107">Método Activate</span><span class="sxs-lookup"><span data-stu-id="3e584-107">Activate Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpoint-activate-method.md)|<span data-ttu-id="3e584-108">Define o estado ativo disso `ICorDebugBreakpoint`.</span><span class="sxs-lookup"><span data-stu-id="3e584-108">Sets the active state of this `ICorDebugBreakpoint`.</span></span>|  
|[<span data-ttu-id="3e584-109">Método IsActive</span><span class="sxs-lookup"><span data-stu-id="3e584-109">IsActive Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpoint-isactive-method.md)|<span data-ttu-id="3e584-110">Obtém um valor que indica se este `ICorDebugBreakpoint` está ativa.</span><span class="sxs-lookup"><span data-stu-id="3e584-110">Gets a value that indicates whether this `ICorDebugBreakpoint` is active.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3e584-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="3e584-111">Remarks</span></span>  
 <span data-ttu-id="3e584-112">Pontos de interrupção não suportam diretamente expressões condicionais.</span><span class="sxs-lookup"><span data-stu-id="3e584-112">Breakpoints do not directly support conditional expressions.</span></span> <span data-ttu-id="3e584-113">Se desejar essa funcionalidade, um depurador deve implementar a ele na parte superior da `ICorDebugBreakpoint`.</span><span class="sxs-lookup"><span data-stu-id="3e584-113">If such functionality is desired, a debugger must implement it on top of `ICorDebugBreakpoint`.</span></span>  
  
 <span data-ttu-id="3e584-114">Estende a interface ICorDebugFunctionBreakpoint `ICorDebugBreakpoint` para dar suporte a pontos de interrupção em funções.</span><span class="sxs-lookup"><span data-stu-id="3e584-114">The ICorDebugFunctionBreakpoint interface extends `ICorDebugBreakpoint` to support breakpoints within functions.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3e584-115">Essa interface não dá suporte a ser chamada remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="3e584-115">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3e584-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3e584-116">Requirements</span></span>  
 <span data-ttu-id="3e584-117">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3e584-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3e584-118">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3e584-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3e584-119">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3e584-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3e584-120">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3e584-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e584-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3e584-121">See also</span></span>

- [<span data-ttu-id="3e584-122">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="3e584-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
