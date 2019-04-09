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
ms.openlocfilehash: 91318ea596cc7d6c8a747901fea2749a64aa2623
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59168110"
---
# <a name="icordebugmanagedcallbackexception-method"></a><span data-ttu-id="dc952-102">Método ICorDebugManagedCallback::Exception</span><span class="sxs-lookup"><span data-stu-id="dc952-102">ICorDebugManagedCallback::Exception Method</span></span>
<span data-ttu-id="dc952-103">Notifica o depurador que foi lançada uma exceção do código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="dc952-103">Notifies the debugger that an exception has been thrown from managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc952-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="dc952-104">Syntax</span></span>  
  
```  
HRESULT Exception (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *pThread,  
    [in] BOOL                unhandled  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dc952-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="dc952-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="dc952-106">[in] Um ponteiro para um objeto ICorDebugAppDomain que representa o domínio de aplicativo no qual a exceção foi gerada.</span><span class="sxs-lookup"><span data-stu-id="dc952-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain in which the exception was thrown.</span></span>  
  
 `pThread`  
 <span data-ttu-id="dc952-107">[in] Um ponteiro para um objeto de ICorDebugThread que representa o thread no qual a exceção foi gerada.</span><span class="sxs-lookup"><span data-stu-id="dc952-107">[in] A pointer to an ICorDebugThread object that represents the thread in which the exception was thrown.</span></span>  
  
 `unhandled`  
 <span data-ttu-id="dc952-108">[in] Se esse valor for `false`, a exceção ainda não tiver sido processada pelo aplicativo; caso contrário, a exceção é tratada e encerrará o processo.</span><span class="sxs-lookup"><span data-stu-id="dc952-108">[in] If this value is `false`, the exception has not yet been processed by the application; otherwise, the exception is unhandled and will terminate the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dc952-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="dc952-109">Remarks</span></span>  
 <span data-ttu-id="dc952-110">A exceção específica pode ser recuperada do objeto de thread.</span><span class="sxs-lookup"><span data-stu-id="dc952-110">The specific exception can be retrieved from the thread object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dc952-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="dc952-111">Requirements</span></span>  
 <span data-ttu-id="dc952-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dc952-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dc952-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="dc952-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dc952-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dc952-114">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="dc952-115">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="dc952-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="dc952-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dc952-116">See also</span></span>

- [<span data-ttu-id="dc952-117">Interface ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="dc952-117">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
