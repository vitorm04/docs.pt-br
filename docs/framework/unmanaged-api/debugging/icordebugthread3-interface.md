---
title: Interface ICorDebugThread3
ms.date: 03/30/2017
api_name:
- ICorDebugThread3
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread3
helpviewer_keywords:
- ICorDebugThread3 interface [.NET Framework debugging]
ms.assetid: eb2860ef-06cb-4968-a6c3-6d048ecda2a4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c9cb9217282af53d9788190844e4e52d5405ee2a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33422770"
---
# <a name="icordebugthread3-interface"></a><span data-ttu-id="14a9f-102">Interface ICorDebugThread3</span><span class="sxs-lookup"><span data-stu-id="14a9f-102">ICorDebugThread3 Interface</span></span>
<span data-ttu-id="14a9f-103">Fornece o ponto de entrada para o [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) e interfaces correspondentes.</span><span class="sxs-lookup"><span data-stu-id="14a9f-103">Provides the entry point to the [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) and corresponding interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="14a9f-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="14a9f-104">Methods</span></span>  
  
|<span data-ttu-id="14a9f-105">Método</span><span class="sxs-lookup"><span data-stu-id="14a9f-105">Method</span></span>|<span data-ttu-id="14a9f-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="14a9f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="14a9f-107">Método CreateStackWalk</span><span class="sxs-lookup"><span data-stu-id="14a9f-107">CreateStackWalk Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-createstackwalk-method.md)|<span data-ttu-id="14a9f-108">Cria um [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) objeto para o thread cuja deseja desenrolamento de pilha.</span><span class="sxs-lookup"><span data-stu-id="14a9f-108">Creates an [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) object for the thread whose stack you want to unwind.</span></span>|  
|[<span data-ttu-id="14a9f-109">Método GetActiveInternalFrames</span><span class="sxs-lookup"><span data-stu-id="14a9f-109">GetActiveInternalFrames Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-getactiveinternalframes-method.md)|<span data-ttu-id="14a9f-110">Retorna uma matriz de quadros internos ([ICorDebugInternalFrame2](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md) objetos) na pilha.</span><span class="sxs-lookup"><span data-stu-id="14a9f-110">Returns an array of internal frames ([ICorDebugInternalFrame2](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md) objects) on the stack.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="14a9f-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="14a9f-111">Remarks</span></span>  
 <span data-ttu-id="14a9f-112">`ICorDebugThread3` é uma extensão lógica para a interface ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="14a9f-112">`ICorDebugThread3` is a logical extension to the ICorDebugThread interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="14a9f-113">Esta interface não dá suporte a que está sendo chamado remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="14a9f-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="14a9f-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="14a9f-114">Requirements</span></span>  
 <span data-ttu-id="14a9f-115">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="14a9f-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="14a9f-116">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="14a9f-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="14a9f-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="14a9f-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="14a9f-118">**Versões do .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="14a9f-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14a9f-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="14a9f-119">See Also</span></span>  
 [<span data-ttu-id="14a9f-120">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="14a9f-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="14a9f-121">Depuração</span><span class="sxs-lookup"><span data-stu-id="14a9f-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
