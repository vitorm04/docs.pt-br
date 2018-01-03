---
title: "Método ICorDebugEval2::RudeAbort"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugEval2.RudeAbort
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugEval2::RudeAbort
helpviewer_keywords:
- ICorDebugEval2::RudeAbort method [.NET Framework debugging]
- RudeAbort method, ICorDebugEval2 interface [.NET Framework debugging]
ms.assetid: 02468edf-d32b-4cb3-aaa8-3dd2abfc8b25
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4a681b19eaa4a1828e6d6b5276713d61a3625121
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugeval2rudeabort-method"></a><span data-ttu-id="58711-102">Método ICorDebugEval2::RudeAbort</span><span class="sxs-lookup"><span data-stu-id="58711-102">ICorDebugEval2::RudeAbort Method</span></span>
<span data-ttu-id="58711-103">Anula o cálculo que este `ICorDebugEval2` está executando no momento.</span><span class="sxs-lookup"><span data-stu-id="58711-103">Aborts the computation that this `ICorDebugEval2` is currently performing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58711-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="58711-104">Syntax</span></span>  
  
```  
HRESULT RudeAbort ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="58711-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="58711-105">Remarks</span></span>  
 <span data-ttu-id="58711-106">`RudeAbort`não liberar todos os bloqueios que mantém o avaliador, portanto ele deixa a sessão de depuração em um estado não seguro.</span><span class="sxs-lookup"><span data-stu-id="58711-106">`RudeAbort` does not release any locks that the evaluator holds, so it leaves the debugging session in an unsafe state.</span></span> <span data-ttu-id="58711-107">Chame este método com extrema cautela.</span><span class="sxs-lookup"><span data-stu-id="58711-107">Call this method with extreme caution.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="58711-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="58711-108">Requirements</span></span>  
 <span data-ttu-id="58711-109">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="58711-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="58711-110">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="58711-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="58711-111">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="58711-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="58711-112">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="58711-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
