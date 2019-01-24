---
title: Método ICorDebugManagedCallback::Break
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.Break
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::Break
helpviewer_keywords:
- Break method [.NET Framework debugging]
- ICorDebugManagedCallback::Break method [.NET Framework debugging]
ms.assetid: 7d78a301-82b3-43b2-9d65-3cda3285ae97
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 83524b24fd05969fa4f45fd742d1df955c441d44
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54732382"
---
# <a name="icordebugmanagedcallbackbreak-method"></a><span data-ttu-id="bdb26-102">Método ICorDebugManagedCallback::Break</span><span class="sxs-lookup"><span data-stu-id="bdb26-102">ICorDebugManagedCallback::Break Method</span></span>
<span data-ttu-id="bdb26-103">Notifica o depurador quando uma <xref:System.Reflection.Emit.OpCodes.Break> instrução no fluxo de código é executada.</span><span class="sxs-lookup"><span data-stu-id="bdb26-103">Notifies the debugger when a <xref:System.Reflection.Emit.OpCodes.Break> instruction in the code stream is executed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bdb26-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bdb26-104">Syntax</span></span>  
  
```  
HRESULT Break (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *thread  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bdb26-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="bdb26-105">Parameters</span></span>  
 `pAppDOmain`  
 <span data-ttu-id="bdb26-106">[in] Um ponteiro para um objeto ICorDebugAppDomain que representa o domínio de aplicativo que contém a instrução break.</span><span class="sxs-lookup"><span data-stu-id="bdb26-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contains the break instruction.</span></span>  
  
 `thread`  
 <span data-ttu-id="bdb26-107">[in] Um ponteiro para um objeto de ICorDebugThread que representa o thread que contém a instrução break.</span><span class="sxs-lookup"><span data-stu-id="bdb26-107">[in] A pointer to an ICorDebugThread object that represents the thread that contains the break instruction.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bdb26-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="bdb26-108">Requirements</span></span>  
 <span data-ttu-id="bdb26-109">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bdb26-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bdb26-110">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bdb26-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bdb26-111">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bdb26-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bdb26-112">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bdb26-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bdb26-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bdb26-113">See also</span></span>
- [<span data-ttu-id="bdb26-114">Interface ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="bdb26-114">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
