---
title: Método ICorDebugManagedCallback::LoadModule
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e49c20d7627f666efd6561cee19ca505f723b714
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57474430"
---
# <a name="icordebugmanagedcallbackloadmodule-method"></a><span data-ttu-id="bac71-102">Método ICorDebugManagedCallback::LoadModule</span><span class="sxs-lookup"><span data-stu-id="bac71-102">ICorDebugManagedCallback::LoadModule Method</span></span>
<span data-ttu-id="bac71-103">Notifica o depurador um módulo de runtime (CLR) de linguagem comum foi carregado com êxito.</span><span class="sxs-lookup"><span data-stu-id="bac71-103">Notifies the debugger that a common language runtime (CLR) module has been successfully loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bac71-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bac71-104">Syntax</span></span>  
  
```  
HRESULT LoadModule (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugModule    *pModule  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bac71-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="bac71-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="bac71-106">[in] Um ponteiro para um objeto ICorDebugAppDomain que representa o domínio de aplicativo no qual o módulo foi carregado.</span><span class="sxs-lookup"><span data-stu-id="bac71-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain into which the module has been loaded.</span></span>  
  
 `pModule`  
 <span data-ttu-id="bac71-107">[in] Um ponteiro para um objeto ICorDebugModule que representa o módulo CLR.</span><span class="sxs-lookup"><span data-stu-id="bac71-107">[in] A pointer to an ICorDebugModule object that represents the CLR module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bac71-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="bac71-108">Remarks</span></span>  
 <span data-ttu-id="bac71-109">O `LoadModule` retorno de chamada fornece um tempo apropriado para examinar metadados para o módulo, definir sinalizadores de compilador do just-in-time (JIT), ou habilitar ou desabilitar o carregamento de retornos de chamada para o módulo de classe.</span><span class="sxs-lookup"><span data-stu-id="bac71-109">The `LoadModule` callback provides an appropriate time to examine metadata for the module, set just-in-time (JIT) compiler flags, or enable or disable class loading callbacks for the module.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bac71-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="bac71-110">Requirements</span></span>  
 <span data-ttu-id="bac71-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bac71-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bac71-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bac71-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bac71-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bac71-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bac71-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bac71-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bac71-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bac71-115">See also</span></span>
- [<span data-ttu-id="bac71-116">Método UnloadModule</span><span class="sxs-lookup"><span data-stu-id="bac71-116">UnloadModule Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadmodule-method.md)
- [<span data-ttu-id="bac71-117">Interface ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="bac71-117">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
