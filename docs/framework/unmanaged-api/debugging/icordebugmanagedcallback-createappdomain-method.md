---
title: Método ICorDebugManagedCallback::CreateAppDomain
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.CreateAppDomain
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::CreateAppDomain
helpviewer_keywords:
- CreateAppDomain method [.NET Framework debugging]
- ICorDebugManagedCallback::CreateAppDomain method [.NET Framework debugging]
ms.assetid: 48d410d7-6749-4125-a8fd-f9562c7088e9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bdac4b5b7a4a64a5fc939a7d35718ef276717fe7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33415422"
---
# <a name="icordebugmanagedcallbackcreateappdomain-method"></a><span data-ttu-id="0e406-102">Método ICorDebugManagedCallback::CreateAppDomain</span><span class="sxs-lookup"><span data-stu-id="0e406-102">ICorDebugManagedCallback::CreateAppDomain Method</span></span>
<span data-ttu-id="0e406-103">Notifica o depurador um domínio de aplicativo foi criado.</span><span class="sxs-lookup"><span data-stu-id="0e406-103">Notifies the debugger that an application domain has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e406-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0e406-104">Syntax</span></span>  
  
```  
HRESULT CreateAppDomain (  
    [in] ICorDebugProcess   *pProcess,  
    [in] ICorDebugAppDomain *pAppDomain  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0e406-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0e406-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="0e406-106">[in] Um ponteiro para um objeto ICorDebugProcess que representa o processo no qual o domínio de aplicativo foi criado.</span><span class="sxs-lookup"><span data-stu-id="0e406-106">[in] A pointer to an ICorDebugProcess object that represents the process in which the application domain was created.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="0e406-107">[in] Um ponteiro para um objeto ICorDebugAppDomain que representa o domínio de aplicativo que foi criado.</span><span class="sxs-lookup"><span data-stu-id="0e406-107">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that has been created.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0e406-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0e406-108">Requirements</span></span>  
 <span data-ttu-id="0e406-109">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0e406-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0e406-110">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0e406-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0e406-111">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0e406-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0e406-112">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0e406-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e406-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0e406-113">See Also</span></span>  
 [<span data-ttu-id="0e406-114">Interface ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="0e406-114">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
