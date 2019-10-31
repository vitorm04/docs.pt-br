---
title: Método ICorDebugManagedCallback::CreateThread
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.CreateThread
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::CreateThread method
helpviewer_keywords:
- ICorDebugManagedCallback::CreateThread method [.NET Framework debugging]
- CreateThread method [.NET Framework debugging]
ms.assetid: 6b961728-21c4-4e8d-ae81-197458be62f4
topic_type:
- apiref
ms.openlocfilehash: 401cb41d8231e78b8657513e1a755a50814e463b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137398"
---
# <a name="icordebugmanagedcallbackcreatethread-method"></a><span data-ttu-id="55012-102">Método ICorDebugManagedCallback::CreateThread</span><span class="sxs-lookup"><span data-stu-id="55012-102">ICorDebugManagedCallback::CreateThread Method</span></span>
<span data-ttu-id="55012-103">Notifica o depurador de que um thread iniciou a execução de código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="55012-103">Notifies the debugger that a thread has started executing managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55012-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="55012-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateThread (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *thread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="55012-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="55012-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="55012-106">no Um ponteiro para um objeto ICorDebugAppDomain que representa o domínio do aplicativo que contém o thread.</span><span class="sxs-lookup"><span data-stu-id="55012-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contains the thread.</span></span>  
  
 `thread`  
 <span data-ttu-id="55012-107">no Um ponteiro para um objeto ICorDebugThread que representa o thread.</span><span class="sxs-lookup"><span data-stu-id="55012-107">[in] A pointer to an ICorDebugThread object that represents the thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="55012-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="55012-108">Remarks</span></span>  
 <span data-ttu-id="55012-109">O thread será posicionado na primeira instrução de código gerenciado a ser executada.</span><span class="sxs-lookup"><span data-stu-id="55012-109">The thread will be positioned at the first managed code instruction to be executed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="55012-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="55012-110">Requirements</span></span>  
 <span data-ttu-id="55012-111">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="55012-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="55012-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="55012-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="55012-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="55012-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="55012-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="55012-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55012-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="55012-115">See also</span></span>

- [<span data-ttu-id="55012-116">Interface ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="55012-116">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
