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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 682d6684b6c86485530b9e5283d843f3b2eb7e46
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33413797"
---
# <a name="icordebugevalabort-method"></a><span data-ttu-id="37d28-102">Método ICorDebugEval::Abort</span><span class="sxs-lookup"><span data-stu-id="37d28-102">ICorDebugEval::Abort Method</span></span>
<span data-ttu-id="37d28-103">Anula a computação que este objeto ICorDebugEval está executando no momento.</span><span class="sxs-lookup"><span data-stu-id="37d28-103">Aborts the computation this ICorDebugEval object is currently performing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37d28-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="37d28-104">Syntax</span></span>  
  
```  
HRESULT Abort ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="37d28-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="37d28-105">Remarks</span></span>  
 <span data-ttu-id="37d28-106">Se a avaliação é aninhada e ele não é o mais recente, o `Abort` método pode falhar.</span><span class="sxs-lookup"><span data-stu-id="37d28-106">If the evaluation is nested and it is not the most recent one, the `Abort` method may fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="37d28-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="37d28-107">Requirements</span></span>  
 <span data-ttu-id="37d28-108">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="37d28-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="37d28-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="37d28-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="37d28-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="37d28-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="37d28-111">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="37d28-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
