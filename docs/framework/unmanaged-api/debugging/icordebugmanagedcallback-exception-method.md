---
title: "Método ICorDebugManagedCallback::Exception"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback.Exception
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback::Exception
helpviewer_keywords:
- Exception method, ICorDebugManagedCallback interface [.NET Framework debugging]
- ICorDebugManagedCallback::Exception method [.NET Framework debugging]
ms.assetid: ab18a509-dff3-4930-b585-bd15e0414176
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b964f38501822360e6fc63600f7854c9a90f094c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmanagedcallbackexception-method"></a><span data-ttu-id="0fd4b-102">Método ICorDebugManagedCallback::Exception</span><span class="sxs-lookup"><span data-stu-id="0fd4b-102">ICorDebugManagedCallback::Exception Method</span></span>
<span data-ttu-id="0fd4b-103">Notifica o depurador que tenha sido lançada uma exceção do código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="0fd4b-103">Notifies the debugger that an exception has been thrown from managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0fd4b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0fd4b-104">Syntax</span></span>  
  
```  
HRESULT Exception (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *pThread,  
    [in] BOOL                unhandled  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0fd4b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0fd4b-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="0fd4b-106">[in] Um ponteiro para um objeto ICorDebugAppDomain que representa o domínio de aplicativo no qual a exceção foi gerada.</span><span class="sxs-lookup"><span data-stu-id="0fd4b-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain in which the exception was thrown.</span></span>  
  
 `pThread`  
 <span data-ttu-id="0fd4b-107">[in] Um ponteiro para um objeto ICorDebugThread que representa o thread em que a exceção foi lançada.</span><span class="sxs-lookup"><span data-stu-id="0fd4b-107">[in] A pointer to an ICorDebugThread object that represents the thread in which the exception was thrown.</span></span>  
  
 `unhandled`  
 <span data-ttu-id="0fd4b-108">[in] Se esse valor for `false`, a exceção ainda não foi processada pelo aplicativo; caso contrário, a exceção é sem tratamento e o processo será encerrado.</span><span class="sxs-lookup"><span data-stu-id="0fd4b-108">[in] If this value is `false`, the exception has not yet been processed by the application; otherwise, the exception is unhandled and will terminate the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0fd4b-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="0fd4b-109">Remarks</span></span>  
 <span data-ttu-id="0fd4b-110">A exceção específica pode ser recuperada do objeto de thread.</span><span class="sxs-lookup"><span data-stu-id="0fd4b-110">The specific exception can be retrieved from the thread object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0fd4b-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0fd4b-111">Requirements</span></span>  
 <span data-ttu-id="0fd4b-112">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0fd4b-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0fd4b-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0fd4b-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0fd4b-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0fd4b-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0fd4b-115">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0fd4b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0fd4b-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0fd4b-116">See Also</span></span>  
 [<span data-ttu-id="0fd4b-117">Interface ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="0fd4b-117">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
