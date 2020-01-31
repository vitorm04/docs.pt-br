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
ms.openlocfilehash: 88ef9fd5a0aac19954a247d0215fe698ebe30d40
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788330"
---
# <a name="icordebugmanagedcallbackunloadmodule-method"></a><span data-ttu-id="5bb05-102">Método ICorDebugManagedCallback::UnloadModule</span><span class="sxs-lookup"><span data-stu-id="5bb05-102">ICorDebugManagedCallback::UnloadModule Method</span></span>
<span data-ttu-id="5bb05-103">Notifica o depurador de que um módulo de Common Language Runtime (DLL) foi descarregado.</span><span class="sxs-lookup"><span data-stu-id="5bb05-103">Notifies the debugger that a common language runtime module (DLL) has been unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5bb05-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5bb05-104">Syntax</span></span>  
  
```cpp  
HRESULT UnloadModule (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugModule     *pModule  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5bb05-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5bb05-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="5bb05-106">no Um ponteiro para um objeto ICorDebugAppDomain que representa o domínio do aplicativo que continha o módulo.</span><span class="sxs-lookup"><span data-stu-id="5bb05-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contained the module.</span></span>  
  
 `pModule`  
 <span data-ttu-id="5bb05-107">no Um ponteiro para um objeto ICorDebugModule que representa o módulo.</span><span class="sxs-lookup"><span data-stu-id="5bb05-107">[in] A pointer to an ICorDebugModule object that represents the module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5bb05-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="5bb05-108">Remarks</span></span>  
 <span data-ttu-id="5bb05-109">O módulo não deve ser usado após esta chamada.</span><span class="sxs-lookup"><span data-stu-id="5bb05-109">The module should not be used after this call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5bb05-110">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="5bb05-110">Requirements</span></span>  
 <span data-ttu-id="5bb05-111">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5bb05-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5bb05-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5bb05-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5bb05-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5bb05-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5bb05-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5bb05-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5bb05-115">Veja também</span><span class="sxs-lookup"><span data-stu-id="5bb05-115">See also</span></span>

- [<span data-ttu-id="5bb05-116">Método LoadModule</span><span class="sxs-lookup"><span data-stu-id="5bb05-116">LoadModule Method</span></span>](icordebugmanagedcallback-loadmodule-method.md)
- [<span data-ttu-id="5bb05-117">Interface ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="5bb05-117">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
