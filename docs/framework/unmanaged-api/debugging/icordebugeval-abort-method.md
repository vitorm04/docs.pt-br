---
title: Método ICorDebugEval::Abort
ms.date: 03/30/2017
api_name:
- ICorDebugEval.Abort
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::Abort
helpviewer_keywords:
- Abort method, ICorDebugEval interface [.NET Framework debugging]
- ICorDebugEval::Abort method [.NET Framework debugging]
ms.assetid: 7070b6d0-f2e0-44ff-b124-0944cd807e69
topic_type:
- apiref
ms.openlocfilehash: 78402e5e099815fe309618e692285de91b8b29f7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124235"
---
# <a name="icordebugevalabort-method"></a><span data-ttu-id="416ae-102">Método ICorDebugEval::Abort</span><span class="sxs-lookup"><span data-stu-id="416ae-102">ICorDebugEval::Abort Method</span></span>
<span data-ttu-id="416ae-103">Anula a computação que esse objeto ICorDebugEval está executando no momento.</span><span class="sxs-lookup"><span data-stu-id="416ae-103">Aborts the computation this ICorDebugEval object is currently performing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="416ae-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="416ae-104">Syntax</span></span>  
  
```cpp  
HRESULT Abort ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="416ae-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="416ae-105">Remarks</span></span>  
 <span data-ttu-id="416ae-106">Se a avaliação estiver aninhada e não for a mais recente, o método `Abort` poderá falhar.</span><span class="sxs-lookup"><span data-stu-id="416ae-106">If the evaluation is nested and it is not the most recent one, the `Abort` method may fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="416ae-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="416ae-107">Requirements</span></span>  
 <span data-ttu-id="416ae-108">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="416ae-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="416ae-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="416ae-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="416ae-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="416ae-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="416ae-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="416ae-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
