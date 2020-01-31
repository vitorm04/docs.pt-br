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
ms.openlocfilehash: 2d8fa00a1a998430a55b913cfa25624246eab967
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788355"
---
# <a name="icordebugmanagedcallbacknamechange-method"></a><span data-ttu-id="842a8-102">Método ICorDebugManagedCallback::NameChange</span><span class="sxs-lookup"><span data-stu-id="842a8-102">ICorDebugManagedCallback::NameChange Method</span></span>
<span data-ttu-id="842a8-103">Notifica o depurador de que o nome de um domínio de aplicativo ou de um thread foi alterado.</span><span class="sxs-lookup"><span data-stu-id="842a8-103">Notifies the debugger that the name of either an application domain or a thread has changed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="842a8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="842a8-104">Syntax</span></span>  
  
```cpp  
HRESULT NameChange (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *pThread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="842a8-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="842a8-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="842a8-106">no Um ponteiro para um objeto ICorDebugAppDomain que representa o domínio do aplicativo que tinha um nome alterado ou que contém o thread que tinha um nome alterado.</span><span class="sxs-lookup"><span data-stu-id="842a8-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that either had a name change or that contains the thread that had a name change.</span></span>  
  
 `pThread`  
 <span data-ttu-id="842a8-107">no Um ponteiro para um objeto ICorDebugThread que representa o thread que tinha um nome alterado.</span><span class="sxs-lookup"><span data-stu-id="842a8-107">[in] A pointer to an ICorDebugThread object that represents the thread that had a name change.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="842a8-108">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="842a8-108">Requirements</span></span>  
 <span data-ttu-id="842a8-109">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="842a8-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="842a8-110">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="842a8-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="842a8-111">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="842a8-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="842a8-112">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="842a8-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="842a8-113">Veja também</span><span class="sxs-lookup"><span data-stu-id="842a8-113">See also</span></span>

- [<span data-ttu-id="842a8-114">Interface ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="842a8-114">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
