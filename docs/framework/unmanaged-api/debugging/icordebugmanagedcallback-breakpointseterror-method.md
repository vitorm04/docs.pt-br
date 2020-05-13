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
ms.openlocfilehash: 0fa25dd33223ad2a9521aed0917ce35a2a33fa2f
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213381"
---
# <a name="icordebugmanagedcallbackbreakpointseterror-method"></a><span data-ttu-id="73636-102">Método ICorDebugManagedCallback::BreakpointSetError</span><span class="sxs-lookup"><span data-stu-id="73636-102">ICorDebugManagedCallback::BreakpointSetError Method</span></span>
<span data-ttu-id="73636-103">Notifica o depurador de que o Common Language Runtime não pôde ligar com precisão um ponto de interrupção definido antes que uma função tenha sido compilada JIT (just-in-time).</span><span class="sxs-lookup"><span data-stu-id="73636-103">Notifies the debugger that the common language runtime was unable to accurately bind a breakpoint that was set before a function was just-in-time (JIT) compiled.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73636-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="73636-104">Syntax</span></span>  
  
```cpp  
HRESULT BreakpointSetError (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] ICorDebugBreakpoint *pBreakpoint,  
    [in] DWORD                dwError  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="73636-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="73636-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="73636-106">no Um ponteiro para um objeto ICorDebugAppDomain que representa o domínio do aplicativo que contém o ponto de interrupção não associado.</span><span class="sxs-lookup"><span data-stu-id="73636-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contains the unbound breakpoint.</span></span>  
  
 `pThread`  
 <span data-ttu-id="73636-107">no Um ponteiro para um objeto ICorDebugThread que representa o thread que contém o ponto de interrupção não associado.</span><span class="sxs-lookup"><span data-stu-id="73636-107">[in] A pointer to an ICorDebugThread object that represents the thread that contains the unbound breakpoint.</span></span>  
  
 `pBreakpoint`  
 <span data-ttu-id="73636-108">no Um ponteiro para um objeto ICorDebugBreakpoint que representa o ponto de interrupção não associado.</span><span class="sxs-lookup"><span data-stu-id="73636-108">[in] A pointer to an ICorDebugBreakpoint object that represents the unbound breakpoint.</span></span>  
  
 `dwError`  
 <span data-ttu-id="73636-109">no Um inteiro que indica o erro.</span><span class="sxs-lookup"><span data-stu-id="73636-109">[in] An integer that indicates the error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="73636-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="73636-110">Remarks</span></span>  
 <span data-ttu-id="73636-111">O ponto de interrupção fornecido nunca será atingido.</span><span class="sxs-lookup"><span data-stu-id="73636-111">The given breakpoint will never be hit.</span></span> <span data-ttu-id="73636-112">O depurador deve desativar e reassociá-lo.</span><span class="sxs-lookup"><span data-stu-id="73636-112">The debugger should deactivate and rebind it.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="73636-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="73636-113">Requirements</span></span>  
 <span data-ttu-id="73636-114">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="73636-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73636-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="73636-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="73636-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="73636-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="73636-117">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="73636-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73636-118">Confira também</span><span class="sxs-lookup"><span data-stu-id="73636-118">See also</span></span>

- [<span data-ttu-id="73636-119">Interface ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="73636-119">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
