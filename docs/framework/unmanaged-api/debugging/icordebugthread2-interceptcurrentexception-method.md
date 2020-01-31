---
title: Método ICorDebugThread2::InterceptCurrentException
ms.date: 03/30/2017
api_name:
- ICorDebugThread2.InterceptCurrentException
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread2::InterceptCurrentException
helpviewer_keywords:
- InterceptCurrentException method [.NET Framework debugging]
- ICorDebugThread2::InterceptCurrentException method [.NET Framework debugging]
ms.assetid: 536d2357-1b97-49e0-a10c-c860aed74e6e
topic_type:
- apiref
ms.openlocfilehash: c25a03ef5bbba18da31787c911f83a1348badd4b
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791447"
---
# <a name="icordebugthread2interceptcurrentexception-method"></a><span data-ttu-id="8d89c-102">Método ICorDebugThread2::InterceptCurrentException</span><span class="sxs-lookup"><span data-stu-id="8d89c-102">ICorDebugThread2::InterceptCurrentException Method</span></span>
<span data-ttu-id="8d89c-103">Permite que um depurador intercepte a exceção atual neste thread.</span><span class="sxs-lookup"><span data-stu-id="8d89c-103">Allows a debugger to intercept the current exception on this thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d89c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8d89c-104">Syntax</span></span>  
  
```cpp  
HRESULT InterceptCurrentException (  
    [in] ICorDebugFrame  *pFrame  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8d89c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8d89c-105">Parameters</span></span>  
 `pFrame`  
 <span data-ttu-id="8d89c-106">no Um ponteiro para um ICorDebugFrame que representa o quadro de ativação ativo.</span><span class="sxs-lookup"><span data-stu-id="8d89c-106">[in] A pointer to an ICorDebugFrame that represents the active stack frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8d89c-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="8d89c-107">Remarks</span></span>  
 <span data-ttu-id="8d89c-108">O método `InterceptCurrentException` pode ser chamado entre um retorno de chamada de exceção ([ICorDebugManagedCallback:: Exception](icordebugmanagedcallback-exception-method.md) ou [ICorDebugManagedCallback2:: Exception](icordebugmanagedcallback2-exception-method.md)) e a chamada associada a [ICorDebugController:: Continue](icordebugcontroller-continue-method.md).</span><span class="sxs-lookup"><span data-stu-id="8d89c-108">The `InterceptCurrentException` method can be called between an exception callback ([ICorDebugManagedCallback::Exception](icordebugmanagedcallback-exception-method.md) or [ICorDebugManagedCallback2::Exception](icordebugmanagedcallback2-exception-method.md)) and the associated call to [ICorDebugController::Continue](icordebugcontroller-continue-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8d89c-109">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="8d89c-109">Requirements</span></span>  
 <span data-ttu-id="8d89c-110">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8d89c-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8d89c-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8d89c-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8d89c-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8d89c-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8d89c-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8d89c-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
