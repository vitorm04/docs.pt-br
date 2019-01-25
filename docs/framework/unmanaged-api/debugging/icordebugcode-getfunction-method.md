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
ms.openlocfilehash: dd544619f9e5fb85a0b08b91ead8231ea25743cb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54651221"
---
# <a name="icordebugcodegetfunction-method"></a><span data-ttu-id="37332-102">Método ICorDebugCode::GetFunction</span><span class="sxs-lookup"><span data-stu-id="37332-102">ICorDebugCode::GetFunction Method</span></span>
<span data-ttu-id="37332-103">Obtém o "ICorDebugFunction" associado com esta "ICorDebugCode".</span><span class="sxs-lookup"><span data-stu-id="37332-103">Gets the "ICorDebugFunction" associated with this "ICorDebugCode".</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37332-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="37332-104">Syntax</span></span>  
  
```  
HRESULT GetFunction (  
    [out] ICorDebugFunction **ppFunction  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="37332-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="37332-105">Parameters</span></span>  
 `ppFunction`  
 <span data-ttu-id="37332-106">[out] Um ponteiro para o endereço da função.</span><span class="sxs-lookup"><span data-stu-id="37332-106">[out] A pointer to the address of the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="37332-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="37332-107">Remarks</span></span>  
 <span data-ttu-id="37332-108">`ICorDebugCode` e `ICorDebugFunction` mantenham uma relação um para um.</span><span class="sxs-lookup"><span data-stu-id="37332-108">`ICorDebugCode` and `ICorDebugFunction` maintain a one-to-one relationship.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="37332-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="37332-109">Requirements</span></span>  
 <span data-ttu-id="37332-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="37332-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="37332-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="37332-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="37332-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="37332-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="37332-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="37332-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37332-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="37332-114">See also</span></span>

