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
ms.openlocfilehash: c18ed781d44c873b4cd1957bf0102a4ce0cccad4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139213"
---
# <a name="icordebugmoduleenableclassloadcallbacks-method"></a><span data-ttu-id="2b806-102">Método ICorDebugModule::EnableClassLoadCallbacks</span><span class="sxs-lookup"><span data-stu-id="2b806-102">ICorDebugModule::EnableClassLoadCallbacks Method</span></span>
<span data-ttu-id="2b806-103">Controla se os retornos de chamada [ICorDebugManagedCallback:: LoadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) e [ICorDebugManagedCallback:: UnloadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md) são chamados para este módulo.</span><span class="sxs-lookup"><span data-stu-id="2b806-103">Controls whether the [ICorDebugManagedCallback::LoadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) and [ICorDebugManagedCallback::UnloadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md) callbacks are called for this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b806-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2b806-104">Syntax</span></span>  
  
```cpp  
HRESULT EnableClassLoadCallbacks(  
    [in] BOOL bClassLoadCallbacks  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2b806-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2b806-105">Parameters</span></span>  
 `bClassLoadCallbacks`  
 <span data-ttu-id="2b806-106">no Defina esse valor como `true` para habilitar o Common Language Runtime (CLR) para chamar os métodos `ICorDebugManagedCallback::LoadClass` e `ICorDebugManagedCallback::UnloadClass` quando seus eventos associados ocorrerem.</span><span class="sxs-lookup"><span data-stu-id="2b806-106">[in] Set this value to `true` to enable the common language runtime (CLR) to call the `ICorDebugManagedCallback::LoadClass` and `ICorDebugManagedCallback::UnloadClass` methods when their associated events occur.</span></span>  
  
 <span data-ttu-id="2b806-107">O valor padrão é `false` para módulos não dinâmicos.</span><span class="sxs-lookup"><span data-stu-id="2b806-107">The default value is `false` for non-dynamic modules.</span></span> <span data-ttu-id="2b806-108">O valor sempre é `true` para módulos dinâmicos e não pode ser alterado.</span><span class="sxs-lookup"><span data-stu-id="2b806-108">The value is always `true` for dynamic modules and cannot be changed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2b806-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="2b806-109">Remarks</span></span>  
 <span data-ttu-id="2b806-110">Os retornos de chamada `ICorDebugManagedCallback::LoadClass` e `ICorDebugManagedCallback::UnloadClass` estão sempre habilitados para módulos dinâmicos e não podem ser desabilitados.</span><span class="sxs-lookup"><span data-stu-id="2b806-110">The `ICorDebugManagedCallback::LoadClass` and `ICorDebugManagedCallback::UnloadClass` callbacks are always enabled for dynamic modules and cannot be disabled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2b806-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2b806-111">Requirements</span></span>  
 <span data-ttu-id="2b806-112">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2b806-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2b806-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2b806-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2b806-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2b806-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2b806-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2b806-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b806-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2b806-116">See also</span></span>
