---
title: "Método ICorDebugEval::Abort"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugEval.Abort
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugEval::Abort
helpviewer_keywords:
- Abort method, ICorDebugEval interface [.NET Framework debugging]
- ICorDebugEval::Abort method [.NET Framework debugging]
ms.assetid: 7070b6d0-f2e0-44ff-b124-0944cd807e69
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 064febeec32e5c43b6b73ef2b3a44625f151eb48
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugevalabort-method"></a><span data-ttu-id="571fe-102">Método ICorDebugEval::Abort</span><span class="sxs-lookup"><span data-stu-id="571fe-102">ICorDebugEval::Abort Method</span></span>
<span data-ttu-id="571fe-103">Anula a computação que este objeto ICorDebugEval está executando no momento.</span><span class="sxs-lookup"><span data-stu-id="571fe-103">Aborts the computation this ICorDebugEval object is currently performing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="571fe-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="571fe-104">Syntax</span></span>  
  
```  
HRESULT Abort ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="571fe-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="571fe-105">Remarks</span></span>  
 <span data-ttu-id="571fe-106">Se a avaliação é aninhada e ele não é o mais recente, o `Abort` método pode falhar.</span><span class="sxs-lookup"><span data-stu-id="571fe-106">If the evaluation is nested and it is not the most recent one, the `Abort` method may fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="571fe-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="571fe-107">Requirements</span></span>  
 <span data-ttu-id="571fe-108">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="571fe-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="571fe-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="571fe-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="571fe-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="571fe-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="571fe-111">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="571fe-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
