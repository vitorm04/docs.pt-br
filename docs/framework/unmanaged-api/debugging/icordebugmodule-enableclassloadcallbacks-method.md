---
title: Método ICorDebugModule::EnableClassLoadCallbacks
ms.date: 03/30/2017
api_name:
- ICorDebugModule.EnableClassLoadCallbacks
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::EnableClassLoadCallbacks
helpviewer_keywords:
- ICorDebugModule::EnableClassLoadCallbacks method [.NET Framework debugging]
- EnableClassLoadCallbacks method [.NET Framework debugging]
ms.assetid: 78dad5e4-8e2e-400f-bec3-92ff0205cd82
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a5bb3ab2eafa3465dba82b5326f663635e2b3e64
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54655212"
---
# <a name="icordebugmoduleenableclassloadcallbacks-method"></a><span data-ttu-id="4a4ba-102">Método ICorDebugModule::EnableClassLoadCallbacks</span><span class="sxs-lookup"><span data-stu-id="4a4ba-102">ICorDebugModule::EnableClassLoadCallbacks Method</span></span>
<span data-ttu-id="4a4ba-103">Controles se o [icordebugmanagedcallback:: loadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) e [icordebugmanagedcallback:: Unloadclass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md) retornos de chamada são chamados para esse módulo.</span><span class="sxs-lookup"><span data-stu-id="4a4ba-103">Controls whether the [ICorDebugManagedCallback::LoadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) and [ICorDebugManagedCallback::UnloadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md) callbacks are called for this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a4ba-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4a4ba-104">Syntax</span></span>  
  
```  
HRESULT EnableClassLoadCallbacks(  
    [in] BOOL bClassLoadCallbacks  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4a4ba-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4a4ba-105">Parameters</span></span>  
 `bClassLoadCallbacks`  
 <span data-ttu-id="4a4ba-106">[in] Defina esse valor como `true` para habilitar o common language runtime (CLR) para chamar o `ICorDebugManagedCallback::LoadClass` e `ICorDebugManagedCallback::UnloadClass` métodos quando ocorrem os eventos associados.</span><span class="sxs-lookup"><span data-stu-id="4a4ba-106">[in] Set this value to `true` to enable the common language runtime (CLR) to call the `ICorDebugManagedCallback::LoadClass` and `ICorDebugManagedCallback::UnloadClass` methods when their associated events occur.</span></span>  
  
 <span data-ttu-id="4a4ba-107">O valor padrão é `false` para os módulos não dinâmicos.</span><span class="sxs-lookup"><span data-stu-id="4a4ba-107">The default value is `false` for non-dynamic modules.</span></span> <span data-ttu-id="4a4ba-108">O valor é sempre `true` para módulos dinâmicos e não pode ser alterado.</span><span class="sxs-lookup"><span data-stu-id="4a4ba-108">The value is always `true` for dynamic modules and cannot be changed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4a4ba-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="4a4ba-109">Remarks</span></span>  
 <span data-ttu-id="4a4ba-110">O `ICorDebugManagedCallback::LoadClass` e `ICorDebugManagedCallback::UnloadClass` retornos de chamada estão sempre habilitados para módulos dinâmicos e não pode ser desabilitados.</span><span class="sxs-lookup"><span data-stu-id="4a4ba-110">The `ICorDebugManagedCallback::LoadClass` and `ICorDebugManagedCallback::UnloadClass` callbacks are always enabled for dynamic modules and cannot be disabled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4a4ba-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4a4ba-111">Requirements</span></span>  
 <span data-ttu-id="4a4ba-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4a4ba-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4a4ba-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4a4ba-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4a4ba-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4a4ba-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4a4ba-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4a4ba-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a4ba-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4a4ba-116">See also</span></span>


