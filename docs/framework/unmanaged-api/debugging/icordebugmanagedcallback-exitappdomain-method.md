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
ms.openlocfilehash: 7bfa71ccff4a65e72a6b548a09d27648b67c0ae5
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76781847"
---
# <a name="icordebugmanagedcallbackexitappdomain-method"></a><span data-ttu-id="243a3-102">Método ICorDebugManagedCallback::ExitAppDomain</span><span class="sxs-lookup"><span data-stu-id="243a3-102">ICorDebugManagedCallback::ExitAppDomain Method</span></span>
<span data-ttu-id="243a3-103">Notifica o depurador de que um domínio de aplicativo foi encerrado.</span><span class="sxs-lookup"><span data-stu-id="243a3-103">Notifies the debugger that an application domain has exited.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="243a3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="243a3-104">Syntax</span></span>  
  
```cpp  
HRESULT ExitAppDomain (  
    [in] ICorDebugProcess   *pProcess,  
    [in] ICorDebugAppDomain *pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="243a3-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="243a3-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="243a3-106">no Um ponteiro para um objeto ICorDebugProcess que representa o processo que contém o domínio de aplicativo fornecido.</span><span class="sxs-lookup"><span data-stu-id="243a3-106">[in] A pointer to an ICorDebugProcess object that represents the process that contains the given application domain.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="243a3-107">no Um ponteiro para um objeto ICorDebugAppDomain que representa o domínio do aplicativo que foi encerrado.</span><span class="sxs-lookup"><span data-stu-id="243a3-107">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that has exited.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="243a3-108">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="243a3-108">Requirements</span></span>  
 <span data-ttu-id="243a3-109">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="243a3-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="243a3-110">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="243a3-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="243a3-111">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="243a3-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="243a3-112">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="243a3-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="243a3-113">Veja também</span><span class="sxs-lookup"><span data-stu-id="243a3-113">See also</span></span>

- [<span data-ttu-id="243a3-114">Interface ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="243a3-114">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
