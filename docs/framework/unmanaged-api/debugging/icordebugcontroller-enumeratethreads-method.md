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
ms.openlocfilehash: 17ba15553d2e7dcd2090870eaab54b4c680631f1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59163079"
---
# <a name="icordebugcontrollerenumeratethreads-method"></a><span data-ttu-id="2a7b8-102">Método ICorDebugController::EnumerateThreads</span><span class="sxs-lookup"><span data-stu-id="2a7b8-102">ICorDebugController::EnumerateThreads Method</span></span>
<span data-ttu-id="2a7b8-103">Obtém um enumerador para os Active Directory threads gerenciados no processo.</span><span class="sxs-lookup"><span data-stu-id="2a7b8-103">Gets an enumerator for the active managed threads in the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a7b8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2a7b8-104">Syntax</span></span>  
  
```  
HRESULT EnumerateThreads (  
    [out] ICorDebugThreadEnum **ppThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2a7b8-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2a7b8-105">Parameters</span></span>  
 `ppThreads`  
 <span data-ttu-id="2a7b8-106">[out] Um ponteiro para o endereço de um objeto de "ICorDebugThreadEnum" que representa um enumerador para todos os threads gerenciados que estão ativos no processo.</span><span class="sxs-lookup"><span data-stu-id="2a7b8-106">[out] A pointer to the address of an "ICorDebugThreadEnum" object that represents an enumerator for all managed threads that are active in the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2a7b8-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="2a7b8-107">Remarks</span></span>  
 <span data-ttu-id="2a7b8-108">Um thread é considerado ativo após o [icordebugmanagedcallback:: CreateThread](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createthread-method.md) retorno de chamada foi distribuído e antes do [icordebugmanagedcallback:: ExitThread](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitthread-method.md) foi distribuído de retorno de chamada .</span><span class="sxs-lookup"><span data-stu-id="2a7b8-108">A thread is considered active after the [ICorDebugManagedCallback::CreateThread](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createthread-method.md) callback has been dispatched and before the [ICorDebugManagedCallback::ExitThread](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitthread-method.md) callback has been dispatched.</span></span> <span data-ttu-id="2a7b8-109">Um thread gerenciado não pode ter necessariamente quadros gerenciados na sua pilha.</span><span class="sxs-lookup"><span data-stu-id="2a7b8-109">A managed thread may not necessarily have any managed frames on its stack.</span></span> <span data-ttu-id="2a7b8-110">Threads podem ser enumerados mesmo antes de [icordebugmanagedcallback:: CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="2a7b8-110">Threads can be enumerated even before the [ICorDebugManagedCallback::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) callback.</span></span> <span data-ttu-id="2a7b8-111">A enumeração naturalmente estará vazia.</span><span class="sxs-lookup"><span data-stu-id="2a7b8-111">The enumeration will naturally be empty.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2a7b8-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2a7b8-112">Requirements</span></span>  
 <span data-ttu-id="2a7b8-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2a7b8-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2a7b8-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2a7b8-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2a7b8-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2a7b8-115">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="2a7b8-116">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="2a7b8-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="2a7b8-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2a7b8-117">See also</span></span>
