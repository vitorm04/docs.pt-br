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
ms.openlocfilehash: c5d8168649f6a0c75844da0ee68bf3782efc9024
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57483856"
---
# <a name="icordebugcodegetfunction-method"></a><span data-ttu-id="aa87d-102">Método ICorDebugCode::GetFunction</span><span class="sxs-lookup"><span data-stu-id="aa87d-102">ICorDebugCode::GetFunction Method</span></span>
<span data-ttu-id="aa87d-103">Obtém o "ICorDebugFunction" associado com esta "ICorDebugCode".</span><span class="sxs-lookup"><span data-stu-id="aa87d-103">Gets the "ICorDebugFunction" associated with this "ICorDebugCode".</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa87d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="aa87d-104">Syntax</span></span>  
  
```  
HRESULT GetFunction (  
    [out] ICorDebugFunction **ppFunction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aa87d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="aa87d-105">Parameters</span></span>  
 `ppFunction`  
 <span data-ttu-id="aa87d-106">[out] Um ponteiro para o endereço da função.</span><span class="sxs-lookup"><span data-stu-id="aa87d-106">[out] A pointer to the address of the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aa87d-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="aa87d-107">Remarks</span></span>  
 <span data-ttu-id="aa87d-108">`ICorDebugCode` e `ICorDebugFunction` mantenham uma relação um para um.</span><span class="sxs-lookup"><span data-stu-id="aa87d-108">`ICorDebugCode` and `ICorDebugFunction` maintain a one-to-one relationship.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aa87d-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="aa87d-109">Requirements</span></span>  
 <span data-ttu-id="aa87d-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aa87d-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aa87d-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="aa87d-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="aa87d-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="aa87d-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="aa87d-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aa87d-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa87d-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="aa87d-114">See also</span></span>

