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
ms.openlocfilehash: 22a838748414f9d89cdc7ff469f7f5cc5e11b9d4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61796884"
---
# <a name="icordebugmoduleenableclassloadcallbacks-method"></a><span data-ttu-id="eeba2-102">Método ICorDebugModule::EnableClassLoadCallbacks</span><span class="sxs-lookup"><span data-stu-id="eeba2-102">ICorDebugModule::EnableClassLoadCallbacks Method</span></span>
<span data-ttu-id="eeba2-103">Controles se o [icordebugmanagedcallback:: loadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) e [icordebugmanagedcallback:: Unloadclass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md) retornos de chamada são chamados para esse módulo.</span><span class="sxs-lookup"><span data-stu-id="eeba2-103">Controls whether the [ICorDebugManagedCallback::LoadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) and [ICorDebugManagedCallback::UnloadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md) callbacks are called for this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eeba2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="eeba2-104">Syntax</span></span>  
  
```  
HRESULT EnableClassLoadCallbacks(  
    [in] BOOL bClassLoadCallbacks  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="eeba2-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="eeba2-105">Parameters</span></span>  
 `bClassLoadCallbacks`  
 <span data-ttu-id="eeba2-106">[in] Defina esse valor como `true` para habilitar o common language runtime (CLR) para chamar o `ICorDebugManagedCallback::LoadClass` e `ICorDebugManagedCallback::UnloadClass` métodos quando ocorrem os eventos associados.</span><span class="sxs-lookup"><span data-stu-id="eeba2-106">[in] Set this value to `true` to enable the common language runtime (CLR) to call the `ICorDebugManagedCallback::LoadClass` and `ICorDebugManagedCallback::UnloadClass` methods when their associated events occur.</span></span>  
  
 <span data-ttu-id="eeba2-107">O valor padrão é `false` para os módulos não dinâmicos.</span><span class="sxs-lookup"><span data-stu-id="eeba2-107">The default value is `false` for non-dynamic modules.</span></span> <span data-ttu-id="eeba2-108">O valor é sempre `true` para módulos dinâmicos e não pode ser alterado.</span><span class="sxs-lookup"><span data-stu-id="eeba2-108">The value is always `true` for dynamic modules and cannot be changed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="eeba2-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="eeba2-109">Remarks</span></span>  
 <span data-ttu-id="eeba2-110">O `ICorDebugManagedCallback::LoadClass` e `ICorDebugManagedCallback::UnloadClass` retornos de chamada estão sempre habilitados para módulos dinâmicos e não pode ser desabilitados.</span><span class="sxs-lookup"><span data-stu-id="eeba2-110">The `ICorDebugManagedCallback::LoadClass` and `ICorDebugManagedCallback::UnloadClass` callbacks are always enabled for dynamic modules and cannot be disabled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eeba2-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="eeba2-111">Requirements</span></span>  
 <span data-ttu-id="eeba2-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eeba2-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eeba2-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="eeba2-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="eeba2-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="eeba2-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eeba2-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eeba2-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eeba2-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="eeba2-116">See also</span></span>
