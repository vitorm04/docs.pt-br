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
ms.openlocfilehash: 1ca3adf30ad633fcfb10a4b43a435698d2899597
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213524"
---
# <a name="icordebugmoduleenableclassloadcallbacks-method"></a><span data-ttu-id="679a0-102">Método ICorDebugModule::EnableClassLoadCallbacks</span><span class="sxs-lookup"><span data-stu-id="679a0-102">ICorDebugModule::EnableClassLoadCallbacks Method</span></span>
<span data-ttu-id="679a0-103">Controla se os retornos de chamada [ICorDebugManagedCallback:: LoadClass](icordebugmanagedcallback-loadclass-method.md) e [ICorDebugManagedCallback:: UnloadClass](icordebugmanagedcallback-unloadclass-method.md) são chamados para este módulo.</span><span class="sxs-lookup"><span data-stu-id="679a0-103">Controls whether the [ICorDebugManagedCallback::LoadClass](icordebugmanagedcallback-loadclass-method.md) and [ICorDebugManagedCallback::UnloadClass](icordebugmanagedcallback-unloadclass-method.md) callbacks are called for this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="679a0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="679a0-104">Syntax</span></span>  
  
```cpp  
HRESULT EnableClassLoadCallbacks(  
    [in] BOOL bClassLoadCallbacks  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="679a0-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="679a0-105">Parameters</span></span>  
 `bClassLoadCallbacks`  
 <span data-ttu-id="679a0-106">no Defina esse valor como `true` para habilitar o Common Language Runtime (CLR) para chamar os `ICorDebugManagedCallback::LoadClass` `ICorDebugManagedCallback::UnloadClass` métodos e quando os eventos associados ocorrerem.</span><span class="sxs-lookup"><span data-stu-id="679a0-106">[in] Set this value to `true` to enable the common language runtime (CLR) to call the `ICorDebugManagedCallback::LoadClass` and `ICorDebugManagedCallback::UnloadClass` methods when their associated events occur.</span></span>  
  
 <span data-ttu-id="679a0-107">O valor padrão é `false` para módulos não dinâmicos.</span><span class="sxs-lookup"><span data-stu-id="679a0-107">The default value is `false` for non-dynamic modules.</span></span> <span data-ttu-id="679a0-108">O valor é sempre `true` para módulos dinâmicos e não pode ser alterado.</span><span class="sxs-lookup"><span data-stu-id="679a0-108">The value is always `true` for dynamic modules and cannot be changed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="679a0-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="679a0-109">Remarks</span></span>  
 <span data-ttu-id="679a0-110">Os `ICorDebugManagedCallback::LoadClass` `ICorDebugManagedCallback::UnloadClass` retornos de chamada e estão sempre habilitados para módulos dinâmicos e não podem ser desabilitados.</span><span class="sxs-lookup"><span data-stu-id="679a0-110">The `ICorDebugManagedCallback::LoadClass` and `ICorDebugManagedCallback::UnloadClass` callbacks are always enabled for dynamic modules and cannot be disabled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="679a0-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="679a0-111">Requirements</span></span>  
 <span data-ttu-id="679a0-112">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="679a0-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="679a0-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="679a0-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="679a0-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="679a0-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="679a0-115">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="679a0-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="679a0-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="679a0-116">See also</span></span>
