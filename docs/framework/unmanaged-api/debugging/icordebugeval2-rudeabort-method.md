---
title: Método ICorDebugEval2::RudeAbort
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.RudeAbort
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::RudeAbort
helpviewer_keywords:
- ICorDebugEval2::RudeAbort method [.NET Framework debugging]
- RudeAbort method, ICorDebugEval2 interface [.NET Framework debugging]
ms.assetid: 02468edf-d32b-4cb3-aaa8-3dd2abfc8b25
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0aabff090634f1ecdeec5636336ad1fb77b8b81c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61988917"
---
# <a name="icordebugeval2rudeabort-method"></a><span data-ttu-id="d0f84-102">Método ICorDebugEval2::RudeAbort</span><span class="sxs-lookup"><span data-stu-id="d0f84-102">ICorDebugEval2::RudeAbort Method</span></span>
<span data-ttu-id="d0f84-103">Anula o cálculo que este `ICorDebugEval2` está executando no momento.</span><span class="sxs-lookup"><span data-stu-id="d0f84-103">Aborts the computation that this `ICorDebugEval2` is currently performing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0f84-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d0f84-104">Syntax</span></span>  
  
```  
HRESULT RudeAbort ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="d0f84-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="d0f84-105">Remarks</span></span>  
 <span data-ttu-id="d0f84-106">`RudeAbort` não libera todos os bloqueios que mantém o avaliador, portanto, ele deixa a sessão de depuração em um estado não seguro.</span><span class="sxs-lookup"><span data-stu-id="d0f84-106">`RudeAbort` does not release any locks that the evaluator holds, so it leaves the debugging session in an unsafe state.</span></span> <span data-ttu-id="d0f84-107">Chame esse método com muito cuidado.</span><span class="sxs-lookup"><span data-stu-id="d0f84-107">Call this method with extreme caution.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d0f84-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d0f84-108">Requirements</span></span>  
 <span data-ttu-id="d0f84-109">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d0f84-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d0f84-110">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d0f84-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d0f84-111">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d0f84-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d0f84-112">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d0f84-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
