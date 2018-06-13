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
ms.openlocfilehash: bcf97f9fffabb9ae9579016517cfc335e6f783a6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33404567"
---
# <a name="icordebugsetmanagedhandler-method"></a><span data-ttu-id="1155d-102">Método ICorDebug::SetManagedHandler</span><span class="sxs-lookup"><span data-stu-id="1155d-102">ICorDebug::SetManagedHandler Method</span></span>
<span data-ttu-id="1155d-103">Especifica o objeto do manipulador de eventos para eventos gerenciados.</span><span class="sxs-lookup"><span data-stu-id="1155d-103">Specifies the event handler object for managed events.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1155d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1155d-104">Syntax</span></span>  
  
```  
HRESULT SetManagedHandler (  
    [in] ICorDebugManagedCallback     *pCallback  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1155d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1155d-105">Parameters</span></span>  
 `pCallback`  
 <span data-ttu-id="1155d-106">[in] Um ponteiro para um [ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md) objeto, que é o objeto do manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="1155d-106">[in] A pointer to an [ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md) object, which is the event handler object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1155d-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="1155d-107">Remarks</span></span>  
 <span data-ttu-id="1155d-108">`SetManagedHandler` deve ser chamado no momento da criação.</span><span class="sxs-lookup"><span data-stu-id="1155d-108">`SetManagedHandler` must be called at creation time.</span></span>  
  
 <span data-ttu-id="1155d-109">Se o `ICorDebugManagedCallback` implementação não contém interfaces suficientes para manipular eventos de depuração para o aplicativo que está sendo depurado, `SetManagedHandler` retorna um HRESULT de E_NOINTERFACE.</span><span class="sxs-lookup"><span data-stu-id="1155d-109">If the `ICorDebugManagedCallback` implementation does not contain sufficient interfaces to handle debugging events for the application that is being debugged, `SetManagedHandler` returns an HRESULT of E_NOINTERFACE.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1155d-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1155d-110">Requirements</span></span>  
 <span data-ttu-id="1155d-111">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1155d-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1155d-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1155d-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1155d-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1155d-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1155d-114">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1155d-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1155d-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1155d-115">See Also</span></span>  
 [<span data-ttu-id="1155d-116">Interface ICorDebug</span><span class="sxs-lookup"><span data-stu-id="1155d-116">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
