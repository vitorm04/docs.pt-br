---
title: "Método ICorDebugManagedCallback::LoadModule"
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
- ICorDebugManagedCallback.LoadModule
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::LoadModule
helpviewer_keywords:
- ICorDebugManagedCallback::LoadModule method [.NET Framework debugging]
- LoadModule method [.NET Framework debugging]
ms.assetid: 66ec04e9-87cb-42ce-9720-81522abb5d5a
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5d17001db68043f5d46a90738a8ad3e0635de762
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmanagedcallbackloadmodule-method"></a><span data-ttu-id="81c2e-102">Método ICorDebugManagedCallback::LoadModule</span><span class="sxs-lookup"><span data-stu-id="81c2e-102">ICorDebugManagedCallback::LoadModule Method</span></span>
<span data-ttu-id="81c2e-103">Notifica o depurador um módulo de runtime (CLR) de linguagem comum foi carregado com êxito.</span><span class="sxs-lookup"><span data-stu-id="81c2e-103">Notifies the debugger that a common language runtime (CLR) module has been successfully loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81c2e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="81c2e-104">Syntax</span></span>  
  
```  
HRESULT LoadModule (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugModule    *pModule  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="81c2e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="81c2e-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="81c2e-106">[in] Um ponteiro para um objeto ICorDebugAppDomain que representa o domínio de aplicativo no qual o módulo foi carregado.</span><span class="sxs-lookup"><span data-stu-id="81c2e-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain into which the module has been loaded.</span></span>  
  
 `pModule`  
 <span data-ttu-id="81c2e-107">[in] Um ponteiro para um objeto ICorDebugModule que representa o módulo CLR.</span><span class="sxs-lookup"><span data-stu-id="81c2e-107">[in] A pointer to an ICorDebugModule object that represents the CLR module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="81c2e-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="81c2e-108">Remarks</span></span>  
 <span data-ttu-id="81c2e-109">O `LoadModule` retorno de chamada oferece um momento apropriado para examinar metadados para o módulo, definir sinalizadores de compilador just-in-time (JIT) ou habilitar ou desabilitar o carregamento de retornos de chamada para o módulo de classe.</span><span class="sxs-lookup"><span data-stu-id="81c2e-109">The `LoadModule` callback provides an appropriate time to examine metadata for the module, set just-in-time (JIT) compiler flags, or enable or disable class loading callbacks for the module.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="81c2e-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="81c2e-110">Requirements</span></span>  
 <span data-ttu-id="81c2e-111">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="81c2e-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="81c2e-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="81c2e-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="81c2e-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="81c2e-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="81c2e-114">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="81c2e-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81c2e-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="81c2e-115">See Also</span></span>  
 [<span data-ttu-id="81c2e-116">Método UnloadModule</span><span class="sxs-lookup"><span data-stu-id="81c2e-116">UnloadModule Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadmodule-method.md)  
 [<span data-ttu-id="81c2e-117">Interface ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="81c2e-117">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
