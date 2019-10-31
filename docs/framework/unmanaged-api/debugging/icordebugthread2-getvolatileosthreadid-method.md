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
ms.openlocfilehash: 2e49dd95cf5d78c0a0f4fa075126eca19dea2693
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138710"
---
# <a name="icordebugthread2getvolatileosthreadid-method"></a><span data-ttu-id="399ac-102">Método ICorDebugThread2::GetVolatileOSThreadID</span><span class="sxs-lookup"><span data-stu-id="399ac-102">ICorDebugThread2::GetVolatileOSThreadID Method</span></span>
<span data-ttu-id="399ac-103">Obtém o identificador de thread do sistema operacional para este ICorDebugThread2.</span><span class="sxs-lookup"><span data-stu-id="399ac-103">Gets the operating system thread identifier for this ICorDebugThread2.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="399ac-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="399ac-104">Syntax</span></span>  
  
```cpp  
HRESULT GetVolatileOSThreadID (  
    [out] DWORD    *pdwTid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="399ac-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="399ac-105">Parameters</span></span>  
 `pdwTid`  
 <span data-ttu-id="399ac-106">fora O identificador de thread do sistema operacional para este thread.</span><span class="sxs-lookup"><span data-stu-id="399ac-106">[out] The operating system thread identifier for this thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="399ac-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="399ac-107">Requirements</span></span>  
 <span data-ttu-id="399ac-108">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="399ac-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="399ac-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="399ac-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="399ac-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="399ac-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="399ac-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="399ac-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
