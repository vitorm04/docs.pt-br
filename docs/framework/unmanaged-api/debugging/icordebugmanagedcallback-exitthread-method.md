---
title: Método ICorDebugManagedCallback::ExitThread
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.ExitThread
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::ExitThread
helpviewer_keywords:
- ExitThread method [.NET Framework debugging]
- ICorDebugManagedCallback::ExitThread method [.NET Framework debugging]
ms.assetid: 62db708b-6cf0-45c5-b897-4b5c75bd2505
topic_type:
- apiref
ms.openlocfilehash: fa649fd1983a76c71d400ad3e6965ac0794da6ed
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76781603"
---
# <a name="icordebugmanagedcallbackexitthread-method"></a><span data-ttu-id="5dff9-102">Método ICorDebugManagedCallback::ExitThread</span><span class="sxs-lookup"><span data-stu-id="5dff9-102">ICorDebugManagedCallback::ExitThread Method</span></span>
<span data-ttu-id="5dff9-103">Notifica o depurador de que um thread que estava executando código gerenciado foi encerrado.</span><span class="sxs-lookup"><span data-stu-id="5dff9-103">Notifies the debugger that a thread that was executing managed code has exited.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5dff9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5dff9-104">Syntax</span></span>  
  
```cpp  
HRESULT ExitThread (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *thread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5dff9-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5dff9-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="5dff9-106">no Um ponteiro para um objeto ICorDebugAppDomain que representa o domínio do aplicativo que contém o thread gerenciado.</span><span class="sxs-lookup"><span data-stu-id="5dff9-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the managed thread.</span></span>  
  
 `thread`  
 <span data-ttu-id="5dff9-107">no Um ponteiro para um objeto ICorDebugThread que representa o thread gerenciado.</span><span class="sxs-lookup"><span data-stu-id="5dff9-107">[in] A pointer to an ICorDebugThread object that represents the managed thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5dff9-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="5dff9-108">Remarks</span></span>  
 <span data-ttu-id="5dff9-109">Depois que o retorno de chamada `ExitThread` for disparado, o thread não aparecerá mais nas enumerações de thread.</span><span class="sxs-lookup"><span data-stu-id="5dff9-109">Once the `ExitThread` callback is fired, the thread will no longer appear in thread enumerations.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5dff9-110">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="5dff9-110">Requirements</span></span>  
 <span data-ttu-id="5dff9-111">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5dff9-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5dff9-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5dff9-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5dff9-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5dff9-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5dff9-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5dff9-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5dff9-115">Veja também</span><span class="sxs-lookup"><span data-stu-id="5dff9-115">See also</span></span>

- [<span data-ttu-id="5dff9-116">Interface ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="5dff9-116">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
