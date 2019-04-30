---
title: Método ICorDebugThread2::GetVolatileOSThreadID
ms.date: 03/30/2017
api_name:
- ICorDebugThread2.GetVolatileOSThreadID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread2::GetVolatileOSThreadID
helpviewer_keywords:
- GetVolatileOSThreadID method [.NET Framework debugging]
- ICorDebugThread2::GetVolatileOSThreadID method [.NET Framework debugging]
ms.assetid: f0922545-c2cf-40c8-9ef6-ca033563e682
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a9bf96371798b38bc392bc6bbd8f6fe8f97c7969
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61946270"
---
# <a name="icordebugthread2getvolatileosthreadid-method"></a><span data-ttu-id="e3759-102">Método ICorDebugThread2::GetVolatileOSThreadID</span><span class="sxs-lookup"><span data-stu-id="e3759-102">ICorDebugThread2::GetVolatileOSThreadID Method</span></span>
<span data-ttu-id="e3759-103">Obtém o identificador de thread do sistema operacional para este ICorDebugThread2.</span><span class="sxs-lookup"><span data-stu-id="e3759-103">Gets the operating system thread identifier for this ICorDebugThread2.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3759-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e3759-104">Syntax</span></span>  
  
```  
HRESULT GetVolatileOSThreadID (  
    [out] DWORD    *pdwTid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e3759-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e3759-105">Parameters</span></span>  
 `pdwTid`  
 <span data-ttu-id="e3759-106">[out] O identificador de thread do sistema operacional para este thread.</span><span class="sxs-lookup"><span data-stu-id="e3759-106">[out] The operating system thread identifier for this thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e3759-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e3759-107">Requirements</span></span>  
 <span data-ttu-id="e3759-108">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e3759-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e3759-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e3759-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e3759-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e3759-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e3759-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e3759-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
