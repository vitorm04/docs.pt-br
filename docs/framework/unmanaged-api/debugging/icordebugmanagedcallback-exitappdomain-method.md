---
title: Método ICorDebugManagedCallback::ExitAppDomain
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: aed6ccd938761385aafd21802829bd741847b4ba
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61988195"
---
# <a name="icordebugmanagedcallbackexitappdomain-method"></a><span data-ttu-id="1890f-102">Método ICorDebugManagedCallback::ExitAppDomain</span><span class="sxs-lookup"><span data-stu-id="1890f-102">ICorDebugManagedCallback::ExitAppDomain Method</span></span>
<span data-ttu-id="1890f-103">Notifica o depurador que um domínio de aplicativo foi encerrado.</span><span class="sxs-lookup"><span data-stu-id="1890f-103">Notifies the debugger that an application domain has exited.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1890f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1890f-104">Syntax</span></span>  
  
```  
HRESULT ExitAppDomain (  
    [in] ICorDebugProcess   *pProcess,  
    [in] ICorDebugAppDomain *pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1890f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1890f-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="1890f-106">[in] Um ponteiro para um objeto ICorDebugProcess que representa o processo que contém o domínio do aplicativo determinado.</span><span class="sxs-lookup"><span data-stu-id="1890f-106">[in] A pointer to an ICorDebugProcess object that represents the process that contains the given application domain.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="1890f-107">[in] Um ponteiro para um objeto ICorDebugAppDomain que representa o domínio de aplicativo foi encerrado.</span><span class="sxs-lookup"><span data-stu-id="1890f-107">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that has exited.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1890f-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1890f-108">Requirements</span></span>  
 <span data-ttu-id="1890f-109">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1890f-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1890f-110">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1890f-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1890f-111">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1890f-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1890f-112">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1890f-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1890f-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1890f-113">See also</span></span>

- [<span data-ttu-id="1890f-114">Interface ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="1890f-114">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
