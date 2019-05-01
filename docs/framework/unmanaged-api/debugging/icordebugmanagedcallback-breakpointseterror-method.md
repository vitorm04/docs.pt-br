---
title: Método ICorDebugManagedCallback::BreakpointSetError
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.BreakpointSetError
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::BreakpointSetError
helpviewer_keywords:
- BreakpointSetError method [.NET Framework debugging]
- ICorDebugManagedCallback::BreakpointSetError method [.NET Framework debugging]
ms.assetid: f2b773a4-c4d0-429c-9717-51d6e2ed86af
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 27d5b8e0127971cc3a46560590fd9d95f0ffd1f0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61988319"
---
# <a name="icordebugmanagedcallbackbreakpointseterror-method"></a><span data-ttu-id="4f8dd-102">Método ICorDebugManagedCallback::BreakpointSetError</span><span class="sxs-lookup"><span data-stu-id="4f8dd-102">ICorDebugManagedCallback::BreakpointSetError Method</span></span>
<span data-ttu-id="4f8dd-103">Notifica o depurador que o common language runtime não pôde ligar com precisão de um ponto de interrupção foi definido antes de uma função ficou just-in-time (JIT) compilado.</span><span class="sxs-lookup"><span data-stu-id="4f8dd-103">Notifies the debugger that the common language runtime was unable to accurately bind a breakpoint that was set before a function was just-in-time (JIT) compiled.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f8dd-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4f8dd-104">Syntax</span></span>  
  
```  
HRESULT BreakpointSetError (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] ICorDebugBreakpoint *pBreakpoint,  
    [in] DWORD                dwError  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4f8dd-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4f8dd-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="4f8dd-106">[in] Um ponteiro para um objeto ICorDebugAppDomain que representa o domínio de aplicativo que contém o ponto de interrupção não associado.</span><span class="sxs-lookup"><span data-stu-id="4f8dd-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contains the unbound breakpoint.</span></span>  
  
 `pThread`  
 <span data-ttu-id="4f8dd-107">[in] Um ponteiro para um objeto de ICorDebugThread que representa o thread que contém o ponto de interrupção não associado.</span><span class="sxs-lookup"><span data-stu-id="4f8dd-107">[in] A pointer to an ICorDebugThread object that represents the thread that contains the unbound breakpoint.</span></span>  
  
 `pBreakpoint`  
 <span data-ttu-id="4f8dd-108">[in] Um ponteiro para um objeto de ICorDebugBreakpoint que representa o ponto de interrupção não associado.</span><span class="sxs-lookup"><span data-stu-id="4f8dd-108">[in] A pointer to an ICorDebugBreakpoint object that represents the unbound breakpoint.</span></span>  
  
 `dwError`  
 <span data-ttu-id="4f8dd-109">[in] Um inteiro que indica o erro.</span><span class="sxs-lookup"><span data-stu-id="4f8dd-109">[in] An integer that indicates the error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4f8dd-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="4f8dd-110">Remarks</span></span>  
 <span data-ttu-id="4f8dd-111">O ponto de interrupção determinado nunca será atingido.</span><span class="sxs-lookup"><span data-stu-id="4f8dd-111">The given breakpoint will never be hit.</span></span> <span data-ttu-id="4f8dd-112">O depurador deve desativar e associá-lo novamente.</span><span class="sxs-lookup"><span data-stu-id="4f8dd-112">The debugger should deactivate and rebind it.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4f8dd-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4f8dd-113">Requirements</span></span>  
 <span data-ttu-id="4f8dd-114">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4f8dd-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4f8dd-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4f8dd-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4f8dd-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4f8dd-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4f8dd-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4f8dd-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f8dd-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4f8dd-118">See also</span></span>

- [<span data-ttu-id="4f8dd-119">Interface ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="4f8dd-119">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
