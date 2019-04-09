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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59151015"
---
# <a name="icordebugmanagedcallbackbreakpointseterror-method"></a><span data-ttu-id="26eb4-102">Método ICorDebugManagedCallback::BreakpointSetError</span><span class="sxs-lookup"><span data-stu-id="26eb4-102">ICorDebugManagedCallback::BreakpointSetError Method</span></span>
<span data-ttu-id="26eb4-103">Notifica o depurador que o common language runtime não pôde ligar com precisão de um ponto de interrupção foi definido antes de uma função ficou just-in-time (JIT) compilado.</span><span class="sxs-lookup"><span data-stu-id="26eb4-103">Notifies the debugger that the common language runtime was unable to accurately bind a breakpoint that was set before a function was just-in-time (JIT) compiled.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26eb4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="26eb4-104">Syntax</span></span>  
  
```  
HRESULT BreakpointSetError (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] ICorDebugBreakpoint *pBreakpoint,  
    [in] DWORD                dwError  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="26eb4-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="26eb4-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="26eb4-106">[in] Um ponteiro para um objeto ICorDebugAppDomain que representa o domínio de aplicativo que contém o ponto de interrupção não associado.</span><span class="sxs-lookup"><span data-stu-id="26eb4-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contains the unbound breakpoint.</span></span>  
  
 `pThread`  
 <span data-ttu-id="26eb4-107">[in] Um ponteiro para um objeto de ICorDebugThread que representa o thread que contém o ponto de interrupção não associado.</span><span class="sxs-lookup"><span data-stu-id="26eb4-107">[in] A pointer to an ICorDebugThread object that represents the thread that contains the unbound breakpoint.</span></span>  
  
 `pBreakpoint`  
 <span data-ttu-id="26eb4-108">[in] Um ponteiro para um objeto de ICorDebugBreakpoint que representa o ponto de interrupção não associado.</span><span class="sxs-lookup"><span data-stu-id="26eb4-108">[in] A pointer to an ICorDebugBreakpoint object that represents the unbound breakpoint.</span></span>  
  
 `dwError`  
 <span data-ttu-id="26eb4-109">[in] Um inteiro que indica o erro.</span><span class="sxs-lookup"><span data-stu-id="26eb4-109">[in] An integer that indicates the error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="26eb4-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="26eb4-110">Remarks</span></span>  
 <span data-ttu-id="26eb4-111">O ponto de interrupção determinado nunca será atingido.</span><span class="sxs-lookup"><span data-stu-id="26eb4-111">The given breakpoint will never be hit.</span></span> <span data-ttu-id="26eb4-112">O depurador deve desativar e associá-lo novamente.</span><span class="sxs-lookup"><span data-stu-id="26eb4-112">The debugger should deactivate and rebind it.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="26eb4-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="26eb4-113">Requirements</span></span>  
 <span data-ttu-id="26eb4-114">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="26eb4-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="26eb4-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="26eb4-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="26eb4-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="26eb4-116">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="26eb4-117">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="26eb4-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="26eb4-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="26eb4-118">See also</span></span>

- [<span data-ttu-id="26eb4-119">Interface ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="26eb4-119">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
