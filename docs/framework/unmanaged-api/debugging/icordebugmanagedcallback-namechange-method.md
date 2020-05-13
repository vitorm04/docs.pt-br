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
ms.openlocfilehash: 48bfce9966ff12fe1b425fbcd9a81860628a54e6
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212666"
---
# <a name="icordebugmanagedcallbacknamechange-method"></a><span data-ttu-id="dcff7-102">Método ICorDebugManagedCallback::NameChange</span><span class="sxs-lookup"><span data-stu-id="dcff7-102">ICorDebugManagedCallback::NameChange Method</span></span>
<span data-ttu-id="dcff7-103">Notifica o depurador de que o nome de um domínio de aplicativo ou de um thread foi alterado.</span><span class="sxs-lookup"><span data-stu-id="dcff7-103">Notifies the debugger that the name of either an application domain or a thread has changed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dcff7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="dcff7-104">Syntax</span></span>  
  
```cpp  
HRESULT NameChange (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *pThread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dcff7-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="dcff7-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="dcff7-106">no Um ponteiro para um objeto ICorDebugAppDomain que representa o domínio do aplicativo que tinha um nome alterado ou que contém o thread que tinha um nome alterado.</span><span class="sxs-lookup"><span data-stu-id="dcff7-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that either had a name change or that contains the thread that had a name change.</span></span>  
  
 `pThread`  
 <span data-ttu-id="dcff7-107">no Um ponteiro para um objeto ICorDebugThread que representa o thread que tinha um nome alterado.</span><span class="sxs-lookup"><span data-stu-id="dcff7-107">[in] A pointer to an ICorDebugThread object that represents the thread that had a name change.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dcff7-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="dcff7-108">Requirements</span></span>  
 <span data-ttu-id="dcff7-109">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dcff7-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dcff7-110">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="dcff7-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dcff7-111">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dcff7-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dcff7-112">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dcff7-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dcff7-113">Confira também</span><span class="sxs-lookup"><span data-stu-id="dcff7-113">See also</span></span>

- [<span data-ttu-id="dcff7-114">Interface ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="dcff7-114">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
