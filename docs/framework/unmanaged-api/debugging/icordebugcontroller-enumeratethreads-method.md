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
ms.openlocfilehash: 815dc63a2dedecc613506b0f98702f58d6e7bd04
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76783786"
---
# <a name="icordebugcontrollerenumeratethreads-method"></a><span data-ttu-id="55d77-102">Método ICorDebugController::EnumerateThreads</span><span class="sxs-lookup"><span data-stu-id="55d77-102">ICorDebugController::EnumerateThreads Method</span></span>
<span data-ttu-id="55d77-103">Obtém um enumerador para os threads gerenciados ativos no processo.</span><span class="sxs-lookup"><span data-stu-id="55d77-103">Gets an enumerator for the active managed threads in the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55d77-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="55d77-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateThreads (  
    [out] ICorDebugThreadEnum **ppThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="55d77-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="55d77-105">Parameters</span></span>  
 `ppThreads`  
 <span data-ttu-id="55d77-106">fora Um ponteiro para o endereço de um objeto "ICorDebugThreadEnum" que representa um enumerador para todos os threads gerenciados que estão ativos no processo.</span><span class="sxs-lookup"><span data-stu-id="55d77-106">[out] A pointer to the address of an "ICorDebugThreadEnum" object that represents an enumerator for all managed threads that are active in the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="55d77-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="55d77-107">Remarks</span></span>  
 <span data-ttu-id="55d77-108">Um thread é considerado ativo após o retorno de chamada [ICorDebugManagedCallback:: CreateThread](icordebugmanagedcallback-createthread-method.md) ter sido expedido e antes de o retorno de chamada [ICorDebugManagedCallback:: ExitThread](icordebugmanagedcallback-exitthread-method.md) ser expedido.</span><span class="sxs-lookup"><span data-stu-id="55d77-108">A thread is considered active after the [ICorDebugManagedCallback::CreateThread](icordebugmanagedcallback-createthread-method.md) callback has been dispatched and before the [ICorDebugManagedCallback::ExitThread](icordebugmanagedcallback-exitthread-method.md) callback has been dispatched.</span></span> <span data-ttu-id="55d77-109">Um thread gerenciado pode não ter necessariamente nenhum quadro gerenciado em sua pilha.</span><span class="sxs-lookup"><span data-stu-id="55d77-109">A managed thread may not necessarily have any managed frames on its stack.</span></span> <span data-ttu-id="55d77-110">Os threads podem ser enumerados mesmo antes do retorno de chamada [ICorDebugManagedCallback:: CreateProcess](icordebugmanagedcallback-createprocess-method.md) .</span><span class="sxs-lookup"><span data-stu-id="55d77-110">Threads can be enumerated even before the [ICorDebugManagedCallback::CreateProcess](icordebugmanagedcallback-createprocess-method.md) callback.</span></span> <span data-ttu-id="55d77-111">A enumeração estará naturalmente vazia.</span><span class="sxs-lookup"><span data-stu-id="55d77-111">The enumeration will naturally be empty.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="55d77-112">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="55d77-112">Requirements</span></span>  
 <span data-ttu-id="55d77-113">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="55d77-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="55d77-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="55d77-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="55d77-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="55d77-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="55d77-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="55d77-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55d77-117">Veja também</span><span class="sxs-lookup"><span data-stu-id="55d77-117">See also</span></span>
