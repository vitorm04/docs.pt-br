---
title: Método ICorDebugManagedCallback::UnloadModule
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8826644ae3bdfbef76e9143de5f8f449c1555095
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67761207"
---
# <a name="icordebugmanagedcallbackunloadmodule-method"></a><span data-ttu-id="74600-102">Método ICorDebugManagedCallback::UnloadModule</span><span class="sxs-lookup"><span data-stu-id="74600-102">ICorDebugManagedCallback::UnloadModule Method</span></span>
<span data-ttu-id="74600-103">Notifica o depurador que um módulo de tempo de execução de linguagem comum (DLL) foi descarregado.</span><span class="sxs-lookup"><span data-stu-id="74600-103">Notifies the debugger that a common language runtime module (DLL) has been unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74600-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="74600-104">Syntax</span></span>  
  
```cpp  
HRESULT UnloadModule (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugModule     *pModule  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="74600-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="74600-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="74600-106">[in] Um ponteiro para um objeto ICorDebugAppDomain que representa o domínio de aplicativo que continha o módulo.</span><span class="sxs-lookup"><span data-stu-id="74600-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contained the module.</span></span>  
  
 `pModule`  
 <span data-ttu-id="74600-107">[in] Um ponteiro para um objeto ICorDebugModule que representa o módulo.</span><span class="sxs-lookup"><span data-stu-id="74600-107">[in] A pointer to an ICorDebugModule object that represents the module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="74600-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="74600-108">Remarks</span></span>  
 <span data-ttu-id="74600-109">O módulo não deve ser usado após esta chamada.</span><span class="sxs-lookup"><span data-stu-id="74600-109">The module should not be used after this call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="74600-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="74600-110">Requirements</span></span>  
 <span data-ttu-id="74600-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="74600-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="74600-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="74600-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="74600-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="74600-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="74600-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="74600-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74600-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="74600-115">See also</span></span>

- [<span data-ttu-id="74600-116">Método LoadModule</span><span class="sxs-lookup"><span data-stu-id="74600-116">LoadModule Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadmodule-method.md)
- [<span data-ttu-id="74600-117">Interface ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="74600-117">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
