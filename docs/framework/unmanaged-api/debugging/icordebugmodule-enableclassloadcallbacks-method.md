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
ms.openlocfilehash: d552b694787b5d9f0d5adc399eda6f75df93c385
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793020"
---
# <a name="icordebugmoduleenableclassloadcallbacks-method"></a><span data-ttu-id="e3c92-102">Método ICorDebugModule::EnableClassLoadCallbacks</span><span class="sxs-lookup"><span data-stu-id="e3c92-102">ICorDebugModule::EnableClassLoadCallbacks Method</span></span>
<span data-ttu-id="e3c92-103">Controla se os retornos de chamada [ICorDebugManagedCallback:: LoadClass](icordebugmanagedcallback-loadclass-method.md) e [ICorDebugManagedCallback:: UnloadClass](icordebugmanagedcallback-unloadclass-method.md) são chamados para este módulo.</span><span class="sxs-lookup"><span data-stu-id="e3c92-103">Controls whether the [ICorDebugManagedCallback::LoadClass](icordebugmanagedcallback-loadclass-method.md) and [ICorDebugManagedCallback::UnloadClass](icordebugmanagedcallback-unloadclass-method.md) callbacks are called for this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3c92-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e3c92-104">Syntax</span></span>  
  
```cpp  
HRESULT EnableClassLoadCallbacks(  
    [in] BOOL bClassLoadCallbacks  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e3c92-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e3c92-105">Parameters</span></span>  
 `bClassLoadCallbacks`  
 <span data-ttu-id="e3c92-106">no Defina esse valor como `true` para habilitar o Common Language Runtime (CLR) para chamar os métodos `ICorDebugManagedCallback::LoadClass` e `ICorDebugManagedCallback::UnloadClass` quando seus eventos associados ocorrerem.</span><span class="sxs-lookup"><span data-stu-id="e3c92-106">[in] Set this value to `true` to enable the common language runtime (CLR) to call the `ICorDebugManagedCallback::LoadClass` and `ICorDebugManagedCallback::UnloadClass` methods when their associated events occur.</span></span>  
  
 <span data-ttu-id="e3c92-107">O valor padrão é `false` para módulos não dinâmicos.</span><span class="sxs-lookup"><span data-stu-id="e3c92-107">The default value is `false` for non-dynamic modules.</span></span> <span data-ttu-id="e3c92-108">O valor sempre é `true` para módulos dinâmicos e não pode ser alterado.</span><span class="sxs-lookup"><span data-stu-id="e3c92-108">The value is always `true` for dynamic modules and cannot be changed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e3c92-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="e3c92-109">Remarks</span></span>  
 <span data-ttu-id="e3c92-110">Os retornos de chamada `ICorDebugManagedCallback::LoadClass` e `ICorDebugManagedCallback::UnloadClass` estão sempre habilitados para módulos dinâmicos e não podem ser desabilitados.</span><span class="sxs-lookup"><span data-stu-id="e3c92-110">The `ICorDebugManagedCallback::LoadClass` and `ICorDebugManagedCallback::UnloadClass` callbacks are always enabled for dynamic modules and cannot be disabled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e3c92-111">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="e3c92-111">Requirements</span></span>  
 <span data-ttu-id="e3c92-112">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e3c92-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e3c92-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e3c92-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e3c92-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e3c92-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e3c92-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e3c92-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3c92-116">Veja também</span><span class="sxs-lookup"><span data-stu-id="e3c92-116">See also</span></span>
