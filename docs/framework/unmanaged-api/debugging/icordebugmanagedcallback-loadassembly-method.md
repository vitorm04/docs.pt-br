---
title: "Método ICorDebugManagedCallback::LoadAssembly"
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
- ICorDebugManagedCallback.LoadAssembly
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::LoadAssembly
helpviewer_keywords:
- LoadAssembly method [.NET Framework debugging]
- ICorDebugManagedCallback::LoadAssembly method [.NET Framework debugging]
ms.assetid: 55cb673a-e240-43a6-a406-6912e7c0fe66
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 90cc41abd01f7cbef7037ee2b28465dc85de5131
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmanagedcallbackloadassembly-method"></a><span data-ttu-id="e9003-102">Método ICorDebugManagedCallback::LoadAssembly</span><span class="sxs-lookup"><span data-stu-id="e9003-102">ICorDebugManagedCallback::LoadAssembly Method</span></span>
<span data-ttu-id="e9003-103">Notifica o depurador que um assembly do common language runtime (CLR) foi carregado com êxito.</span><span class="sxs-lookup"><span data-stu-id="e9003-103">Notifies the debugger that a common language runtime (CLR) assembly has been successfully loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9003-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e9003-104">Syntax</span></span>  
  
```  
HRESULT LoadAssembly (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugAssembly  *pAssembly  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e9003-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e9003-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="e9003-106">[in] Um ponteiro para um objeto ICorDebugAppDomain que representa o domínio de aplicativo no qual o assembly foi carregado.</span><span class="sxs-lookup"><span data-stu-id="e9003-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain into which the assembly has been loaded.</span></span>  
  
 `pAssembly`  
 <span data-ttu-id="e9003-107">[in] Um ponteiro para um objeto ICorDebugAssembly que representa o assembly.</span><span class="sxs-lookup"><span data-stu-id="e9003-107">[in] A pointer to an ICorDebugAssembly object that represents the assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e9003-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e9003-108">Requirements</span></span>  
 <span data-ttu-id="e9003-109">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e9003-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e9003-110">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e9003-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e9003-111">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e9003-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e9003-112">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e9003-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9003-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e9003-113">See Also</span></span>  
 [<span data-ttu-id="e9003-114">Método UnloadAssembly</span><span class="sxs-lookup"><span data-stu-id="e9003-114">UnloadAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadassembly-method.md)  
 [<span data-ttu-id="e9003-115">Interface ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="e9003-115">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
