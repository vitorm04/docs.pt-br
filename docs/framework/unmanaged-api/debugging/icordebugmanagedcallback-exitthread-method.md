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
ms.openlocfilehash: 3ba1280aa44a9445f6af7fe9a8769b7cdc7edb66
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83205254"
---
# <a name="icordebugmanagedcallbackexitthread-method"></a><span data-ttu-id="5ef97-102">Método ICorDebugManagedCallback::ExitThread</span><span class="sxs-lookup"><span data-stu-id="5ef97-102">ICorDebugManagedCallback::ExitThread Method</span></span>
<span data-ttu-id="5ef97-103">Notifica o depurador de que um thread que estava executando código gerenciado foi encerrado.</span><span class="sxs-lookup"><span data-stu-id="5ef97-103">Notifies the debugger that a thread that was executing managed code has exited.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ef97-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5ef97-104">Syntax</span></span>  
  
```cpp  
HRESULT ExitThread (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *thread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5ef97-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5ef97-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="5ef97-106">no Um ponteiro para um objeto ICorDebugAppDomain que representa o domínio do aplicativo que contém o thread gerenciado.</span><span class="sxs-lookup"><span data-stu-id="5ef97-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the managed thread.</span></span>  
  
 `thread`  
 <span data-ttu-id="5ef97-107">no Um ponteiro para um objeto ICorDebugThread que representa o thread gerenciado.</span><span class="sxs-lookup"><span data-stu-id="5ef97-107">[in] A pointer to an ICorDebugThread object that represents the managed thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5ef97-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="5ef97-108">Remarks</span></span>  
 <span data-ttu-id="5ef97-109">Depois que o `ExitThread` retorno de chamada for acionado, o thread não aparecerá mais nas enumerações de thread.</span><span class="sxs-lookup"><span data-stu-id="5ef97-109">Once the `ExitThread` callback is fired, the thread will no longer appear in thread enumerations.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5ef97-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5ef97-110">Requirements</span></span>  
 <span data-ttu-id="5ef97-111">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5ef97-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5ef97-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5ef97-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5ef97-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5ef97-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5ef97-114">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5ef97-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ef97-115">Confira também</span><span class="sxs-lookup"><span data-stu-id="5ef97-115">See also</span></span>

- [<span data-ttu-id="5ef97-116">Interface ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="5ef97-116">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
