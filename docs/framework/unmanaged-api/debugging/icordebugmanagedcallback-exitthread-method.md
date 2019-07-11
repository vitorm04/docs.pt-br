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
ms.openlocfilehash: 85247f2f3672e7827f4dd0c93e50cd5da914ee8f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67755771"
---
# <a name="icordebugmanagedcallbackexitthread-method"></a><span data-ttu-id="bb2b5-102">Método ICorDebugManagedCallback::ExitThread</span><span class="sxs-lookup"><span data-stu-id="bb2b5-102">ICorDebugManagedCallback::ExitThread Method</span></span>
<span data-ttu-id="bb2b5-103">Notifica o depurador que um thread que estava executando código gerenciado foi encerrado.</span><span class="sxs-lookup"><span data-stu-id="bb2b5-103">Notifies the debugger that a thread that was executing managed code has exited.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb2b5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bb2b5-104">Syntax</span></span>  
  
```cpp  
HRESULT ExitThread (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *thread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bb2b5-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="bb2b5-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="bb2b5-106">[in] Um ponteiro para um objeto ICorDebugAppDomain que representa o domínio de aplicativo que contém o thread gerenciado.</span><span class="sxs-lookup"><span data-stu-id="bb2b5-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the managed thread.</span></span>  
  
 `thread`  
 <span data-ttu-id="bb2b5-107">[in] Um ponteiro para um objeto de ICorDebugThread que representa o thread gerenciado.</span><span class="sxs-lookup"><span data-stu-id="bb2b5-107">[in] A pointer to an ICorDebugThread object that represents the managed thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bb2b5-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="bb2b5-108">Remarks</span></span>  
 <span data-ttu-id="bb2b5-109">Uma vez o `ExitThread` retorno de chamada é acionado, o thread não aparecerá mais em enumerações de thread.</span><span class="sxs-lookup"><span data-stu-id="bb2b5-109">Once the `ExitThread` callback is fired, the thread will no longer appear in thread enumerations.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bb2b5-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="bb2b5-110">Requirements</span></span>  
 <span data-ttu-id="bb2b5-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bb2b5-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bb2b5-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bb2b5-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bb2b5-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bb2b5-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bb2b5-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bb2b5-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb2b5-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bb2b5-115">See also</span></span>

- [<span data-ttu-id="bb2b5-116">Interface ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="bb2b5-116">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
