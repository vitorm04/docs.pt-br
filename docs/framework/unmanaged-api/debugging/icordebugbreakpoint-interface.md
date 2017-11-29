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
ms.openlocfilehash: b78b61b99fb8f236e787f3acbf993d0a1c57e797
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugbreakpoint-interface1"></a><span data-ttu-id="d33b8-102">ICorDebugBreakpoint Interface1</span><span class="sxs-lookup"><span data-stu-id="d33b8-102">ICorDebugBreakpoint Interface1</span></span>
<span data-ttu-id="d33b8-103">Representa um ponto de interrupção em uma função ou um ponto de inspeção em um valor.</span><span class="sxs-lookup"><span data-stu-id="d33b8-103">Represents a breakpoint in a function, or a watch point on a value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d33b8-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="d33b8-104">Methods</span></span>  
  
|<span data-ttu-id="d33b8-105">Método</span><span class="sxs-lookup"><span data-stu-id="d33b8-105">Method</span></span>|<span data-ttu-id="d33b8-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="d33b8-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d33b8-107">O método Activate</span><span class="sxs-lookup"><span data-stu-id="d33b8-107">Activate Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpoint-activate-method.md)|<span data-ttu-id="d33b8-108">Define o estado ativo deste `ICorDebugBreakpoint`.</span><span class="sxs-lookup"><span data-stu-id="d33b8-108">Sets the active state of this `ICorDebugBreakpoint`.</span></span>|  
|[<span data-ttu-id="d33b8-109">Método IsActive</span><span class="sxs-lookup"><span data-stu-id="d33b8-109">IsActive Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpoint-isactive-method.md)|<span data-ttu-id="d33b8-110">Obtém um valor que indica se este `ICorDebugBreakpoint` está ativa.</span><span class="sxs-lookup"><span data-stu-id="d33b8-110">Gets a value that indicates whether this `ICorDebugBreakpoint` is active.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d33b8-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="d33b8-111">Remarks</span></span>  
 <span data-ttu-id="d33b8-112">Pontos de interrupção não dão suporte diretamente a expressões condicionais.</span><span class="sxs-lookup"><span data-stu-id="d33b8-112">Breakpoints do not directly support conditional expressions.</span></span> <span data-ttu-id="d33b8-113">Se essa funcionalidade é desejada, um depurador deve implementar a ele na parte superior do `ICorDebugBreakpoint`.</span><span class="sxs-lookup"><span data-stu-id="d33b8-113">If such functionality is desired, a debugger must implement it on top of `ICorDebugBreakpoint`.</span></span>  
  
 <span data-ttu-id="d33b8-114">Estende a interface ICorDebugFunctionBreakpoint `ICorDebugBreakpoint` para dar suporte a pontos de interrupção em funções.</span><span class="sxs-lookup"><span data-stu-id="d33b8-114">The ICorDebugFunctionBreakpoint interface extends `ICorDebugBreakpoint` to support breakpoints within functions.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d33b8-115">Esta interface não dá suporte a que está sendo chamado remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="d33b8-115">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d33b8-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d33b8-116">Requirements</span></span>  
 <span data-ttu-id="d33b8-117">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d33b8-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d33b8-118">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d33b8-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d33b8-119">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d33b8-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d33b8-120">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d33b8-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d33b8-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d33b8-121">See Also</span></span>  
 [<span data-ttu-id="d33b8-122">Interfaces de depuração</span><span class="sxs-lookup"><span data-stu-id="d33b8-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
