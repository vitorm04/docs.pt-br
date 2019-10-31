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
ms.openlocfilehash: 456a79ec290964df8e9f74fc6ca19ef9aabe1230
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130685"
---
# <a name="icordebugmanagedcallbacknamechange-method"></a><span data-ttu-id="38102-102">Método ICorDebugManagedCallback::NameChange</span><span class="sxs-lookup"><span data-stu-id="38102-102">ICorDebugManagedCallback::NameChange Method</span></span>
<span data-ttu-id="38102-103">Notifica o depurador de que o nome de um domínio de aplicativo ou de um thread foi alterado.</span><span class="sxs-lookup"><span data-stu-id="38102-103">Notifies the debugger that the name of either an application domain or a thread has changed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38102-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="38102-104">Syntax</span></span>  
  
```cpp  
HRESULT NameChange (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *pThread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="38102-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="38102-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="38102-106">no Um ponteiro para um objeto ICorDebugAppDomain que representa o domínio do aplicativo que tinha um nome alterado ou que contém o thread que tinha um nome alterado.</span><span class="sxs-lookup"><span data-stu-id="38102-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that either had a name change or that contains the thread that had a name change.</span></span>  
  
 `pThread`  
 <span data-ttu-id="38102-107">no Um ponteiro para um objeto ICorDebugThread que representa o thread que tinha um nome alterado.</span><span class="sxs-lookup"><span data-stu-id="38102-107">[in] A pointer to an ICorDebugThread object that represents the thread that had a name change.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="38102-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="38102-108">Requirements</span></span>  
 <span data-ttu-id="38102-109">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="38102-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="38102-110">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="38102-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="38102-111">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="38102-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="38102-112">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38102-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38102-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="38102-113">See also</span></span>

- [<span data-ttu-id="38102-114">Interface ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="38102-114">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
