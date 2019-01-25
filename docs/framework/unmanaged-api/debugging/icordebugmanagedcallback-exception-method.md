---
title: Método ICorDebugManagedCallback::Exception
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.Exception
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::Exception
helpviewer_keywords:
- Exception method, ICorDebugManagedCallback interface [.NET Framework debugging]
- ICorDebugManagedCallback::Exception method [.NET Framework debugging]
ms.assetid: ab18a509-dff3-4930-b585-bd15e0414176
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: db4f0bbef1ce0e6e4a2a0e904bfe8ebb997d5f4d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54586582"
---
# <a name="icordebugmanagedcallbackexception-method"></a><span data-ttu-id="ad491-102">Método ICorDebugManagedCallback::Exception</span><span class="sxs-lookup"><span data-stu-id="ad491-102">ICorDebugManagedCallback::Exception Method</span></span>
<span data-ttu-id="ad491-103">Notifica o depurador que foi lançada uma exceção do código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="ad491-103">Notifies the debugger that an exception has been thrown from managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad491-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ad491-104">Syntax</span></span>  
  
```  
HRESULT Exception (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *pThread,  
    [in] BOOL                unhandled  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ad491-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ad491-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="ad491-106">[in] Um ponteiro para um objeto ICorDebugAppDomain que representa o domínio de aplicativo no qual a exceção foi gerada.</span><span class="sxs-lookup"><span data-stu-id="ad491-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain in which the exception was thrown.</span></span>  
  
 `pThread`  
 <span data-ttu-id="ad491-107">[in] Um ponteiro para um objeto de ICorDebugThread que representa o thread no qual a exceção foi gerada.</span><span class="sxs-lookup"><span data-stu-id="ad491-107">[in] A pointer to an ICorDebugThread object that represents the thread in which the exception was thrown.</span></span>  
  
 `unhandled`  
 <span data-ttu-id="ad491-108">[in] Se esse valor for `false`, a exceção ainda não tiver sido processada pelo aplicativo; caso contrário, a exceção é tratada e encerrará o processo.</span><span class="sxs-lookup"><span data-stu-id="ad491-108">[in] If this value is `false`, the exception has not yet been processed by the application; otherwise, the exception is unhandled and will terminate the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ad491-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="ad491-109">Remarks</span></span>  
 <span data-ttu-id="ad491-110">A exceção específica pode ser recuperada do objeto de thread.</span><span class="sxs-lookup"><span data-stu-id="ad491-110">The specific exception can be retrieved from the thread object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ad491-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ad491-111">Requirements</span></span>  
 <span data-ttu-id="ad491-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ad491-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ad491-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ad491-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ad491-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ad491-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ad491-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ad491-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad491-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ad491-116">See also</span></span>
- [<span data-ttu-id="ad491-117">Interface ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="ad491-117">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
