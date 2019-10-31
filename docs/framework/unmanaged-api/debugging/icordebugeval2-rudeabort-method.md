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
ms.openlocfilehash: a486935d5d53a6fc7d862160ed1186c5774814c7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73084793"
---
# <a name="icordebugeval2rudeabort-method"></a><span data-ttu-id="a3040-102">Método ICorDebugEval2::RudeAbort</span><span class="sxs-lookup"><span data-stu-id="a3040-102">ICorDebugEval2::RudeAbort Method</span></span>
<span data-ttu-id="a3040-103">Anula a computação que esse `ICorDebugEval2` está executando no momento.</span><span class="sxs-lookup"><span data-stu-id="a3040-103">Aborts the computation that this `ICorDebugEval2` is currently performing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3040-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a3040-104">Syntax</span></span>  
  
```cpp  
HRESULT RudeAbort ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="a3040-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="a3040-105">Remarks</span></span>  
 <span data-ttu-id="a3040-106">`RudeAbort` não libera os bloqueios que o avaliador mantém, portanto, deixa a sessão de depuração em um estado não seguro.</span><span class="sxs-lookup"><span data-stu-id="a3040-106">`RudeAbort` does not release any locks that the evaluator holds, so it leaves the debugging session in an unsafe state.</span></span> <span data-ttu-id="a3040-107">Chame esse método com extrema cautela.</span><span class="sxs-lookup"><span data-stu-id="a3040-107">Call this method with extreme caution.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a3040-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a3040-108">Requirements</span></span>  
 <span data-ttu-id="a3040-109">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a3040-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a3040-110">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a3040-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a3040-111">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a3040-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a3040-112">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a3040-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
