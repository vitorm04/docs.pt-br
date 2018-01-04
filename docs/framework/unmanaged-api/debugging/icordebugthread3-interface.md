---
title: Interface ICorDebugThread3
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread3
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread3
helpviewer_keywords: ICorDebugThread3 interface [.NET Framework debugging]
ms.assetid: eb2860ef-06cb-4968-a6c3-6d048ecda2a4
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6cfb3267637210567f3df9fa08bb75135dc585ec
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugthread3-interface"></a><span data-ttu-id="2d5f0-102">Interface ICorDebugThread3</span><span class="sxs-lookup"><span data-stu-id="2d5f0-102">ICorDebugThread3 Interface</span></span>
<span data-ttu-id="2d5f0-103">Fornece o ponto de entrada para o [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) e interfaces correspondentes.</span><span class="sxs-lookup"><span data-stu-id="2d5f0-103">Provides the entry point to the [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) and corresponding interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2d5f0-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="2d5f0-104">Methods</span></span>  
  
|<span data-ttu-id="2d5f0-105">Método</span><span class="sxs-lookup"><span data-stu-id="2d5f0-105">Method</span></span>|<span data-ttu-id="2d5f0-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="2d5f0-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2d5f0-107">Método CreateStackWalk</span><span class="sxs-lookup"><span data-stu-id="2d5f0-107">CreateStackWalk Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-createstackwalk-method.md)|<span data-ttu-id="2d5f0-108">Cria um [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) objeto para o thread cuja deseja desenrolamento de pilha.</span><span class="sxs-lookup"><span data-stu-id="2d5f0-108">Creates an [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) object for the thread whose stack you want to unwind.</span></span>|  
|[<span data-ttu-id="2d5f0-109">Método GetActiveInternalFrames</span><span class="sxs-lookup"><span data-stu-id="2d5f0-109">GetActiveInternalFrames Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-getactiveinternalframes-method.md)|<span data-ttu-id="2d5f0-110">Retorna uma matriz de quadros internos ([ICorDebugInternalFrame2](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md) objetos) na pilha.</span><span class="sxs-lookup"><span data-stu-id="2d5f0-110">Returns an array of internal frames ([ICorDebugInternalFrame2](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md) objects) on the stack.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2d5f0-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="2d5f0-111">Remarks</span></span>  
 <span data-ttu-id="2d5f0-112">`ICorDebugThread3`é uma extensão lógica para a interface ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="2d5f0-112">`ICorDebugThread3` is a logical extension to the ICorDebugThread interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2d5f0-113">Esta interface não dá suporte a que está sendo chamado remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="2d5f0-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2d5f0-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2d5f0-114">Requirements</span></span>  
 <span data-ttu-id="2d5f0-115">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2d5f0-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2d5f0-116">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2d5f0-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2d5f0-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2d5f0-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2d5f0-118">**Versões do .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2d5f0-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d5f0-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2d5f0-119">See Also</span></span>  
 [<span data-ttu-id="2d5f0-120">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="2d5f0-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="2d5f0-121">Depuração</span><span class="sxs-lookup"><span data-stu-id="2d5f0-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
