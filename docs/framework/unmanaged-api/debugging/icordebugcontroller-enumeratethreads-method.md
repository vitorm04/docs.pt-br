---
title: Método ICorDebugController::EnumerateThreads
ms.date: 03/30/2017
api_name:
- ICorDebugController.EnumerateThreads
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::EnumerateThreads
helpviewer_keywords:
- ICorDebugController::EnumerateThreads method [.NET Framework debugging]
- EnumerateThreads method [.NET Framework debugging]
ms.assetid: 73f536f6-4668-4a4a-b3e4-ac7df862d5be
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d73a82ddbb15ba7895f1e5e10f7066909a3c7e43
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54697135"
---
# <a name="icordebugcontrollerenumeratethreads-method"></a><span data-ttu-id="bf524-102">Método ICorDebugController::EnumerateThreads</span><span class="sxs-lookup"><span data-stu-id="bf524-102">ICorDebugController::EnumerateThreads Method</span></span>
<span data-ttu-id="bf524-103">Obtém um enumerador para os Active Directory threads gerenciados no processo.</span><span class="sxs-lookup"><span data-stu-id="bf524-103">Gets an enumerator for the active managed threads in the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf524-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bf524-104">Syntax</span></span>  
  
```  
HRESULT EnumerateThreads (  
    [out] ICorDebugThreadEnum **ppThreads  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bf524-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="bf524-105">Parameters</span></span>  
 `ppThreads`  
 <span data-ttu-id="bf524-106">[out] Um ponteiro para o endereço de um objeto de "ICorDebugThreadEnum" que representa um enumerador para todos os threads gerenciados que estão ativos no processo.</span><span class="sxs-lookup"><span data-stu-id="bf524-106">[out] A pointer to the address of an "ICorDebugThreadEnum" object that represents an enumerator for all managed threads that are active in the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bf524-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="bf524-107">Remarks</span></span>  
 <span data-ttu-id="bf524-108">Um thread é considerado ativo após o [icordebugmanagedcallback:: CreateThread](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createthread-method.md) retorno de chamada foi distribuído e antes do [icordebugmanagedcallback:: ExitThread](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitthread-method.md) foi distribuído de retorno de chamada .</span><span class="sxs-lookup"><span data-stu-id="bf524-108">A thread is considered active after the [ICorDebugManagedCallback::CreateThread](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createthread-method.md) callback has been dispatched and before the [ICorDebugManagedCallback::ExitThread](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitthread-method.md) callback has been dispatched.</span></span> <span data-ttu-id="bf524-109">Um thread gerenciado não pode ter necessariamente quadros gerenciados na sua pilha.</span><span class="sxs-lookup"><span data-stu-id="bf524-109">A managed thread may not necessarily have any managed frames on its stack.</span></span> <span data-ttu-id="bf524-110">Threads podem ser enumerados mesmo antes de [icordebugmanagedcallback:: CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="bf524-110">Threads can be enumerated even before the [ICorDebugManagedCallback::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) callback.</span></span> <span data-ttu-id="bf524-111">A enumeração naturalmente estará vazia.</span><span class="sxs-lookup"><span data-stu-id="bf524-111">The enumeration will naturally be empty.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bf524-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="bf524-112">Requirements</span></span>  
 <span data-ttu-id="bf524-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bf524-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bf524-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bf524-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bf524-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bf524-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bf524-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bf524-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf524-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bf524-117">See also</span></span>

