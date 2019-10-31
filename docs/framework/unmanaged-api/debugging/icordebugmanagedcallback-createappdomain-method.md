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
ms.openlocfilehash: fa829d0a08846287835d2ac66a461b4b9b27a09a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73090237"
---
# <a name="icordebugmanagedcallbackcreateappdomain-method"></a><span data-ttu-id="13713-102">Método ICorDebugManagedCallback::CreateAppDomain</span><span class="sxs-lookup"><span data-stu-id="13713-102">ICorDebugManagedCallback::CreateAppDomain Method</span></span>
<span data-ttu-id="13713-103">Notifica o depurador de que um domínio de aplicativo foi criado.</span><span class="sxs-lookup"><span data-stu-id="13713-103">Notifies the debugger that an application domain has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13713-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="13713-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateAppDomain (  
    [in] ICorDebugProcess   *pProcess,  
    [in] ICorDebugAppDomain *pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="13713-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="13713-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="13713-106">no Um ponteiro para um objeto ICorDebugProcess que representa o processo no qual o domínio do aplicativo foi criado.</span><span class="sxs-lookup"><span data-stu-id="13713-106">[in] A pointer to an ICorDebugProcess object that represents the process in which the application domain was created.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="13713-107">no Um ponteiro para um objeto ICorDebugAppDomain que representa o domínio do aplicativo que foi criado.</span><span class="sxs-lookup"><span data-stu-id="13713-107">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that has been created.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="13713-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="13713-108">Requirements</span></span>  
 <span data-ttu-id="13713-109">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="13713-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="13713-110">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="13713-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="13713-111">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="13713-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="13713-112">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="13713-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13713-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="13713-113">See also</span></span>

- [<span data-ttu-id="13713-114">Interface ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="13713-114">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
