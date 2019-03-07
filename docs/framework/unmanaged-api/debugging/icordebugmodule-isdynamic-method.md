---
title: Método ICorDebugModule::IsDynamic
ms.date: 03/30/2017
api_name:
- ICorDebugModule.IsDynamic
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::IsDynamic
helpviewer_keywords:
- IsDynamic method [.NET Framework debugging]
- ICorDebugModule::IsDynamic method [.NET Framework debugging]
ms.assetid: 5eefe716-5025-4a4c-970c-c823cdc7bb87
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f8012d669cabc1bb589dcfe66bdf2e9b83dc5cb2
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57502443"
---
# <a name="icordebugmoduleisdynamic-method"></a><span data-ttu-id="accc1-102">Método ICorDebugModule::IsDynamic</span><span class="sxs-lookup"><span data-stu-id="accc1-102">ICorDebugModule::IsDynamic Method</span></span>
<span data-ttu-id="accc1-103">Obtém um valor que indica se esse módulo é dinâmico.</span><span class="sxs-lookup"><span data-stu-id="accc1-103">Gets a value that indicates whether this module is dynamic.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="accc1-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="accc1-104">Syntax</span></span>  
  
```  
HRESULT IsDynamic(  
    [out] BOOL *pDynamic  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="accc1-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="accc1-105">Parameters</span></span>  
 `pDynamic`  
 <span data-ttu-id="accc1-106">[out] `true` se esse módulo é dinâmico; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="accc1-106">[out] `true` if this module is dynamic; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="accc1-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="accc1-107">Remarks</span></span>  
 <span data-ttu-id="accc1-108">Um módulo dinâmico pode adicionar novas classes e excluir as classes existentes, mesmo depois que o módulo foi carregado.</span><span class="sxs-lookup"><span data-stu-id="accc1-108">A dynamic module can add new classes and delete existing classes even after the module has been loaded.</span></span> <span data-ttu-id="accc1-109">O [icordebugmanagedcallback:: loadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) e [icordebugmanagedcallback:: Unloadclass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md) retornos de chamada para informar o depurador quando uma classe foi adicionada ou excluída.</span><span class="sxs-lookup"><span data-stu-id="accc1-109">The [ICorDebugManagedCallback::LoadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) and [ICorDebugManagedCallback::UnloadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md) callbacks inform the debugger when a class has been added or deleted.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="accc1-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="accc1-110">Requirements</span></span>  
 <span data-ttu-id="accc1-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="accc1-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="accc1-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="accc1-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="accc1-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="accc1-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="accc1-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="accc1-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
