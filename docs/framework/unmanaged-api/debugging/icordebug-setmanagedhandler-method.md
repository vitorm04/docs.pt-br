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
ms.openlocfilehash: c195e61b5929acdb0aec7d9043ce6122b0a80739
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54643267"
---
# <a name="icordebugsetmanagedhandler-method"></a><span data-ttu-id="3c896-102">Método ICorDebug::SetManagedHandler</span><span class="sxs-lookup"><span data-stu-id="3c896-102">ICorDebug::SetManagedHandler Method</span></span>
<span data-ttu-id="3c896-103">Especifica o objeto de manipulador de eventos para eventos gerenciados.</span><span class="sxs-lookup"><span data-stu-id="3c896-103">Specifies the event handler object for managed events.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c896-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3c896-104">Syntax</span></span>  
  
```  
HRESULT SetManagedHandler (  
    [in] ICorDebugManagedCallback     *pCallback  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3c896-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3c896-105">Parameters</span></span>  
 `pCallback`  
 <span data-ttu-id="3c896-106">[in] Um ponteiro para um [ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md) objeto, que é o objeto de manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="3c896-106">[in] A pointer to an [ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md) object, which is the event handler object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3c896-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="3c896-107">Remarks</span></span>  
 <span data-ttu-id="3c896-108">`SetManagedHandler` deve ser chamado no momento da criação.</span><span class="sxs-lookup"><span data-stu-id="3c896-108">`SetManagedHandler` must be called at creation time.</span></span>  
  
 <span data-ttu-id="3c896-109">Se o `ICorDebugManagedCallback` a implementação não contêm interfaces suficientes para lidar com eventos de depuração para o aplicativo que está sendo depurado, `SetManagedHandler` retorna um HRESULT de E_NOINTERFACE.</span><span class="sxs-lookup"><span data-stu-id="3c896-109">If the `ICorDebugManagedCallback` implementation does not contain sufficient interfaces to handle debugging events for the application that is being debugged, `SetManagedHandler` returns an HRESULT of E_NOINTERFACE.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3c896-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3c896-110">Requirements</span></span>  
 <span data-ttu-id="3c896-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3c896-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3c896-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3c896-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3c896-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3c896-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3c896-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3c896-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c896-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3c896-115">See also</span></span>
- [<span data-ttu-id="3c896-116">Interface ICorDebug</span><span class="sxs-lookup"><span data-stu-id="3c896-116">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
