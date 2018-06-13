---
title: Método ICorDebugCode::GetFunction
ms.date: 03/30/2017
api_name:
- ICorDebugCode.GetFunction
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::GetFunction
helpviewer_keywords:
- GetFunction method, ICorDebugCode interface [.NET Framework debugging]
- ICorDebugCode::GetFunction method [.NET Framework debugging]
ms.assetid: c568b737-fdb2-4816-accd-051f5ab760f1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8d0e7f20be3f18e49dcc1b986460d5da0c3d7777
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33401934"
---
# <a name="icordebugcodegetfunction-method"></a><span data-ttu-id="dd5ff-102">Método ICorDebugCode::GetFunction</span><span class="sxs-lookup"><span data-stu-id="dd5ff-102">ICorDebugCode::GetFunction Method</span></span>
<span data-ttu-id="dd5ff-103">Obtém o "ICorDebugFunction" associado a essa "ICorDebugCode".</span><span class="sxs-lookup"><span data-stu-id="dd5ff-103">Gets the "ICorDebugFunction" associated with this "ICorDebugCode".</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd5ff-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="dd5ff-104">Syntax</span></span>  
  
```  
HRESULT GetFunction (  
    [out] ICorDebugFunction **ppFunction  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dd5ff-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="dd5ff-105">Parameters</span></span>  
 `ppFunction`  
 <span data-ttu-id="dd5ff-106">[out] Um ponteiro para o endereço da função.</span><span class="sxs-lookup"><span data-stu-id="dd5ff-106">[out] A pointer to the address of the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dd5ff-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="dd5ff-107">Remarks</span></span>  
 <span data-ttu-id="dd5ff-108">`ICorDebugCode` e `ICorDebugFunction` manter uma relação um para um.</span><span class="sxs-lookup"><span data-stu-id="dd5ff-108">`ICorDebugCode` and `ICorDebugFunction` maintain a one-to-one relationship.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dd5ff-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="dd5ff-109">Requirements</span></span>  
 <span data-ttu-id="dd5ff-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dd5ff-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dd5ff-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="dd5ff-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dd5ff-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dd5ff-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dd5ff-113">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dd5ff-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd5ff-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dd5ff-114">See Also</span></span>  
 
