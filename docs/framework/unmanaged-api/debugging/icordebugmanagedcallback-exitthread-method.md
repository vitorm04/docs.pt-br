---
title: Método ICorDebugManagedCallback::ExitThread
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.ExitThread
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::ExitThread
helpviewer_keywords:
- ExitThread method [.NET Framework debugging]
- ICorDebugManagedCallback::ExitThread method [.NET Framework debugging]
ms.assetid: 62db708b-6cf0-45c5-b897-4b5c75bd2505
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 24b01fecc7947d14e36b4411a58d200667b0f2a7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugmanagedcallbackexitthread-method"></a><span data-ttu-id="eab39-102">Método ICorDebugManagedCallback::ExitThread</span><span class="sxs-lookup"><span data-stu-id="eab39-102">ICorDebugManagedCallback::ExitThread Method</span></span>
<span data-ttu-id="eab39-103">Notifica o depurador que um thread que estava executando código gerenciado foi encerrado.</span><span class="sxs-lookup"><span data-stu-id="eab39-103">Notifies the debugger that a thread that was executing managed code has exited.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eab39-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="eab39-104">Syntax</span></span>  
  
```  
HRESULT ExitThread (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *thread  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="eab39-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="eab39-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="eab39-106">[in] Um ponteiro para um objeto ICorDebugAppDomain que representa o domínio de aplicativo que contém o thread gerenciado.</span><span class="sxs-lookup"><span data-stu-id="eab39-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the managed thread.</span></span>  
  
 `thread`  
 <span data-ttu-id="eab39-107">[in] Um ponteiro para um objeto ICorDebugThread que representa o thread gerenciado.</span><span class="sxs-lookup"><span data-stu-id="eab39-107">[in] A pointer to an ICorDebugThread object that represents the managed thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="eab39-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="eab39-108">Remarks</span></span>  
 <span data-ttu-id="eab39-109">Uma vez o `ExitThread` retorno de chamada é acionado, o thread não aparecerá mais no enumerações de thread.</span><span class="sxs-lookup"><span data-stu-id="eab39-109">Once the `ExitThread` callback is fired, the thread will no longer appear in thread enumerations.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eab39-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="eab39-110">Requirements</span></span>  
 <span data-ttu-id="eab39-111">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eab39-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eab39-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="eab39-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="eab39-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="eab39-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eab39-114">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eab39-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eab39-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="eab39-115">See Also</span></span>  
 [<span data-ttu-id="eab39-116">Interface ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="eab39-116">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
