---
title: Método ICorDebug::SetManagedHandler
ms.date: 03/30/2017
api_name:
- ICorDebug.SetManagedHandler
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::SetManagedHandler
helpviewer_keywords:
- ICorDebug::SetManagedHandler method [.NET Framework debugging]
- SetManagedHandler method [.NET Framework debugging]
ms.assetid: d079131b-685b-4869-95be-826b88d28bd2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 88f30089879f2d023c8fb04b52e75b2942da2a83
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61786341"
---
# <a name="icordebugsetmanagedhandler-method"></a><span data-ttu-id="63548-102">Método ICorDebug::SetManagedHandler</span><span class="sxs-lookup"><span data-stu-id="63548-102">ICorDebug::SetManagedHandler Method</span></span>
<span data-ttu-id="63548-103">Especifica o objeto de manipulador de eventos para eventos gerenciados.</span><span class="sxs-lookup"><span data-stu-id="63548-103">Specifies the event handler object for managed events.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63548-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="63548-104">Syntax</span></span>  
  
```  
HRESULT SetManagedHandler (  
    [in] ICorDebugManagedCallback     *pCallback  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="63548-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="63548-105">Parameters</span></span>  
 `pCallback`  
 <span data-ttu-id="63548-106">[in] Um ponteiro para um [ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md) objeto, que é o objeto de manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="63548-106">[in] A pointer to an [ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md) object, which is the event handler object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="63548-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="63548-107">Remarks</span></span>  
 <span data-ttu-id="63548-108">`SetManagedHandler` deve ser chamado no momento da criação.</span><span class="sxs-lookup"><span data-stu-id="63548-108">`SetManagedHandler` must be called at creation time.</span></span>  
  
 <span data-ttu-id="63548-109">Se o `ICorDebugManagedCallback` a implementação não contêm interfaces suficientes para lidar com eventos de depuração para o aplicativo que está sendo depurado, `SetManagedHandler` retorna um HRESULT de E_NOINTERFACE.</span><span class="sxs-lookup"><span data-stu-id="63548-109">If the `ICorDebugManagedCallback` implementation does not contain sufficient interfaces to handle debugging events for the application that is being debugged, `SetManagedHandler` returns an HRESULT of E_NOINTERFACE.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="63548-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="63548-110">Requirements</span></span>  
 <span data-ttu-id="63548-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="63548-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="63548-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="63548-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="63548-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="63548-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="63548-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="63548-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63548-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="63548-115">See also</span></span>

- [<span data-ttu-id="63548-116">Interface ICorDebug</span><span class="sxs-lookup"><span data-stu-id="63548-116">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
