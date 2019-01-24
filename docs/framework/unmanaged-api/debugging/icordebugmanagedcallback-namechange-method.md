---
title: Método ICorDebugManagedCallback::NameChange
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.NameChange
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::NameChange
helpviewer_keywords:
- ICorDebugManagedCallback::NameChange method [.NET Framework debugging]
- NameChange method [.NET Framework debugging]
ms.assetid: a7018a0e-880e-4b68-b52a-1cd22c7aad62
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c33f287cf7ccadeb75ba0bbccf9118aeedc1f942
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54607419"
---
# <a name="icordebugmanagedcallbacknamechange-method"></a><span data-ttu-id="1f33d-102">Método ICorDebugManagedCallback::NameChange</span><span class="sxs-lookup"><span data-stu-id="1f33d-102">ICorDebugManagedCallback::NameChange Method</span></span>
<span data-ttu-id="1f33d-103">Notifica o depurador que o nome de um domínio de aplicativo ou um thread foi alterado.</span><span class="sxs-lookup"><span data-stu-id="1f33d-103">Notifies the debugger that the name of either an application domain or a thread has changed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f33d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1f33d-104">Syntax</span></span>  
  
```  
HRESULT NameChange (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *pThread  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1f33d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1f33d-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="1f33d-106">[in] Um ponteiro para um objeto de ICorDebugAppDomain que representa o domínio do aplicativo que teve uma alteração de nome ou que contém o segmento que tiveram uma alteração de nome.</span><span class="sxs-lookup"><span data-stu-id="1f33d-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that either had a name change or that contains the thread that had a name change.</span></span>  
  
 `pThread`  
 <span data-ttu-id="1f33d-107">[in] Um ponteiro para um objeto de ICorDebugThread que representa o thread que tiveram uma alteração de nome.</span><span class="sxs-lookup"><span data-stu-id="1f33d-107">[in] A pointer to an ICorDebugThread object that represents the thread that had a name change.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1f33d-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1f33d-108">Requirements</span></span>  
 <span data-ttu-id="1f33d-109">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1f33d-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1f33d-110">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1f33d-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1f33d-111">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1f33d-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1f33d-112">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1f33d-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f33d-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1f33d-113">See also</span></span>
- [<span data-ttu-id="1f33d-114">Interface ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="1f33d-114">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
