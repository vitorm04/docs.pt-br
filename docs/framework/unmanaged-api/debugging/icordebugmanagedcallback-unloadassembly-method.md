---
title: Método ICorDebugManagedCallback::UnloadAssembly
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.UnloadAssembly
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::UnloadAssembly
helpviewer_keywords:
- ICorDebugManagedCallback::UnloadAssembly method [.NET Framework debugging]
- UnloadAssembly method [.NET Framework debugging]
ms.assetid: 6734321c-c8a9-401f-a558-cad715ec4a77
topic_type:
- apiref
ms.openlocfilehash: 4ae4856eca2c1441ea53df0d9ed3648700b39b24
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130651"
---
# <a name="icordebugmanagedcallbackunloadassembly-method"></a><span data-ttu-id="cc86e-102">Método ICorDebugManagedCallback::UnloadAssembly</span><span class="sxs-lookup"><span data-stu-id="cc86e-102">ICorDebugManagedCallback::UnloadAssembly Method</span></span>
<span data-ttu-id="cc86e-103">Notifica o depurador de que um assembly Common Language Runtime foi descarregado.</span><span class="sxs-lookup"><span data-stu-id="cc86e-103">Notifies the debugger that a common language runtime assembly has been unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc86e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cc86e-104">Syntax</span></span>  
  
```cpp  
HRESULT UnloadAssembly (  
    [in] IcorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugAssembly   *pAssembly  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cc86e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="cc86e-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="cc86e-106">no Um ponteiro para um objeto ICorDebugAppDomain que representa o domínio do aplicativo que continha o assembly.</span><span class="sxs-lookup"><span data-stu-id="cc86e-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contained the assembly.</span></span>  
  
 `pAssembly`  
 <span data-ttu-id="cc86e-107">no Um ponteiro para um objeto ICorDebugAssembly que representa o assembly.</span><span class="sxs-lookup"><span data-stu-id="cc86e-107">[in] A pointer to an ICorDebugAssembly object that represents the assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cc86e-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="cc86e-108">Remarks</span></span>  
 <span data-ttu-id="cc86e-109">O assembly não deve ser usado após este retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="cc86e-109">The assembly should not be used after this callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cc86e-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="cc86e-110">Requirements</span></span>  
 <span data-ttu-id="cc86e-111">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cc86e-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cc86e-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cc86e-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cc86e-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cc86e-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cc86e-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cc86e-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc86e-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cc86e-115">See also</span></span>

- [<span data-ttu-id="cc86e-116">Método LoadAssembly</span><span class="sxs-lookup"><span data-stu-id="cc86e-116">LoadAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadassembly-method.md)
- [<span data-ttu-id="cc86e-117">Interface ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="cc86e-117">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
