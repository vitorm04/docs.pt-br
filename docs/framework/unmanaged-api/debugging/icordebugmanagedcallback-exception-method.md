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
ms.openlocfilehash: e944a6debf790907b75760c8856ae3a365a84650
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67759626"
---
# <a name="icordebugmanagedcallbackexception-method"></a><span data-ttu-id="06343-102">Método ICorDebugManagedCallback::Exception</span><span class="sxs-lookup"><span data-stu-id="06343-102">ICorDebugManagedCallback::Exception Method</span></span>
<span data-ttu-id="06343-103">Notifica o depurador que foi lançada uma exceção do código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="06343-103">Notifies the debugger that an exception has been thrown from managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06343-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="06343-104">Syntax</span></span>  
  
```cpp  
HRESULT Exception (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *pThread,  
    [in] BOOL                unhandled  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="06343-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="06343-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="06343-106">[in] Um ponteiro para um objeto ICorDebugAppDomain que representa o domínio de aplicativo no qual a exceção foi gerada.</span><span class="sxs-lookup"><span data-stu-id="06343-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain in which the exception was thrown.</span></span>  
  
 `pThread`  
 <span data-ttu-id="06343-107">[in] Um ponteiro para um objeto de ICorDebugThread que representa o thread no qual a exceção foi gerada.</span><span class="sxs-lookup"><span data-stu-id="06343-107">[in] A pointer to an ICorDebugThread object that represents the thread in which the exception was thrown.</span></span>  
  
 `unhandled`  
 <span data-ttu-id="06343-108">[in] Se esse valor for `false`, a exceção ainda não tiver sido processada pelo aplicativo; caso contrário, a exceção é tratada e encerrará o processo.</span><span class="sxs-lookup"><span data-stu-id="06343-108">[in] If this value is `false`, the exception has not yet been processed by the application; otherwise, the exception is unhandled and will terminate the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="06343-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="06343-109">Remarks</span></span>  
 <span data-ttu-id="06343-110">A exceção específica pode ser recuperada do objeto de thread.</span><span class="sxs-lookup"><span data-stu-id="06343-110">The specific exception can be retrieved from the thread object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="06343-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="06343-111">Requirements</span></span>  
 <span data-ttu-id="06343-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="06343-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="06343-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="06343-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="06343-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="06343-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="06343-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="06343-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06343-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="06343-116">See also</span></span>

- [<span data-ttu-id="06343-117">Interface ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="06343-117">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
