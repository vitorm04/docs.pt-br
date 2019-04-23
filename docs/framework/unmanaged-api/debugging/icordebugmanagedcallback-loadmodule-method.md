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
ms.openlocfilehash: cfca06c656f3274f4c5ddb06373a0296dc5e6905
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59164535"
---
# <a name="icordebugmanagedcallbackloadmodule-method"></a><span data-ttu-id="8c4a7-102">Método ICorDebugManagedCallback::LoadModule</span><span class="sxs-lookup"><span data-stu-id="8c4a7-102">ICorDebugManagedCallback::LoadModule Method</span></span>
<span data-ttu-id="8c4a7-103">Notifica o depurador um módulo de runtime (CLR) de linguagem comum foi carregado com êxito.</span><span class="sxs-lookup"><span data-stu-id="8c4a7-103">Notifies the debugger that a common language runtime (CLR) module has been successfully loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c4a7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8c4a7-104">Syntax</span></span>  
  
```  
HRESULT LoadModule (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugModule    *pModule  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8c4a7-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8c4a7-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="8c4a7-106">[in] Um ponteiro para um objeto ICorDebugAppDomain que representa o domínio de aplicativo no qual o módulo foi carregado.</span><span class="sxs-lookup"><span data-stu-id="8c4a7-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain into which the module has been loaded.</span></span>  
  
 `pModule`  
 <span data-ttu-id="8c4a7-107">[in] Um ponteiro para um objeto ICorDebugModule que representa o módulo CLR.</span><span class="sxs-lookup"><span data-stu-id="8c4a7-107">[in] A pointer to an ICorDebugModule object that represents the CLR module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8c4a7-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="8c4a7-108">Remarks</span></span>  
 <span data-ttu-id="8c4a7-109">O `LoadModule` retorno de chamada fornece um tempo apropriado para examinar metadados para o módulo, definir sinalizadores de compilador do just-in-time (JIT), ou habilitar ou desabilitar o carregamento de retornos de chamada para o módulo de classe.</span><span class="sxs-lookup"><span data-stu-id="8c4a7-109">The `LoadModule` callback provides an appropriate time to examine metadata for the module, set just-in-time (JIT) compiler flags, or enable or disable class loading callbacks for the module.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8c4a7-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8c4a7-110">Requirements</span></span>  
 <span data-ttu-id="8c4a7-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8c4a7-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c4a7-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8c4a7-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8c4a7-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8c4a7-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8c4a7-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8c4a7-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c4a7-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8c4a7-115">See also</span></span>

- [<span data-ttu-id="8c4a7-116">Método UnloadModule</span><span class="sxs-lookup"><span data-stu-id="8c4a7-116">UnloadModule Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadmodule-method.md)
- [<span data-ttu-id="8c4a7-117">Interface ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="8c4a7-117">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
