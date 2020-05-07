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
ms.openlocfilehash: 9f785eafa8925324e3bd269ca08a3b1367b74c44
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82893586"
---
# <a name="icordebugcodegetfunction-method"></a><span data-ttu-id="cd440-102">Método ICorDebugCode::GetFunction</span><span class="sxs-lookup"><span data-stu-id="cd440-102">ICorDebugCode::GetFunction Method</span></span>
<span data-ttu-id="cd440-103">Obtém o "ICorDebugFunction" associado a este "ICorDebugCode".</span><span class="sxs-lookup"><span data-stu-id="cd440-103">Gets the "ICorDebugFunction" associated with this "ICorDebugCode".</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd440-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cd440-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFunction (  
    [out] ICorDebugFunction **ppFunction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cd440-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="cd440-105">Parameters</span></span>  
 `ppFunction`  
 <span data-ttu-id="cd440-106">fora Um ponteiro para o endereço da função.</span><span class="sxs-lookup"><span data-stu-id="cd440-106">[out] A pointer to the address of the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cd440-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="cd440-107">Remarks</span></span>  
 <span data-ttu-id="cd440-108">`ICorDebugCode`e `ICorDebugFunction` manter uma relação um-para-um.</span><span class="sxs-lookup"><span data-stu-id="cd440-108">`ICorDebugCode` and `ICorDebugFunction` maintain a one-to-one relationship.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cd440-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="cd440-109">Requirements</span></span>  
 <span data-ttu-id="cd440-110">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cd440-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cd440-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cd440-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cd440-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cd440-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cd440-113">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cd440-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
