---
title: Método ICorDebugManagedCallback::ExitProcess
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.ExitProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::ExitProcess
helpviewer_keywords:
- ExitProcess method, ICorDebugManagedCallback interface [.NET Framework debugging]
- ICorDebugManagedCallback::ExitProcess method [.NET Framework debugging]
ms.assetid: 63a7d47a-0d54-4e29-9767-9f09feaa38b7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 51162bfb6f9763d2ab4ac1f86e0ccdc15b601271
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61995222"
---
# <a name="icordebugmanagedcallbackexitprocess-method"></a><span data-ttu-id="61bde-102">Método ICorDebugManagedCallback::ExitProcess</span><span class="sxs-lookup"><span data-stu-id="61bde-102">ICorDebugManagedCallback::ExitProcess Method</span></span>
<span data-ttu-id="61bde-103">Notifica o depurador que um processo foi encerrado.</span><span class="sxs-lookup"><span data-stu-id="61bde-103">Notifies the debugger that a process has exited.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61bde-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="61bde-104">Syntax</span></span>  
  
```  
HRESULT ExitProcess (  
    [in] ICorDebugProcess *pProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="61bde-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="61bde-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="61bde-106">[in] Um ponteiro para um objeto ICorDebugProcess que representa o processo.</span><span class="sxs-lookup"><span data-stu-id="61bde-106">[in] A pointer to an ICorDebugProcess object that represents the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="61bde-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="61bde-107">Remarks</span></span>  
 <span data-ttu-id="61bde-108">Você não pode continuar a partir um `ExitProcess` eventos.</span><span class="sxs-lookup"><span data-stu-id="61bde-108">You cannot continue from an `ExitProcess` event.</span></span> <span data-ttu-id="61bde-109">Esse evento pode disparar assincronamente a outros eventos, enquanto o processo parece ser interrompido.</span><span class="sxs-lookup"><span data-stu-id="61bde-109">This event may fire asynchronously to other events while the process appears to be stopped.</span></span> <span data-ttu-id="61bde-110">Isso pode ocorrer se o processo é encerrado enquanto estiver parado, geralmente devido a algumas force externo.</span><span class="sxs-lookup"><span data-stu-id="61bde-110">This can occur if the process terminates while stopped, usually due to some external force.</span></span>  
  
 <span data-ttu-id="61bde-111">Se o common language runtime (CLR) já está distribuindo um retorno de chamada gerenciado, esse evento será atrasado até que esse retorno de chamada foi retornado.</span><span class="sxs-lookup"><span data-stu-id="61bde-111">If the common language runtime (CLR) is already dispatching a managed callback, this event will be delayed until after that callback has returned.</span></span>  
  
 <span data-ttu-id="61bde-112">O `ExitProcess` evento é o único evento de saída/unload é garantido que seja chamado no desligamento.</span><span class="sxs-lookup"><span data-stu-id="61bde-112">The `ExitProcess` event is the only exit/unload event that is guaranteed to get called on shutdown.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="61bde-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="61bde-113">Requirements</span></span>  
 <span data-ttu-id="61bde-114">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="61bde-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="61bde-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="61bde-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="61bde-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="61bde-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="61bde-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="61bde-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61bde-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="61bde-118">See also</span></span>

- [<span data-ttu-id="61bde-119">Interface ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="61bde-119">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
