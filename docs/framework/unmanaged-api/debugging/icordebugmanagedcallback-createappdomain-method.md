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
ms.openlocfilehash: 35ea69d32ee9b994cc0bf91339c798edcd472f44
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788421"
---
# <a name="icordebugmanagedcallbackcreateappdomain-method"></a><span data-ttu-id="e7c51-102">Método ICorDebugManagedCallback::CreateAppDomain</span><span class="sxs-lookup"><span data-stu-id="e7c51-102">ICorDebugManagedCallback::CreateAppDomain Method</span></span>
<span data-ttu-id="e7c51-103">Notifica o depurador de que um domínio de aplicativo foi criado.</span><span class="sxs-lookup"><span data-stu-id="e7c51-103">Notifies the debugger that an application domain has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7c51-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e7c51-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateAppDomain (  
    [in] ICorDebugProcess   *pProcess,  
    [in] ICorDebugAppDomain *pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e7c51-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e7c51-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="e7c51-106">no Um ponteiro para um objeto ICorDebugProcess que representa o processo no qual o domínio do aplicativo foi criado.</span><span class="sxs-lookup"><span data-stu-id="e7c51-106">[in] A pointer to an ICorDebugProcess object that represents the process in which the application domain was created.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="e7c51-107">no Um ponteiro para um objeto ICorDebugAppDomain que representa o domínio do aplicativo que foi criado.</span><span class="sxs-lookup"><span data-stu-id="e7c51-107">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that has been created.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e7c51-108">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="e7c51-108">Requirements</span></span>  
 <span data-ttu-id="e7c51-109">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e7c51-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e7c51-110">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e7c51-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e7c51-111">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e7c51-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e7c51-112">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e7c51-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7c51-113">Veja também</span><span class="sxs-lookup"><span data-stu-id="e7c51-113">See also</span></span>

- [<span data-ttu-id="e7c51-114">Interface ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="e7c51-114">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
