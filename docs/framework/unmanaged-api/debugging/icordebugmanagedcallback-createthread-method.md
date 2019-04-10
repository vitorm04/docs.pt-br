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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c48e92c73347957d8acc5c209f6f5473e9e18524
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59223245"
---
# <a name="icordebugmanagedcallbackcreatethread-method"></a><span data-ttu-id="3dcff-102">Método ICorDebugManagedCallback::CreateThread</span><span class="sxs-lookup"><span data-stu-id="3dcff-102">ICorDebugManagedCallback::CreateThread Method</span></span>
<span data-ttu-id="3dcff-103">Notifica o depurador que um thread foi iniciado executando código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="3dcff-103">Notifies the debugger that a thread has started executing managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3dcff-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3dcff-104">Syntax</span></span>  
  
```  
HRESULT CreateThread (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *thread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3dcff-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3dcff-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="3dcff-106">[in] Um ponteiro para um objeto ICorDebugAppDomain que representa o domínio de aplicativo que contém o segmento.</span><span class="sxs-lookup"><span data-stu-id="3dcff-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contains the thread.</span></span>  
  
 `thread`  
 <span data-ttu-id="3dcff-107">[in] Um ponteiro para um objeto de ICorDebugThread que representa o thread.</span><span class="sxs-lookup"><span data-stu-id="3dcff-107">[in] A pointer to an ICorDebugThread object that represents the thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3dcff-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="3dcff-108">Remarks</span></span>  
 <span data-ttu-id="3dcff-109">O thread será posicionado na primeira instrução de código gerenciado a ser executado.</span><span class="sxs-lookup"><span data-stu-id="3dcff-109">The thread will be positioned at the first managed code instruction to be executed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3dcff-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3dcff-110">Requirements</span></span>  
 <span data-ttu-id="3dcff-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3dcff-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3dcff-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3dcff-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3dcff-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3dcff-113">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="3dcff-114">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="3dcff-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="3dcff-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3dcff-115">See also</span></span>

- [<span data-ttu-id="3dcff-116">Interface ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="3dcff-116">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
