---
title: "Método ICorDebugManagedCallback::UnloadModule"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugManagedCallback.UnloadModule
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::UnloadModule
helpviewer_keywords:
- ICorDebugManagedCallback::UnloadModule method [.NET Framework debugging]
- UnloadModule method [.NET Framework debugging]
ms.assetid: b12bfcd9-1e29-48bf-9a3d-44bfae5df5e8
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7aeb3f12d5217c57d8d8f1f5665840a4515c0998
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmanagedcallbackunloadmodule-method"></a><span data-ttu-id="61d64-102">Método ICorDebugManagedCallback::UnloadModule</span><span class="sxs-lookup"><span data-stu-id="61d64-102">ICorDebugManagedCallback::UnloadModule Method</span></span>
<span data-ttu-id="61d64-103">Notifica o depurador que um módulo de tempo de execução de linguagem comum (DLL) foi descarregado.</span><span class="sxs-lookup"><span data-stu-id="61d64-103">Notifies the debugger that a common language runtime module (DLL) has been unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61d64-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="61d64-104">Syntax</span></span>  
  
```  
HRESULT UnloadModule (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugModule     *pModule  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="61d64-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="61d64-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="61d64-106">[in] Um ponteiro para um objeto ICorDebugAppDomain que representa o domínio de aplicativo que continha o módulo.</span><span class="sxs-lookup"><span data-stu-id="61d64-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contained the module.</span></span>  
  
 `pModule`  
 <span data-ttu-id="61d64-107">[in] Um ponteiro para um objeto ICorDebugModule que representa o módulo.</span><span class="sxs-lookup"><span data-stu-id="61d64-107">[in] A pointer to an ICorDebugModule object that represents the module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="61d64-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="61d64-108">Remarks</span></span>  
 <span data-ttu-id="61d64-109">O módulo não deve ser usado após esta chamada.</span><span class="sxs-lookup"><span data-stu-id="61d64-109">The module should not be used after this call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="61d64-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="61d64-110">Requirements</span></span>  
 <span data-ttu-id="61d64-111">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="61d64-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="61d64-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="61d64-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="61d64-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="61d64-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="61d64-114">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="61d64-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61d64-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="61d64-115">See Also</span></span>  
 [<span data-ttu-id="61d64-116">Método LoadModule</span><span class="sxs-lookup"><span data-stu-id="61d64-116">LoadModule Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadmodule-method.md)  
 [<span data-ttu-id="61d64-117">Interface ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="61d64-117">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
