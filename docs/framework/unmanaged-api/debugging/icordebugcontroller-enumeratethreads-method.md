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
ms.openlocfilehash: 291f6c05171b5e507afaa70537aafdc9002a506e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125406"
---
# <a name="icordebugcontrollerenumeratethreads-method"></a><span data-ttu-id="2330f-102">Método ICorDebugController::EnumerateThreads</span><span class="sxs-lookup"><span data-stu-id="2330f-102">ICorDebugController::EnumerateThreads Method</span></span>
<span data-ttu-id="2330f-103">Obtém um enumerador para os threads gerenciados ativos no processo.</span><span class="sxs-lookup"><span data-stu-id="2330f-103">Gets an enumerator for the active managed threads in the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2330f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2330f-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateThreads (  
    [out] ICorDebugThreadEnum **ppThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2330f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2330f-105">Parameters</span></span>  
 `ppThreads`  
 <span data-ttu-id="2330f-106">fora Um ponteiro para o endereço de um objeto "ICorDebugThreadEnum" que representa um enumerador para todos os threads gerenciados que estão ativos no processo.</span><span class="sxs-lookup"><span data-stu-id="2330f-106">[out] A pointer to the address of an "ICorDebugThreadEnum" object that represents an enumerator for all managed threads that are active in the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2330f-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="2330f-107">Remarks</span></span>  
 <span data-ttu-id="2330f-108">Um thread é considerado ativo após o retorno de chamada [ICorDebugManagedCallback:: CreateThread](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createthread-method.md) ter sido expedido e antes de o retorno de chamada [ICorDebugManagedCallback:: ExitThread](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitthread-method.md) ser expedido.</span><span class="sxs-lookup"><span data-stu-id="2330f-108">A thread is considered active after the [ICorDebugManagedCallback::CreateThread](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createthread-method.md) callback has been dispatched and before the [ICorDebugManagedCallback::ExitThread](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitthread-method.md) callback has been dispatched.</span></span> <span data-ttu-id="2330f-109">Um thread gerenciado pode não ter necessariamente nenhum quadro gerenciado em sua pilha.</span><span class="sxs-lookup"><span data-stu-id="2330f-109">A managed thread may not necessarily have any managed frames on its stack.</span></span> <span data-ttu-id="2330f-110">Os threads podem ser enumerados mesmo antes do retorno de chamada [ICorDebugManagedCallback:: CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) .</span><span class="sxs-lookup"><span data-stu-id="2330f-110">Threads can be enumerated even before the [ICorDebugManagedCallback::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) callback.</span></span> <span data-ttu-id="2330f-111">A enumeração estará naturalmente vazia.</span><span class="sxs-lookup"><span data-stu-id="2330f-111">The enumeration will naturally be empty.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2330f-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2330f-112">Requirements</span></span>  
 <span data-ttu-id="2330f-113">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2330f-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2330f-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2330f-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2330f-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2330f-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2330f-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2330f-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2330f-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2330f-117">See also</span></span>
