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
ms.openlocfilehash: d5f4cecda80238e7a53cf2aa2a8219c49c2b3f9b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54531714"
---
# <a name="icordebugthread3-interface"></a><span data-ttu-id="ca809-102">Interface ICorDebugThread3</span><span class="sxs-lookup"><span data-stu-id="ca809-102">ICorDebugThread3 Interface</span></span>
<span data-ttu-id="ca809-103">Fornece o ponto de entrada para o [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) e as interfaces correspondentes.</span><span class="sxs-lookup"><span data-stu-id="ca809-103">Provides the entry point to the [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) and corresponding interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ca809-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="ca809-104">Methods</span></span>  
  
|<span data-ttu-id="ca809-105">Método</span><span class="sxs-lookup"><span data-stu-id="ca809-105">Method</span></span>|<span data-ttu-id="ca809-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="ca809-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ca809-107">Método CreateStackWalk</span><span class="sxs-lookup"><span data-stu-id="ca809-107">CreateStackWalk Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-createstackwalk-method.md)|<span data-ttu-id="ca809-108">Cria uma [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) objeto para o thread cuja pilha que você deseja de desenrolamento.</span><span class="sxs-lookup"><span data-stu-id="ca809-108">Creates an [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) object for the thread whose stack you want to unwind.</span></span>|  
|[<span data-ttu-id="ca809-109">Método GetActiveInternalFrames</span><span class="sxs-lookup"><span data-stu-id="ca809-109">GetActiveInternalFrames Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-getactiveinternalframes-method.md)|<span data-ttu-id="ca809-110">Retorna uma matriz de quadros internos ([ICorDebugInternalFrame2](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md) objetos) na pilha.</span><span class="sxs-lookup"><span data-stu-id="ca809-110">Returns an array of internal frames ([ICorDebugInternalFrame2](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md) objects) on the stack.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ca809-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="ca809-111">Remarks</span></span>  
 <span data-ttu-id="ca809-112">`ICorDebugThread3` é uma extensão lógica para a interface ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="ca809-112">`ICorDebugThread3` is a logical extension to the ICorDebugThread interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ca809-113">Essa interface não dá suporte a ser chamada remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="ca809-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ca809-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ca809-114">Requirements</span></span>  
 <span data-ttu-id="ca809-115">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ca809-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ca809-116">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ca809-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ca809-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ca809-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ca809-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ca809-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca809-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ca809-119">See also</span></span>
- [<span data-ttu-id="ca809-120">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="ca809-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="ca809-121">Depuração</span><span class="sxs-lookup"><span data-stu-id="ca809-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
