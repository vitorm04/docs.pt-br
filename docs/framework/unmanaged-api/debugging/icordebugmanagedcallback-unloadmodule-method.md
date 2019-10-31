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
ms.openlocfilehash: 70aaf32b9da751b49571ab98a95e432b7f84caa9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130643"
---
# <a name="icordebugmanagedcallbackunloadmodule-method"></a><span data-ttu-id="45ea3-102">Método ICorDebugManagedCallback::UnloadModule</span><span class="sxs-lookup"><span data-stu-id="45ea3-102">ICorDebugManagedCallback::UnloadModule Method</span></span>
<span data-ttu-id="45ea3-103">Notifica o depurador de que um módulo de Common Language Runtime (DLL) foi descarregado.</span><span class="sxs-lookup"><span data-stu-id="45ea3-103">Notifies the debugger that a common language runtime module (DLL) has been unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45ea3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="45ea3-104">Syntax</span></span>  
  
```cpp  
HRESULT UnloadModule (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugModule     *pModule  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="45ea3-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="45ea3-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="45ea3-106">no Um ponteiro para um objeto ICorDebugAppDomain que representa o domínio do aplicativo que continha o módulo.</span><span class="sxs-lookup"><span data-stu-id="45ea3-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contained the module.</span></span>  
  
 `pModule`  
 <span data-ttu-id="45ea3-107">no Um ponteiro para um objeto ICorDebugModule que representa o módulo.</span><span class="sxs-lookup"><span data-stu-id="45ea3-107">[in] A pointer to an ICorDebugModule object that represents the module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="45ea3-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="45ea3-108">Remarks</span></span>  
 <span data-ttu-id="45ea3-109">O módulo não deve ser usado após esta chamada.</span><span class="sxs-lookup"><span data-stu-id="45ea3-109">The module should not be used after this call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="45ea3-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="45ea3-110">Requirements</span></span>  
 <span data-ttu-id="45ea3-111">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="45ea3-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="45ea3-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="45ea3-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="45ea3-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="45ea3-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="45ea3-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="45ea3-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45ea3-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="45ea3-115">See also</span></span>

- [<span data-ttu-id="45ea3-116">Método LoadModule</span><span class="sxs-lookup"><span data-stu-id="45ea3-116">LoadModule Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadmodule-method.md)
- [<span data-ttu-id="45ea3-117">Interface ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="45ea3-117">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
