---
title: Método ICorDebugManagedCallback::Breakpoint
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.Breakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::Breakpoint
helpviewer_keywords:
- ICorDebugManagedCallback::Breakpoint method [.NET Framework debugging]
- Breakpoint method [.NET Framework debugging]
ms.assetid: 60b279b0-a726-46d2-8c53-76986a007ebb
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c13898443f27d7275a58823c8a94ec5657748f28
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57477095"
---
# <a name="icordebugmanagedcallbackbreakpoint-method"></a><span data-ttu-id="b0463-102">Método ICorDebugManagedCallback::Breakpoint</span><span class="sxs-lookup"><span data-stu-id="b0463-102">ICorDebugManagedCallback::Breakpoint Method</span></span>
<span data-ttu-id="b0463-103">Notifica o depurador quando um ponto de interrupção é encontrado.</span><span class="sxs-lookup"><span data-stu-id="b0463-103">Notifies the debugger when a breakpoint is encountered.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0463-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b0463-104">Syntax</span></span>  
  
```  
HRESULT Breakpoint (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] ICorDebugBreakpoint *pBreakpoint  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b0463-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b0463-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="b0463-106">[in] Um ponteiro para um objeto ICorDebugAppDomain que representa o domínio de aplicativo que contém o ponto de interrupção.</span><span class="sxs-lookup"><span data-stu-id="b0463-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contains the breakpoint.</span></span>  
  
 `pThread`  
 <span data-ttu-id="b0463-107">[in] Um ponteiro para um objeto de ICorDebugThread que representa o thread que contém o ponto de interrupção.</span><span class="sxs-lookup"><span data-stu-id="b0463-107">[in] A pointer to an ICorDebugThread object that represents the thread that contains the breakpoint.</span></span>  
  
 `pBreakpoint`  
 <span data-ttu-id="b0463-108">[in] Um ponteiro para um objeto de ICorDebugBreakpoint que representa o ponto de interrupção.</span><span class="sxs-lookup"><span data-stu-id="b0463-108">[in] A pointer to an ICorDebugBreakpoint object that represents the breakpoint.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b0463-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b0463-109">Requirements</span></span>  
 <span data-ttu-id="b0463-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b0463-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b0463-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b0463-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b0463-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b0463-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b0463-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b0463-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0463-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b0463-114">See also</span></span>
- [<span data-ttu-id="b0463-115">Interface ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="b0463-115">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
