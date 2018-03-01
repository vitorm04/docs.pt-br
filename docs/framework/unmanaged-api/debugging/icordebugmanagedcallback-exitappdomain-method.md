---
title: "Método ICorDebugManagedCallback::ExitAppDomain"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugManagedCallback.ExitAppDomain
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::ExitAppDomain
helpviewer_keywords:
- ICorDebugManagedCallback::ExitAppDomain method [.NET Framework debugging]
- ExitAppDomain method [.NET Framework debugging]
ms.assetid: d815486e-b3bd-4fe8-ba28-02abdb4d67ba
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 352ea9b93059237526edad41ec56f200d399a60f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmanagedcallbackexitappdomain-method"></a><span data-ttu-id="f1a42-102">Método ICorDebugManagedCallback::ExitAppDomain</span><span class="sxs-lookup"><span data-stu-id="f1a42-102">ICorDebugManagedCallback::ExitAppDomain Method</span></span>
<span data-ttu-id="f1a42-103">Notifica o depurador que um domínio de aplicativo foi encerrado.</span><span class="sxs-lookup"><span data-stu-id="f1a42-103">Notifies the debugger that an application domain has exited.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1a42-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f1a42-104">Syntax</span></span>  
  
```  
HRESULT ExitAppDomain (  
    [in] ICorDebugProcess   *pProcess,  
    [in] ICorDebugAppDomain *pAppDomain  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f1a42-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f1a42-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="f1a42-106">[in] Um ponteiro para um objeto ICorDebugProcess que representa o processo que contém o domínio de determinado aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f1a42-106">[in] A pointer to an ICorDebugProcess object that represents the process that contains the given application domain.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="f1a42-107">[in] Um ponteiro para um objeto ICorDebugAppDomain que representa o domínio de aplicativo que foi encerrado.</span><span class="sxs-lookup"><span data-stu-id="f1a42-107">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that has exited.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f1a42-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f1a42-108">Requirements</span></span>  
 <span data-ttu-id="f1a42-109">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f1a42-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f1a42-110">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f1a42-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f1a42-111">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f1a42-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f1a42-112">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f1a42-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1a42-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f1a42-113">See Also</span></span>  
 [<span data-ttu-id="f1a42-114">Interface ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="f1a42-114">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
