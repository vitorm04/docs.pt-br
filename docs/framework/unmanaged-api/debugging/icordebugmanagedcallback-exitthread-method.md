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
ms.openlocfilehash: bbe2727e4b93cf6d7b3111b6060d170e497024a4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130764"
---
# <a name="icordebugmanagedcallbackexitthread-method"></a><span data-ttu-id="0bd70-102">Método ICorDebugManagedCallback::ExitThread</span><span class="sxs-lookup"><span data-stu-id="0bd70-102">ICorDebugManagedCallback::ExitThread Method</span></span>
<span data-ttu-id="0bd70-103">Notifica o depurador de que um thread que estava executando código gerenciado foi encerrado.</span><span class="sxs-lookup"><span data-stu-id="0bd70-103">Notifies the debugger that a thread that was executing managed code has exited.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0bd70-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0bd70-104">Syntax</span></span>  
  
```cpp  
HRESULT ExitThread (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *thread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0bd70-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0bd70-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="0bd70-106">no Um ponteiro para um objeto ICorDebugAppDomain que representa o domínio do aplicativo que contém o thread gerenciado.</span><span class="sxs-lookup"><span data-stu-id="0bd70-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the managed thread.</span></span>  
  
 `thread`  
 <span data-ttu-id="0bd70-107">no Um ponteiro para um objeto ICorDebugThread que representa o thread gerenciado.</span><span class="sxs-lookup"><span data-stu-id="0bd70-107">[in] A pointer to an ICorDebugThread object that represents the managed thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0bd70-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="0bd70-108">Remarks</span></span>  
 <span data-ttu-id="0bd70-109">Depois que o retorno de chamada `ExitThread` for disparado, o thread não aparecerá mais nas enumerações de thread.</span><span class="sxs-lookup"><span data-stu-id="0bd70-109">Once the `ExitThread` callback is fired, the thread will no longer appear in thread enumerations.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0bd70-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0bd70-110">Requirements</span></span>  
 <span data-ttu-id="0bd70-111">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0bd70-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0bd70-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0bd70-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0bd70-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0bd70-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0bd70-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0bd70-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0bd70-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0bd70-115">See also</span></span>

- [<span data-ttu-id="0bd70-116">Interface ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="0bd70-116">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
