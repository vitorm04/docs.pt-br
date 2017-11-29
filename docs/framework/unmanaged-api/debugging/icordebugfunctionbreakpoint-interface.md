---
title: ICorDebugFunctionBreakpoint Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugFunctionBreakpoint
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugFunctionBreakpoint
helpviewer_keywords: ICorDebugFunctionBreakpoint interface [.NET Framework debugging]
ms.assetid: 9c149303-14b1-4138-83d7-e8c3e0fcd332
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 910317bea8af3a80ee66544651de2372808734bb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugfunctionbreakpoint-interface1"></a><span data-ttu-id="88acd-102">ICorDebugFunctionBreakpoint Interface1</span><span class="sxs-lookup"><span data-stu-id="88acd-102">ICorDebugFunctionBreakpoint Interface1</span></span>
<span data-ttu-id="88acd-103">Estende a interface ICorDebugBreakpoint para dar suporte a pontos de interrupção em funções.</span><span class="sxs-lookup"><span data-stu-id="88acd-103">Extends the ICorDebugBreakpoint interface to support breakpoints within functions.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="88acd-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="88acd-104">Methods</span></span>  
  
|<span data-ttu-id="88acd-105">Método</span><span class="sxs-lookup"><span data-stu-id="88acd-105">Method</span></span>|<span data-ttu-id="88acd-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="88acd-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="88acd-107">Método GetFunction</span><span class="sxs-lookup"><span data-stu-id="88acd-107">GetFunction Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunctionbreakpoint-getfunction-method.md)|<span data-ttu-id="88acd-108">Obtém um ponteiro de interface para um ICorDebugFunction que faz referência à função na qual o ponto de interrupção está definido.</span><span class="sxs-lookup"><span data-stu-id="88acd-108">Gets an interface pointer to an ICorDebugFunction that references the function in which the breakpoint is set.</span></span>|  
|[<span data-ttu-id="88acd-109">Método GetOffset</span><span class="sxs-lookup"><span data-stu-id="88acd-109">GetOffset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunctionbreakpoint-getoffset-method.md)|<span data-ttu-id="88acd-110">Obtém o deslocamento do ponto de interrupção na função.</span><span class="sxs-lookup"><span data-stu-id="88acd-110">Gets the offset of the breakpoint within the function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="88acd-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="88acd-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="88acd-112">Esta interface não dá suporte a que está sendo chamado remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="88acd-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="88acd-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="88acd-113">Requirements</span></span>  
 <span data-ttu-id="88acd-114">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="88acd-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="88acd-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="88acd-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="88acd-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="88acd-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="88acd-117">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="88acd-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88acd-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="88acd-118">See Also</span></span>  
 [<span data-ttu-id="88acd-119">Interfaces de depuração</span><span class="sxs-lookup"><span data-stu-id="88acd-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
