---
title: Método ICorDebugEval::IsActive
ms.date: 03/30/2017
api_name:
- ICorDebugEval.IsActive
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::IsActive
helpviewer_keywords:
- IsActive method, ICorDebugEval interface [.NET Framework debugging]
- ICorDebugEval::IsActive method [.NET Framework debugging]
ms.assetid: bf2bba24-d278-43bd-b1c5-35680e748d3e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2fe29b3e35d2fbd42fac2d9ec1d1c594abe1239c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugevalisactive-method"></a><span data-ttu-id="032d7-102">Método ICorDebugEval::IsActive</span><span class="sxs-lookup"><span data-stu-id="032d7-102">ICorDebugEval::IsActive Method</span></span>
<span data-ttu-id="032d7-103">Obtém um valor que indica se este objeto ICorDebugEval está em execução.</span><span class="sxs-lookup"><span data-stu-id="032d7-103">Gets a value that indicates whether this ICorDebugEval object is currently executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="032d7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="032d7-104">Syntax</span></span>  
  
```  
HRESULT IsActive (  
    [out] BOOL              *pbActive  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="032d7-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="032d7-105">Parameters</span></span>  
 `pbActive`  
 <span data-ttu-id="032d7-106">[out] Ponteiro para um valor que indica se esta avaliação está ativa.</span><span class="sxs-lookup"><span data-stu-id="032d7-106">[out] Pointer to a value that indicates whether this evaluation is active.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="032d7-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="032d7-107">Requirements</span></span>  
 <span data-ttu-id="032d7-108">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="032d7-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="032d7-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="032d7-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="032d7-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="032d7-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="032d7-111">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="032d7-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
